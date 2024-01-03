# Fees

### Introduction

The **Prisma** protocol is designed with flexibility and adaptability at its core, allowing it to accommodate the varying needs of its users. The protocol offers two types of fees:

*   Fixed fees ([Minting fee](/protocol-concepts/fees#1.-minting-fees) and [Redemption fee](/protocol-concepts/fees#2.-redemption-fees))
    

*   ​[Borrowing interes](/protocol-concepts/fees#3.-borrow-interest-rate)​[t rate](/protocol-concepts/fees#3.-borrow-interest-rate)​
    

The aim of these fees is to maintain the stability and liquidity of the protocol while also providing an incentive for user participation.

Both fixed fees and continuous interest can be adjusted by the governance of the **Prisma** Protocol. This means that the **Prisma** community can vote on the parameters of these fees for each collateral type, allowing the protocol to adapt to changing market conditions and ensuring that it continues to offer competitive rates for its users.

### Minting Fees

Minting fees are one-time fees charged at the moment of borrowing. In the Prisma protocol, this fee is applied when a user borrows `mkUSD` against their collateral.

Every time `mkUSD` is drawn from an vault, a minting fee is charged on the drawn amount and added to the debt. Please note that the minting fee is variable (and determined algorithmically), with a minimum value of `0.5%` under normal operation. The fee is `0%` during [`Recovery Mode`](/protocol-concepts/recovery-mode). A `200 mkUSD` `Liquidation Reserve` charge will be applied as well, but returned upon repayment of debt.

#### Minting fee calculation

The minting fee is added to the debt of the vault and is determined by a `baseRate`. The fee rate is confined to a range between `0.5%` and `5%` and is multiplied by the amount of liquidity drawn by the borrower.

_For example:_ The borrowing fee stands at `0.5%` and the borrower wants to receive `4,000 mkUSD` to their wallet. Being charged a borrowing fee of `20.00 mkUSD`, the borrower will incur a debt of `4,220 mkUSD` after the Liquidation Reserve and mint fee are added.

### Redemption fees

In **Prisma**, redemptions are transactions where users can exchange their `mkUSD` for a collateral of their choice at face value, subject to a fee known as the Redemption Fee. The purpose of this fee is to protect the system during periods of low collateral ratio by disincentivizing redemptions and ensuring the system remains solvent. You can find more detail on how it's calculated [here](/protocol-concepts/redemptions).

### Borrow Interest Rate

Borrow Interest Rate is a fee that accrues over time on outstanding debt. This is common in most lending protocols and serves as a source of revenue that helps maintain the protocol's operations. In **Prisma**, this fee is charged on the `mkUSD` borrowed against the collateral and the DAO will have a say concerning its parameters.

#### Interest Calculation

Interest accrues to all borrowers in a market when any _Ethereum_ address interacts with the protocol contracts, calling one of these functions: `liquidateaVault`, `batchLiquidateVault`, `redeemCollateral`, `openVault`, `addColl`, `withdrawColl`, `repayDebt`, `adjustVault`, `closeVault`.

Successful execution of one of these functions triggers the `_accrueActiveInterests` method, which causes interest to be added to the underlying balance of every borrower in the market. Interest accrues for the current block, as well as each prior block in which the `_accrueActiveInterests` method was not triggered (no user interacted with the `Vault Manager` contract). Interest compounds only during blocks in which one of the aforementioned methods is invoked.

#### Example of interest accrual:

*   Alice mints `10,000 mkUSD` from the **Prisma** protocol.
*   At the time of supply, the `interestRate` is `0.00000031709792 per second`.
*   No one interacts with the `Vault Manager` contract for 100 seconds.
*   Subsequently, Bob borrows some `mkUSD`.
*   Alice’s underlying debt is now `10,000.317097919837646 mkUSD` (which is `0.00000031709792 times 100 seconds times the principal`, plus the original `10,000 mkUSD`).
*   Alice’s underlying `mkUSD` balance in subsequent blocks will have interest accrued based on the new value of `10,000.317097919837646 mkUSD` instead of the initial `10,000 mkUSD`.
    

### Interest Rate Index and Borrowing Balance

#### Implementation

Each time a transaction occurs, the Interest Rate Index for the asset is updated to compound the interest since the prior index. This is done using the interest for the period, denominated by

r∗t r \* tr∗t

, calculated using a per-second interest rate. The formula for this is:

activeInterestIndexc,n\=activeInterestIndexc,(n−1)∗(1+r∗t)activeInterestIndex\_{c,n} = activeInterestIndex\_{c,(n-1)} \* (1 + r \* t)activeInterestIndexc,n​\=activeInterestIndexc,(n−1)​∗(1+r∗t)

In this formula:


activeInterestIndexc,n activeInterestIndex\_{c,n} activeInterestIndexc,n​
    
c represents the Interest Rate Index for collateral type
n at time
​r represents the per-second interest rate
​t represents the time period since the last index update
    

The market's total borrowing outstanding is also updated to include the interest accrued since the last index. The formula for this update is:

totalDebtc,n\=totalDebtc,(n−1)∗(1+r∗t)totalDebt\_{c,n} = totalDebt\_{c,(n-1)} \* (1 + r \* t)totalDebtc,n​\=totalDebtc,(n−1)​∗(1+r∗t)

In this formula:

totalDebtc,n totalDebt\_{c,n} totalDebtc,n​

c represents the total debt balance for collateral type
n at time


Each individual `vault` tracks the `activeInterestIndex` at the time of its last debt change.

The current vault debt at any time is then:

currentVaultDebt\=vault.debt∗activeInterestIndexvault.activeInterestIndexcurrentVaultDebt = \\frac{vault.debt \* activeInterestIndex}{vault.activeInterestIndex}currentVaultDebt\=vault.activeInterestIndexvault.debt∗activeInterestIndex​

#### Limitations

When calculating interest in `_accrueActiveInterests` simple interest is applied over the seconds since the last update. This will underestimate the amount of interest that would be calculated if it were compounded every second.

The code is designed to accrue interest as frequently as possible. Additionally, the size of the discrepancy between the computed and theoretical interest will depend on the volume of transactions being handled by the Prisma protocol, which may change unpredictably.
