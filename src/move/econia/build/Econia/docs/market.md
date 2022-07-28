
<a name="0xc0deb00c_market"></a>

# Module `0xc0deb00c::market`

Market-side functionality


-  [Resource `EconiaCapabilityStore`](#0xc0deb00c_market_EconiaCapabilityStore)
-  [Struct `Order`](#0xc0deb00c_market_Order)
-  [Resource `OrderBook`](#0xc0deb00c_market_OrderBook)
-  [Constants](#@Constants_0)
-  [Function `init_econia_capability_store`](#0xc0deb00c_market_init_econia_capability_store)
-  [Function `register_market`](#0xc0deb00c_market_register_market)
-  [Function `get_econia_capability`](#0xc0deb00c_market_get_econia_capability)
    -  [Assumes](#@Assumes_1)
-  [Function `init_book`](#0xc0deb00c_market_init_book)


<pre><code><b>use</b> <a href="">0x1::signer</a>;
<b>use</b> <a href="capability.md#0xc0deb00c_capability">0xc0deb00c::capability</a>;
<b>use</b> <a href="critbit.md#0xc0deb00c_critbit">0xc0deb00c::critbit</a>;
<b>use</b> <a href="registry.md#0xc0deb00c_registry">0xc0deb00c::registry</a>;
</code></pre>



<a name="0xc0deb00c_market_EconiaCapabilityStore"></a>

## Resource `EconiaCapabilityStore`

Stores an <code>EconiaCapability</code> for cross-module authorization


<pre><code><b>struct</b> <a href="market.md#0xc0deb00c_market_EconiaCapabilityStore">EconiaCapabilityStore</a> <b>has</b> key
</code></pre>



<details>
<summary>Fields</summary>


<dl>
<dt>
<code>econia_capability: <a href="capability.md#0xc0deb00c_capability_EconiaCapability">capability::EconiaCapability</a></code>
</dt>
<dd>

</dd>
</dl>


</details>

<a name="0xc0deb00c_market_Order"></a>

## Struct `Order`

An order on the order book


<pre><code><b>struct</b> <a href="market.md#0xc0deb00c_market_Order">Order</a> <b>has</b> store
</code></pre>



<details>
<summary>Fields</summary>


<dl>
<dt>
<code>base_parcels: u64</code>
</dt>
<dd>
 Number of base parcels to be filled
</dd>
<dt>
<code><a href="user.md#0xc0deb00c_user">user</a>: <b>address</b></code>
</dt>
<dd>
 Address of corresponding user
</dd>
<dt>
<code>custodian_id: u8</code>
</dt>
<dd>
 For given user, custodian ID of corresponding market account
</dd>
</dl>


</details>

<a name="0xc0deb00c_market_OrderBook"></a>

## Resource `OrderBook`

An order book for the given market


<pre><code><b>struct</b> <a href="market.md#0xc0deb00c_market_OrderBook">OrderBook</a>&lt;B, Q, E&gt; <b>has</b> key
</code></pre>



<details>
<summary>Fields</summary>


<dl>
<dt>
<code>scale_factor: u64</code>
</dt>
<dd>
 Number of base units in a base parcel
</dd>
<dt>
<code>asks: <a href="critbit.md#0xc0deb00c_critbit_CritBitTree">critbit::CritBitTree</a>&lt;<a href="market.md#0xc0deb00c_market_Order">market::Order</a>&gt;</code>
</dt>
<dd>
 Asks tree
</dd>
<dt>
<code>bids: <a href="critbit.md#0xc0deb00c_critbit_CritBitTree">critbit::CritBitTree</a>&lt;<a href="market.md#0xc0deb00c_market_Order">market::Order</a>&gt;</code>
</dt>
<dd>
 Bids tree
</dd>
<dt>
<code>min_ask: u128</code>
</dt>
<dd>
 Order ID of minimum ask, per price-time priority
</dd>
<dt>
<code>max_bid: u128</code>
</dt>
<dd>
 Order ID of maximum bid, per price-time priority
</dd>
<dt>
<code>counter: u64</code>
</dt>
<dd>
 Serial counter for number of orders placed on book
</dd>
</dl>


</details>

<a name="@Constants_0"></a>

## Constants


<a name="0xc0deb00c_market_E_NOT_ECONIA"></a>

When caller is not Econia


<pre><code><b>const</b> <a href="market.md#0xc0deb00c_market_E_NOT_ECONIA">E_NOT_ECONIA</a>: u64 = 1;
</code></pre>



<a name="0xc0deb00c_market_LEFT"></a>

Left direction, denoting predecessor traversal


<pre><code><b>const</b> <a href="market.md#0xc0deb00c_market_LEFT">LEFT</a>: bool = <b>true</b>;
</code></pre>



<a name="0xc0deb00c_market_RIGHT"></a>

Right direction, denoting successor traversal


<pre><code><b>const</b> <a href="market.md#0xc0deb00c_market_RIGHT">RIGHT</a>: bool = <b>false</b>;
</code></pre>



<a name="0xc0deb00c_market_ASK"></a>

Ask flag


<pre><code><b>const</b> <a href="market.md#0xc0deb00c_market_ASK">ASK</a>: bool = <b>true</b>;
</code></pre>



<a name="0xc0deb00c_market_BID"></a>

Bid flag


<pre><code><b>const</b> <a href="market.md#0xc0deb00c_market_BID">BID</a>: bool = <b>false</b>;
</code></pre>



<a name="0xc0deb00c_market_E_BOOK_EXISTS"></a>

When an order book already exists at given address


<pre><code><b>const</b> <a href="market.md#0xc0deb00c_market_E_BOOK_EXISTS">E_BOOK_EXISTS</a>: u64 = 0;
</code></pre>



<a name="0xc0deb00c_market_E_CAPABILITY_STORE_EXISTS"></a>

When <code><a href="market.md#0xc0deb00c_market_EconiaCapabilityStore">EconiaCapabilityStore</a></code> already exists under Econia account


<pre><code><b>const</b> <a href="market.md#0xc0deb00c_market_E_CAPABILITY_STORE_EXISTS">E_CAPABILITY_STORE_EXISTS</a>: u64 = 2;
</code></pre>



<a name="0xc0deb00c_market_MAX_BID_DEFAULT"></a>

Default value for maximum bid order ID


<pre><code><b>const</b> <a href="market.md#0xc0deb00c_market_MAX_BID_DEFAULT">MAX_BID_DEFAULT</a>: u128 = 0;
</code></pre>



<a name="0xc0deb00c_market_MIN_ASK_DEFAULT"></a>

Default value for minimum ask order ID


<pre><code><b>const</b> <a href="market.md#0xc0deb00c_market_MIN_ASK_DEFAULT">MIN_ASK_DEFAULT</a>: u128 = 340282366920938463463374607431768211455;
</code></pre>



<a name="0xc0deb00c_market_init_econia_capability_store"></a>

## Function `init_econia_capability_store`

Initializes an <code><a href="market.md#0xc0deb00c_market_EconiaCapabilityStore">EconiaCapabilityStore</a></code>, aborting if one already
exists under the Econia account or if caller is not Econia


<pre><code><b>public</b> <b>fun</b> <a href="market.md#0xc0deb00c_market_init_econia_capability_store">init_econia_capability_store</a>(account: &<a href="">signer</a>)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="market.md#0xc0deb00c_market_init_econia_capability_store">init_econia_capability_store</a>(
    account: &<a href="">signer</a>
) {
    // Assert caller is Econia account
    <b>assert</b>!(address_of(account) == @econia, <a href="market.md#0xc0deb00c_market_E_NOT_ECONIA">E_NOT_ECONIA</a>);
    // Assert <a href="capability.md#0xc0deb00c_capability">capability</a> store not already registered
    <b>assert</b>!(!<b>exists</b>&lt;<a href="market.md#0xc0deb00c_market_EconiaCapabilityStore">EconiaCapabilityStore</a>&gt;(@econia),
        <a href="market.md#0xc0deb00c_market_E_CAPABILITY_STORE_EXISTS">E_CAPABILITY_STORE_EXISTS</a>);
    // Get new <a href="capability.md#0xc0deb00c_capability">capability</a> instance (aborts <b>if</b> caller is not Econia)
    <b>let</b> econia_capability = <a href="capability.md#0xc0deb00c_capability_get_econia_capability">capability::get_econia_capability</a>(account);
    <b>move_to</b>&lt;<a href="market.md#0xc0deb00c_market_EconiaCapabilityStore">EconiaCapabilityStore</a>&gt;(account, <a href="market.md#0xc0deb00c_market_EconiaCapabilityStore">EconiaCapabilityStore</a>{
        econia_capability}); // Move <b>to</b> account <a href="capability.md#0xc0deb00c_capability">capability</a> store
}
</code></pre>



</details>

<a name="0xc0deb00c_market_register_market"></a>

## Function `register_market`

Register a market for the given base type, quote type,
scale exponent type, and move an <code><a href="market.md#0xc0deb00c_market_OrderBook">OrderBook</a></code> to <code>host</code>.


<pre><code><b>public</b> <b>fun</b> <a href="market.md#0xc0deb00c_market_register_market">register_market</a>&lt;B, Q, E&gt;(host: &<a href="">signer</a>)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="market.md#0xc0deb00c_market_register_market">register_market</a>&lt;B, Q, E&gt;(
    host: &<a href="">signer</a>,
) <b>acquires</b> <a href="market.md#0xc0deb00c_market_EconiaCapabilityStore">EconiaCapabilityStore</a> {
    // Add an entry <b>to</b> the <a href="market.md#0xc0deb00c_market">market</a> <a href="registry.md#0xc0deb00c_registry">registry</a> <a href="">table</a>
    <a href="registry.md#0xc0deb00c_registry_register_market_internal">registry::register_market_internal</a>&lt;B, Q, E&gt;(address_of(host),
        &<a href="market.md#0xc0deb00c_market_get_econia_capability">get_econia_capability</a>());
    // Initialize an order book under host account
    <a href="market.md#0xc0deb00c_market_init_book">init_book</a>&lt;B, Q, E&gt;(host, <a href="registry.md#0xc0deb00c_registry_scale_factor">registry::scale_factor</a>&lt;E&gt;());
}
</code></pre>



</details>

<a name="0xc0deb00c_market_get_econia_capability"></a>

## Function `get_econia_capability`

Return an <code>EconiaCapability</code>


<a name="@Assumes_1"></a>

### Assumes

* <code><a href="market.md#0xc0deb00c_market_EconiaCapabilityStore">EconiaCapabilityStore</a></code> has already been successfully
initialized, and thus skips existence checks


<pre><code><b>fun</b> <a href="market.md#0xc0deb00c_market_get_econia_capability">get_econia_capability</a>(): <a href="capability.md#0xc0deb00c_capability_EconiaCapability">capability::EconiaCapability</a>
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>fun</b> <a href="market.md#0xc0deb00c_market_get_econia_capability">get_econia_capability</a>():
EconiaCapability
<b>acquires</b> <a href="market.md#0xc0deb00c_market_EconiaCapabilityStore">EconiaCapabilityStore</a> {
    <b>borrow_global</b>&lt;<a href="market.md#0xc0deb00c_market_EconiaCapabilityStore">EconiaCapabilityStore</a>&gt;(@econia).econia_capability
}
</code></pre>



</details>

<a name="0xc0deb00c_market_init_book"></a>

## Function `init_book`

Initialize <code><a href="market.md#0xc0deb00c_market_OrderBook">OrderBook</a></code> with given <code>scale_factor</code> under <code>host</code>
account, aborting if one already exists


<pre><code><b>fun</b> <a href="market.md#0xc0deb00c_market_init_book">init_book</a>&lt;B, Q, E&gt;(host: &<a href="">signer</a>, scale_factor: u64)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>fun</b> <a href="market.md#0xc0deb00c_market_init_book">init_book</a>&lt;B, Q, E&gt;(
    host: &<a href="">signer</a>,
    scale_factor: u64,
) {
    // Assert book does not already exist under host account
    <b>assert</b>!(!<b>exists</b>&lt;<a href="market.md#0xc0deb00c_market_OrderBook">OrderBook</a>&lt;B, Q, E&gt;&gt;(address_of(host)), <a href="market.md#0xc0deb00c_market_E_BOOK_EXISTS">E_BOOK_EXISTS</a>);
    // Move <b>to</b> host a newly-packed order book
    <b>move_to</b>&lt;<a href="market.md#0xc0deb00c_market_OrderBook">OrderBook</a>&lt;B, Q, E&gt;&gt;(host, <a href="market.md#0xc0deb00c_market_OrderBook">OrderBook</a>{
        scale_factor,
        asks: <a href="critbit.md#0xc0deb00c_critbit_empty">critbit::empty</a>(),
        bids: <a href="critbit.md#0xc0deb00c_critbit_empty">critbit::empty</a>(),
        min_ask: <a href="market.md#0xc0deb00c_market_MIN_ASK_DEFAULT">MIN_ASK_DEFAULT</a>,
        max_bid: <a href="market.md#0xc0deb00c_market_MAX_BID_DEFAULT">MAX_BID_DEFAULT</a>,
        counter: 0
    });
}
</code></pre>



</details>