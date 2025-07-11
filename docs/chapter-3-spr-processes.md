# Chapter 3: Processes & Information Flows – Solidarity Premium Scheme (SPR)

## 3.1 Introduction
This section describes the necessary information exchange for the robust implementation of the solidarity premium scheme (SPR). Figure 1 schematically illustrates the flows between the Pension Administration Organization (PUO), Investment Manager, and Investment Administrator.

## 3.2 SPR Information Flows
The roles of the parties are as follows: The PUO is responsible for allocating returns to participants. The fiduciary manager supports and executes the investment policy. The investment administrator provides independent administration and calculates total returns.

The information flow from the PUO to the fiduciary/investment administrator (stream 1) consists of three messages:
*   **Message 1. Assets (1a)**: On a periodic (e.g., monthly) basis, the fiduciary manager receives the total pension assets (`startAmount`) per scheme and, optionally, per cohort. This allows for checking alignment with the fund's policy and rebalancing if necessary. The message can also specify the desired allocation to different portfolios (`startExposureAmount`, `startExposurePercentage`).
*   **Message 2. Cashflow (1b)**: This message provides the inflow (`contributionAmount`) and outflow (`withdrawalAmount`) or the net cash flow (`netAmount`) per scheme and cohort. This includes premiums, value transfers, benefits, and shifts between cohorts. It can be used prospectively for liquidity management or retrospectively for analysis and reporting.
*   **Message 3. Pension Projection (1c)**: Provides the projected benefits (`amount` for `expectedPensionPayment`) per cohort for future periods. This is crucial for managing the protection portfolio. The message also includes the `hedgedExpectedPensionPaymentAmount`, which represents the cash flows to be hedged, calculated based on the protection percentage per cohort.

The information flow from the investment administrator to the PUO (stream 2) consists of:
*   **Message 4. Return Information (2)**: The PUO receives the start and end values (`startAmount`, `endAmount`) and the return (`returnPercentage`) for the period, per portfolio. This information is crucial for allocating returns to participants. Depending on whether the scheme uses direct (actual) or indirect (theoretical) protection returns, the message will contain either the total return or a breakdown by protection and excess return portfolios.


---
<div style='display: flex; justify-content: space-between;'><div>[< Previous: Chapter 2: Principles](chapter-2-principles.md)</div><div>[Next: Chapter 4: FPR Processes>](chapter-4-fpr-processes.md)</div></div>