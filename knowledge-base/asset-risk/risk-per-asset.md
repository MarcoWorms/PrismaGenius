# Risk per Asset

This section showcases the results of the risk assessment provided by PrismaRisk.

## Lido wstETH

Full report from Prisma Risk Team: [https://hackmd.io/@PrismaRisk/wsteth](https://hackmd.io/@PrismaRisk/wsteth) This section will summarize the findings of the report by highlighting the most significant risk factors in each of the three risk categories: Market Risk, Technology Risk, and Counterparty Risk.

#### 1\. Market Risk

_LIQUIDITY: Does the LSD have a liquid market that can facilitate liquidations in all foreseeable market events?_

Lido is a clear market leader, commanding over 70% of the LSD market since its inception in December 2021. It has been integrated widely as collateral into several DeFi lending protocols such as MakerDAO and Aave, and has over $600m worth of liquidity on DEXs such as Curve and Balancer. The [DeFillama Liquidity Tool](https://defillama.com/liquidity) estimates a swap size of $300m (158k stETH) would be required to produce >1% slippage. stETH/wstETH account for 2/3 of all LSD trading volume, and its strong standing against competitors does not appear to be waning.

_VOLATILITY: Has the LSD had any significant depeg event (post merge)?_

Arriving at the merge in September 2022, stETH had been experiencing a prolonged depeg event since the Terra collapse in May 2022. It recovered around the time of the merge, but experienced a second, relatively minor depeg in November 2022. A whale [removed 88,131](https://twitter.com/lookonchain/status/1595719510387875840?s=20) ETH from the stETH/ETH pool, causing a sharp depeg to .9682 that did not completely recover until January 2023.

Since ETH withdrawals have been activated in April 2023, the liquid staking basis has markedly stabilized, meaning stETH has maintained a consistent peg against ETH. We do observe, however, that staking yields have been declining as demand for staking continues to boom. Reduced yields may affect demand for LSDs such as stETH, resulting in the need to process large amounts of withdrawals.

Withdrawals are not instantaneous and can take weeks to process if the exit queue is long or a major slashing event occurs. Tumultuous market circumstances or network problems within Lido or Ethereum at large may precipitate a depeg in the future that cannot be immediately arbitraged.

#### 2\. Technology Risk

_SMART CONTRACTS: Does the analysis of the audits and development activity suggest any cause for concern?_

Lido V2 codebase has undergone extensive audits in 2023 by various auditing firms including Oxorio, Statemind, Hexens, MixBytes, and Certora. There is also an active bug bounty program with ImmuneFi since May 2021. Lido discloses network problems that result in losses in their Post Mortem blog. Losses have historically been minimal, and where applicable, Lido has reimbursed affected users.

The recent upgrade to Lido V2 in May 2023 allows additional functionality, including ETH withdrawals. This increases the uncertainty of smart contract security due to the short duration on mainnet.

_DEPENDENCIES: Does the analysis of dependencies (e.g. oracles) suggest any cause for concern?_

In case of no finality on the Consensus Layer, Lido’s oracle daemons may stop pushing regular updates (set to 225 epochs or 1 day), preventing rebases from taking place. If sanity checks fail (on max APR or total staked amount drop), this could cause significant disruptions in Lido’s operations, including incorrect distribution of rewards and liquidity mismanagement.

Due to extreme market events on November 9 and 11, 2022, a protocol-enforced sanity check was erroneously triggered that prevented Oracle updates and caused a disruption in rewards distribution. The event was documented in this [post mortem](https://blog.lido.fi/postmortem-disrupted-rewards-distribution-due-to-missed-oracle-reports/).

Lido has a reliable Chainlink pricefeed oracle available for both stETH/ETH and stETH/USD pairs.

#### 3\. Counterparty Risk

_CENTRALIZATION: Are there any significant centralization vectors that could rug users?_

Concerning smart contract access control, Lido has taken precautions to protect contract upgrades and other critical system controls behind an Aragon DAO governed by LDO tokenholders. For convenience, EasyTrack optimistic voting is used for a limited subset of recurring vote types. LDO has never experienced a governance attack, and while it may be theoretically exposed to such a risk by not requiring a lock to participate in governance, LDO does not realistically have market liquidity or presence on lending platforms to be a concern at this time.

A number of multisigs have privileges limited to specific functions, such as the GateSeal committee’s ability to emergency pause the system. The GateSeal further decreases the likelihood of a governance attack, although with the tradeoff of requiring trust in the committee to take necessary action.

Lido also takes measures to decentralize its permissioned set of node operators by monitoring the distribution of stake across NOs, and diversity metrics such as clients, staking infrastructure, and geographies of operation. These precautions minimize the risk of a major slashing event.

In short, users are required to trust in the reliable performance of third-party NOs, but Lido has taken precautions to avoid centralization of the NO network.

_LEGAL: Does the legal analysis of the protocol suggest any cause for concern?_

While the regulatory climate surrounding DAO and DeFi remains uncertain, it is unclear how an enforcement action might be carried out against a DAO. As Lido is governed by LDO tokenholders, legal action is unlikely to disrupt the platform’s operations. A potential centralization risk is from the large proportion of NOs operating in Europe (60% of ETH staked in Lido), which increases the network’s risk exposure to regulatory action in those jurisdictions.

There is no discernible evidence that Lido has been involved with any unlawful activities and it has not received any enforcement actions. The interface [Terms of Use](https://lido.fi/terms-of-use) takes reasonable precautions to limit Lido’s liability. While enforcement actions are always a possibility in an uncertain regulatory climate, Lido appears to be reasonably protected.

#### 4\. Risk Rating

Based on the risks identified for each category, the following chart summarizes a risk rating for wstETH as collateral. The rating for each category is ranked from excellent, good, ok, and poor.

*   We rank wstETH **excellent on liquidity** for being the clear market leader with deepest liquidity.
*   We rank wstETH **ok in volatility** due to multiple depeg events pre-Shanghai and a high level of uncertainty about withdrawal processing, which may inhibit arbitrage.
*   We rank wstETH **good in smart contracts** for being heavily audited, having a bug bounty program, and having a long history securing billions in TVL without major incident. The recent upgrade to V2 increases smart contract uncertainty.
*   We rank wstETH **good in dependencies** for having a reliable pricefeed available. Dependency of lido oracle daemons can result in disruptions that can cause incorrect reward distribution or liquidity mismanagement.
*   We rank wstETH **good in centralization** for having core system controls with a DAO that has reasonable backstop measures. Multiple multisigs are employed with limited privileges for specific precautionary functions.
*   We rank wstETH **good in legal** for having no enforcement actions historically, Lido limits liability in their terms and conditions and decentralization is sufficient that legal action is unlikely to disrupt the network. A concentration of NOs in Europe increases vulnerability in those jurisdictions.
    
    ![](https://content.gitbook.com/content/1tAi6RdL45CCiZaxKFFS/blobs/MN6Bo7k5zOOtziGbTGUK/image.png)
    

The overall risk profile and persistently dominant market standing of Lido make wstETH suitable as a core collateral type within Prisma. All additional LSDs reviewed will undergo a comparative analysis against Lido to determine how well they complement wstETH for suitability within the collateral basket.

## RocketPool rETH

Full report from Prisma Risk Team: [https://hackmd.io/@PrismaRisk/rETH](https://hackmd.io/@PrismaRisk/rETH) This section will summarize the findings of the report by highlighting the most significant risk factors in each of the three risk categories: Market Risk, Technology Risk, and Counterparty Risk.

#### Market Risk

**LIQUIDITY: Does the LSD have a liquid market that can facilitate liquidations in all foreseeable market events?**

rETH ranks thirds in the LSD category by marketcap with ~1.61b in TVL. Its liquidity is primarily on-chain across several DEXs (Balancer, Curve, PancakeSwap, and Uniswap). Of the liquidity venues, there is not a dominant DEX by trade volume, although Uniswap makes up a high portion of trade volume compared to its low TVL. The Curve rETH/ETH pool ($9.04m) and Balancer rETH/ETH pool ($80.87m) represent the main sources of liquidity backing rETH’s stability.

When comparing its liquidity to marketcap, ~4.4% of the total token supply is on exchange. stETH ranks somewhat lower at ~3%. According to the DeFiLlama Token Liquidity tool, a rETH>ETH trade of $38.22m would produce a 1% slippage compared to a $300m swap required from stETH>ETH. While stETH is substantially more liquid overall, rETH performs on par in terms of liquidity depth given its substantially lower TVL (rETH has 10.75% the amount of ETH staked compared to stETH).

**VOLATILITY: Has the LSD had any significant depeg event (post merge)?**

Post-merge, rETH has not experienced a negative depeg against ETH. In fact, post-merge from November '22 until March '23, rETH depegged to the upside, at some point trading at a over 2% premium to fair value.

Source: [Dune Analytics](https://dune.com/rp_community/lst-comparison)​

Since withdrawals were activated in mid-April, rETH has kept a strong peg to ETH and has no significant depeg to the downside. However, the withdrawal mechanism requires that users deposit fresh ETH into the system or node operators exit their minipools (or rewards are distributed) to make ETH available for withdrawals. It is conceivable that in some circumstances, there may not be enough ETH available to facilitate arbitrage during a severe market event.

#### Technology Risk

**SMART CONTRACTS: Does the analysis of the audits and development activity suggest any cause for concern?**

The Rocketpool protocol has gone through several audits:

*   ​[Consensys Audit](https://consensys.net/diligence/audits/2021/04/rocketpool/#rocketpool-cli---lax-data-validation-and-output-sanitation) released April 2021
*   ​[Sigma Prime Audit](https://rocketpool.net/files/sigma-prime-audit.pdf) released May 2021
*   ​[Trail Of Bits Audit](https://github.com/trailofbits/publications/blob/master/reviews/RocketPool.pdf) released September 9 2021
*   ​[Sigma Prime Audit](https://rocketpool.net/files/sigma-prime-fix-review.pdf) released November 2021
*   ​[Consensys Audit- Atlas (v1.2)](https://consensys.net/diligence/audits/2023/01/rocket-pool-atlas-v1.2/) released January 2023
    

The commit history is not sparse, it can be seen that regular updates are being made over the year. The [Atlas Update](https://docs.rocketpool.net/guides/atlas/whats-new.html) was deployed in April. The new contracts were audited, but have added additional functionality and there may be unfound bugs or unintended change in the behavior of the system.

**DEPENDENCIES: Does the analysis of dependencies (e.g. oracles) suggest any cause for concern?**

Due to limitations of the Ethereum network requiring an oracle to communicate state between the consensus and execution layer, Rocket Pool makes use of an oDAO composed of a whitelisted subset of node operators.

These oracles push updates about system balances that update the rETH:ETH exchange rate, vote on introducing contract upgrades, facilitate onboarding/offboarding validators, and are necessary to process rewards. The oDAO can add or remove members and currently stands at 18 members with a consensus of 10 required to execute actions.

There is a Chainlink price feed available for rETH/ETH that can be considered highly reliable.

#### Counterparty Risk

**CENTRALIZATION: Are there any significant centralization vectors that could rug users?**

There is a strong trust assumption in the honest and reliable behavior of the oDAO members. The oDAO performs a number of responsibilities that effectively custody user funds. The oDAO can choose to push any price or exchange rate update and can update system contracts, both of which could result in loss of user funds if the oDAO misbehaves.

The pDAO EOA guardian is also trusted to set sensible parameters for the system and to custody Treasury funds. There is a proposal in the research phase to transition to an on-chain DAO and deprecate the guardian role, but the timeline of the governance upgrade is unknown.

**LEGAL: Does the legal analysis of the protocol suggest any cause for concern?** Rocket Pool Pty Ltd is an Australian Private Company, officially registered on May 10, 2018, and since then, it has been maintaining active status with the Australian Business Register.

There is regulatory uncertainty in Australia concerning crypto staking or classified staking as a financial product or an auxiliary service to a financial product. The existence of a team-controlled guardian that can access treasury funds and set system parameters may pose a centralization argument by the competent authorities and put the project in a situation to be obliged to pursue VASP licensing. In the same line of thought the team may be vulnerable to enforcement actions in the future."

There are no enforcement actions presently or historically against Rocket Pool Pty Ltd. Rocket Pool Pty Ltd appears to be protected to a significant degree under the Terms of Service.

#### Risk Rating

*   We rank rETH **good in liquidity** because despite having a fraction of the TVL as stETH, it has comparable liquidity depth in relation to its marketcap. Liquidity is distributed across several DEXs, including AMMs supporting high liquidity density on Balancer and Curve.
*   We rank rETH **good in volatility** because since the merge, rETH has not depegged to the downside and has exhibited low volatility since the Shappella upgrade. The decentralized design may prevent adequate withdrawal liquidity in some market situations that could result in higher volatility.
*   We rank rETH **good in smart contract** because there have been multiple smart contract audits, including an audit for the most recent Atlas update. Since the update happened several months ago, the contracts cannot be considered mature, and there may be undiscovered issues.
*   We rank rETH **good in dependencies** because there is a reliable pricefeed available for rETH. The oDAO is a somewhat decentralized mechanism for updating rates and other processes between the consensus and execution layer, requiring 10 of 18 members to reach consensus.
*   We rank rETH **ok in decentralization** because in the current bootstrapping phase, a team-controlled EOA acts as the guardian on behalf of the DAO. It can set parameters and handle treasury funds. The oDAO is a multisig that has significant power in the system, including to update contracts.
*   We rank rETH **good in legal** because Rocket Pool has a legal entity (Rocket Pool Pty Ltd) that provides front end and technology service to support the system. They appear to cover their liabilities thoroughly in the Terms of Use and do not have any current or historical enforcement actions against them. However, due to the centralized guardian role, they may be exposed to legal liability in the future.
    

Our overall assessment is that rETH performs quite well all-around with the exception of some centralization concerns.

Compared to its DeFi competitors (stETH and frxETH), rETH provides good balance. It scores somewhat lower than Frax on the market risk side, but scores higher on legal and dependencies. We’ve scored is higher than stETH in volatility as it has not experienced problematic volatility events as has stETH. However, it doesn’t score as high as stETH on decentralization or liquidity.

Our opinion is that the strongest case to limit protocol exposure of rETH is the potentially problematic centralization vector posed by the team-controlled guardian and to a lesser extent, the 18-member oracle DAO. This exposes users to additional counterparty risk and possible legal issues in the future (although Rocket Pool’s legal history does appear to be very clean).

Otherwise, rETH represents a well-rounded LSD product from a risk perspective. It would make a suitable addition to the collateral basket with minority exposure after wstETH. Rocket Pool’s transition to on-chain governance should be monitored, at which point it may be appropriate to consider a more dominant rETH presence within the basket.

## Coinbase cbETH

Full report from Prisma Risk Team: [https://hackmd.io/@PrismaRisk/cbETH](https://hackmd.io/@PrismaRisk/cbETH) This section will summarize the findings of the report by highlighting the most significant risk factors in each of the three risk categories: Market Risk, Technology Risk, and Counterparty Risk.

#### 1\. Market Risk

_LIQUIDITY: Does the LSD have a liquid market that can facilitate liquidations in all foreseeable market events?_

cbETH ranks second in LSD marketshare after Lido stETH, but it is by a large margin. cbETH commands around 11% of the market compared to Lido’s 74.4%. While stETH has ~$600m liquidity across DEXs, cbETH has $44.16m pool TVL in DeFi with 9,501.45 cbETH. Over 97% of cbETH is on Coinbase.

The DefilLlama Liquidity Tool estimates a cbETH>ETH swap size of 9000 cbETH (worth ~$18.1m) would produce a 1% slippage. By comparison, a $300m stETH swap would produce a comparable figure. This ranks cbETH at around 6% of the on-chain liquidity depth of stETH.

cbETH may face greater liquidity challenges in the future. Its fees are the highest of the primary LSD competitors, resulting in consistently lower yields for users. Regulatory scrutiny has caused Coinbase to cease promotional activites or incentive programs to help drive cbETH adoption in DeFi.

_VOLATILITY: Has the LSD had any significant depeg event (post merge)?_

Following the Shapella upgrade along with some withdrawal demand, cbETH did experience some increased volatility that caused it to trade slightly below its fair value for a brief period. Overall, it has stabilized relative to ETH following the upgrade.

Arriving to the upgrade, Coinbase had [warned customers](https://www.coinbase.com/blog/ethereums-shapella-upgrade-is-coming-heres-what-you-need-to-know) that they “anticipate the Ethereum protocol will take weeks to months to process unstaking requests immediately following the upgrade.” Although withdrawal demand is quite low currently, falling yields or network issues may precipitate large withdrawal demand that cannot be immediately arbitraged.

One advantage of a centralized LSD service is the possibility Coinbase can expedite user withdrawals from the business’s cash flow, potentially averting a withdrawal bottleneck. However, section 1.7(j) of the [User Agreement](https://www.coinbase.com/legal/user_agreement/united_states) states “Coinbase will not backstop or otherwise intervene to guarantee cbETH liquidity”.

#### 2\. Technology Risk

_SMART CONTRACTS: Does the analysis of the audits and development activity suggest any cause for concern?_

Custody of the underlying ETH is managed by Coinbase internally, and therefore the smart contract security is significant only for accounting purposes.

The system Coinbase deployed was forked from Centre’s [FiatTokenV2\_1](https://github.com/centrehq/centre-tokens/blob/v2.1.0/contracts/v2/FiatTokenV2_1.sol), which is used with USDC and has significant SC maturity, having been on mainnet for multiple years. The additional contracts introduced with cbETH (ExchangeRateUpdater and MintForwarder) have been audited and have access controls centralized to Coinbase.

_DEPENDENCIES: Does the analysis of dependencies (e.g. oracles) suggest any cause for concern?_

Because cbETH operations are entirely centralized to Coinbase, the most significant risk to users is counterparty risk involving failure of the node operator, lost or stolen private keys, etc.

Withdrawal times are advertised as a minimum of 27 hours and Coinbase has warned users that in times of high network-wide withdrawal demand, processing times can be in the weeks to months.

Coinbase does have a reliable Chainlink pricefeed available for the cbETH/ETH pair.

#### 3\. Counterparty Risk

_CENTRALIZATION: Are there any significant centralization vectors that could rug users?_

Coinbase has complete centralized control over the cbETH system and user funds. While ownership of staked ETH remains with the user (as per the User Agreement), Coinbase discloses risks that could cause losses for users.

*   Staking involves the risk of slashing. In some cases, Coinbase will reimburse users, but not “if slashing was the result of a hack, your own actions, or a bug in the protocol itself” ([source](https://help.coinbase.com/en/coinbase/coinbase-staking/staking/staking-risks))
*   Cyberattacks and security breaches of the platform.
*   Theft, loss or destruction of private keys under Coinbase Custody.
*   Various economic and regulatory uncertainties could threaten Coinbase as a business, and therefore the continued operation of cbETH.
    

_LEGAL: Does the legal analysis of the protocol suggest any cause for concern?_

On June 6, 2023, the [SEC Charged Coinbase](https://www.sec.gov/news/press-release/2023-102) with operating as an Unregistered Securities Exchange, Broker and Clearing Agency. A complete list of allegations is in the [SEC Complaint](https://www.sec.gov/litigation/complaints/2023/comp-pr2023-102.pdf). Coinbase responded on June 28th with an [Answer to the Plaintiff’s Complaint](https://storage.courtlistener.com/recap/gov.uscourts.nysd.599908/gov.uscourts.nysd.599908.22.0.pdf) that outlines various defense strategies.

The enforcement actions and regulatory scrutiny generally have apparently caused Coinbase to exercise caution with promoting cbETH for fear it could be considered a securities offering. It is too early to know for sure how the enforcement action will play out, but in the short term it has dampened the growth of cbETH relative to competitors and there is some uncertainty about the future of the product offering.

#### 4\. Risk Rating

Based on the risks identified for each category, the following chart summarizes a risk rating for cbETH as collateral. The rating for each category is ranked from excellent, good, ok, and poor.

*   We rank cbETH **ok on liquidity** because although it ranks 2nd by LSD marketshare after stETH, >97% of liquidity is on Coinbase and an $18.1m on-chain swap produces a similar slippage as a $300m stETH swap.
*   We rank cbETH **good in volatility** because a centralized service provider should be capable of expedited withdrawal processing during times of high demand than a decentralized protocol. This would strengthen the LSB in certain circumstances. However, Coinbase does not claim to expedite withdrawal requests.
*   We rank cbETH **excellent in smart contracts** because the contract architecture is straightforward, managed by permissioned Coinbase addresses, based on battle-tested contracts, is audited, and the contracts themselves do not handle user funds.
*   We rank cbETH **good in dependencies** for having a reliable pricefeed available. A centralized service can be an advantage when managing system accounting, withdrawal processing, and unforeseen network issues (high withdrawal demand, Ethereum network issues, etc.)
*   We rank cbETH **ok in centralization** because it is a centralized service operated by Coinbase and users are thus exposed to counterparty risk. The User Agreement does offer assurances that users retain legal ownership of their staked ETH. Coinbase does make an effort to reduce centralization of its validators by diversifying across several software clients.
*   We rank wstETH **ok in legal** for recently receiving an enforcement action from the SEC alleging that Coinbase’s staking program constitutes a securities offering. See section 5.4.3 for details. Despite regulatory scrutiny, Coinbase has a long history striving for regulatory compliance and appears prepared with a solid legal basis to defend itself.
    

Compared with Lido stETH, we assess that cbETH is stronger in the categories Smart Contract and Volatility. It is weaker in the categories Liquidity, Centralization, and Legal.

There are potential advantages of a centralized LSD product within a diversified collateral basket, namely that the service provider can react more quickly during adverse circumstances, leading to less volatility and possibly greater user trust in the product.

Care should be taken to limit exposure to cbETH for the primary reasons:

*   1. liquidity is quite low despite cbETH having the second highest LSD marketshare and is highly concentrated on Coinbase.
*   2. A recent SEC enforcement action demonstrates a level of regulatory scrutiny that creates some uncertainty about the future of the cbETH product or, at the very least, Coinbase’s ability to remain competitive against competing LSD products.
    

Our assessment overall is that cbETH is a suitable collateral asset within a diverse basket of LSDs, but DAO voters are recommended to limit protocol exposure to cbETH by targeting a basket allocation composed primarily of wstETH. wstETH has a much stronger liquidity profile and achieves a level of decentralization that offers stronger user assurances. cbETH is a good contender with risk attributes making it quite complementary to wstETH, but due to weaknesses in its liquidity profile and legal situation, it should remain a minority member of the collateral basket at this time.

## Frax sfrxETH

Full report from Prisma Risk Team: [https://hackmd.io/@PrismaRisk/sfrxETH](https://hackmd.io/@PrismaRisk/sfrxETH) This section will summarize the findings of the report by highlighting the most significant risk factors in each of the three risk categories: Market Risk, Technology Risk, and Counterparty Risk.

#### 1\. Market Risk

_LIQUIDITY: Does the LSD have a liquid market that can facilitate liquidations in all foreseeable market events?_

frxETH can be considered not only an ETH liquid staking token but also a liquidity management protocol, thus setting it apart from its competitors. This gives Frax a unique advantage to grow and sustain its liquidity depth through its AMO activities in the Curve frxETH/ETH pool and other liquidity venues.

Although the total frxETH marketshare is fairly low (2.31%), its available on-chain liquidity makes up a large proportion of its marketcap. Whereas stETH has ~$425m on-chain liquidity on $14.39b in TVL (3% of TVL), Frax has ~$75m on-chain liquidity on $448m TVL (>16% of TVL). Despite frxETH having 5% of the TVL compared to stETH, it has 25% the liquidity depth (a $50m frxETH>ETH swap produces 1% slippage compared to $300m stETH>ETH swap).

Available liquidity is dependent on Frax’s ability to incentivize its frxETH pools, but the protocol model is highly focused on ensuring deep liquidity.

_VOLATILITY: Has the LSD had any significant depeg event (post merge)?_

As with frxETH liquidity, the Frax liquidity management focus has kept frxETH remarkably on peg, especially compared to competitors such as stETH and cbETH. Users should be aware that price stability comes as a cost of trusting the Frax team to responsibly manage liquidity.

As a recent example, the Curve pool became somewhat imbalanced in mid-June. In response, the frxETH Treasury increased the ETH withheld on frxETH deposits to 70%. This allowed the treasury to divert user deposits toward balancing the pool. It is possible that redemption demand becomes excessive enough that Frax must exit validators to balance the pool. This process can be time consuming, especially if network-wide withdrawal demand is high. The responsibility of maintaining price stability is therefore the burden of the frxETH treasury and Frax team as operators of the frxETH validators, and it is possible that poor management could result in increased volatility.

#### 2\. Technology Risk

_SMART CONTRACTS: Does the analysis of the audits and development activity suggest any cause for concern?_

There has only been one audit of frxETH and sfrxETH by [code4rena](https://code4rena.com/reports/2022-09-frax) on 29th of November, 2022 (contest taking place from 22nd to 25th September). The frxETH code heavily borrows from Frax and FPI stablecoins. Both of these are battle tested and have gone through extensive audits.

_DEPENDENCIES: Does the analysis of dependencies (e.g. oracles) suggest any cause for concern?_

There is no Chainlink pricefeed available for frxETH at this time, although the Frax team has said they are working to introduce one. For now, the two pricefeed options are a UniswapV3 frxETH/FRAX TWAP oracle and a Curve frxETH/ETH EMA oracle. Curve is currently recommending third parties to not integrate the EMA oracle, as it can be manipulable over multiple blocks, especially in low-volume pools. Curve is working to move to a new pool implementation that ameliorates this concern.

For now, there is not a pricefeed solution that can be considered highly reliable, although there appear to be active efforts to rectify this.

#### 3\. Counterparty Risk

_CENTRALIZATION: Are there any significant centralization vectors that could rug users?_

The 3-of-5 frxETH Treasury multisig is responsible for protocol operations and funds management. All user funds are managed by this multisig and by ETH staking validators operated by the Frax team. The total value managed by the Frax team (which can potentially be rugged) is currently [$437m](https://debank.com/profile/0x8306300ffd616049FD7e4b0354a64Da835c1A81C).

While Frax has expressed an intention to upgrade funds management to an on-chain DAO governed by veFXS tokenholders, including having open sourced code for the upgrade, they have so far not begun the governance upgrade process. It is unknown when the upgrade will take place. Llama Risk began covering Frax in 12/21, and at that time the upgrade was planned for Q2 '22. The roadmap for the upgrade has since been delayed at least a year.

Frax has also announced plans for a frxETH v2 that would behave as a collateralized lending market that diversifies the frxETH node operator set. The timeline for this upgrade is unknown.

_LEGAL: Does the legal analysis of the protocol suggest any cause for concern?_

Frax operates as a DAO with no legal entity. It is possible a DAO could be considered an “unincorporated general partnership” with uncertain consequences. In the most extreme case, a member of the DAO could be held liable for all the debts and legal issues faced by the DAO.

Frax has not had any enforcement actions against it, although due to factors such as the centralization of operations and funds management along with questionable sanctions compliance, Frax may be exposed to regulatory risk.

Individuals who are creators, owners, operators, or others who maintain control or wield substantial influence over the Frax protocol may fall under the FATF’s definition of a VASP (“Virtual Asset Service Provider”) and would be required to comply with regulatory guidelines.

Frax does not appear to track addresses for sanctions compliance, nor does its terms of use include explicit restrictions of access to its services by sanctioned persons or residents of sanctioned countries. While this may not necessarily indicate a lack of compliance, the absence of such clauses might create ambiguity and potential enforcement risk.

#### 4\. Risk Rating

Based on the risks identified for each category, the following chart summarizes a risk rating for wstETH as collateral. The rating for each category is ranked from excellent, good, ok, and poor.

*   We rank sfrxETH as **excellent on liquidity** because relative to its marketcap, frxETH has very deep market depth that provides strong assurances of liquidity in nearly all foreseeable market circumstances.
*   We rank sfrxETH as **excellent on volatility** because Frax places a strong emphasis on maintaining price stability through its Curve pool integration that creates a stronger assurance than competitors.
*   We rank sfrxETH as **good on smart contract** because it has undergone one audit but contracts have only been on mainnet since October '22 and therefore are still somewhat immature.
*   We rank sfrxETH as **ok on dependencies** because there is no highly reliable price feed available currently. However, Frax is actively working on a Chainlink feed and Curve is actively working to improve its EMA oracle.
*   We rank sfrxETH as **ok on decentralization** because there is a significant trust assumption in the Frax team to responsibly and honestly manage ~$437m worth of user funds. The team has a roadmap to decentralize, although they have a history of postponing decentralization efforts.
*   We rank sfrxETH as **ok on legal** because it is susceptible to enforcement action due to centralization of core managing functions in the hands of a few team members, and yet it has not formed any legal entity or implemented any sanctions compliance measures.
    

Our overall assessment is that sfrxETH performs well on market risk factors (liquidity and volatility) and poor on counterparty risk factors (decentralization and legal) relative to competitors wstETH and cbETH. We scored sfrxETH lower on dependencies because it does not have a highly reliable pricefeed at this time, although this is likely a problem that will be resolved in the near term.

The clear advantage of sfrxETH is the focus Frax places on ensuring deep liquidity through its liquidity management operations. This should allow it to immediately process withdrawal demand in most market scenarios through the managed Curve pool, and otherwise provide users with an assurance that Frax will restore the balance in uncommon situations involving significant liquidations and/or withdrawal demand.

Care should be taken to limit exposure to sfrxETH for the primary reasons:

*   There is no highly reliable pricefeed for frxETH at this time.
*   There is significant counterparty risk due to a high level of centralization in frxETH contract operations, validator operations, and funds management.

Both of the primary concerns are points that the Frax team has publicly stated they are working to resolve, including announcements of a [frxETH v2](https://medium.com/coinmonks/introducing-frxeth-v2-the-evolution-of-decentralized-lending-markets-and-stablecoins-142b52b5f81e) involving a decentralized node operator set and open sourcing the [GitHub repo](https://github.com/FraxFinance/frax-governance) for decentralized governance. Assuming both upgrades are successful, sfrxETH may become the most desirable LSD from a risk perspective. Until then, there is substantial counterparty risk and it is recommended to limit protocol exposure to sfrxETH as a collateral asset.

## Binance WBETH

Full report from Prisma Risk Team: [https://hackmd.io/@PrismaRisk/WBETH](https://hackmd.io/@PrismaRisk/WBETH) This section will summarize the findings of the report by highlighting the most significant risk factors in each of the three risk categories: Market Risk, Technology Risk, and Counterparty Risk.

#### 1\. Market Risk

_LIQUIDITY: Does the LSD have a liquid market that can facilitate liquidations in all foreseeable market events?_

WBETH ranks sixth in the LSD market, making up .72% of the market share. While WBETH has liquidity in multiple pools and platforms, the analysis highlights potential challenges in terms of liquidity depth, utilization, and slippage.

As of July 8th, 2023, Ethereum on-chain liquidity for WBETH is only present on Curve ($3.1M TVL), Balancer ($4.5M TVL), and PancakeSwap ($2.6M TVL) with the majority of WBETH on Binance. This is orders of magnitude less than its main competitors stETH (~$600M on-chain TVL) and cbETH (~$40M on-chain TVL).

The DefiLlama token liquidity tool estimates a swap size of $3.25M would produce a 1% slippage. This is a very low figure compared to competitors. stETH would require a ~$300m swap and cbETH an ~$18m swap to produce similar slippage.

_VOLATILITY: Has the LSD had any significant depeg event (post merge)?_

As indicated by the daily LSB, BETH has generally traded at a discount relative to ETH before staking withdrawals were enabled. The maximum price difference was at a maximum around -5%, although over time the magnitude of the discount has decreased. No significant price depeg can be observed for BETH post-merge.

A unique feature of Binance’s LSD is the Binance-managed withdrawal pool that helps ensure a stable supply of exit liquidity. This may be advantageous to Binance during times of high withdrawal demand and may be a stronger assurance to support the WBETH peg than is offered by competitors.

Binance does have a 5 day withdrawal processing time, and in addition to not guaranteeing exit liquidity during times of high withdrawal demand, they may change the processing time without notice.

#### 2\. Technology Risk

_SMART CONTRACTS: Does the analysis of the audits and development activity suggest any cause for concern?_

There are no published audits specifically for the BETH or WBETH contracts. However, Binance has an internal auditing team, and the contracts may have been audited internally. While Binance’s security and compliance team has been expanded and the company has a bug bounty program, the lack of specific audits for BETH and WBETH raises some concerns about the transparency and external verification of the contract’s security. Additionally, the closed-source nature of the Github repository specifically for WBETH and BETH limits the ability to assess the code and development activity.

_DEPENDENCIES: Does the analysis of dependencies (e.g. oracles) suggest any cause for concern?_

The WBETH contract relies on a centralized oracle system to update the WBETH:ETH exchange rate based on staking rewards earned by Binance validators. This operation is controlled by a Binance-approved address. This introduces a potential concern regarding the reliance on a centralized entity for updating the exchange rate between BETH and WBETH. Because minting WBETH from ETH is a permissionless function, unauthorized access or vulnerabilities in the ExchangeRateUpdater contract could lead to manipulation of the exchange rate and potential financial losses or market disruption.

WBETH does not have a reliable pricefeed oracle on Ethereum which may be a blocking factor from introducing WBETH as collateral. Both Chainlink and Binance Oracle have a pricefeed on Binance Chain, but do not support Ethereum at this time. WBETH DEX pools have low liquidity and untested pricefeed oracles that cannot be considered reliable sources.

#### 3\. Counterparty Risk

_CENTRALIZATION: Are there any significant centralization vectors that could rug users?_

Binance has full control over the governance of the service. Additionally, Binance acts as the sole node operator for the staking service, handling a large number of validators. This high level of centralization increases the risk of manipulation and control by a single entity, which could potentially be harmful to users.

Binance articulates the user’s agreement when using Binance staking services in the [Binance ETH Staking Terms and Conditions](https://www.binance.com/en/terms-ETH-2-0-staking) and general agreements in the [Terms of Use](https://www.binance.com/en/terms).

_LEGAL: Does the legal analysis of the protocol suggest any cause for concern?_

The legal analysis of the Binance ETH Staking Service protocol suggests some cause for concern. The Terms and Conditions require users to consent to Binance or a Binance Operator staking their assets, acting as a validator, and delegating voting rights attached to the assets. The lack of clear designation of the governing law and the legal entities responsible for providing the service could lead to ambiguity and uncertainty in legal disputes. It may also make it difficult for users to identify the applicable jurisdiction and understand their legal exposure.

Moreover, the complex corporate structure and undisclosed ownership of Binance raise regulatory and compliance issues, as highlighted by the recent enforcement actions by the CFTC and complaint by the SEC. Although Binance specifically restricts U.S. citizens from using the binance.com exchange, U.S. regulators are placing a high level of scrutiny on Binance’s operations.

#### 4\. Risk Rating

Based on the risks identified for each category, the following chart summarizes a risk rating for WBETH as collateral. The rating for each category is ranked from excellent, good, ok, and poor.

*   We rank WBETH **poor on liquidity** because of limited DeFi integrations resulting in poor on-chain liquidity. Most WBETH liquidity is on Binance and only 3,037 WBETH is in Ethereum liquidity pools as of July 8th.
*   We rank WBETH **good in volatility** because Binance manages a withdrawal pool that helps ensure ample exit liquidity which may strengthen its peg assurance compared with competitors.
*   We rank WBETH **ok in smart contract** because WBETH is mostly forked from cbETH which has been audited and have somewhat mature contracts on mainnet. However, Binance has not released any audit report of their additions to the contracts or open sourced their development activity.
*   We rank WBETH **poor in dependencies** because there is no reliable pricefeed oracle available on Ethereum for WBETH at this time which may be a blocker for integration into lending platforms.
*   We rank WBETH **poor in decentralization** because not only is WBETH completely centralized to Binance, the ownership structure and official jurisdiction of Binance have remained elusive, raising suspicion that Binance intentionally obscures this information to circumvent scrutiny and regulation.
*   We rank WBETH **poor in legal** because of enforcement actions, complaints, and investigations from multiple agencies in multiple jurisdictions that may threaten Binance’s ability to continue supporting WBETH in the future. Agencies include the CFTC, SEC, the U.S. DOJ, and the French AMF.

We assess that WBETH is riskier in all categories except volatility compared with both stETH and cbETH.

There are potential advantages of a centralized LSD product within a diversified collateral basket, namely that the service provider can react more quickly during adverse circumstances, leading to less volatility and possibly greater user trust in the product.

Care should be taken to limit WBETH exposure for the primary reasons:

*   1. There is no reliable pricefeed for WBETH/BETH on Ethereum. It is possible that WBETH loses its peg to ETH which may result in the accrual of bad debt to a lending platform that lacks a reliable pricefeed.
*   2. WBETH is the least liquid LSD of the initial proposed Prisma basket (wstETH, cbETH, sfrxETH, rETH, and WBETH). It has poor DeFi integration and, as a result, the vast majority of BETH/WBETH liquidity is on Binance.
    

Compared with other LSDs being considered for onboarding, WBETH offers no real advantage from a risk perspective. Its most analogous competitor, Coinbase cbETH, scores higher in almost every category. Whereas the risk profile of cbETH may balance certain deficiencies observed in stETH, WBETH does not adequately balance the risk profile of a diversified basket.
