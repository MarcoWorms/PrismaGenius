## Risk Parameters

Each asset within the Prisma Protocol has specific values related to their risk, which influences how they are supplied and how mkUSD is minted within the protocol. It is crucial for the Prisma community to understand the underlying risk of each asset: assess the smart contract security, understand the risks of centralization and market risks. Onboarded assets, onboard their risk to the Prisma protocol. Prisma sets out to safely onboard collateral with risk mitigation parameters.

### Risk Parameters Analysis

The risk parameters mitigate the market risks of the collateral supported by the Prisma protocol. Each mkUSD that is minted is based on over-collateralization with one of the listed collaterals on Prisma as backing. Sufficient margin and incentives are needed for the position to remain collateralized in the event of adverse market conditions. If the value of the collateral falls below a predetermined threshold, the vault will be auctioned off to repay the debt position.

Market risks can be mitigated through Prisma's risk parameters, which define collateralization and liquidation rules. These parameters are calibrated on a per asset basis to account for the specific risks identified.

#### Supply Caps

Supply caps define the maximum amount of an asset that can be supplied to the protocol. Supply caps can be used to limit the protocol's exposure to riskier assets. A supply cap is an optional parameter, and the value will depend on on-chain liquidity of the asset and total volume of collateral assets in the pool.

​