# Depositing Collateral and Minting mkUSD

### Minting mkUSD

Users open a vault and mint `mkUSD` by depositing a [Prisma supported collateral](/protocol-concepts/supported-collaterals). A **minimum debt** of `2,000 mkUSD` is required (this includes the `200 mkUSD` [Liquidation Reserve](/protocol-concepts/depositing-collateral-and-minting-mkusd#liquidation-reserve)) up to a **maximum debt** at a collateral ratio of `120%.`

### Vault

A vault is a loan against a specific collateral type. Each vault is linked to an Ethereum address and each address can have just one vault for a given collateral type. If you are familiar with accounts or CDPs from other platforms, vaults are similar in concept.

Vaults maintain two balances: the collateral balance and the `mkUSD` debt balance. Users can manage these balances by adding or removing collateral, or increasing or repaying debt. A vault's collateral ratio changes as these balances are adjusted.

Vaults can be closed at any time by fully paying off its debt.

### Borrowing fees

Borrowing may incur fees, see [Fees](/protocol-concepts/fees).

### Loan duration

Loans issued by the protocol do not have a repayment schedule; debt can be repaid at any time.

### Vault Collateral Ratio

The collateral ratio is the ratio between the US Dollar value of the collateral in a vault and its debt in `mkUSD`. The collateral ratio of a vault will fluctuate as the price of the collateral changes. Users can adjust the ratio by adding or removing collateral, or increasing or repaying debt.

_For example:_ Assuming the present value of `rETH` stands at `$2,000` and you opt to deposit `30 rETH`, taking out a loan of `30,000` `mkUSD` would give you a collateral ratio of `200%`.

```math
$2000∗30rETH30000mkUSD∗100%\=200%\\frac{\\$2000 \* 30 rETH}{30000 mkUSD} \* 100\\% = 200\\% 30000mkUSD$2000∗30rETH​∗100%\=200%
```

However, if the `rETH` price drops to `$1,000` the ratio becomes `100%`.

### **Minimum collateral ratio (MCR)**

The Minimum Collateral Ratio (MCR) denotes the foundational debt-to-collateral ratio that, when maintained, prevents liquidation during standard operations, termed as Normal Mode. This parameter, integral to the protocol, is determined by governance for each specific collateral type. For instance, with an MCR set at `120%`, a vault holding a debt of `20,000` `mkUSD` requires a collateral valuation of no less than `$24,000` to safeguard against liquidation.

To avoid being liquidated in [Recovery Mode](/protocol-concepts/recovery-mode) it's advisable to maintain a ratio well beyond `150%`, ideally around `200%` to `250%`.

### Multiple Collateral Types

**Prisma** supports multiple collateral types, therefore users can open multiple vaults, one for each supported collateral. It is important to note the following points:

*   1. Collateral types are segregated, therefore each collateral's Total Collateral Ratio (TCR) is calculated independently.
*   2. Collateral types may have different protocol parameters so at any given time using each collateral might be cheaper or more expensive than the others (see [Fees](/protocol-concepts/fees)).
*   3. [Prisma emissions](/governance/prisma-emission-voting) might be different for each collateral type.
    

### Vault liquidations

During [liquidations](/protocol-concepts/depositing-collateral-and-minting-mkusd#account-liquidations), a vault's collateral is lost as it is used to pay off the account's debt. The vault owner will no longer be able to retrieve the collateral by repaying debt. A liquidation thus results in a net loss of `16.67% (= 100% * 20 / 120)` of the collateral’s `usd` value.

### Liquidation Reserve

When a vault is opened, a sum of `200 mkUSD` is reserved and held by the protocol. This is known as the `Liquidation Reserve`, and it serves to cover the gas costs incurred by the liquidator initiating the transaction in the case that a vault gets liquidated.

The Liquidation Reserve is completely refundable. This reserve is returned when a vault is closed by paying off the debt or if there is a [redemption against it.](/protocol-concepts/depositing-collateral-and-minting-mkusd#redemptions)​

It's crucial to note that the Liquidation Reserve is considered part of a vault's debt, and therefore, it’s factored into the computation of a vault's collateral ratio and interest payment. This slightly increases the actual requirements for collateral.

### Redemptions

When `mkUSD` is redeemed, the collateral provided to the redeemer is allocated from the vault(s) with the lowest collateral ratio (even if it is above `120%`) for that collateral type. If at the time of redemption you have the vault with the lowest ratio, you will give up some of your collateral, but your debt will be reduced accordingly.

For more details see [Redemptions](/protocol-concepts/redemptions).
