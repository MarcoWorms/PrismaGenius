# Recovery Mode

### Introduction

Recovery Mode is activated when the Global Total Collateral Ratio (**GTCR**) of the system dips below `150%`. In this state, any vault with a collateral ratio less than the GTCR is subject to liquidation.

Further, the system puts a halt to any borrower transactions that could potentially exacerbate the decrease in GTCR. The only way new `mkUSD` can be generated during this period is by either improving the collateral ratio of existing vaults or by establishing a new vault with a collateral ratio that is greater than or equal to `150%`.

Generally, if an adjustment to an existing vault leads to a decrease in its collateral ratio, the transaction will only go through if the resultant GTCR remains above `150%`.

### Definition of GTCR

The Global Total Collateral Ratio, or GTCR, refers to the proportion of the total value of all collaterals within the protocol, evaluated at their present prices, to the total outstanding debt across the protocol.

Put differently, it's the collective value of all vaults' collateral measured in USD, divided by the cumulative debt of all vaults, denominated in `mkUSD`.

### Rationale for the Recovery Mode

The primary objective of Recovery Mode is to encourage actions that rapidly increase the global Total Collateral Ratio (GTCR) to over `150%`, and to motivate `mkUSD` holders to refill the Stability Pool. From an economic perspective, Recovery Mode is structured to promote additional collateral deposits and debt repayments.

Moreover, the very prospect of entering Recovery Mode serves as a preventive measure, steering the system away from ever entering this state. It's important to note that Recovery Mode is not an optimal state for the system to operate in.

### Impact on fees

During Recovery Mode, while the redemption fee remains unaffected, the Minting fee is reduced to 0% to stimulate borrowing activities that positively impact the GTCR.

### Impact on liquidations

While in Recovery Mode, if your vault’s Individual Collateral Ratio **(ICR)** falls below the GTCR, your vault can be liquidated (even if your vault's collateral ratio is above `120%`). To prevent this from happening, in both Normal and Recovery Mode, a user should maintain their collateral ratio over `150%.`

During Recovery Mode, the liquidation loss is capped at `120%` of a vault's collateral. Any residual amount, i.e. the collateral above `120%` (and below the Global Total Collateral Ratio or GTCR), can be recouped by the borrower who faced liquidation by claiming the surplus collateral.

This implies that a borrower will encounter the same liquidation "penalty" (`20%`) in Recovery Mode as they would in Normal Mode if their vault undergoes liquidation.
