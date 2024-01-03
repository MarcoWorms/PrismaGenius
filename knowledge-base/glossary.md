# Glossary

*   **Vault Collateral Ratio:** The collateral ratio is the ratio between the US Dollar value of the collateral in an vault and its debt in `mkUSD`.
    

*   **Emission Boost**: By locking PRISMA rewards, users have the opportunity to boost (i.e., increase) the rewards they receive while participating in eligible liquidity pools. The amount of boost depends on how much PRISMA they have locked and their proportional stake in the pool. In other words, the more PRISMA they lock and the larger their stake in the pool, the higher the boost to their rewards.
    

*   **Loan-to-Value (LTV)**: The Loan-to-Value ratio defines the maximum amount of `mkUSD` that can be minted with a specific collateral. It is expressed as a percentage (e.g., at LTV=80%, for every 1 ETH worth of collateral, minters will be able to mint 0.80 ETH worth of `mkUSD`). Once a mint occurs, the LTV changes with market conditions.
    

*   **Liquidation Penalty**: The liquidation penalty is a fee rendered on the price of assets of the collateral when liquidators purchase it as part of the liquidation of a loan that has passed the liquidation threshold.
    

*   **Liquidation Price**: The liquidation price of an vault is the price at which the position becomes subject to liquidation. During Normal Mode this happens when the collateral value drops below the Minimum Collateral Ratio (MCR) of `120%`. During Recovery Mode this is calculated based on a Collateral Ratio of `150%.`
    

*   **Liquidity**: Liquidity based on on-chain liquidity and trading volume, is key for the liquidation process. These can be mitigated through the caps and liquidation parameters (i.e., the lower the liquidity, the higher the incentives).
    

*   **Locking** Locking refers to the process of locking PRISMA tokens in order to participate in gauge weight or governance votes and claim protocol rewards.
    

*   **Market Capitalization**: Market cap—or market capitalization—refers to the total value of all a protocols tokens.
    
    *   It is an important measure of a market's size, particularly in the context of using assets as collateral. When dealing with assets with smaller market capitalizations, the risk is somewhat limited, but these assets tend to be more prone to price fluctuations as they are generally still in their early stages of development. On the other hand, a higher market capitalization typically indicates a more established market ecosystem with greater trading activity, making it easier to liquidate assets without significantly affecting their prices.
        
    
    *   Both the Market Capitalization and the Liquidity are crucial for assessing and managing the risks associated with liquidation.
        
    

*   **Minimum Collateral Ratio (MCR)**: The minimum collateral ratio (MCR) is the lowest ratio of debt to collateral that will not trigger a liquidation under normal operations (aka Normal Mode). This is a protocol parameter that is set to `120%`.
    

*   **Recovery Mode:** Recovery Mode is activated when the Global Total Collateral Ratio (**GTCR**) of the system dips below `150%`. In this state, any vault with a collateral ratio less than the GTCR is subject to liquidation.
    

*   **Redemption:** refers to the act of exchanging `mkUSD` for the underlying collateral
    

*   **Stability Pool:** The Stability Pool is the primary safeguard to ensure the solvency of the system, by providing the required liquidity to cover debts from liquidated vaults, thus ensuring that the total `mkUSD` supply always remains adequately collateralized.
    

*   **Volatility**: Price volatility can negatively affect the collateral which must cover liabilities and safeguards the solvency of the protocol. The risk of the collateral falling below the borrowed amounts can be mitigated through the level of coverage required through the LTV. It also affects the liquidation process as the margin for liquidators needs to allow for profit.
    

