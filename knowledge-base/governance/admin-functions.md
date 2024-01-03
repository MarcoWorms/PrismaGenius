# Admin Functions

### Introduction

Prisma is an immutable and fully on-chain protocol. Despite this, some minimal admin functions are retained and operated via governance.

All members on the Emergency Multisig can be found [here](/governance/admin-functions/emergency-multisig).

### Emergency Pausing

Pausing in Prisma is designed to halt all operations except those which allow collateral recovery by the user. This mechanism is designed to maximize safety while at the same time reduce collateral from being stuck due to unforeseen bugs in an immutable protocol.

This also increases users' confidence that Governance and/or Guardians cannot unduly lock their capital.

#### Protocol-wide

In the unlikely event of a protocol-wide catastrophic issue, these functions can be paused by a multi-sig controlled by a set of notable DeFi figures:

*   Opening a new vault
*   Increase collateral for an existing vault
*   Increase debt for an existing vault
*   Deposit `mkUSD` into the Stability Pool
    

#### Collateral Pausing

If there are urgent problems with a specific collateral, the guardian multi-sig can pause the `Account Manager` relative to that collateral. In this case, pausing will affect the following functions:

*   Opening a new vault
*   Increase collateral for an existing vault
*   Increase debt for an existing vault
    

### Unpausing

Unpausing both protocol-wide and at the collateral level can only be enacted via governance.

### Setting Guardians multi-sig

Governance can vote to change the guardian multi-sig.

### Changing the fee receiver

All protocol fees are directed to an address labeled fee receiver. The initial fee receiver implementation is a simple contract that allows token transfers via a governance vote. It is also possible for governance to vote to change the fee receiver address.

### Changing Price Feed

In the interest of future-proofing, governance can vote to replace the protocol price feed.

### Collateral sunset

​[Collateral sunset](/governance/adding-and-removing-collaterals#sunsetting-collaterals) can be voted via governance.

### Adding new collateral

​[Adding a new collateral](/governance/adding-and-removing-collaterals#adding-collaterals) can be voted via governance.

### Replacing default Account Manager and Sorted Account implementations

Whenever a new collateral is added, an `Account Manager` and a `Sorted Account` contract are deployed as a clone of a default implementation.

Governance has the power to change said default implementations.