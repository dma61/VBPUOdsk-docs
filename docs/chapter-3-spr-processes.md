# Chapter 3: Processes & Information Flows – Solidarity Premium Scheme (SPR)

## 3.1 Introduction
This section describes the necessary information exchange for the solidarity premium scheme (SPR). The investment administrator provides information to the pension administration organization (PUO) independently of the fiduciary manager.

## 3.2 SPR Information Flows
The PUO is responsible for allocating returns, while the fiduciary manager handles the investment policy.

The information flow from the PUO to the fiduciary (stream 1) consists of three messages:
*   **Message 1. Assets (1a)**: On a periodic basis, the fiduciary manager receives the total pension assets (`startAmount`) per scheme and optionally per cohort. This allows for checking alignment with the fund's policy. The message can also specify the desired allocation to different portfolios.
*   **Message 2. Cashflow (1b)**: This message provides the inflow (`contributionAmount`) and outflow (`withdrawalAmount`) or the net cash flow (`netAmount`) per scheme and cohort. This can be used prospectively for liquidity management or retrospectively for analysis.
*   **Message 3. Pension Projection (1c)**: Provides the projected benefits (`amount`) per cohort for future periods, which is crucial for managing the protection portfolio. The message also includes the `hedgedExpectedPensionPaymentAmount`, representing the cash flows to be hedged.

The information flow to the PUO consists of:
*   **Message 4. Return Information (2)**: The PUO receives the start and end values and the return percentage for the period, per portfolio. This information is crucial for allocating returns to participants.


---
[< Previous: Chapter 2: Principles](chapter-2-principles.md)     [Next: Chapter 4: FPR Processes>](chapter-4-fpr-processes.md)