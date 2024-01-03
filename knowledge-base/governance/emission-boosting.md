# Emissions Boosting

### What is Boost?

Users with lock weight are eligible to receive boosted PRISMA emissions. "Boost" refers to a bonus on claimable PRISMA tokens that a vault receives based on it's locked PRISMA weight. A user with "max boost" earns PRISMA rewards at 2x the rate of a vault that is unboosted.

### How is Boost Calculated?

Boost works as follows:

*   In a given week, the percentage of the weekly PRISMA rewards that a vault can claim with maximum boost is the same as the percentage of PRISMA lock weight that the vault has, relative to the total lock weight.
*   Once a vault's weekly claims exceed the amount allowed with max boost, the boost rate decays linearly from 2x to 1x. This decay occurs over the same amount of tokens that were available for maximum boost.
*   Once a vault's weekly claims are more than double the amount allowed for max boost, the boost bonus is fully depleted.
*   At the start of the next week, boost amounts are recalculated.
    

Note that boost is applied at the time of claiming a reward, not at the time the reward was earned. A vault that has depleted it's boost may opt to wait for the start of the next week in order to claim with a larger boost.

### Example of Boost Calculation

*   At the end of week 1, Alice has a lock weight of 100. There is a total lock weight of 1,000. Alice controls 10% of the total lock weight.
*   During week 2, a total of 500,000 new PRISMA rewards are made available
*   Because Alice has 10% of the lock weight in week 1, during week 2 she can claim up to 10% of the rewards (50,000 PRISMA) with her full boost.
*   Once Alice's weekly claim exceeds 50,000 PRISMA, her boost decays linearly. Over the next 50,000 potential PRISMA claimed, she receives only 37,500.
*   Once Alice's weekly potential claims exceed 100,000 PRISMA, any further claims are "unboosted" and receive only half as many tokens as they would have boosted.
*   At the start of the next week, Alice's boost is fully replenished. She still controls 10% of the total lock weight, so she can claim another 10% of this week's emissions at full boost.
    

### Boost Delegation

Anyone with lock weight has the option to make their boost available for use by other users. This is known as "boost delegation". When enabling delegation, a user can set:

*   a percentage fee, taken from the claimant and given to the delegate each time the delegate's boost is used
*   an optional smart contract that receives a callback each time a delegate's boost is used
    

The callback contract can be used to build an additional layer on top of delegation. It could implement white/blacklists, distribute additional incentives, etc.

### Technical Details

On a technical level, we consider the full earned reward to be the maximum boosted amount. "Unboosted" is more accurately described as "paying a 50% penalty on potential claimable rewards".

Rewards that go undistributed due to claims with lowered boost are returned to the unallocated token supply and distributed in the emissions of future weeks. Thus, boost also serves as a mechanism to extend the timespan of meaningful PRISMA emissions.
