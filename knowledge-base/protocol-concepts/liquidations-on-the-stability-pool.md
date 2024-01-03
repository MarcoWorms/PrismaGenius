# Liquidations and the Stability Pool

### Introduction

The stability pool serves as a primary safeguard to ensure the solvency of the system. Its role is to provide the necessary liquidity to cover the debt from liquidated vaults, thereby guaranteeing that the total `mkUSD` supply is always adequately collateralized.

Whenever a vault is liquidated, an equivalent amount of `mkUSD` (corresponding to the remaining debt of the vault) is destroyed from the stability pool's balance to settle its debt. As a result, the entirety of the vault's collateral is transferred to the stability pool.

The stability pool is financed by users (known as stability providers) depositing `mkUSD` into it. Over time, these stability providers witness a proportional reduction in their `mkUSD` deposits, but in return, they gain a proportional share of the liquidated collaterals.

Given that vaults are usually liquidated at slightly below `120%` collateral ratios, it is anticipated that stability providers will amass a larger `usd` value of collaterals relative to the debt they offset.

### Benefits for Stability Providers

Stability providers benefit from financing the stability pool in several ways.

#### Collateral distribution

To start with, stability providers get access to discounted collaterals (from all the supported collaterals in Prisma) from liquidations without the need to spend gas or run liquidation bots.

As liquidations happen just below the `MCR`, which is greater than `100%`, stability providers receive a discount of `MCR - 100%` on the liquidated collateral, thus experiencing a net gain when a vault is liquidated.

Assume a total of `2,000,000 mkUSD` exists in the stability Pool, and you've deposited `200,000 mkUSD`.

If a vault with `200,000 mkUSD` debt and `300 rETH` collateral faces liquidation when the `rETH` price is `$666`, and another with `100,000 mkUSD` debt and `200 wstETH` collateral is liquidated at a `wstETH` price of `$666`, you'll be impacted based on your 10% pool share.

Specifically, your deposit will decrease by `10%` of the liquidated debt, amounting to `30,000 mkUSD`. This means your deposit will diminish from `200,000 to 170,000 mkUSD`. In compensation, you'll acquire 10% of the liquidated collateral: `30 rETH` and `20 wstETH`. At the given price, this collateral is valued at `$33,300`, rendering you a net profit of `$3,300` from the liquidation event.

#### Prisma Token Emissions

Furthermore, the stability pool is natively integrated into the [Prima emission system](/governance/prisma-emission-voting) and therefore they accrue emissions while providing liquidity.

Stability providers can coordinate and vote to maximize the share of emission directed toward stability pool deposits

### Liquidations

In order to maintain full collateral backing for the entire `mkUSD` supply, vaults that descend beneath the minimum collateral ratio of `120%` are subject to liquidation.

The debt associated with the liquidated vault is nullified and absorbed by the stability pool, and the collateral is redistributed amongst the stability providers.

Despite the liquidation, the vault owner retains the full amount of `mkUSD` borrowed but suffers an overall loss up to `20%` in value. Consequently, it is crucial for borrowers to maintain their collateral ratio above the minimum threshold of `120%`, and ideally, they should aim to keep it above `150%`.

#### Liquidators

Anyone can initiate the liquidation of an vault once its collateral ratio falls below the Minimum Collateral Ratio of `120%`. To incentivize this action, the liquidator is rewarded with a gas compensation.

Liquidating vaults involves certain gas costs that the liquidator must bear. To mitigate these costs, the protocol allows batch liquidations of multiple vaults, reducing the cost per vault. However, to ensure liquidations remain profitable even when gas prices skyrocket, the protocol provides a gas compensation determined by the following formula:

`Gas Compensation = 200 mkUSD + 0.5% of vault's Collateral`

The `200 mkUSD` is sourced from the Liquidation Reserve, while the variable `0.5%` portion is taken from the liquidated collateral. This slightly diminishes the liquidation gain for stability providers.

#### Liquidations rules

The way liquidations are enacted varies depending on certain conditions. This table elucidates all the different scenarios.

**`ICR`** `= Individual Collateral Ratio`

**`MCR`** `= Minimum Collateral Ratio`

**`GTCR`** `= Global Total Collateral Ratio`

**`SP`** `= Stability Pool`

Condition

Liquidation Behavior

`ICR <=100%`

Redistribute all debt and collateral (minus collateral gas compensation) to active vaults.

`100% < ICR < MCR`

The stability Pool `mkUSD` is offset with an equal amount of debt from the vault. A fraction of the vault's collateral (equal to the ratio of its offset debt to its entire debt) is shared between depositors. Any remaining debt and collateral (minus collateral gas compensation) is redistributed to active vaults.

`GTCR < 150% & MCR <= ICR < GTCR & SP mkUSD >= vault debt`

The protocol is in [recovery mode](/protocol-concepts/recovery-mode). The stability Pool `mkUSD` is offset with an equal amount of debt from the vault. A fraction of collateral with dollar value equal to `1.2 * debt` is shared between depositors. Nothing is redistributed to other active vaults. Since its `ICR` was `> 1.2`, the vault has a collateral remainder, which is claimable by the borrower. The vault is closed.

#### Should liquidations occur while the stability pool is unfunded, what will happen?

When the stability pool lacks funds, an alternate liquidation process known as "redistribution" comes into play. In this scenario, the system reallocates the debt and collateral held within liquidated vault to all other vaults currently in existence. This reallocation is performed based on the collateral value of each receiving vault.

#### Claiming liquidated collateral

Collateral transferred to the stability pool in the contexts of liquidations can be claimed by depositors. Before being able to claim the user must accrue its current apportioned amounts.

Operations which perform such an accruing are

*   1. Depositing to the pool
*   2. Withdrawing from the pool (also 0 amount)
*   3. Claiming Prisma rewards
    

To avoid an extra transactions the claimer can assess if the accrued value is up to date with the following client side check:

​```
claimable \= sp.getDepositorCollateralGain(account)

for i in range(len(claimable)):

if claimable\[i\] \> 0:

assert sp.collateralGainsByDepositor(account, i) \== claimable\[i\]
```
​
if this check passes, the user can call `claimCollateralGains` normally using the indexes with non zero claimable amounts in the claimable array. if this check fails, they must either:

*   1. claim any pending PRISMA rewards first
*   2. send a transaction to withdraw 0 mkUSD from the stability pool, updating the claimable balance.
    