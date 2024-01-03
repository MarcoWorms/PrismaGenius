# DAO Admin Voting

Certain Prisma smart contracts contain admin-only functionality. All admin functions are callable only after the creation and successful passing of an admin DAO vote.

### Types of Admin Votes

Some examples of possible admin actions are:

*   modifying fees
*   adding or removing a collateral
*   pausing or unpausing protocol functionality
*   transfer protocol fees
*   adjusting the quorum on admin votes
    

### How voting works

In order to create a vote, a user must meet a minimum lock weight requirement. This is done to prevent vote spamming.

A vote consists of one or more smart contract calls, collectively referred to as the "payload". It is important that each voter reviews the payload prior to voting, to ensure the vote does not perform any malicious actions.

Users who are in favor of the vote can allocate their lock weight toward the proposal. A vote passes once the weight signaling in support exceeds a quorum. There is no concept of a "no" vote, users who are not in favor should abstain from voting.

24 hours after a vote has passed quorum, the payload can be executed by anyone. The 24 hour delay serves as protection from malicious votes - in the unlikely event that a vote which passes has a payload containing an action that would do damage to the protocol, there is time for users to react prior to the payload being executed.

Votes are valid for one week from their creation time.

### Guardian

#### Powers

A DAO guardian (operated via a multi-sig) has the power to cancel any pending proposals.

#### Replacing the guardian

The replacement of the guardian must be submitted as the first action in a proposal. Such a proposal is non-cancellable by the guardian.

This can be used if the guardian is acting maliciously.
