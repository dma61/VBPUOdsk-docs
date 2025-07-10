# Chapter 4: Processes & Information Flows – Flexible Premium Scheme (FPR)

            ## 4.1 Introduction
            This chapter describes information exchange for the Flexible Premium Scheme (FPR), distinguishing between a direct order model and a layered order model.

            ## 4.2 Model 1: Simpler, Direct Order Model
            Investments consist of directly tradable funds. The PUO aggregates participant mutations into orders. A **cohort pool** groups participants with the same investment mix.

            ## 4.3 Model 2: More Extensive, Layered Order Model
            This model accommodates less liquid assets. Participants invest in **cohort pools**, which in turn invest in **investment pools**. This layered structure uses units for robust allocation.

            ## 4.4 Information Flows FPR - Model 1
            This model involves direct orders from the PUO.
            *   **Message 5. Order Instruction (00541)**: PUO sends an order to execute a trade.
            *   **Message 6. Order Confirmation (00542)**: The executing party sends a confirmation.

            ## 4.5 Information Flows FPR - Model 2
            This model uses a more complex, multi-step process. Key messages include:
            *   **Message 7 (00551)**: PUO sends mutations to the pool administrator.
            *   **Messages 8 & 9 (00552a/b)**: Reconcile positions.
            *   **Message 10 (00553)**: Administrator instructs fiduciary on cash transactions.
            *   **Message 11 (00554)**: Administrator sends rebalancing transactions.
            *   **Messages 12 & 13 (00555a/b)**: Final unit values are distributed.
            *   **Message 14 (00556)**: Administrator sends payment instructions for withdrawals.

            ## 4.6 Feedback Message (& Resending)
            The feedback message provides status on message processing (Accepted/Rejected). Corrections are handled strictly: **"Once accepted messages are not unilaterally corrected."**

---
<div style='display: flex; justify-content: space-between;'><div>[< Previous: Chapter 3: SPR Processes](chapter-3-spr-processes.md)</div><div>[Next: Chapter 5: Data Standard Setup>](chapter-5-data-standard-setup.md)</div></div>