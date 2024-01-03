# The PRISMA token

PRISMA is the governance token of the Prisma protocol. It is distributed to users of the protocol for performing a variety of actions, and can be locked to participate in protocol governance.

### Earning PRISMA

PRISMA is distributed to protocol users for performing a variety of actions. Some examples include:

*   Depositing to the Stability Pool
    

*   Minting new `mkUSD`
    

*   Maintaining an active `mkUSD` debt
    

*   Staking Curve LP tokens
    

### PRISMA Utility

PRISMA is used within the protocol as a governance token.

*   1. PRISMA is [locked](/governance/prisma-locking-and-lock-weight) for up to 52 weeks in order to receive lock weight
*   2. Lock weight is used to vote for the distribution of [PRISMA emissions](/governance/prisma-emission-voting)​
*   3. Lock weight can be used to vote on [protocol ownership](/governance/dao-admin-voting) actions
    
Other use cases may arise in the future, as a result of protocol ownership voting.

### Total Supply and Allocation

PRISMA has a maximum total supply of 300 million. All tokens are minted immediately when the protocol is deployed. Tokens are initially held by the `Treasury`, and released gradually over time. The treasury balance is not considered to be in circulation.

The supply of PRISMA is allocated as follows:

*   62% (186,000,000 PRISMA) are allocated towards emissions. These emissions are directed by the Prisma DAO and incentivise certain actions within the Prisma Protocol. Emissions can additionally be used to incentivise liquidity on liquidity pools.
*   20% (60,000,000 PRISMA) are allocated to the Core Contributors. These tokens will be unlocked linearly for 12 months starting at Genesis.
*   10% (30,000,000 PRISMA) is allocated to Early Supporters who assisted in bootstrapping costs associated with the initial development of the Prisma Protocol. These tokens will be unlocked linearly for 12 months starting at Genesis.
*   5% (15,000,000 PRISMA) will be held in the Prisma DAO Treasury.
*   3% (9,000,000 PRISMA) will be distributed towards veCRV voters and Prisma Point holders.
    
**Genesis** is the time and date at which the token emissions of PRISMA start.

### Incentive Distribution Schedule

New protocol incentives are allocated weekly according to the [emission voting](/governance/prisma-emission-voting) results. The total amount to be released each week follows a set schedule:

The first four weeks are the "high emission period". A maximum of 9 million PRISMA is released linearly over this period (3% of the total supply). During this time, all earned PRISMA is locked for 26 weeks upon claiming. The goal is to reward early users and encourage a healthy amount of lock weight to participate in protocol governance.

After the high emission period finishes, the amount of weekly emissions is calculated as a percentage of the remaining unallocated PRISMA supply. The percentage released each week is as follows:

Time

Emissions

Weeks 1-4

2,250,000 tokens per week

Weeks 5-13

1.2% of the remaining emission tokens per week

Weeks 14-26

1% the remaining emission tokens per week

Weeks 27-39

0.9% the remaining emission tokens per week

Weeks 40-52

0.8% the remaining emission tokens per week

Year 1-2

0.7% the remaining emission tokens per week

Year 2-3

0.6% the remaining emission tokens per week

Year 3+

0.5% the remaining emission tokens per week

Note that because of how the Prisma boost system works, the numbers quoted above are the maximum amount claimable in that week; the actual claims will be somewhere between 50-100% of these numbers, and anything unclaimed due to this is returned to the unallocated supply.

Earned PRISMA continues to be locked upon claiming for the first year. The number of weeks of the lock decreases by one every 2 weeks, eventually reaching 0 slightly after 1 year from launch. It is possible to exit a locked position early by paying a withdrawal fee (see [Withdrawing early from Locked Positions](/governance/prisma-locking-and-lock-weight)). According to this schedule, up to 60% of the total supply will be released within the first year. The actual amount will likely be less, due to claims made without [maximum boost](/governance/emissions-boosting).
