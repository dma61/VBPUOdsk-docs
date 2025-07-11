# Chapter 4: Processes & Information Flows – Flexible Premium Scheme (FPR)

## 4.1 Introduction
This chapter describes the necessary information exchange for the Flexible Premium Scheme (FPR). Two main models for ordering investments are distinguished:
1.  **Model 1:** A simpler, direct order model.
2.  **Model 2:** A more extensive, layered order model.

## 4.2 Model 1: Simpler, Direct Order Model
In this model, investments consist of directly tradable funds (e.g., via platforms like AllFunds). The PUO translates participant-level mutations into aggregated orders for these funds. The fiduciary manager typically supports the design of the lifecycles. A **cohort pool** is an administrative grouping of participants with the same investment allocation, often based on age, status (active, deferred), and risk profile. Rebalancing occurs based on age (moving to a new cohort) or due to market movements causing deviations from target weights.

## 4.3 Model 2: More Extensive, Layered Order Model
This model accommodates less liquid or non-platform-tradable assets and mandates. It has a layered structure: participants invest in **cohort pools**, which in turn invest in **investment pools** (e.g., equities, fixed income). These investment pools hold the underlying assets. This structure allows for robust and traceable allocation, as units are issued for each pool. The process involves multiple roles that can be combined or separated: the PUO, a pool administrator, the fiduciary manager, and the investment administrator/custodian.

## 4.4 Information Flows FPR - Model 1
This model involves direct orders from the PUO to brokers, transfer agents, or order desks.
*   **Message 5. Order Instruction (00541)**: The PUO sends an order instruction with the minimal required data to execute a trade or switch in a specific investment fund.
*   **Message 6. Order Confirmation (00542)**: The executing party sends back a confirmation of the executed order.

## 4.5 Information Flows FPR - Model 2
This model has a more complex, multi-step process flow. The core idea is that the PUO provides mutation data, which the pool administrator uses to calculate necessary transactions. These are instructed to the fiduciary manager, executed, and reconciled, leading to new unit values.
The key messages in this flow are:
*   **Message 7. Balance Adjustments (00551)**: PUO sends aggregated mutations (purchases, sales, switches) per cohort pool to the pool administrator.
*   **Message 8. Reconciliation Information (00552a)** & **9. PUO Reconciliation Information (00552b)**: Used to reconcile positions between the pool administrator, fiduciary manager, and the investment administrator. Message 9 is for the variant where the PUO acts as the cohort pool administrator.
*   **Message 10. Control Information Investment Pools (00553)**: The pool administrator calculates the required cash transactions per investment pool and instructs the fiduciary manager.
*   **Message 11. Rebalancing Information (00554)**: The pool administrator sends month-end rebalancing transactions to the fiduciary manager.
*   **Message 12. Value Information Cohort Pool (00555a)** & **13. Value Information Investment Pool (00555b)**: The final unit/participation values are calculated and distributed back to the PUO and fiduciary manager.
*   **Message 14. Payment Information (00556)**: The pool administrator sends payment instructions for withdrawals to the fiduciary manager.

## 4.6 Feedback Message (& Resending)
It is essential for the sender to know if a message was received and processed correctly. The feedback message is used for both asynchronous and synchronous processing to provide status (Accepted/Rejected) and detailed error information.
The process for corrections is strict: **"Once accepted messages are not unilaterally corrected."** If a correction is needed after acceptance, the sender must contact the receiver to agree on the procedure.


---
<div style='display: flex; justify-content: space-between;'><div>[< Previous: Chapter 3: SPR Processes](chapter-3-spr-processes.md)</div><div>[Next: Chapter 5: Data Standard Setup>](chapter-5-data-standard-setup.md)</div></div>