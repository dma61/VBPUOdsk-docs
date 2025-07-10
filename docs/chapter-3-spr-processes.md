# Chapter 3: Processes & Information Flows – Solidarity Premium Scheme (SPR)

            ## 3.1 Introduction
            This section describes the necessary information exchange for the solidarity premium scheme (SPR).

            ## 3.2 SPR Information Flows
            The information flow from the Pension Administration Organization (PUO) to the fiduciary/investment administrator (stream 1) consists of three messages:
            *   **Message 1. Assets (1a)**: Periodically provides total pension assets (`startAmount`) per scheme and optionally per cohort. Can also specify desired portfolio allocation.
            *   **Message 2. Cashflow (1b)**: Provides inflow, outflow, or net cash flow per scheme and cohort. Can be used prospectively (liquidity) or retrospectively (analysis).
            *   **Message 3. Pension Projection (1c)**: Provides projected benefits per cohort for future periods, which is crucial for managing the protection portfolio. Includes the `hedgedExpectedPensionPaymentAmount` for cash flows to be hedged.

            The information flow to the PUO consists of:
            *   **Message 4. Return Information (2)**: The PUO receives start/end values and the return percentage per portfolio to allocate returns to participants.

---
<div style='display: flex; justify-content: space-between;'><div>[< Previous: Chapter 2: Principles](chapter-2-principles.md)</div><div>[Next: Chapter 4: FPR Processes>](chapter-4-fpr-processes.md)</div></div>