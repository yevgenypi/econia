
<a name="0xc0deb00c_incentives"></a>

# Module `0xc0deb00c::incentives`

Incentive-associated parameters and data structures.


-  [Resource `EconiaFeeStore`](#0xc0deb00c_incentives_EconiaFeeStore)
-  [Resource `FeeAccountSignerCapabilityStore`](#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore)
-  [Resource `IncentiveParameters`](#0xc0deb00c_incentives_IncentiveParameters)
-  [Struct `IntegratorFeeStore`](#0xc0deb00c_incentives_IntegratorFeeStore)
-  [Resource `IntegratorFeeStores`](#0xc0deb00c_incentives_IntegratorFeeStores)
-  [Struct `IntegratorFeeStoreTierParameters`](#0xc0deb00c_incentives_IntegratorFeeStoreTierParameters)
-  [Resource `UtilityCoinStore`](#0xc0deb00c_incentives_UtilityCoinStore)
-  [Constants](#@Constants_0)
-  [Function `get_cost_to_upgrade_integrator_fee_store`](#0xc0deb00c_incentives_get_cost_to_upgrade_integrator_fee_store)
    -  [Type parameters](#@Type_parameters_1)
    -  [Parameters](#@Parameters_2)
    -  [Returns](#@Returns_3)
    -  [Aborts if](#@Aborts_if_4)
    -  [Restrictions](#@Restrictions_5)
-  [Function `get_custodian_registration_fee`](#0xc0deb00c_incentives_get_custodian_registration_fee)
-  [Function `get_fee_account_address`](#0xc0deb00c_incentives_get_fee_account_address)
-  [Function `get_fee_share_divisor`](#0xc0deb00c_incentives_get_fee_share_divisor)
-  [Function `get_market_registration_fee`](#0xc0deb00c_incentives_get_market_registration_fee)
-  [Function `get_n_fee_store_tiers`](#0xc0deb00c_incentives_get_n_fee_store_tiers)
-  [Function `get_taker_fee_divisor`](#0xc0deb00c_incentives_get_taker_fee_divisor)
-  [Function `get_taker_fee_divisor_ref`](#0xc0deb00c_incentives_get_taker_fee_divisor_ref)
-  [Function `get_tier_activation_fee`](#0xc0deb00c_incentives_get_tier_activation_fee)
-  [Function `get_withdrawal_fee`](#0xc0deb00c_incentives_get_withdrawal_fee)
-  [Function `is_utility_coin_type`](#0xc0deb00c_incentives_is_utility_coin_type)
-  [Function `upgrade_integrator_fee_store`](#0xc0deb00c_incentives_upgrade_integrator_fee_store)
    -  [Type parameters](#@Type_parameters_6)
    -  [Parameters](#@Parameters_7)
-  [Function `verify_utility_coin_type`](#0xc0deb00c_incentives_verify_utility_coin_type)
-  [Function `withdraw_econia_fees`](#0xc0deb00c_incentives_withdraw_econia_fees)
    -  [Type parameters](#@Type_parameters_8)
    -  [Parameters](#@Parameters_9)
    -  [Aborts if](#@Aborts_if_10)
-  [Function `withdraw_econia_fees_all`](#0xc0deb00c_incentives_withdraw_econia_fees_all)
    -  [Type parameters](#@Type_parameters_11)
    -  [Parameters](#@Parameters_12)
    -  [Aborts if](#@Aborts_if_13)
-  [Function `withdraw_integrator_fees`](#0xc0deb00c_incentives_withdraw_integrator_fees)
    -  [Type parameters](#@Type_parameters_14)
    -  [Parameters](#@Parameters_15)
    -  [Returns](#@Returns_16)
-  [Function `withdraw_utility_coins`](#0xc0deb00c_incentives_withdraw_utility_coins)
-  [Function `withdraw_utility_coins_all`](#0xc0deb00c_incentives_withdraw_utility_coins_all)
-  [Function `update_incentives`](#0xc0deb00c_incentives_update_incentives)
-  [Function `upgrade_integrator_fee_store_via_coinstore`](#0xc0deb00c_incentives_upgrade_integrator_fee_store_via_coinstore)
-  [Function `assess_taker_fees`](#0xc0deb00c_incentives_assess_taker_fees)
    -  [Type parameters](#@Type_parameters_17)
    -  [Parameters](#@Parameters_18)
-  [Function `deposit_custodian_registration_utility_coins`](#0xc0deb00c_incentives_deposit_custodian_registration_utility_coins)
-  [Function `deposit_market_registration_utility_coins`](#0xc0deb00c_incentives_deposit_market_registration_utility_coins)
-  [Function `init_incentives`](#0xc0deb00c_incentives_init_incentives)
-  [Function `register_econia_fee_store_entry`](#0xc0deb00c_incentives_register_econia_fee_store_entry)
-  [Function `register_integrator_fee_store`](#0xc0deb00c_incentives_register_integrator_fee_store)
    -  [Type parameters](#@Type_parameters_19)
    -  [Parameters](#@Parameters_20)
-  [Function `calculate_max_quote_match`](#0xc0deb00c_incentives_calculate_max_quote_match)
    -  [User input](#@User_input_21)
    -  [Matching](#@Matching_22)
        -  [Example buy](#@Example_buy_23)
        -  [Example sell](#@Example_sell_24)
    -  [Variables](#@Variables_25)
    -  [Equations](#@Equations_26)
        -  [Buy](#@Buy_27)
        -  [Sell](#@Sell_28)
    -  [Parameters](#@Parameters_29)
    -  [Assumptions](#@Assumptions_30)
    -  [Aborts if](#@Aborts_if_31)
-  [Function `deposit_utility_coins`](#0xc0deb00c_incentives_deposit_utility_coins)
-  [Function `deposit_utility_coins_verified`](#0xc0deb00c_incentives_deposit_utility_coins_verified)
-  [Function `get_fee_account`](#0xc0deb00c_incentives_get_fee_account)
-  [Function `init_fee_account`](#0xc0deb00c_incentives_init_fee_account)
    -  [Parameters](#@Parameters_32)
    -  [Returns](#@Returns_33)
    -  [Seed considerations](#@Seed_considerations_34)
    -  [Aborts if](#@Aborts_if_35)
-  [Function `init_utility_coin_store`](#0xc0deb00c_incentives_init_utility_coin_store)
    -  [Type Parameters](#@Type_Parameters_36)
    -  [Parameters](#@Parameters_37)
    -  [Aborts if](#@Aborts_if_38)
-  [Function `set_incentive_parameters`](#0xc0deb00c_incentives_set_incentive_parameters)
    -  [Type Parameters](#@Type_Parameters_39)
    -  [Parameters](#@Parameters_40)
    -  [Assumptions](#@Assumptions_41)
    -  [Aborts if](#@Aborts_if_42)
-  [Function `set_incentive_parameters_parse_tiers_vector`](#0xc0deb00c_incentives_set_incentive_parameters_parse_tiers_vector)
    -  [Aborts if](#@Aborts_if_43)
    -  [Assumptions](#@Assumptions_44)
-  [Function `set_incentive_parameters_range_check_inputs`](#0xc0deb00c_incentives_set_incentive_parameters_range_check_inputs)
    -  [Parameters](#@Parameters_45)
    -  [Aborts if](#@Aborts_if_46)


<pre><code><b>use</b> <a href="">0x1::account</a>;
<b>use</b> <a href="">0x1::coin</a>;
<b>use</b> <a href="">0x1::signer</a>;
<b>use</b> <a href="">0x1::type_info</a>;
<b>use</b> <a href="">0x1::vector</a>;
<b>use</b> <a href="table_list.md#0xc0deb00c_table_list">0xc0deb00c::table_list</a>;
</code></pre>



<a name="0xc0deb00c_incentives_EconiaFeeStore"></a>

## Resource `EconiaFeeStore`

Portion of taker fees not claimed by an integrator, which are
reserved for Econia.


<pre><code><b>struct</b> <a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a>&lt;QuoteCoinType&gt; <b>has</b> key
</code></pre>



<details>
<summary>Fields</summary>


<dl>
<dt>
<code>map: <a href="table_list.md#0xc0deb00c_table_list_TableList">table_list::TableList</a>&lt;u64, <a href="_Coin">coin::Coin</a>&lt;QuoteCoinType&gt;&gt;</code>
</dt>
<dd>
 Map from market ID to fees collected for given market,
 enabling duplicate checks and interable indexing.
</dd>
</dl>


</details>

<a name="0xc0deb00c_incentives_FeeAccountSignerCapabilityStore"></a>

## Resource `FeeAccountSignerCapabilityStore`

Stores a signing capability for the resource account where
fees, collected by Econia, are stored.


<pre><code><b>struct</b> <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a> <b>has</b> key
</code></pre>



<details>
<summary>Fields</summary>


<dl>
<dt>
<code>fee_account_signer_capability: <a href="_SignerCapability">account::SignerCapability</a></code>
</dt>
<dd>
 Signing capability for fee collection resource account.
</dd>
</dl>


</details>

<a name="0xc0deb00c_incentives_IncentiveParameters"></a>

## Resource `IncentiveParameters`

Incentive parameters for assorted operations.


<pre><code><b>struct</b> <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a> <b>has</b> key
</code></pre>



<details>
<summary>Fields</summary>


<dl>
<dt>
<code>utility_coin_type_info: <a href="_TypeInfo">type_info::TypeInfo</a></code>
</dt>
<dd>
 Utility coin type info. Corresponds to the phantom
 <code>CoinType</code> (<code><b>address</b>:module::MyCoin</code> rather than
 <code>aptos_framework::coin::Coin&lt;<b>address</b>:module::MyCoin&gt;</code>) of
 the coin required for utility purposes. Set to <code>APT</code> at
 mainnet launch, later the Econia coin.
</dd>
<dt>
<code>market_registration_fee: u64</code>
</dt>
<dd>
 <code>Coin.value</code> required to register a market.
</dd>
<dt>
<code>custodian_registration_fee: u64</code>
</dt>
<dd>
 <code>Coin.value</code> required to register as a custodian.
</dd>
<dt>
<code>taker_fee_divisor: u64</code>
</dt>
<dd>
 Nominal amount divisor for quote coin fee charged to takers.
 For example, if a transaction involves a quote coin fill of
 1000000 units and the taker fee divisor is 2000, takers pay
 1/2000th (0.05%) of the nominal amount (500 quote coin
 units) in fees. Instituted as a divisor for optimized
 calculations.
</dd>
<dt>
<code>integrator_fee_store_tiers: <a href="">vector</a>&lt;<a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStoreTierParameters">incentives::IntegratorFeeStoreTierParameters</a>&gt;</code>
</dt>
<dd>
 0-indexed list from tier number to corresponding parameters.
</dd>
</dl>


</details>

<a name="0xc0deb00c_incentives_IntegratorFeeStore"></a>

## Struct `IntegratorFeeStore`

Fee store for a given integrator, on a given market.


<pre><code><b>struct</b> <a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStore">IntegratorFeeStore</a>&lt;QuoteCoinType&gt; <b>has</b> store
</code></pre>



<details>
<summary>Fields</summary>


<dl>
<dt>
<code>tier: u8</code>
</dt>
<dd>
 Activation tier, incremented by paying utility coins.
</dd>
<dt>
<code>coins: <a href="_Coin">coin::Coin</a>&lt;QuoteCoinType&gt;</code>
</dt>
<dd>
 Collected fees, in quote coins for given market.
</dd>
</dl>


</details>

<a name="0xc0deb00c_incentives_IntegratorFeeStores"></a>

## Resource `IntegratorFeeStores`

All of an integrator's <code>IntregratorFeeStore</code>s for given
<code>QuoteCoinType</code>.


<pre><code><b>struct</b> <a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>&lt;QuoteCoinType&gt; <b>has</b> key
</code></pre>



<details>
<summary>Fields</summary>


<dl>
<dt>
<code>map: <a href="table_list.md#0xc0deb00c_table_list_TableList">table_list::TableList</a>&lt;u64, <a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStore">incentives::IntegratorFeeStore</a>&lt;QuoteCoinType&gt;&gt;</code>
</dt>
<dd>
 Map from market ID to <code><a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStore">IntegratorFeeStore</a></code>, enabling
 duplicate checks and iterable indexing.
</dd>
</dl>


</details>

<a name="0xc0deb00c_incentives_IntegratorFeeStoreTierParameters"></a>

## Struct `IntegratorFeeStoreTierParameters`

Integrator fee store tier parameters for a given tier.


<pre><code><b>struct</b> <a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStoreTierParameters">IntegratorFeeStoreTierParameters</a> <b>has</b> drop, store
</code></pre>



<details>
<summary>Fields</summary>


<dl>
<dt>
<code>fee_share_divisor: u64</code>
</dt>
<dd>
 Nominal amount divisor for taker quote coin fee reserved for
 integrators having activated their fee store to the given
 tier. For example, if a transaction involves a quote coin
 fill of 1000000 units and the fee share divisor at the given
 tier is 4000, integrators get 1/4000th (0.025%) of the
 nominal amount (250 quote coin units) in fees at the given
 tier. Instituted as a divisor for optimized calculations.
 May not be larger than the
 <code><a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>.taker_fee_divisor</code>, since the
 integrator fee share is deducted from the taker fee (with
 the remaining proceeds going to an <code><a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a></code> for the
 given market).
</dd>
<dt>
<code>tier_activation_fee: u64</code>
</dt>
<dd>
 Cumulative cost, in utility coin units, to activate to the
 current tier. For example, if an integrator has already
 activated to tier 3, which has a tier activation fee of 1000
 units, and tier 4 has a tier activation fee of 10000 units,
 the integrator only has to pay 9000 units to activate to
 tier 4.
</dd>
<dt>
<code>withdrawal_fee: u64</code>
</dt>
<dd>
 Cost, in utility coin units, to withdraw from an integrator
 fee store. Shall never be nonzero, since a disincentive is
 required to prevent excessively-frequent withdrawals and
 thus transaction collisions with the matching engine.
</dd>
</dl>


</details>

<a name="0xc0deb00c_incentives_UtilityCoinStore"></a>

## Resource `UtilityCoinStore`

Container for utility coin fees collected by Econia.


<pre><code><b>struct</b> <a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>&lt;CoinType&gt; <b>has</b> key
</code></pre>



<details>
<summary>Fields</summary>


<dl>
<dt>
<code>coins: <a href="_Coin">coin::Coin</a>&lt;CoinType&gt;</code>
</dt>
<dd>
 Coins collected as utility fees.
</dd>
</dl>


</details>

<a name="@Constants_0"></a>

## Constants


<a name="0xc0deb00c_incentives_E_NOT_ECONIA"></a>

When caller is not Econia, but should be.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_NOT_ECONIA">E_NOT_ECONIA</a>: u64 = 0;
</code></pre>



<a name="0xc0deb00c_incentives_BUY"></a>

Buy direction flag.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_BUY">BUY</a>: bool = <b>true</b>;
</code></pre>



<a name="0xc0deb00c_incentives_E_ACTIVATION_FEE_TOO_SMALL"></a>

When the indicated tier activation fee is too small.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_ACTIVATION_FEE_TOO_SMALL">E_ACTIVATION_FEE_TOO_SMALL</a>: u64 = 9;
</code></pre>



<a name="0xc0deb00c_incentives_E_CUSTODIAN_REGISTRATION_FEE_LESS_THAN_MIN"></a>

When custodian registration fee is less than the minimum.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_CUSTODIAN_REGISTRATION_FEE_LESS_THAN_MIN">E_CUSTODIAN_REGISTRATION_FEE_LESS_THAN_MIN</a>: u64 = 6;
</code></pre>



<a name="0xc0deb00c_incentives_E_EMPTY_FEE_STORE_TIERS"></a>

When passed fee store tiers vector is empty.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_EMPTY_FEE_STORE_TIERS">E_EMPTY_FEE_STORE_TIERS</a>: u64 = 2;
</code></pre>



<a name="0xc0deb00c_incentives_E_FEE_SHARE_DIVISOR_TOO_BIG"></a>

When indicated fee share divisor for given tier is too big.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_FEE_SHARE_DIVISOR_TOO_BIG">E_FEE_SHARE_DIVISOR_TOO_BIG</a>: u64 = 3;
</code></pre>



<a name="0xc0deb00c_incentives_E_FEE_SHARE_DIVISOR_TOO_SMALL"></a>

When the indicated fee share divisor for a given tier is less
than the indicated taker fee divisor.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_FEE_SHARE_DIVISOR_TOO_SMALL">E_FEE_SHARE_DIVISOR_TOO_SMALL</a>: u64 = 4;
</code></pre>



<a name="0xc0deb00c_incentives_E_FEWER_TIERS"></a>

When an update to the incentive parameters set indicates a
reduction in fee store tiers.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_FEWER_TIERS">E_FEWER_TIERS</a>: u64 = 16;
</code></pre>



<a name="0xc0deb00c_incentives_E_FIRST_TIER_ACTIVATION_FEE_NONZERO"></a>

When the cost to activate to tier 0 is nonzero.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_FIRST_TIER_ACTIVATION_FEE_NONZERO">E_FIRST_TIER_ACTIVATION_FEE_NONZERO</a>: u64 = 18;
</code></pre>



<a name="0xc0deb00c_incentives_E_INVALID_UTILITY_COIN_TYPE"></a>

When type is not the utility coin type.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_INVALID_UTILITY_COIN_TYPE">E_INVALID_UTILITY_COIN_TYPE</a>: u64 = 12;
</code></pre>



<a name="0xc0deb00c_incentives_E_MARKET_REGISTRATION_FEE_LESS_THAN_MIN"></a>

When market registration fee is less than the minimum.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_MARKET_REGISTRATION_FEE_LESS_THAN_MIN">E_MARKET_REGISTRATION_FEE_LESS_THAN_MIN</a>: u64 = 5;
</code></pre>



<a name="0xc0deb00c_incentives_E_MAX_QUOTE_MATCH_OVERFLOW"></a>

When maximum amount of quote coins to match overflows a <code>u64</code>.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_MAX_QUOTE_MATCH_OVERFLOW">E_MAX_QUOTE_MATCH_OVERFLOW</a>: u64 = 17;
</code></pre>



<a name="0xc0deb00c_incentives_E_NOT_AN_UPGRADE"></a>

When indicated tier is not higher than existing tier.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_NOT_AN_UPGRADE">E_NOT_AN_UPGRADE</a>: u64 = 15;
</code></pre>



<a name="0xc0deb00c_incentives_E_NOT_COIN"></a>

When type does not correspond to an initialized coin.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_NOT_COIN">E_NOT_COIN</a>: u64 = 1;
</code></pre>



<a name="0xc0deb00c_incentives_E_NOT_ENOUGH_UTILITY_COINS"></a>

When not enough utility coins provided.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_NOT_ENOUGH_UTILITY_COINS">E_NOT_ENOUGH_UTILITY_COINS</a>: u64 = 13;
</code></pre>



<a name="0xc0deb00c_incentives_E_TAKER_DIVISOR_LESS_THAN_MIN"></a>

When taker fee divisor is less than the minimum.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_TAKER_DIVISOR_LESS_THAN_MIN">E_TAKER_DIVISOR_LESS_THAN_MIN</a>: u64 = 7;
</code></pre>



<a name="0xc0deb00c_incentives_E_TIER_FIELDS_WRONG_LENGTH"></a>

When the wrong number of fields are passed for a given tier.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_TIER_FIELDS_WRONG_LENGTH">E_TIER_FIELDS_WRONG_LENGTH</a>: u64 = 8;
</code></pre>



<a name="0xc0deb00c_incentives_E_TOO_MANY_TIERS"></a>

When too many integrater fee store tiers indicated.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_TOO_MANY_TIERS">E_TOO_MANY_TIERS</a>: u64 = 14;
</code></pre>



<a name="0xc0deb00c_incentives_E_WITHDRAWAL_FEE_TOO_BIG"></a>

When the indicated withdrawal fee is too big.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_WITHDRAWAL_FEE_TOO_BIG">E_WITHDRAWAL_FEE_TOO_BIG</a>: u64 = 10;
</code></pre>



<a name="0xc0deb00c_incentives_E_WITHDRAWAL_FEE_TOO_SMALL"></a>

When the indicated withdrawal fee is too small.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_E_WITHDRAWAL_FEE_TOO_SMALL">E_WITHDRAWAL_FEE_TOO_SMALL</a>: u64 = 11;
</code></pre>



<a name="0xc0deb00c_incentives_FEE_SHARE_DIVISOR_INDEX"></a>

Index of fee share in vectorized representation of an
<code><a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStoreTierParameters">IntegratorFeeStoreTierParameters</a></code>.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_FEE_SHARE_DIVISOR_INDEX">FEE_SHARE_DIVISOR_INDEX</a>: u64 = 0;
</code></pre>



<a name="0xc0deb00c_incentives_HI_64"></a>

<code>u64</code> bitmask with all bits set


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_HI_64">HI_64</a>: u64 = 18446744073709551615;
</code></pre>



<a name="0xc0deb00c_incentives_MAX_INTEGRATOR_FEE_STORE_TIERS"></a>

Maximum number of integrator fee store tiers is largest number
that can fit in a <code>u8</code>.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_MAX_INTEGRATOR_FEE_STORE_TIERS">MAX_INTEGRATOR_FEE_STORE_TIERS</a>: u64 = 255;
</code></pre>



<a name="0xc0deb00c_incentives_MIN_DIVISOR"></a>

Minimum possible divisor for avoiding divide-by-zero error.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_MIN_DIVISOR">MIN_DIVISOR</a>: u64 = 1;
</code></pre>



<a name="0xc0deb00c_incentives_MIN_FEE"></a>

Minimum possible flat fee, required to disincentivize excessive
bogus transactions.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_MIN_FEE">MIN_FEE</a>: u64 = 1;
</code></pre>



<a name="0xc0deb00c_incentives_N_TIER_FIELDS"></a>

Number of fields in an <code><a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStoreTierParameters">IntegratorFeeStoreTierParameters</a></code>


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_N_TIER_FIELDS">N_TIER_FIELDS</a>: u64 = 3;
</code></pre>



<a name="0xc0deb00c_incentives_SELL"></a>

Sell direction flag.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_SELL">SELL</a>: bool = <b>false</b>;
</code></pre>



<a name="0xc0deb00c_incentives_TIER_ACTIVATION_FEE_INDEX"></a>

Index of tier activation fee in vectorized representation of an
<code><a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStoreTierParameters">IntegratorFeeStoreTierParameters</a></code>.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_TIER_ACTIVATION_FEE_INDEX">TIER_ACTIVATION_FEE_INDEX</a>: u64 = 1;
</code></pre>



<a name="0xc0deb00c_incentives_WITHDRAWAL_FEE_INDEX"></a>

Index of withdrawal fee in vectorized representation of an
<code><a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStoreTierParameters">IntegratorFeeStoreTierParameters</a></code>.


<pre><code><b>const</b> <a href="incentives.md#0xc0deb00c_incentives_WITHDRAWAL_FEE_INDEX">WITHDRAWAL_FEE_INDEX</a>: u64 = 2;
</code></pre>



<a name="0xc0deb00c_incentives_get_cost_to_upgrade_integrator_fee_store"></a>

## Function `get_cost_to_upgrade_integrator_fee_store`

Calculate cost to upgrade <code><a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStore">IntegratorFeeStore</a></code> to higher tier.


<a name="@Type_parameters_1"></a>

### Type parameters

* <code>QuoteCoinType</code>: The quote coin type for market.
* <code>UtilityCoinType</code>: The utility coin type.


<a name="@Parameters_2"></a>

### Parameters

* <code>integrator</code>: Integrator account.
* <code>market_id_ref</code>: Immuable reference to Market ID of
corresponding market.
* <code>new_tier_ref</code>: Immutable reference to tier to upgrade to.


<a name="@Returns_3"></a>

### Returns

* <code>u64</code>: Cost, in utility coins, to upgrade to given tier,
calculated as the difference between the cumulative activation
cost for each tier. For example, if it costs 1000 to activate
to tier 3 and 100 to activate to tier 1, it costs 900 to
upgrade from tier 1 to tier 3.


<a name="@Aborts_if_4"></a>

### Aborts if

* <code>new_tier_ref</code> does not indicate a tier higher than the one
that the <code><a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStore">IntegratorFeeStore</a></code> is already activated to.


<a name="@Restrictions_5"></a>

### Restrictions

* Requires signature of integrator to prevent excessive public
queries on an <code><a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStore">IntegratorFeeStore</a></code> and thus transaction
collisions with the matching engine.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_cost_to_upgrade_integrator_fee_store">get_cost_to_upgrade_integrator_fee_store</a>&lt;QuoteCoinType, UtilityCoinType&gt;(integrator: &<a href="">signer</a>, market_id_ref: &u64, new_tier_ref: &u8): u64
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_cost_to_upgrade_integrator_fee_store">get_cost_to_upgrade_integrator_fee_store</a>&lt;
    QuoteCoinType,
    UtilityCoinType
&gt;(
    integrator: &<a href="">signer</a>,
    market_id_ref: &u64,
    new_tier_ref: &u8,
): u64
<b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>
{
    // Borrow mutable reference <b>to</b> integrator fee store for given
    // quote <a href="">coin</a> type and market ID.
    <b>let</b> integrator_fee_store_ref_mut = <a href="table_list.md#0xc0deb00c_table_list_borrow_mut">table_list::borrow_mut</a>(
            &<b>mut</b> <b>borrow_global_mut</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>&lt;QuoteCoinType&gt;&gt;(
                address_of(integrator)).map, *market_id_ref);
    // Get current tier number.
    <b>let</b> current_tier = integrator_fee_store_ref_mut.tier;
    // Assert actually attempting <b>to</b> upgrade <b>to</b> new tier.
    <b>assert</b>!(*new_tier_ref &gt; current_tier, <a href="incentives.md#0xc0deb00c_incentives_E_NOT_AN_UPGRADE">E_NOT_AN_UPGRADE</a>);
    // Return difference in cumulative cost <b>to</b> upgrade.
    <a href="incentives.md#0xc0deb00c_incentives_get_tier_activation_fee">get_tier_activation_fee</a>(new_tier_ref) -
        <a href="incentives.md#0xc0deb00c_incentives_get_tier_activation_fee">get_tier_activation_fee</a>(&current_tier)
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_get_custodian_registration_fee"></a>

## Function `get_custodian_registration_fee`

Return custodian registration fee.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_custodian_registration_fee">get_custodian_registration_fee</a>(): u64
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_custodian_registration_fee">get_custodian_registration_fee</a>():
u64
<b>acquires</b> <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a> {
    <b>borrow_global</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>&gt;(@econia).custodian_registration_fee
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_get_fee_account_address"></a>

## Function `get_fee_account_address`

Return fee account address.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_fee_account_address">get_fee_account_address</a>(): <b>address</b>
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_fee_account_address">get_fee_account_address</a>():
<b>address</b>
<b>acquires</b> <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a> {
    <a href="_get_signer_capability_address">account::get_signer_capability_address</a>(
        &<b>borrow_global</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>&gt;(@econia).
            fee_account_signer_capability)
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_get_fee_share_divisor"></a>

## Function `get_fee_share_divisor`

Return fee share divisor for tier indicated by <code>tier_ref</code>.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_fee_share_divisor">get_fee_share_divisor</a>(tier_ref: &u8): u64
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_fee_share_divisor">get_fee_share_divisor</a>(
    tier_ref: &u8
): u64
<b>acquires</b> <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a> {
    <a href="_borrow">vector::borrow</a>(&<b>borrow_global</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>&gt;(@econia).
        integrator_fee_store_tiers, (*tier_ref <b>as</b> u64)).fee_share_divisor
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_get_market_registration_fee"></a>

## Function `get_market_registration_fee`

Return market registration fee.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_market_registration_fee">get_market_registration_fee</a>(): u64
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_market_registration_fee">get_market_registration_fee</a>():
u64
<b>acquires</b> <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a> {
    <b>borrow_global</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>&gt;(@econia).market_registration_fee
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_get_n_fee_store_tiers"></a>

## Function `get_n_fee_store_tiers`

Return number of fee store tiers.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_n_fee_store_tiers">get_n_fee_store_tiers</a>(): u64
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_n_fee_store_tiers">get_n_fee_store_tiers</a>():
u64
<b>acquires</b> <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a> {
    <a href="_length">vector::length</a>(&<b>borrow_global</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>&gt;(@econia).
        integrator_fee_store_tiers)
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_get_taker_fee_divisor"></a>

## Function `get_taker_fee_divisor`

Return taker fee divisor.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_taker_fee_divisor">get_taker_fee_divisor</a>(): u64
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_taker_fee_divisor">get_taker_fee_divisor</a>():
u64
<b>acquires</b> <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a> {
    <b>borrow_global</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>&gt;(@econia).taker_fee_divisor
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_get_taker_fee_divisor_ref"></a>

## Function `get_taker_fee_divisor_ref`

Like <code><a href="incentives.md#0xc0deb00c_incentives_get_taker_fee_divisor">get_taker_fee_divisor</a>()</code>, but pass-by-reference.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_taker_fee_divisor_ref">get_taker_fee_divisor_ref</a>(taker_fee_divisor_ref_mut: &<b>mut</b> u64)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_taker_fee_divisor_ref">get_taker_fee_divisor_ref</a>(
    taker_fee_divisor_ref_mut: &<b>mut</b> u64
) <b>acquires</b> <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a> {
    *taker_fee_divisor_ref_mut =
        <b>borrow_global</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>&gt;(@econia).taker_fee_divisor;
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_get_tier_activation_fee"></a>

## Function `get_tier_activation_fee`

Return tier activation fee for tier indicated by <code>tier_ref</code>.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_tier_activation_fee">get_tier_activation_fee</a>(tier_ref: &u8): u64
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_tier_activation_fee">get_tier_activation_fee</a>(
    tier_ref: &u8
): u64
<b>acquires</b> <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a> {
    <a href="_borrow">vector::borrow</a>(&<b>borrow_global</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>&gt;(@econia).
        integrator_fee_store_tiers, (*tier_ref <b>as</b> u64)).tier_activation_fee
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_get_withdrawal_fee"></a>

## Function `get_withdrawal_fee`

Return withdrawal fee for tier indicated by <code>tier_ref</code>.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_withdrawal_fee">get_withdrawal_fee</a>(tier_ref: &u8): u64
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_withdrawal_fee">get_withdrawal_fee</a>(
    tier_ref: &u8
): u64
<b>acquires</b> <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a> {
    <a href="_borrow">vector::borrow</a>(&<b>borrow_global</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>&gt;(@econia).
        integrator_fee_store_tiers, (*tier_ref <b>as</b> u64)).withdrawal_fee
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_is_utility_coin_type"></a>

## Function `is_utility_coin_type`

Return <code><b>true</b></code> if <code>T</code> is the utility coin type.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_is_utility_coin_type">is_utility_coin_type</a>&lt;T&gt;(): bool
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_is_utility_coin_type">is_utility_coin_type</a>&lt;T&gt;():
bool
<b>acquires</b> <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a> {
    <a href="_type_of">type_info::type_of</a>&lt;T&gt;() ==
        <b>borrow_global</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>&gt;(@econia).utility_coin_type_info
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_upgrade_integrator_fee_store"></a>

## Function `upgrade_integrator_fee_store`

Upgrade <code><a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStore">IntegratorFeeStore</a></code> to a higher tier.


<a name="@Type_parameters_6"></a>

### Type parameters

* <code>QuoteCoinType</code>: The quote coin type for market.
* <code>UtilityCoinType</code>: The utility coin type.


<a name="@Parameters_7"></a>

### Parameters

* <code>integrator</code>: Integrator account.
* <code>market_id_ref</code>: Immuable reference to Market ID of
corresponding market.
* <code>new_tier_ref</code>: Immutable reference to tier to upgrade to.
* <code>utility_coins</code>: Utility coins paid for upgrade.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_upgrade_integrator_fee_store">upgrade_integrator_fee_store</a>&lt;QuoteCoinType, UtilityCoinType&gt;(integrator: &<a href="">signer</a>, market_id_ref: &u64, new_tier_ref: &u8, utility_coins: <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_upgrade_integrator_fee_store">upgrade_integrator_fee_store</a>&lt;
    QuoteCoinType,
    UtilityCoinType
&gt;(
    integrator: &<a href="">signer</a>,
    market_id_ref: &u64,
    new_tier_ref: &u8,
    utility_coins: <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;
) <b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>,
    <a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>
{
    // Get cost <b>to</b> upgrade <b>to</b> new tier.
    <b>let</b> cost = <a href="incentives.md#0xc0deb00c_incentives_get_cost_to_upgrade_integrator_fee_store">get_cost_to_upgrade_integrator_fee_store</a>&lt;QuoteCoinType,
        UtilityCoinType&gt;(integrator, market_id_ref, new_tier_ref);
    // Deposit verified amount and type of utility coins.
    <a href="incentives.md#0xc0deb00c_incentives_deposit_utility_coins_verified">deposit_utility_coins_verified</a>&lt;UtilityCoinType&gt;(utility_coins, &cost);
    <a href="table_list.md#0xc0deb00c_table_list_borrow_mut">table_list::borrow_mut</a>( // Set new tier.
        &<b>mut</b> <b>borrow_global_mut</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>&lt;QuoteCoinType&gt;&gt;(
            address_of(integrator)).map, *market_id_ref).tier =
                *new_tier_ref;
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_verify_utility_coin_type"></a>

## Function `verify_utility_coin_type`

Assert <code>T</code> is utility coin type.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_verify_utility_coin_type">verify_utility_coin_type</a>&lt;T&gt;()
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_verify_utility_coin_type">verify_utility_coin_type</a>&lt;T&gt;()
<b>acquires</b> <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a> {
    <b>assert</b>!(<a href="incentives.md#0xc0deb00c_incentives_is_utility_coin_type">is_utility_coin_type</a>&lt;T&gt;(), <a href="incentives.md#0xc0deb00c_incentives_E_INVALID_UTILITY_COIN_TYPE">E_INVALID_UTILITY_COIN_TYPE</a>);
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_withdraw_econia_fees"></a>

## Function `withdraw_econia_fees`

Withdraw specified amount of fees from an <code><a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a></code>.


<a name="@Type_parameters_8"></a>

### Type parameters

* <code>QuoteCoinType</code>: Quote coin type for market.


<a name="@Parameters_9"></a>

### Parameters

* <code><a href="">account</a></code>: The Econia account.
* <code>market_id_ref</code>: Immutable reference to market ID.
* <code>amount_ref</code>: Immutable reference to amount to withdraw.


<a name="@Aborts_if_10"></a>

### Aborts if

* <code><a href="">account</a></code> is not Econia.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_withdraw_econia_fees">withdraw_econia_fees</a>&lt;QuoteCoinType&gt;(<a href="">account</a>: &<a href="">signer</a>, market_id_ref: &u64, amount_ref: &u64): <a href="_Coin">coin::Coin</a>&lt;QuoteCoinType&gt;
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_withdraw_econia_fees">withdraw_econia_fees</a>&lt;QuoteCoinType&gt;(
    <a href="">account</a>: &<a href="">signer</a>,
    market_id_ref: &u64,
    amount_ref: &u64
): <a href="_Coin">coin::Coin</a>&lt;QuoteCoinType&gt;
<b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a>
{
    // Assert <a href="">account</a> is Econia.
    <b>assert</b>!(address_of(<a href="">account</a>) == @econia, <a href="incentives.md#0xc0deb00c_incentives_E_NOT_ECONIA">E_NOT_ECONIA</a>);
    <a href="_extract">coin::extract</a>( // Extract indicated amount of coins.
        <a href="table_list.md#0xc0deb00c_table_list_borrow_mut">table_list::borrow_mut</a>(
            &<b>mut</b> <b>borrow_global_mut</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a>&lt;QuoteCoinType&gt;&gt;(
            <a href="incentives.md#0xc0deb00c_incentives_get_fee_account_address">get_fee_account_address</a>()).map,
            *market_id_ref
        ),
        *amount_ref
    )
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_withdraw_econia_fees_all"></a>

## Function `withdraw_econia_fees_all`

Withdraw all fees from an <code><a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a></code>.


<a name="@Type_parameters_11"></a>

### Type parameters

* <code>QuoteCoinType</code>: Quote coin type for market.


<a name="@Parameters_12"></a>

### Parameters

* <code><a href="">account</a></code>: The Econia account.
* <code>market_id_ref</code>: Immutable reference to market ID.


<a name="@Aborts_if_13"></a>

### Aborts if

* <code><a href="">account</a></code> is not Econia.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_withdraw_econia_fees_all">withdraw_econia_fees_all</a>&lt;QuoteCoinType&gt;(<a href="">account</a>: &<a href="">signer</a>, market_id_ref: &u64): <a href="_Coin">coin::Coin</a>&lt;QuoteCoinType&gt;
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_withdraw_econia_fees_all">withdraw_econia_fees_all</a>&lt;QuoteCoinType&gt;(
    <a href="">account</a>: &<a href="">signer</a>,
    market_id_ref: &u64,
): <a href="_Coin">coin::Coin</a>&lt;QuoteCoinType&gt;
<b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a>
{
    // Assert <a href="">account</a> is Econia.
    <b>assert</b>!(address_of(<a href="">account</a>) == @econia, <a href="incentives.md#0xc0deb00c_incentives_E_NOT_ECONIA">E_NOT_ECONIA</a>);
    <a href="_extract_all">coin::extract_all</a>( // Extract all coins.
        <a href="table_list.md#0xc0deb00c_table_list_borrow_mut">table_list::borrow_mut</a>(
            &<b>mut</b> <b>borrow_global_mut</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a>&lt;QuoteCoinType&gt;&gt;(
            <a href="incentives.md#0xc0deb00c_incentives_get_fee_account_address">get_fee_account_address</a>()).map,
            *market_id_ref
        )
    )
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_withdraw_integrator_fees"></a>

## Function `withdraw_integrator_fees`

Withdraw all fees from an <code><a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStore">IntegratorFeeStore</a></code>.


<a name="@Type_parameters_14"></a>

### Type parameters

* <code>QuoteCoinType</code>: The quote coin type for market.
* <code>UtilityCoinType</code>: The utility coin type.


<a name="@Parameters_15"></a>

### Parameters

* <code>integrator</code>: Integrator account.
* <code>market_id</code>: Market ID of corresponding market.
* <code>utility_coins</code>: Utility coins paid in order to make
withdrawal, required to disincentivize excessively frequent
withdrawals and thus transaction collisions with the matching
engine.


<a name="@Returns_16"></a>

### Returns

* <code><a href="_Coin">coin::Coin</a>&lt;QuoteCoinType&gt;</code>: Quote coin fees for given market.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_withdraw_integrator_fees">withdraw_integrator_fees</a>&lt;QuoteCoinType, UtilityCoinType&gt;(integrator: &<a href="">signer</a>, market_id: u64, utility_coins: <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;): <a href="_Coin">coin::Coin</a>&lt;QuoteCoinType&gt;
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_withdraw_integrator_fees">withdraw_integrator_fees</a>&lt;
    QuoteCoinType,
    UtilityCoinType
&gt;(
    integrator: &<a href="">signer</a>,
    market_id: u64,
    utility_coins: <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;
): <a href="_Coin">coin::Coin</a>&lt;QuoteCoinType&gt;
<b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>,
    <a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>
{
    // Borrow mutable reference <b>to</b> integrator fee stores map for
    // quote <a href="">coin</a> type.
    <b>let</b> integrator_fee_stores_map_ref_mut = &<b>mut</b> <b>borrow_global_mut</b>&lt;
        <a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>&lt;QuoteCoinType&gt;&gt;(address_of(integrator)).map;
    // Borrow mutable reference <b>to</b> corresponding integrator fee
    // store.
    <b>let</b> integrator_fee_store_ref_mut = <a href="table_list.md#0xc0deb00c_table_list_borrow_mut">table_list::borrow_mut</a>(
        integrator_fee_stores_map_ref_mut, market_id);
    // Deposit verified amount and type of utility coins.
    <a href="incentives.md#0xc0deb00c_incentives_deposit_utility_coins_verified">deposit_utility_coins_verified</a>(utility_coins,
        &<a href="incentives.md#0xc0deb00c_incentives_get_withdrawal_fee">get_withdrawal_fee</a>(&integrator_fee_store_ref_mut.tier));
    // Extract and <b>return</b> all coins in integrator fee store.
    <a href="_extract_all">coin::extract_all</a>(&<b>mut</b> integrator_fee_store_ref_mut.coins)
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_withdraw_utility_coins"></a>

## Function `withdraw_utility_coins`

Withdraw <code>amount</code> of utility coins from the <code><a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a></code>,
aborting if <code><a href="">account</a></code> is not Econia.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_withdraw_utility_coins">withdraw_utility_coins</a>&lt;UtilityCoinType&gt;(<a href="">account</a>: &<a href="">signer</a>, amount: u64): <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_withdraw_utility_coins">withdraw_utility_coins</a>&lt;UtilityCoinType&gt;(
    <a href="">account</a>: &<a href="">signer</a>,
    amount: u64
): <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;
<b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>
{
    // Assert <a href="">account</a> is Econia.
    <b>assert</b>!(address_of(<a href="">account</a>) == @econia, <a href="incentives.md#0xc0deb00c_incentives_E_NOT_ECONIA">E_NOT_ECONIA</a>);
    <a href="_extract">coin::extract</a>( // Extract indicated amount of coins.
        &<b>mut</b> <b>borrow_global_mut</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>&lt;UtilityCoinType&gt;&gt;(
            <a href="incentives.md#0xc0deb00c_incentives_get_fee_account_address">get_fee_account_address</a>()).coins, amount)
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_withdraw_utility_coins_all"></a>

## Function `withdraw_utility_coins_all`

Withdraw all utility coins from the <code><a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a></code>, aborting
if <code><a href="">account</a></code> is not Econia.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_withdraw_utility_coins_all">withdraw_utility_coins_all</a>&lt;UtilityCoinType&gt;(<a href="">account</a>: &<a href="">signer</a>): <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_withdraw_utility_coins_all">withdraw_utility_coins_all</a>&lt;UtilityCoinType&gt;(
    <a href="">account</a>: &<a href="">signer</a>
): <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;
<b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>
{
    // Assert <a href="">account</a> is Econia.
    <b>assert</b>!(address_of(<a href="">account</a>) == @econia, <a href="incentives.md#0xc0deb00c_incentives_E_NOT_ECONIA">E_NOT_ECONIA</a>);
    <a href="_extract_all">coin::extract_all</a>( // Extract all coins.
        &<b>mut</b> <b>borrow_global_mut</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>&lt;UtilityCoinType&gt;&gt;(
            <a href="incentives.md#0xc0deb00c_incentives_get_fee_account_address">get_fee_account_address</a>()).coins)
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_update_incentives"></a>

## Function `update_incentives`

Wrapped call to <code>set_incentives()</code>, when calling after
initialization.

Accepts same arguments as <code>set_incentives()</code>, but pass-by-value
instead of pass-by-reference.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_update_incentives">update_incentives</a>&lt;UtilityCoinType&gt;(econia: &<a href="">signer</a>, market_registration_fee: u64, custodian_registration_fee: u64, taker_fee_divisor: u64, integrator_fee_store_tiers: <a href="">vector</a>&lt;<a href="">vector</a>&lt;u64&gt;&gt;)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> entry <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_update_incentives">update_incentives</a>&lt;UtilityCoinType&gt;(
    econia: &<a href="">signer</a>,
    market_registration_fee: u64,
    custodian_registration_fee: u64,
    taker_fee_divisor: u64,
    integrator_fee_store_tiers: <a href="">vector</a>&lt;<a href="">vector</a>&lt;u64&gt;&gt;
) <b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>
{
    <a href="incentives.md#0xc0deb00c_incentives_set_incentive_parameters">set_incentive_parameters</a>&lt;UtilityCoinType&gt;(econia,
        &market_registration_fee, &custodian_registration_fee,
        &taker_fee_divisor, &integrator_fee_store_tiers, &<b>true</b>);
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_upgrade_integrator_fee_store_via_coinstore"></a>

## Function `upgrade_integrator_fee_store_via_coinstore`

Wrapped call to <code><a href="incentives.md#0xc0deb00c_incentives_upgrade_integrator_fee_store">upgrade_integrator_fee_store</a>()</code>, for paying
utility coins from an <code>aptos_framework::Coin::CoinStore</code>.

See wrapped function <code><a href="incentives.md#0xc0deb00c_incentives_upgrade_integrator_fee_store">upgrade_integrator_fee_store</a>()</code>.


<pre><code><b>public</b> <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_upgrade_integrator_fee_store_via_coinstore">upgrade_integrator_fee_store_via_coinstore</a>&lt;QuoteCoinType, UtilityCoinType&gt;(integrator: &<a href="">signer</a>, market_id: u64, new_tier: u8)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> entry <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_upgrade_integrator_fee_store_via_coinstore">upgrade_integrator_fee_store_via_coinstore</a>&lt;
    QuoteCoinType,
    UtilityCoinType
&gt;(
    integrator: &<a href="">signer</a>,
    market_id: u64,
    new_tier: u8,
) <b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>,
    <a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>
{
    // Get cost <b>to</b> upgrade <b>to</b> new tier.
    <b>let</b> cost = <a href="incentives.md#0xc0deb00c_incentives_get_cost_to_upgrade_integrator_fee_store">get_cost_to_upgrade_integrator_fee_store</a>&lt;QuoteCoinType,
        UtilityCoinType&gt;(integrator, &market_id, &new_tier);
    // Upgrade integrator fee store, paying cost from <a href="">coin</a> store.
    <a href="incentives.md#0xc0deb00c_incentives_upgrade_integrator_fee_store">upgrade_integrator_fee_store</a>&lt;QuoteCoinType, UtilityCoinType&gt;(
        integrator, &market_id, &new_tier, <a href="_withdraw">coin::withdraw</a>(
            integrator, cost));
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_assess_taker_fees"></a>

## Function `assess_taker_fees`

Assess fees after a taker fill.

First attempts to assess an integrator's share of taker fees,
then provides Econia with the remaining share. If the integrator
address indicated by <code>integrator_address_ref</code> does not have an
<code><a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStore">IntegratorFeeStore</a></code> for the given market ID and quote coin
type, all taker fees are passed on to Econia. Otherwise the
integrator's fee share is determined based on their tier for the
given market.


<a name="@Type_parameters_17"></a>

### Type parameters

* <code>QuoteCoinType</code>: Quote coin type for market.


<a name="@Parameters_18"></a>

### Parameters

* <code>market_id_ref</code>: Immutable reference to market ID.
* <code>integrator_address_ref</code>: Immutable reference to integrator's
address. May be intentionally marked an address known not to
be an integrator, for example <code>@0x0</code> or <code>@econia</code>, in the
service of diverting all fees to Econia.
* <code>quote_fill_ref</code>: Quote coins filled during a taker match.
* <code>quote_coins_ref_mut</code>: Quote coins to withdraw fees from.


<pre><code><b>public</b>(<b>friend</b>) <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_assess_taker_fees">assess_taker_fees</a>&lt;QuoteCoinType&gt;(market_id_ref: &u64, integrator_address_ref: &<b>address</b>, quote_fill_ref: &u64, quote_coins_ref_mut: &<b>mut</b> <a href="_Coin">coin::Coin</a>&lt;QuoteCoinType&gt;)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b>(<b>friend</b>) <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_assess_taker_fees">assess_taker_fees</a>&lt;QuoteCoinType&gt;(
    market_id_ref: &u64,
    integrator_address_ref: &<b>address</b>,
    quote_fill_ref: &u64,
    quote_coins_ref_mut: &<b>mut</b> <a href="_Coin">coin::Coin</a>&lt;QuoteCoinType&gt;
) <b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>
{
    // Declare tracker for amount of fees collected by integrator.
    <b>let</b> integrator_fee_share = 0;
    // If integrator fee stores map for quote <a href="">coin</a> type <b>exists</b> at
    // indicated integrator <b>address</b>:
    <b>if</b> (<b>exists</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>&lt;QuoteCoinType&gt;&gt;(
        *integrator_address_ref)) {
        // Borrow mutable reference <b>to</b> integrator fee stores map.
        <b>let</b> integrator_fee_stores_map_ref_mut =
            &<b>mut</b> <b>borrow_global_mut</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>&lt;QuoteCoinType&gt;&gt;(
                *integrator_address_ref).map;
        // If fee stores map contains an entry for given market ID:
        <b>if</b> (<a href="table_list.md#0xc0deb00c_table_list_contains">table_list::contains</a>(integrator_fee_stores_map_ref_mut,
            *market_id_ref)) {
            // Borrow mutable reference <b>to</b> corresponding fee store.
            <b>let</b> integrator_fee_store_ref_mut = <a href="table_list.md#0xc0deb00c_table_list_borrow_mut">table_list::borrow_mut</a>(
                integrator_fee_stores_map_ref_mut, *market_id_ref);
            // Calculate integrator fee share for corresponding
            // divisor.
            integrator_fee_share = *quote_fill_ref /
                <a href="incentives.md#0xc0deb00c_incentives_get_fee_share_divisor">get_fee_share_divisor</a>(&integrator_fee_store_ref_mut.tier);
            // Merge into the fee store the corresponding fee share.
            <a href="_merge">coin::merge</a>(&<b>mut</b> integrator_fee_store_ref_mut.coins,
                <a href="_extract">coin::extract</a>(quote_coins_ref_mut, integrator_fee_share));
        }
    }; // Integrator fee share <b>has</b> been assessed.
    // Fee share remaining for Econia is the total taker fee amount
    // less the integrator fee share.
    <b>let</b> econia_fee_share = *quote_fill_ref / <a href="incentives.md#0xc0deb00c_incentives_get_taker_fee_divisor">get_taker_fee_divisor</a>() -
        integrator_fee_share;
    // Merge the corresponding fee share into the Econia fee store
    // for the corresponding market ID and quote <a href="">coin</a> type.
    <a href="_merge">coin::merge</a>(
        <a href="table_list.md#0xc0deb00c_table_list_borrow_mut">table_list::borrow_mut</a>(
            &<b>mut</b> <b>borrow_global_mut</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a>&lt;QuoteCoinType&gt;&gt;(
                <a href="incentives.md#0xc0deb00c_incentives_get_fee_account_address">get_fee_account_address</a>()).map,
            *market_id_ref
        ),
        <a href="_extract">coin::extract</a>(quote_coins_ref_mut, econia_fee_share)
    );
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_deposit_custodian_registration_utility_coins"></a>

## Function `deposit_custodian_registration_utility_coins`

Deposit <code>coins</code> of <code>UtilityCoinType</code>, verifying that the proper
amount is supplied for custodian registration.


<pre><code><b>public</b>(<b>friend</b>) <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_deposit_custodian_registration_utility_coins">deposit_custodian_registration_utility_coins</a>&lt;UtilityCoinType&gt;(coins: <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b>(<b>friend</b>) <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_deposit_custodian_registration_utility_coins">deposit_custodian_registration_utility_coins</a>&lt;
    UtilityCoinType
&gt;(
    coins: <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;
) <b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>,
    <a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>
{
    <a href="incentives.md#0xc0deb00c_incentives_deposit_utility_coins_verified">deposit_utility_coins_verified</a>&lt;UtilityCoinType&gt;(coins,
        &<a href="incentives.md#0xc0deb00c_incentives_get_custodian_registration_fee">get_custodian_registration_fee</a>());
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_deposit_market_registration_utility_coins"></a>

## Function `deposit_market_registration_utility_coins`

Deposit <code>coins</code> of <code>UtilityCoinType</code>, verifying that the proper
amount is supplied for market registration.


<pre><code><b>public</b>(<b>friend</b>) <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_deposit_market_registration_utility_coins">deposit_market_registration_utility_coins</a>&lt;UtilityCoinType&gt;(coins: <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b>(<b>friend</b>) <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_deposit_market_registration_utility_coins">deposit_market_registration_utility_coins</a>&lt;
    UtilityCoinType
&gt;(
    coins: <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;
) <b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>,
    <a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>
{
    <a href="incentives.md#0xc0deb00c_incentives_deposit_utility_coins_verified">deposit_utility_coins_verified</a>&lt;UtilityCoinType&gt;(coins,
        &<a href="incentives.md#0xc0deb00c_incentives_get_market_registration_fee">get_market_registration_fee</a>());
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_init_incentives"></a>

## Function `init_incentives`

Wrapped call to <code>set_incentives()</code>, when calling for the first
time.


<pre><code><b>public</b>(<b>friend</b>) <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_init_incentives">init_incentives</a>&lt;UtilityCoinType&gt;(econia: &<a href="">signer</a>, market_registration_fee_ref: &u64, custodian_registration_fee_ref: &u64, taker_fee_divisor_ref: &u64, integrator_fee_store_tiers_ref: &<a href="">vector</a>&lt;<a href="">vector</a>&lt;u64&gt;&gt;)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b>(<b>friend</b>) <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_init_incentives">init_incentives</a>&lt;UtilityCoinType&gt;(
    econia: &<a href="">signer</a>,
    market_registration_fee_ref: &u64,
    custodian_registration_fee_ref: &u64,
    taker_fee_divisor_ref: &u64,
    integrator_fee_store_tiers_ref: &<a href="">vector</a>&lt;<a href="">vector</a>&lt;u64&gt;&gt;
) <b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>
{
    <a href="incentives.md#0xc0deb00c_incentives_set_incentive_parameters">set_incentive_parameters</a>&lt;UtilityCoinType&gt;(econia,
        market_registration_fee_ref, custodian_registration_fee_ref,
        taker_fee_divisor_ref, integrator_fee_store_tiers_ref, &<b>false</b>);
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_register_econia_fee_store_entry"></a>

## Function `register_econia_fee_store_entry`

Register an <code><a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a></code> entry for market ID indicated by
<code>market_id_ref</code>, for given <code>QuoteCoinType</code>.


<pre><code><b>public</b>(<b>friend</b>) <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_register_econia_fee_store_entry">register_econia_fee_store_entry</a>&lt;QuoteCoinType&gt;(market_id_ref: &u64)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b>(<b>friend</b>) <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_register_econia_fee_store_entry">register_econia_fee_store_entry</a>&lt;QuoteCoinType&gt;(
    market_id_ref: &u64
) <b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>
{
    <b>let</b> fee_account = <a href="incentives.md#0xc0deb00c_incentives_get_fee_account">get_fee_account</a>(); // Get fee <a href="">account</a> <a href="">signer</a>.
    // If an Econia fee store for the quote <a href="">coin</a> type <b>has</b> already
    // been initialized at the fee <a href="">account</a>:
    <b>if</b> (<b>exists</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a>&lt;QuoteCoinType&gt;&gt;(address_of(&fee_account))) {
        // Add <b>to</b> the fee store's underlying map an entry having the
        // market ID <b>as</b> the key, and zero coins <b>as</b> the value.
        <a href="table_list.md#0xc0deb00c_table_list_add">table_list::add</a>(
            &<b>mut</b> <b>borrow_global_mut</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a>&lt;QuoteCoinType&gt;&gt;(
                address_of(&fee_account)).map, *market_id_ref,
                    <a href="_zero">coin::zero</a>&lt;QuoteCoinType&gt;());
    // If an Econia fee store for quote <a href="">coin</a> type <b>has</b> not been
    // initialized at the fee <a href="">account</a>:
    } <b>else</b> {
        // Move <b>to</b> the fee <a href="">account</a> an Econia fee store for the quote
        // <a href="">coin</a> type, initializing the underlying map <b>with</b> a
        // singleton <a href="">table</a> list having the market ID <b>as</b> the key, and
        // zero coins <b>as</b> the value.
        <b>move_to</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a>&lt;QuoteCoinType&gt;&gt;(&fee_account,
            <a href="incentives.md#0xc0deb00c_incentives_EconiaFeeStore">EconiaFeeStore</a>{map: <a href="table_list.md#0xc0deb00c_table_list_singleton">table_list::singleton</a>(*market_id_ref,
                <a href="_zero">coin::zero</a>&lt;QuoteCoinType&gt;())});
    };
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_register_integrator_fee_store"></a>

## Function `register_integrator_fee_store`

Register an <code><a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStore">IntegratorFeeStore</a></code> entry at <code><a href="">account</a></code>.


<a name="@Type_parameters_19"></a>

### Type parameters

* <code>QuoteCoinType</code>: The quote coin type for market.
* <code>UtilityCoinType</code>: The utility coin type.


<a name="@Parameters_20"></a>

### Parameters

* <code><a href="">account</a></code>: Integrator account.
* <code>market_id_ref</code>: Immutable reference to market ID of
corresponding market.
* <code>tier_ref</code>: Immutable reference to the fee store tier to
activate to.
* <code>utility_coins</code>: Utility coins paid to activate to given tier.


<pre><code><b>public</b>(<b>friend</b>) <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_register_integrator_fee_store">register_integrator_fee_store</a>&lt;QuoteCoinType, UtilityCoinType&gt;(<a href="">account</a>: &<a href="">signer</a>, market_id_ref: &u64, tier_ref: &u8, utility_coins: <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b>(<b>friend</b>) <b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_register_integrator_fee_store">register_integrator_fee_store</a>&lt;
    QuoteCoinType,
    UtilityCoinType
&gt;(
    <a href="">account</a>: &<a href="">signer</a>,
    market_id_ref: &u64,
    tier_ref: &u8,
    utility_coins: <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;
) <b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>,
    <a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>
{
    // Deposit verified amount and type of utility coins.
    <a href="incentives.md#0xc0deb00c_incentives_deposit_utility_coins_verified">deposit_utility_coins_verified</a>(utility_coins,
        &<a href="incentives.md#0xc0deb00c_incentives_get_tier_activation_fee">get_tier_activation_fee</a>(tier_ref));
    // Declare integrator fee store for given tier, <b>with</b> no coins.
    <b>let</b> integrator_fee_store = <a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStore">IntegratorFeeStore</a>{tier: *tier_ref, coins:
        <a href="_zero">coin::zero</a>&lt;QuoteCoinType&gt;()};
    // If an integrator fee stores map for quote <a href="">coin</a> type <b>exists</b> at
    // the given <a href="">account</a>:
    <b>if</b> (<b>exists</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>&lt;QuoteCoinType&gt;&gt;(address_of(<a href="">account</a>))) {
        // Add <b>to</b> the map an entry having the market ID <b>as</b> the key,
        // and the integrator fee store <b>as</b> the value.
        <a href="table_list.md#0xc0deb00c_table_list_add">table_list::add</a>(
            &<b>mut</b> <b>borrow_global_mut</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>&lt;QuoteCoinType&gt;&gt;(
                address_of(<a href="">account</a>)).map, *market_id_ref,
                    integrator_fee_store);
    // If an integrator fee stores maps for quote <a href="">coin</a> type does not
    // exist at given <a href="">account</a>:
    } <b>else</b> {
        // Move <b>to</b> the <a href="">account</a> an integrator fee stores map for the
        // quote <a href="">coin</a> type, initializing it <b>with</b> a singleton <a href="">table</a>
        // list having the market ID <b>as</b> the key, and the integrator
        // fee store <b>as</b> the value.
        <b>move_to</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>&lt;QuoteCoinType&gt;&gt;(<a href="">account</a>,
            <a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStores">IntegratorFeeStores</a>{map: <a href="table_list.md#0xc0deb00c_table_list_singleton">table_list::singleton</a>(*market_id_ref,
                integrator_fee_store)});
    }
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_calculate_max_quote_match"></a>

## Function `calculate_max_quote_match`

Get max quote coin match amount, per user input and fee divisor.


<a name="@User_input_21"></a>

### User input

Whether a taker buy or sell, users specify a maximum quote coin
amount when initiating the transaction. This amount indicates
the maximum amount of quote coins they are willing to spend in
the case of a taker buy, and the maximum amount of quote coins
they are willing to receive in the case of a taker sell.


<a name="@Matching_22"></a>

### Matching

The user-specified amount is inclusive of fees, however, and the
matching engine does not manage fees. Instead it accepts a
maximum amount of quote coins to match (or more specifically,
ticks), with fees assessed after matching concludes:


<a name="@Example_buy_23"></a>

#### Example buy

* Taker is willing to spend 105 quote coins.
* Fee is 5% (divisor of 20).
* Max match is thus 100 quote coins.
* Matching engine returns after 100 quote coins filled.
* 5% fee then assessed, withdrawn from takers's quote coins.
* Taker has spent 105 quote coins.


<a name="@Example_sell_24"></a>

#### Example sell

* Taker is willing to receive 100 quote coins.
* Fee is 4% (divisor of 25).
* Max match is thus 104 quote coins.
* Matching engine returns after 104 quote coins filled.
* 4% fee then assessed, withdrawn from quote coins received.
* Taker has received 100 quote coins.


<a name="@Variables_25"></a>

### Variables

Hence, the relationship between user-indicated maxmum quote coin
amount, taker fee divisor, and the amount of quote coins matched
can be described with the following variables:
* $\Delta_t$: Change in quote coins seen by taker.
* $d_t$: Taker fee divisor.
* $q_m$: Quote coins matched.
* $f = \frac{q_m}{d_t}$: Fees assessed.


<a name="@Equations_26"></a>

### Equations



<a name="@Buy_27"></a>

#### Buy


$$q_m = \Delta_t - f = \Delta_t - \frac{q_m}{d_t}$$

$$\Delta_t = q_m + \frac{q_m}{d_t} = q_m(1 + \frac{1}{d_t})$$

$$ q_m = \frac{\Delta_t}{1 + \frac{1}{d_t}} $$

$$ q_m = \frac{d_t \Delta_t}{d_t + 1}$$


<a name="@Sell_28"></a>

#### Sell


$$q_m = \Delta_t + f = \Delta_t + \frac{q_m}{d_t}$$

$$\Delta_t = q_m - \frac{q_m}{d_t} = q_m(1 - \frac{1}{d_t})$$

$$ q_m = \frac{\Delta_t}{1 - \frac{1}{d_t}} $$

$$ q_m = \frac{d_t \Delta_t}{d_t - 1}$$


<a name="@Parameters_29"></a>

### Parameters

* <code>direction_ref</code>: <code>&<a href="incentives.md#0xc0deb00c_incentives_BUY">BUY</a></code> or <code>&<a href="incentives.md#0xc0deb00c_incentives_SELL">SELL</a></code>.
* <code>taker_fee_divisor_ref</code>: Immutable reference to taker fee
divisor.
* <code>max_quote_delta_user_ref</code>: Immutable reference to maximum
change in quote coins seen by user: spent if a <code><a href="incentives.md#0xc0deb00c_incentives_BUY">BUY</a></code> and
received if a <code><a href="incentives.md#0xc0deb00c_incentives_SELL">SELL</a></code>.
* <code>max_quote_to_match_ref_mut</code>: Mutable reference to maximum
amount of quote coins to match.


<a name="@Assumptions_30"></a>

### Assumptions

* Taker fee divisor is greater than 1.


<a name="@Aborts_if_31"></a>

### Aborts if

* Maximum amount to match does not fit in a <code>u64</code>, which should
only be possible in the case of a <code><a href="incentives.md#0xc0deb00c_incentives_SELL">SELL</a></code>.


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_calculate_max_quote_match">calculate_max_quote_match</a>(direction_bool: &bool, taker_fee_divisor_ref: &u64, max_quote_delta_user_ref: &u64, max_quote_match_ref_mut: &<b>mut</b> u64)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_calculate_max_quote_match">calculate_max_quote_match</a>(
    direction_bool: &bool,
    taker_fee_divisor_ref: &u64,
    max_quote_delta_user_ref: &u64,
    max_quote_match_ref_mut: &<b>mut</b> u64
) {
    // Calculate numerator for both buy and sell equations.
    <b>let</b> numerator = (*taker_fee_divisor_ref <b>as</b> u128) *
        (*max_quote_delta_user_ref <b>as</b> u128);
    // Calculate denominator based on direction.
    <b>let</b> denominator = <b>if</b> (*direction_bool == <a href="incentives.md#0xc0deb00c_incentives_BUY">BUY</a>)
        (*taker_fee_divisor_ref + 1 <b>as</b> u128) <b>else</b>
        (*taker_fee_divisor_ref - 1 <b>as</b> u128);
    // Calculate maximum quote coins <b>to</b> match.
    <b>let</b> max_quote_match = numerator / denominator;
    // Assert maximum quote <b>to</b> match fits in a u64.
    <b>assert</b>!(max_quote_match &lt;= (<a href="incentives.md#0xc0deb00c_incentives_HI_64">HI_64</a> <b>as</b> u128),
        <a href="incentives.md#0xc0deb00c_incentives_E_MAX_QUOTE_MATCH_OVERFLOW">E_MAX_QUOTE_MATCH_OVERFLOW</a>);
    // Cast and reassign maximum quote match value.
    *max_quote_match_ref_mut = (max_quote_match <b>as</b> u64);
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_deposit_utility_coins"></a>

## Function `deposit_utility_coins`

Deposit <code>coins</code> to a <code><a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a></code>.


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_deposit_utility_coins">deposit_utility_coins</a>&lt;UtilityCoinType&gt;(coins: <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_deposit_utility_coins">deposit_utility_coins</a>&lt;UtilityCoinType&gt;(
    coins: <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;
) <b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>
{
    <a href="_merge">coin::merge</a>(&<b>mut</b> <b>borrow_global_mut</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>&lt;UtilityCoinType&gt;&gt;(
        <a href="incentives.md#0xc0deb00c_incentives_get_fee_account_address">get_fee_account_address</a>()).coins, coins);
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_deposit_utility_coins_verified"></a>

## Function `deposit_utility_coins_verified`

Verify that <code>UtilityCoinType</code> is the utility coin type and that
<code>coins</code> has at least the amount indicated by <code>min_amount_ref</code>,
then deposit all utility coins to <code><a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a></code>.


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_deposit_utility_coins_verified">deposit_utility_coins_verified</a>&lt;UtilityCoinType&gt;(coins: <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;, min_amount_ref: &u64)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_deposit_utility_coins_verified">deposit_utility_coins_verified</a>&lt;UtilityCoinType&gt;(
    coins: <a href="_Coin">coin::Coin</a>&lt;UtilityCoinType&gt;,
    min_amount_ref: &u64
) <b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>,
    <a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>
{
    // Verify utility <a href="">coin</a> type.
    <a href="incentives.md#0xc0deb00c_incentives_verify_utility_coin_type">verify_utility_coin_type</a>&lt;UtilityCoinType&gt;();
    // Assert sufficient utility coins provided.
    <b>assert</b>!(<a href="_value">coin::value</a>(&coins) &gt;= *min_amount_ref,
        <a href="incentives.md#0xc0deb00c_incentives_E_NOT_ENOUGH_UTILITY_COINS">E_NOT_ENOUGH_UTILITY_COINS</a>);
    // Deposit all utility coins <b>to</b> utility <a href="">coin</a> store.
    <a href="incentives.md#0xc0deb00c_incentives_deposit_utility_coins">deposit_utility_coins</a>(coins);
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_get_fee_account"></a>

## Function `get_fee_account`

Return fee account signer generated from stored capability.


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_fee_account">get_fee_account</a>(): <a href="">signer</a>
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_get_fee_account">get_fee_account</a>():
<a href="">signer</a>
<b>acquires</b> <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a> {
    <a href="_create_signer_with_capability">account::create_signer_with_capability</a>(
        &<b>borrow_global</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>&gt;(@econia).
            fee_account_signer_capability)
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_init_fee_account"></a>

## Function `init_fee_account`

Initialize the resource account where fees, collected by Econia,
are stored.


<a name="@Parameters_32"></a>

### Parameters

* <code>econia</code>: The Econia account <code><a href="">signer</a></code>.


<a name="@Returns_33"></a>

### Returns

* <code><a href="">signer</a></code>: The resource account <code><a href="">signer</a></code>.


<a name="@Seed_considerations_34"></a>

### Seed considerations

* Resource account creation seed supplied as an empty vector,
pending the acceptance of <code>aptos-core</code> PR #4173. If PR is not
accepted by version release, will be updated to accept a seed
as a function argument.


<a name="@Aborts_if_35"></a>

### Aborts if

* <code>econia</code> does not indicate the Econia account.


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_init_fee_account">init_fee_account</a>(econia: &<a href="">signer</a>): <a href="">signer</a>
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_init_fee_account">init_fee_account</a>(
    econia: &<a href="">signer</a>
): <a href="">signer</a> {
    // Assert <a href="">signer</a> is from Econia <a href="">account</a>.
    <b>assert</b>!(address_of(econia) == @econia, <a href="incentives.md#0xc0deb00c_incentives_E_NOT_ECONIA">E_NOT_ECONIA</a>);
    // Create resource <a href="">account</a>, storing signing capability.
    <b>let</b> (fee_account, fee_account_signer_capability) = account::
        create_resource_account(econia, b"");
    // Store fee <a href="">account</a> <a href="">signer</a> capability under Econia <a href="">account</a>.
    <b>move_to</b>(econia, <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>{
        fee_account_signer_capability});
    fee_account // Return fee <a href="">account</a> <a href="">signer</a>.
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_init_utility_coin_store"></a>

## Function `init_utility_coin_store`

Initialize a <code><a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a></code> under the Econia fee account.

Returns without initializing if a <code><a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a></code> already
exists for given <code>CoinType</code>.


<a name="@Type_Parameters_36"></a>

### Type Parameters

* <code>CoinType</code>: Utility coin phantom type.


<a name="@Parameters_37"></a>

### Parameters

* <code>fee_account</code>: Econia fee account <code><a href="">signer</a></code>.


<a name="@Aborts_if_38"></a>

### Aborts if

* <code>CoinType</code> does not correspond to an initialized
<code>aptos_framework::coin::Coin</code>.


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_init_utility_coin_store">init_utility_coin_store</a>&lt;CoinType&gt;(fee_account: &<a href="">signer</a>)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_init_utility_coin_store">init_utility_coin_store</a>&lt;CoinType&gt;(
    fee_account: &<a href="">signer</a>
) {
    // Assert <a href="">coin</a> type corresponds <b>to</b> initialized <a href="">coin</a>.
    <b>assert</b>!(<a href="_is_coin_initialized">coin::is_coin_initialized</a>&lt;CoinType&gt;(), <a href="incentives.md#0xc0deb00c_incentives_E_NOT_COIN">E_NOT_COIN</a>);
    // If a utility <a href="">coin</a> store does not already exist at <a href="">account</a>,
    <b>if</b>(!<b>exists</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>&lt;CoinType&gt;&gt;(address_of(fee_account)))
        // Initialize one and <b>move</b> it <b>to</b> the <a href="">account</a>.
        <b>move_to</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>&lt;CoinType&gt;&gt;(fee_account, <a href="incentives.md#0xc0deb00c_incentives_UtilityCoinStore">UtilityCoinStore</a>{
            coins: <a href="_zero">coin::zero</a>&lt;CoinType&gt;()});
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_set_incentive_parameters"></a>

## Function `set_incentive_parameters`

Set all fields for <code><a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a></code> under Econia account.

Rather than pass-by-value a
<code><a href="">vector</a>&lt;<a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStoreTierParameters">IntegratorFeeStoreTierParameters</a>&gt;</code>, mutably reassigns
the values of <code><a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>.integrator_fee_store_tiers</code>
via <code><a href="incentives.md#0xc0deb00c_incentives_set_incentive_parameters_parse_tiers_vector">set_incentive_parameters_parse_tiers_vector</a>()</code>.


<a name="@Type_Parameters_39"></a>

### Type Parameters

* <code>UtilityCoinType</code>: Utility coin phantom type.


<a name="@Parameters_40"></a>

### Parameters

* <code>econia</code>: Econia account <code><a href="">signer</a></code>.
* <code>market_registration_fee_ref</code>: Immutable reference to market
registration fee to set.
* <code>custodian_registration_fee_ref</code>: Immutable reference to
custodian registration fee to set.
* <code>taker_fee_divisor_ref</code>: Immutable reference to
taker fee divisor to set.
* <code>integrator_fee_store_tiers_ref</code>: Immutable reference to
0-indexed vector of 3-element vectors, with each 3-element
vector containing fields for a corresponding
<code><a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStoreTierParameters">IntegratorFeeStoreTierParameters</a></code>.
* <code>updating_ref</code>: <code>&<b>true</b></code> if updating incentive parameters that
have already beeen set, <code>&<b>false</b></code> if setting parameters for the
first time.


<a name="@Assumptions_41"></a>

### Assumptions

* If <code>updating_ref</code> is <code>&<b>true</b></code>, an <code><a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a></code> and a
<code><a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a></code> already exist at the Econia
account.
* If <code>updating_ref</code> is <code>&<b>false</b></code>, neither an
<code><a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a></code> nor a <code><a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a></code>
exist at the Econia account.


<a name="@Aborts_if_42"></a>

### Aborts if

* <code>updating_ref</code> is <code>&<b>true</b></code> and the new parameter set indicates
a reduction in the number of fee store activation tiers, which
would mean that integrators who had previously upgraded to the
highest tier would become subject to undefined behavior.


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_set_incentive_parameters">set_incentive_parameters</a>&lt;UtilityCoinType&gt;(econia: &<a href="">signer</a>, market_registration_fee_ref: &u64, custodian_registration_fee_ref: &u64, taker_fee_divisor_ref: &u64, integrator_fee_store_tiers_ref: &<a href="">vector</a>&lt;<a href="">vector</a>&lt;u64&gt;&gt;, updating_ref: &bool)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_set_incentive_parameters">set_incentive_parameters</a>&lt;UtilityCoinType&gt;(
    econia: &<a href="">signer</a>,
    market_registration_fee_ref: &u64,
    custodian_registration_fee_ref: &u64,
    taker_fee_divisor_ref: &u64,
    integrator_fee_store_tiers_ref: &<a href="">vector</a>&lt;<a href="">vector</a>&lt;u64&gt;&gt;,
    updating_ref: &bool
) <b>acquires</b>
    <a href="incentives.md#0xc0deb00c_incentives_FeeAccountSignerCapabilityStore">FeeAccountSignerCapabilityStore</a>,
    <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>
{
    // Range check inputs.
    <a href="incentives.md#0xc0deb00c_incentives_set_incentive_parameters_range_check_inputs">set_incentive_parameters_range_check_inputs</a>(econia,
        market_registration_fee_ref, custodian_registration_fee_ref,
        taker_fee_divisor_ref, integrator_fee_store_tiers_ref);
    // Get fee <a href="">account</a> <a href="">signer</a>: <b>if</b> updating previously-set values,
    // get it from the stored capability.
    <b>let</b> fee_account = <b>if</b> (*updating_ref) <a href="incentives.md#0xc0deb00c_incentives_get_fee_account">get_fee_account</a>() <b>else</b>
        // Else get fee <a href="">account</a> <a href="">signer</a> by initializing the <a href="">account</a>.
        <a href="incentives.md#0xc0deb00c_incentives_init_fee_account">init_fee_account</a>(econia);
    // Initialize a utility <a href="">coin</a> store under the fee acount (aborts
    // <b>if</b> not an initialized <a href="">coin</a> type).
    <a href="incentives.md#0xc0deb00c_incentives_init_utility_coin_store">init_utility_coin_store</a>&lt;UtilityCoinType&gt;(&fee_account);
    <b>if</b> (*updating_ref) { // If updating previously-set values:
        // Assert new parameters set indicates at least <b>as</b> many fee
        // store tiers <b>as</b> the set from before the upgrade.
        <b>assert</b>!(<a href="_length">vector::length</a>(integrator_fee_store_tiers_ref) &gt;=
            <a href="incentives.md#0xc0deb00c_incentives_get_n_fee_store_tiers">get_n_fee_store_tiers</a>(), <a href="incentives.md#0xc0deb00c_incentives_E_FEWER_TIERS">E_FEWER_TIERS</a>);
    } <b>else</b> { // If initializing parameter set:
        // Initialize an incentive parameters resource <b>with</b>
        // range-checked inputs and empty tiers <a href="">vector</a>.
        <b>move_to</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>&gt;(econia, <a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>{
            utility_coin_type_info: <a href="_type_of">type_info::type_of</a>&lt;UtilityCoinType&gt;(),
            market_registration_fee: *market_registration_fee_ref,
            custodian_registration_fee: *custodian_registration_fee_ref,
            taker_fee_divisor: *taker_fee_divisor_ref,
            integrator_fee_store_tiers: <a href="_empty">vector::empty</a>()
        });
    };
    // Borrow a mutable reference <b>to</b> the incentive parameters
    // resource at the Econia <a href="">account</a>.
    <b>let</b> incentive_parameters_ref_mut =
        <b>borrow_global_mut</b>&lt;<a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>&gt;(@econia);
    // Parse in integrator fee store tiers (aborts for invalid
    // values).
    <b>if</b> (*updating_ref) { // If updating previously-set values:
        incentive_parameters_ref_mut.utility_coin_type_info =
            <a href="_type_of">type_info::type_of</a>&lt;UtilityCoinType&gt;();
        // Set market registration fee.
        incentive_parameters_ref_mut.market_registration_fee =
            *market_registration_fee_ref;
        // Set custodian registration fee.
        incentive_parameters_ref_mut.custodian_registration_fee =
            *custodian_registration_fee_ref;
        // Set taker fee divisor.
        incentive_parameters_ref_mut.taker_fee_divisor =
            *taker_fee_divisor_ref;
        // Set integrator fee stores <b>to</b> empty <a href="">vector</a>.
        incentive_parameters_ref_mut.integrator_fee_store_tiers =
            <a href="_empty">vector::empty</a>();
    };
    <a href="incentives.md#0xc0deb00c_incentives_set_incentive_parameters_parse_tiers_vector">set_incentive_parameters_parse_tiers_vector</a>(
        taker_fee_divisor_ref, integrator_fee_store_tiers_ref,
        &<b>mut</b> incentive_parameters_ref_mut.integrator_fee_store_tiers);
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_set_incentive_parameters_parse_tiers_vector"></a>

## Function `set_incentive_parameters_parse_tiers_vector`

Parse vectorized fee store tier parameters passed to
<code><a href="incentives.md#0xc0deb00c_incentives_set_incentive_parameters">set_incentive_parameters</a>()</code>.

* <code>taker_fee_divisor_ref</code>: Immutable reference to
taker fee divisor to compare against.
* <code>integrator_fee_store_tiers_ref</code>: Immutable reference to
0-indexed vector of 3-element vectors, with each 3-element
vector containing fields for a corresponding
<code><a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStoreTierParameters">IntegratorFeeStoreTierParameters</a></code>.
* <code>integrator_fee_store_tiers_target_ref_mut</code>: Mutable reference
to the <code><a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a>.integrator_fee_store_tiers</code> field
to parse into.


<a name="@Aborts_if_43"></a>

### Aborts if

* An indicated inner vector from
<code>integrator_fee_store_tiers_ref</code> is the wrong length.
* Fee share divisor does not decrease with tier number.
* A fee share divisor is less than taker fee divisor.
* Tier activation fee for first tier is nonzero.
* Tier activation fee does not increase with tier number.
* There is no tier activation fee for the first tier.
* Withdrawal fee does not decrease with tier number.
* The withdrawal fee for a given tier does not meet minimum
threshold.


<a name="@Assumptions_44"></a>

### Assumptions

* <code>taker_fee_divisor_ref</code> indicates a value that has already
been range-checked.
* An <code><a href="incentives.md#0xc0deb00c_incentives_IncentiveParameters">IncentiveParameters</a></code> exists at the Econia account.
* <code>integrator_fee_store_tiers_ref</code> does not indicate an empty
vector.
* <code>integrator_fee_store_tiers_target_ref_mut</code> indicates an empty
vector.


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_set_incentive_parameters_parse_tiers_vector">set_incentive_parameters_parse_tiers_vector</a>(taker_fee_divisor_ref: &u64, integrator_fee_store_tiers_ref: &<a href="">vector</a>&lt;<a href="">vector</a>&lt;u64&gt;&gt;, integrator_fee_store_tiers_target_ref_mut: &<b>mut</b> <a href="">vector</a>&lt;<a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStoreTierParameters">incentives::IntegratorFeeStoreTierParameters</a>&gt;)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_set_incentive_parameters_parse_tiers_vector">set_incentive_parameters_parse_tiers_vector</a>(
    taker_fee_divisor_ref: &u64,
    integrator_fee_store_tiers_ref: &<a href="">vector</a>&lt;<a href="">vector</a>&lt;u64&gt;&gt;,
    integrator_fee_store_tiers_target_ref_mut:
        &<b>mut</b> <a href="">vector</a>&lt;<a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStoreTierParameters">IntegratorFeeStoreTierParameters</a>&gt;
) {
    // Initialize tracker variables for the fee store parameters of
    // the last parsed tier.
    <b>let</b> (divisor_last, activation_fee_last, withdrawal_fee_last) = (
                <a href="incentives.md#0xc0deb00c_incentives_HI_64">HI_64</a>,               <a href="incentives.md#0xc0deb00c_incentives_HI_64">HI_64</a>,               <a href="incentives.md#0xc0deb00c_incentives_HI_64">HI_64</a>);
    // Get number of specified integrator fee store tiers.
    <b>let</b> n_tiers = <a href="_length">vector::length</a>(integrator_fee_store_tiers_ref);
    <b>let</b> i = 0; // Declare counter for <b>loop</b> variable.
    <b>while</b> (i &lt; n_tiers) { // Loop over all specified tiers
        // Borrow immutable reference <b>to</b> fields for given tier.
        <b>let</b> tier_fields_ref =
            <a href="_borrow">vector::borrow</a>(integrator_fee_store_tiers_ref, i);
        // Assert containing <a href="">vector</a> is correct length.
        <b>assert</b>!(<a href="_length">vector::length</a>(tier_fields_ref) == <a href="incentives.md#0xc0deb00c_incentives_N_TIER_FIELDS">N_TIER_FIELDS</a>,
            <a href="incentives.md#0xc0deb00c_incentives_E_TIER_FIELDS_WRONG_LENGTH">E_TIER_FIELDS_WRONG_LENGTH</a>);
        // Borrow immutable reference <b>to</b> fee share divisor.
        <b>let</b> fee_share_divisor_ref =
            <a href="_borrow">vector::borrow</a>(tier_fields_ref, <a href="incentives.md#0xc0deb00c_incentives_FEE_SHARE_DIVISOR_INDEX">FEE_SHARE_DIVISOR_INDEX</a>);
        // Assert indicated fee share divisor is less than divisor
        // from last tier.
        <b>assert</b>!(*fee_share_divisor_ref &lt; divisor_last,
            <a href="incentives.md#0xc0deb00c_incentives_E_FEE_SHARE_DIVISOR_TOO_BIG">E_FEE_SHARE_DIVISOR_TOO_BIG</a>);
        // Assert indicated fee share divisor is greater than or
        // equal <b>to</b> taker fee divisor.
        <b>assert</b>!(*fee_share_divisor_ref &gt;= *taker_fee_divisor_ref,
            <a href="incentives.md#0xc0deb00c_incentives_E_FEE_SHARE_DIVISOR_TOO_SMALL">E_FEE_SHARE_DIVISOR_TOO_SMALL</a>);
        // Borrow immutable reference <b>to</b> tier activation fee.
        <b>let</b> tier_activation_fee_ref =
            <a href="_borrow">vector::borrow</a>(tier_fields_ref, <a href="incentives.md#0xc0deb00c_incentives_TIER_ACTIVATION_FEE_INDEX">TIER_ACTIVATION_FEE_INDEX</a>);
        <b>if</b> (i == 0) { // If parsing parameters for first tier:
            // Assert activation fee is 0
            <b>assert</b>!(*tier_activation_fee_ref == 0,
                <a href="incentives.md#0xc0deb00c_incentives_E_FIRST_TIER_ACTIVATION_FEE_NONZERO">E_FIRST_TIER_ACTIVATION_FEE_NONZERO</a>);
        } <b>else</b> { // If parameters for tier that is not first:
            // Assert activation fee greater than that of last tier.
            <b>assert</b>!(*tier_activation_fee_ref &gt; activation_fee_last,
                <a href="incentives.md#0xc0deb00c_incentives_E_ACTIVATION_FEE_TOO_SMALL">E_ACTIVATION_FEE_TOO_SMALL</a>);
        };
        // Borrow immutable reference <b>to</b> withdrawal fee.
        <b>let</b> withdrawal_fee_ref =
            <a href="_borrow">vector::borrow</a>(tier_fields_ref, <a href="incentives.md#0xc0deb00c_incentives_WITHDRAWAL_FEE_INDEX">WITHDRAWAL_FEE_INDEX</a>);
        // Assert withdrawal fee is less than that of last tier.
        <b>assert</b>!(*withdrawal_fee_ref &lt; withdrawal_fee_last,
            <a href="incentives.md#0xc0deb00c_incentives_E_WITHDRAWAL_FEE_TOO_BIG">E_WITHDRAWAL_FEE_TOO_BIG</a>);
        // Assert withdrawal fee is above minimum threshold.
        <b>assert</b>!(*withdrawal_fee_ref &gt; <a href="incentives.md#0xc0deb00c_incentives_MIN_FEE">MIN_FEE</a>, <a href="incentives.md#0xc0deb00c_incentives_E_WITHDRAWAL_FEE_TOO_SMALL">E_WITHDRAWAL_FEE_TOO_SMALL</a>);
        // Mark indicated tier in target tiers <a href="">vector</a>.
        <a href="_push_back">vector::push_back</a>(integrator_fee_store_tiers_target_ref_mut,
            <a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStoreTierParameters">IntegratorFeeStoreTierParameters</a>{
                fee_share_divisor: *fee_share_divisor_ref,
                tier_activation_fee: *tier_activation_fee_ref,
                withdrawal_fee: *withdrawal_fee_ref});
        // Store divisor for comparison during next iteration.
        divisor_last = *fee_share_divisor_ref;
        // Store activation fee <b>to</b> compare during next iteration.
        activation_fee_last = *tier_activation_fee_ref;
        // Store withdrawal fee <b>to</b> compare during next iteration.
        withdrawal_fee_last = *withdrawal_fee_ref;
        i = i + 1; // Increment <b>loop</b> counter
    };
}
</code></pre>



</details>

<a name="0xc0deb00c_incentives_set_incentive_parameters_range_check_inputs"></a>

## Function `set_incentive_parameters_range_check_inputs`

Range check inputs for <code><a href="incentives.md#0xc0deb00c_incentives_set_incentive_parameters">set_incentive_parameters</a>()</code>.


<a name="@Parameters_45"></a>

### Parameters

* <code>econia</code>: Econia account <code><a href="">signer</a></code>.
* <code>market_registration_fee_ref</code>: Immutable reference to market
registration fee to set.
* <code>custodian_registration_fee_ref</code>: Immutable reference to
custodian registration fee to set.
* <code>taker_fee_divisor_ref</code>: Immutable reference to
taker fee divisor to set.
* <code>integrator_fee_store_tiers_ref</code>: Immutable reference to
0-indexed vector of 3-element vectors, with each 3-element
vector containing fields for a corresponding
<code><a href="incentives.md#0xc0deb00c_incentives_IntegratorFeeStoreTierParameters">IntegratorFeeStoreTierParameters</a></code>.


<a name="@Aborts_if_46"></a>

### Aborts if

* <code>econia</code> is not Econia account.
* <code>market_registration_fee_ref</code> indicates fee that does not
meet minimum threshold.
* <code>custodian_registration_fee_ref</code> indicates fee that does
not meet minimum threshold.
* <code>taker_fee_divisor_ref</code> indicates divisor that does not
meet minimum threshold.
* <code>integrator_fee_store_tiers_ref</code> indicates an empty vector.
* <code>integrator_fee_store_tiers_ref</code> indicates a vector that is
too long.


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_set_incentive_parameters_range_check_inputs">set_incentive_parameters_range_check_inputs</a>(econia: &<a href="">signer</a>, market_registration_fee_ref: &u64, custodian_registration_fee_ref: &u64, taker_fee_divisor_ref: &u64, integrator_fee_store_tiers_ref: &<a href="">vector</a>&lt;<a href="">vector</a>&lt;u64&gt;&gt;)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>fun</b> <a href="incentives.md#0xc0deb00c_incentives_set_incentive_parameters_range_check_inputs">set_incentive_parameters_range_check_inputs</a>(
    econia: &<a href="">signer</a>,
    market_registration_fee_ref: &u64,
    custodian_registration_fee_ref: &u64,
    taker_fee_divisor_ref: &u64,
    integrator_fee_store_tiers_ref: &<a href="">vector</a>&lt;<a href="">vector</a>&lt;u64&gt;&gt;
) {
    // Assert <a href="">signer</a> is from Econia <a href="">account</a>.
    <b>assert</b>!(address_of(econia) == @econia, <a href="incentives.md#0xc0deb00c_incentives_E_NOT_ECONIA">E_NOT_ECONIA</a>);
    // Assert market registration fee meets minimum threshold.
    <b>assert</b>!(*market_registration_fee_ref &gt;= <a href="incentives.md#0xc0deb00c_incentives_MIN_FEE">MIN_FEE</a>,
        <a href="incentives.md#0xc0deb00c_incentives_E_MARKET_REGISTRATION_FEE_LESS_THAN_MIN">E_MARKET_REGISTRATION_FEE_LESS_THAN_MIN</a>);
    // Assert custodian registration fee meets minimum threshold.
    <b>assert</b>!(*custodian_registration_fee_ref &gt;= <a href="incentives.md#0xc0deb00c_incentives_MIN_FEE">MIN_FEE</a>,
        <a href="incentives.md#0xc0deb00c_incentives_E_CUSTODIAN_REGISTRATION_FEE_LESS_THAN_MIN">E_CUSTODIAN_REGISTRATION_FEE_LESS_THAN_MIN</a>);
    // Assert taker fee divisor is meets minimum threshold.
    <b>assert</b>!(*taker_fee_divisor_ref &gt;= <a href="incentives.md#0xc0deb00c_incentives_MIN_DIVISOR">MIN_DIVISOR</a>,
        <a href="incentives.md#0xc0deb00c_incentives_E_TAKER_DIVISOR_LESS_THAN_MIN">E_TAKER_DIVISOR_LESS_THAN_MIN</a>);
    // Assert integrator fee store parameters <a href="">vector</a> not empty.
    <b>assert</b>!(!<a href="_is_empty">vector::is_empty</a>(integrator_fee_store_tiers_ref),
        <a href="incentives.md#0xc0deb00c_incentives_E_EMPTY_FEE_STORE_TIERS">E_EMPTY_FEE_STORE_TIERS</a>);
    // Assert integrator fee store parameters <a href="">vector</a> not too long.
    <b>assert</b>!(<a href="_length">vector::length</a>(integrator_fee_store_tiers_ref) &lt;=
        <a href="incentives.md#0xc0deb00c_incentives_MAX_INTEGRATOR_FEE_STORE_TIERS">MAX_INTEGRATOR_FEE_STORE_TIERS</a>, <a href="incentives.md#0xc0deb00c_incentives_E_TOO_MANY_TIERS">E_TOO_MANY_TIERS</a>);
}
</code></pre>



</details>