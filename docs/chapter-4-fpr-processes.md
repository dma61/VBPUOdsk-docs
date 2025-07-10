# Chapter 4: Processes & Information Flows – Flexible Premium Scheme (FPR)

## 4.1 Introduction
This chapter describes the information exchange for the Flexible Premium Scheme (FPR), distinguishing between a direct order model and a more extensive, layered order model.

## 4.2 Model 1: Simpler, Direct Order Model
In this model, investments consist of directly tradable funds. The PUO translates participant-level mutations into aggregated orders. A **cohort pool** is a group of participants with the same investment allocation.

## 4.3 Model 2: More Extensive, Layered Order Model
This model accommodates less liquid assets. It has a layered structure: participants invest in **cohort pools**, which in turn invest in **investment pools**. This structure uses units for robust and traceable allocation.

## 4.4 Information Flows FPR - Model 1
This model involves direct orders from the PUO to brokers or transfer agents.
*   **Message 5. Order Instruction (00541)**: The PUO sends an order instruction to execute a trade.
*   **Message 6. Order Confirmation (00542)**: The executing party sends back a confirmation.

## 4.5 Information Flows FPR - Model 2
This model has a more complex, multi-step process flow. The core idea is that the PUO provides mutation data, which the pool administrator uses to calculate necessary transactions, which are then instructed to the fiduciary manager. The key messages in this flow are:
*   **Message 7 (00551)**: PUO sends aggregated mutations per cohort pool.
*   **Messages 8 & 9 (00552a/b)**: Used to reconcile positions between the various administrators.
*   **Message 10 (00553)**: The pool administrator instructs the fiduciary manager on required cash transactions.
*   **Message 11 (00554)**: The pool administrator sends month-end rebalancing transactions.
*   **Messages 12 & 13 (00555a/b)**: The final unit/participation values are calculated and distributed.
*   **Message 14 (00556)**: The pool administrator sends payment instructions for withdrawals.

## 4.6 Feedback Message (& Resending)
The feedback message is essential for the sender to know if a message was processed correctly (status: Accepted or Rejected). The process for corrections is strict: **"Once accepted messages are not unilaterally corrected."**


---
<div style='display: flex; justify-content: space-between;'><div>[< Previous: Chapter 3: SPR Processes](chapter-3-spr-processes.md)</div><div>[Next: Chapter 5: Data Standard Setup>](chapter-5-data-standard-setup.md)</div></div>