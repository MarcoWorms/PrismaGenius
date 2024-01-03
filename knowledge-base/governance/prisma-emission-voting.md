# PRISMA Emission Voting

Users who have locked PRISMA can submit votes to determine how PRISMA emissions are distributed within the protocol.

Prisma's emission voting is conceptually similar to Curve's gauge weight voting.

### How it works

Users can allocate their lock weight towards one or more emission receivers. At the start of each week, receivers are allocated a fraction of the weekly PRISMA emissions, proportional to how much lock weight they were allocated.

Lock weight is allocated in percentage. Each user has a maximum of 100%. A user must allocate all 100% in order to vote with their entire lock weight. Votes can be modified at any time. Whatever votes a user has submitted by the start of Thursday of each week, is the vote applied for the following week. Note that your votes persist week-to-week unless you either override them or "clear your votes" on the PRISMA tab. This feature will make you save gas and prevent you from missing votes deadlines.

### Registering Vote Weight

The first year of PRISMA emissions are distributed as locked positions. This means:

*   Users lock weights have the potential to change very frequently - adjusting vote weights each time a lock weight changes would be very gas-intensive.
*   For this reason, users must register their lock weight within the voting contract in order to submit a vote.
*   If their lock weight increases after submitting the vote, they may optionally resubmit the vote with the increased weight.
    
This functionality is largely abstracted from end users via Prisma's front-end, but integrators should review the `IncentiveVoting` contract and be aware of this requirement.

### Voting on weekly emissions

Users can vote on 4 different actions across the protocol. Performing these actions will earn you PRISMA. These are:

*   Depositing to the Stability Pool
*   Minting new `mkUSD` (with a particular collateral)
*   Maintaining an active `mkUSD` debt (with a particular collateral)
*   Staking Curve LP tokens
    
For example, if you had an active debt position collateralised by stETH, you could choose to vote for maintaining an active `mkUSD` debt - collateralised by stETH. In turn, this would direct more PRISMA emissions for the following week towards this action.

Or, you could choose to vote for minting new `mkUSD` with stETH as collateral - if you had planned to mint more `mkUSD` against your existing collateral. You may also wish to deposit more stETH and mint `mkUSD` against it as a way to receive a portion of that week’s PRISMA emissions allocated to this action.
