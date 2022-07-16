
<a name="0xc0deb00c_Match"></a>

# Module `0xc0deb00c::Match`

Matching engine functionality, integrating user-side and book-side
modules


<a name="@Testing_0"></a>

## Testing


Test-only constants and functions are used to construct a test
market with simulated positions. During testing, the "incoming
market order" fills against the "target position" during iterated
traversal, with markets constructed so that on either side, user 1's
position is filled before user 2's, which is filled before user 3's.
Hence, the following tests exercise logic at sequential milestones
along the process of clearing out the book:
* <code>ask_partial_1()</code>
* <code>bid_exact_1()</code>
* <code>bid_partial_2()</code>
* <code>ask_exact_2()</code>
* <code>ask_partial_3()</code>
* <code>bid_exact_3()</code>
* <code>ask_clear_book()</code>


-  [Testing](#@Testing_0)
-  [Constants](#@Constants_1)
-  [Function `submit_market_order`](#0xc0deb00c_Match_submit_market_order)
    -  [Parameters](#@Parameters_2)
    -  [Abort conditions](#@Abort_conditions_3)
-  [Function `fill_market_order`](#0xc0deb00c_Match_fill_market_order)
    -  [Parameters](#@Parameters_4)
    -  [Terminology](#@Terminology_5)
    -  [Returns](#@Returns_6)
    -  [Assumptions](#@Assumptions_7)


<pre><code><b>use</b> <a href="../../../build/MoveStdlib/docs/Signer.md#0x1_Signer">0x1::Signer</a>;
<b>use</b> <a href="Book.md#0xc0deb00c_Book">0xc0deb00c::Book</a>;
<b>use</b> <a href="Caps.md#0xc0deb00c_Caps">0xc0deb00c::Caps</a>;
<b>use</b> <a href="ID.md#0xc0deb00c_ID">0xc0deb00c::ID</a>;
<b>use</b> <a href="Orders.md#0xc0deb00c_Orders">0xc0deb00c::Orders</a>;
<b>use</b> <a href="User.md#0xc0deb00c_User">0xc0deb00c::User</a>;
</code></pre>



<a name="@Constants_1"></a>

## Constants


<a name="0xc0deb00c_Match_ASK"></a>

Ask flag


<pre><code><b>const</b> <a href="Match.md#0xc0deb00c_Match_ASK">ASK</a>: bool = <b>true</b>;
</code></pre>



<a name="0xc0deb00c_Match_BID"></a>

Bid flag


<pre><code><b>const</b> <a href="Match.md#0xc0deb00c_Match_BID">BID</a>: bool = <b>false</b>;
</code></pre>



<a name="0xc0deb00c_Match_E_NOT_ENOUGH_COLLATERAL"></a>

When not enough collateral for an operation


<pre><code><b>const</b> <a href="Match.md#0xc0deb00c_Match_E_NOT_ENOUGH_COLLATERAL">E_NOT_ENOUGH_COLLATERAL</a>: u64 = 2;
</code></pre>



<a name="0xc0deb00c_Match_E_NO_MARKET"></a>

When no corresponding market registered


<pre><code><b>const</b> <a href="Match.md#0xc0deb00c_Match_E_NO_MARKET">E_NO_MARKET</a>: u64 = 0;
</code></pre>



<a name="0xc0deb00c_Match_E_NO_O_C"></a>

When user does not have order collateral container


<pre><code><b>const</b> <a href="Match.md#0xc0deb00c_Match_E_NO_O_C">E_NO_O_C</a>: u64 = 1;
</code></pre>



<a name="0xc0deb00c_Match_BUY"></a>

Flag for submitting a market buy


<pre><code><b>const</b> <a href="Match.md#0xc0deb00c_Match_BUY">BUY</a>: bool = <b>true</b>;
</code></pre>



<a name="0xc0deb00c_Match_SELL"></a>

Flag for submitting a market sell


<pre><code><b>const</b> <a href="Match.md#0xc0deb00c_Match_SELL">SELL</a>: bool = <b>true</b>;
</code></pre>



<a name="0xc0deb00c_Match_submit_market_order"></a>

## Function `submit_market_order`

Submit market order for market <code>&lt;B, Q, E&gt;</code>, filling as much
as possible against the book


<a name="@Parameters_2"></a>

### Parameters

* <code>user</code>: User submitting a limit order
* <code>host</code>: The market host (See <code>Econia::Registry</code>)
* <code>side</code>: <code><a href="Match.md#0xc0deb00c_Match_ASK">ASK</a></code> or <code><a href="Match.md#0xc0deb00c_Match_BID">BID</a></code>
* <code>price</code>: Scaled integer price (see <code>Econia::ID</code>)
* <code>requested_size</code>: Requested number of base coin parcels to be
* <code>max_quote_to_spend</code>: Maximum number of quote coins that can
be spent in the case of a market buy (unused in case of a
market sell)


<a name="@Abort_conditions_3"></a>

### Abort conditions

* If no such market exists at host address
* If user does not have order collateral container for market
* If user does not have enough collateral
* If placing an order would cross the spread (temporary)


<pre><code><b>fun</b> <a href="Match.md#0xc0deb00c_Match_submit_market_order">submit_market_order</a>&lt;B, Q, E&gt;(user: &signer, host: <b>address</b>, side: bool, requested_size: u64, max_quote_to_spend: u64)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>fun</b> <a href="Match.md#0xc0deb00c_Match_submit_market_order">submit_market_order</a>&lt;B, Q, E&gt;(
    user: &signer,
    host: <b>address</b>,
    side: bool,
    requested_size: u64,
    max_quote_to_spend: u64
) {
    // Get book-side and open-orders side capabilities
    <b>let</b> (book_cap, orders_cap) = (book_cap(), orders_cap());
    // Update user sequence counter
    update_user_seq_counter(user, &orders_cap);
    // Assert market <b>exists</b> at given host <b>address</b>
    <b>assert</b>!(exists_book&lt;B, Q, E&gt;(host, &book_cap), <a href="Match.md#0xc0deb00c_Match_E_NO_MARKET">E_NO_MARKET</a>);
    <b>let</b> user_address = address_of(user); // Get user <b>address</b>
    // Assert user <b>has</b> order collateral container
    <b>assert</b>!(exists_o_c&lt;B, Q, E&gt;(user_address, &orders_cap), <a href="Match.md#0xc0deb00c_Match_E_NO_O_C">E_NO_O_C</a>);
    // Get available collateral for user on given market
    <b>let</b> (base_available, quote_available) =
        get_available_collateral&lt;B, Q, E&gt;(user_address, &orders_cap);
    // If submitting a market buy (<b>if</b> filling against ask positions
    // on the order book)
    <b>if</b> (side == <a href="Match.md#0xc0deb00c_Match_BUY">BUY</a>) {
        // Assert user <b>has</b> enough quote coins <b>to</b> spend
        <b>assert</b>!(quote_available &gt;= max_quote_to_spend,
            <a href="Match.md#0xc0deb00c_Match_E_NOT_ENOUGH_COLLATERAL">E_NOT_ENOUGH_COLLATERAL</a>);
        // Fill a market order through the matching engine, storing
        // numer of quote coins spent
        <b>let</b> (_, quote_coins_spent) = <a href="Match.md#0xc0deb00c_Match_fill_market_order">fill_market_order</a>&lt;B, Q, E&gt;(
            host, user_address, <a href="Match.md#0xc0deb00c_Match_ASK">ASK</a>, requested_size, max_quote_to_spend,
            &book_cap());
        // Update count of available quote coins
        dec_available_collateral&lt;B, Q, E&gt;(
            user_address, 0, quote_coins_spent, &orders_cap);
    } <b>else</b> { // If submitting a market sell (filling against bids)
        // Get number of base coins required <b>to</b> execute market sell
        <b>let</b> base_coins_required = requested_size *
            orders_scale_factor&lt;B, Q, E&gt;(user_address, &orders_cap());
        // Assert user <b>has</b> enough available base coins <b>to</b> sell
        <b>assert</b>!(base_available &gt;= base_coins_required,
            <a href="Match.md#0xc0deb00c_Match_E_NOT_ENOUGH_COLLATERAL">E_NOT_ENOUGH_COLLATERAL</a>);
        // Fill a market order through the matching engine, storing
        // numer of base coin subunits sold
        <b>let</b> (base_coins_sold, _) = <a href="Match.md#0xc0deb00c_Match_fill_market_order">fill_market_order</a>&lt;B, Q, E&gt;(
            host, user_address, <a href="Match.md#0xc0deb00c_Match_BID">BID</a>, requested_size, 0, &book_cap());
        // Update count of available base coins
        dec_available_collateral&lt;B, Q, E&gt;(
            user_address, base_coins_sold, 0, &orders_cap);
    }
}
</code></pre>



</details>

<a name="0xc0deb00c_Match_fill_market_order"></a>

## Function `fill_market_order`

Fill a market order against the book as much as possible,
returning when there is no liquidity left or when order is
completely filled


<a name="@Parameters_4"></a>

### Parameters

* <code>host</code> Host of corresponding order book
* <code>addr</code>: Address of user placing market order
* <code>side</code>: <code><a href="Match.md#0xc0deb00c_Match_ASK">ASK</a></code> or <code><a href="Match.md#0xc0deb00c_Match_BID">BID</a></code>, denoting the side on the order book
which should be filled against. If <code><a href="Match.md#0xc0deb00c_Match_ASK">ASK</a></code>, user is submitting
a market buy, if <code><a href="Match.md#0xc0deb00c_Match_BID">BID</a></code>, user is submitting a market sell
* <code>requested_size</code>: Base coin parcels to be filled
* <code>quote_available</code>: Quote coin parcels available for filling if
filling against asks
* <code>book_cap</code>: Immutable reference to <code>Econia::Book:FriendCap</code>


<a name="@Terminology_5"></a>

### Terminology

* "Incoming order" is the market order being matched against
the order book
* "Target position" is the position on the book for each stage
of iterated traversal


<a name="@Returns_6"></a>

### Returns

* <code>u64</code>: Amount of base coin subunits filled
* <code>u64</code>: Amount of quote coin subunits filled


<a name="@Assumptions_7"></a>

### Assumptions

* Order book has been properly initialized at host address
* <code>size</code> is nonzero


<pre><code><b>fun</b> <a href="Match.md#0xc0deb00c_Match_fill_market_order">fill_market_order</a>&lt;B, Q, E&gt;(host: <b>address</b>, addr: <b>address</b>, side: bool, requested_size: u64, quote_available: u64, book_cap: &<a href="Book.md#0xc0deb00c_Book_FriendCap">Book::FriendCap</a>): (u64, u64)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>fun</b> <a href="Match.md#0xc0deb00c_Match_fill_market_order">fill_market_order</a>&lt;B, Q, E&gt;(
    host: <b>address</b>,
    addr: <b>address</b>,
    side: bool,
    requested_size: u64,
    quote_available: u64,
    book_cap: &BookCap
): (
    u64,
    u64,
) {
    // Get number of positions on corresponding order book side
    <b>let</b> n_positions = <b>if</b> (side == <a href="Match.md#0xc0deb00c_Match_ASK">ASK</a>) n_asks&lt;B, Q, E&gt;(host, book_cap)
        <b>else</b> n_bids&lt;B, Q, E&gt;(host, book_cap);
    // Return no fills <b>if</b> no positions on book
    <b>if</b> (n_positions == 0) <b>return</b> (0, 0);
    // Get scale factor of corresponding order book
    <b>let</b> scale_factor = scale_factor&lt;B, Q, E&gt;(host, book_cap);
    // Initialize counters for base coin parcels and quote coin
    // subunits filled
    <b>let</b> (base_parcels_filled, quote_coins_filled) = (0, 0);
    // Initialize traversal, storing <a href="ID.md#0xc0deb00c_ID">ID</a> of target position, <b>address</b>
    // of user holding it, the parent field of corresponding tree
    // node, child index of corresponding node, amount filled, <b>if</b> an
    // exact match between incoming order and target position, and
    // <b>if</b> the incoming order <b>has</b> insufficient quote coins in case of
    // an ask
    <b>let</b> (target_id, target_addr, target_p_f, target_c_i, filled, exact,
         insufficient_quote) =
        init_traverse_fill&lt;B, Q, E&gt;(
            host, addr, side, requested_size, quote_available, book_cap);
    <b>loop</b> { // Begin traversal <b>loop</b>
        // Update counter for number of base parcels filled
        base_parcels_filled = base_parcels_filled + filled;
        // Update counter for number of quote coins filled
        quote_coins_filled = quote_coins_filled + id_p(target_id) * filled;
        // Decrement requested size left <b>to</b> match
        requested_size = requested_size - filled;
        // Determine <b>if</b> target position completely filled
        <b>let</b> complete = ((exact || requested_size &gt; 0) &&
                        !insufficient_quote);
        // Route funds between conterparties, <b>update</b> open orders
        process_fill&lt;B, Q, E&gt;(target_addr, addr, side, target_id, filled,
                              scale_factor, complete);
        // If incoming order unfilled and can traverse
        <b>if</b> (requested_size &gt; 0 && n_positions &gt; 1 && !insufficient_quote) {
            // Traverse pop fill <b>to</b> next position
            (target_id, target_addr, target_p_f, target_c_i, filled, exact,
                insufficient_quote)
                = traverse_pop_fill&lt;B, Q, E&gt;(
                    host, addr, side, requested_size, quote_available,
                    n_positions, target_id, target_p_f, target_c_i,
                    book_cap);
            // Decrement count of positions on book for given side
            n_positions = n_positions - 1;
        } <b>else</b> { // If should not <b>continue</b> iterated traverse fill
            // Determine <b>if</b> a partial target fill was made
            <b>let</b> partial_target_fill =
                (requested_size == 0 && !exact) || insufficient_quote;
            // If anything other than a partial target fill made
            <b>if</b> (!partial_target_fill) {
                // Cancel target position
                cancel_position&lt;B, Q, E&gt;(host, side, target_id, book_cap);
            };
            // Refresh the max bid/<b>min</b> ask <a href="ID.md#0xc0deb00c_ID">ID</a> for the order book
            refresh_extreme_order_id&lt;B, Q, E&gt;(host, side, book_cap);
            <b>break</b> // Break out of iterated traversal <b>loop</b>
        };
    };
    // Return base coin subunits and quote coin subunits filled
    (base_parcels_filled * scale_factor, quote_coins_filled)
}
</code></pre>



</details>