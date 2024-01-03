# Adding and Removing Collaterals

### Introduction

**Prisma** design allows for the inclusion of a variety of collateral types. These collaterals can be added or removed via a governance vote. This page provides an overview of how collaterals can be added, how they can be removed (a process referred to as `sunsetting`), and the implications for the `Stability Pool`. Note than any new collateral need to go through a Risk Report by the independent Prisma Risk Team before any vote proposal.

### Adding Collaterals

Collaterals can be added to the Prisma protocol through a proposal and voting process. If the majority of the governance token holders agree, a new collateral type can be added. Once a new collateral type is added, it can be used to secure loans and participate in other system functionalities. The interest rate, loan-to-value ratio, and other parameters for each collateral type are set by governance.

#### Implementation

A new collateral is added by calling the function `deployNewInstance` on the `Factory` contract. A collateral type cannot be added more than once. Upon execution of the aforementioned function the following actions are performed:

*   1. A new `Account Manager` and `Sorted Accounts` are deployed
*   2. The collateral is allowed into the `Stability Pool`, `Borrower Operations`, `Liquidation Manager` and `mkUSD` contracts
*   3. Initial parameters for that collateral are set within the protocol
    

### Sunsetting Collaterals

Sometimes, it may become necessary to remove a collateral type from the **Prisma** protocol. This process is known as `sunsetting` a collateral. Sunsetting is initiated via a governance vote and has several implications:

*   1. **Collateral Handoff:** When a collateral type is being sunset, collateral handoff from `Account Manager` to the stability Pool (SP) for any liquidation is disabled. Instead, only redistribution of collateral and debt among vaults for the same collateral type is allowed.
    

*   2. **Interest Rate Adjustment:** The interest rate for the sunset collateral is increased to 50% APR. This high interest rate is intended to incentivize the repayment of loans backed by the sunset collateral.
    

*   3. **Redemption Fees:** The redemption fees for the sunset collateral are removed. This makes it more attractive for users to redeem `mkUSD` against that collateral.
    

*   4. **New Loans:** The creation of new loans backed by the sunset collateral is disabled. This helps to gradually phase out the use of the sunset collateral.
    

### Stability Pool Implications

The [stability pool](/protocol-concepts/liquidations-and-the-stability-pool) plays a critical role in maintaining the stability of the **Prisma** system. During the sunsetting of a collateral, certain rules apply to the stability pool:

*   1. **Collateral Withdrawals:** Withdrawals for the sunset collateral from the stability pool are halted and all balances cleared 180 days after the initiation of the sunsetting process.
    
*   2. **Collateral Index Reuse:** After the sunset period has ended, the collateral index used to identify a collateral in the s_tability pool_ can be reused.
