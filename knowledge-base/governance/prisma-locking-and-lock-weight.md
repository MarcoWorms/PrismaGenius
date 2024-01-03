# PRISMA Locking and Lock Weight

Participating in Prisma governance requires that a user lock a balance of PRISMA tokens. Once locked, the tokens give the user "lock weight", which is used in determining voting power.

Prisma's token locking is inspired by, and functions similarly to, the popular veToken model created by Curve.

### How Locking Works

*   Users receive lock weight by locking PRISMA for a number of weeks. "Weeks" refers to the number of weeks that must pass before the tokens can be withdrawn.
*   The maximum duration for a lock is 52 weeks.
*   Each user can have multiple locks of different durations.
*   It is possible to extend the duration of an existing lock.
*   Locks can be split (by extending the duration for only a portion of a locked balance) or merged (by extending one lock's duration to the same duration as another lock).
*   Every Thursday, the number of weeks for a lock decreases by 1. When the lock duration reaches 0 weeks, the tokens may be withdrawn at any time.
    

### How Lock Weight is Calculated

A user's lock weight is calculated as:

LOCK\_WEIGHT \= sum(weeks \* balance for (weeks, balance) in USER\_LOCKS)

### Freezing your Lock Weight

Users can optionally "freeze" their lock weight. When frozen, all active locks are extended to 52 weeks. The time-to-unlock no longer decays each week. Any tokens added to a frozen lock are also frozen.

Freezing is useful for integrators, protocols participating in emission voting, or anyone that never intends to withdraw their locked position. Freezing greatly reduces gas costs for emission voting. Emission votes from frozen locks also do not decay.

A frozen lock can be unfrozen at any time and the lock weight will being to decay at the end of the same week it is unfrozen.

### Withdrawing early from Locked Positions

It is possible to exit a locked position early by paying a withdrawal fee. The fee to exit early starts at 100% and decays linearly based on the number of weeks remaining until the tokens unlock. The exact calculation used is:

fee\_amount \= (total\_amount \* weeks\_to\_unlock) // 52

Penalty withdrawals are always processed starting with the lock that will expire soonest. Locks for 52 weeks are ignored, because the penalty to withdraw would be 100%.

Penalty fees are sent to the Prisma [fee receiver](/governance/admin-functions#changing-the-fee-receiver).
