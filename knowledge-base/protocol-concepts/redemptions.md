# Redemptions


### Peg mechanisms

`mkUSD` maintains a close association with `usd` due to its redeemability for collaterals at face value (i.e., 1 `mkUSD` can be exchanged for $1 worth of a collateral of choice), and the mandated minimum collateral ratio of `120%`. These conditions create a price floor and ceiling, respectively, through arbitrage opportunities. These are known as "hard peg mechanisms" as they rely on explicit operations.

However, `mkUSD` also utilizes more indirect methods to maintain `usd` parity — referred to as "soft peg mechanisms". One such mechanism is parity as a Schelling point. As the **Prisma** protocol treats `mkUSD` as equivalent to `usd`, parity between the two is an inherent equilibrium state of the system.

Another mechanism is the minting fee on new debts. As redemptions rise (indicating `mkUSD` is below $1), the base rate also increases — thus making borrowing less appealing, which prevents new `mkUSD` from flooding the market and driving the price below $1.

### Redemptions

A redemption refers to the act of exchanging `mkUSD` for collateral at face value, assuming 1 `mkUSD` is exactly equal to `$1`. Therefore, for X `mkUSD`, you receive X Dollars worth of collateral in return.

Users are free to redeem their `mkUSD` for any collateral of choice among those supported by **Prisma** anytime without restrictions. However, a redemption fee may be imposed on the redeemed amount.

For instance, if the prevailing redemption fee is `1%`, the price of `rETH` is `$500`, and you redeem `100 mkUSD`, you would receive `0.198 rETH` (`0.2 rETH` less a redemption fee of `0.002 rETH`).

Note that the redeemed amount contributes to the calculation of the `baseRate` and may influence the redemption fee, particularly for large amounts.

#### Redemption fee calculation

Under normal circumstances, the redemption fee is calculated using the formula:

`(baseRate + 0.5%) * CollateralDrawn`

#### baseRate calculation

Redemption fees are based on the `baseRate` state variable in `Vault Manager`, which is dynamically updated. The `baseRate` rises with each redemption and decays proportionally to the time elapsed since the last redemption or `mkUSD` issuance (fee event).

Each redemption causes the following changes:

*   The `baseRate` experiences decay relative to the time passed since the last fee event.
*   The `baseRate` increases by an amount in proportion to the fraction of the total `mkUSD` supply that was redeemed.
    
#### Redemptions effect on vaults

If a vault is redeemed against, it does not suffer a net loss. However, its collateral exposure will decrease. The vault's collateral ratio will also improve after a redemption.

The most effective way to prevent redemption against your vault is to maintain a high collateral ratio relative to the rest of the vaults in the system. Keep in mind: The riskiest vaults (i.e., the least collateralized vaults) are targeted first when a redemption occurs.
