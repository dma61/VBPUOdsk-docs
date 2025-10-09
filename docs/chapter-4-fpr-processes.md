# Chapter 4: Processes & Information Flows – Flexible Premium Scheme (FPR) & Feedback message (SPR and FPR)

## 4.1 Introduction
This chapter describes the information exchange for the Flexible Premium Scheme (FPR), distinguishing between a direct order model and a more extensive, layered order model.

## 4.2 Model 1: Simpler, Direct Order Model
<u>Figure 2, showing a schematic of the direct order model, can be found in the official Dutch manual.</u>

In this model, the pension administration organization translates mutations at the participant level into the necessary (netted) transactions in the investment funds of operational asset managers and has them executed via a trading platform. Such a setup can also be implemented jointly with the asset service provider/custodian, where the pension administration organization translates participant-level mutations into netted mutations, and the asset service provider/custodian handles the execution of transactions in investment funds via a trading platform (see Figure 6 - Model 1b in the original manual). When compiling the orders, aspects such as the minimum order size per investment product, the settlement cycle, and the associated financial flows are taken into account.

In the direct order model, the pension administrator is generally supported by the fiduciary manager with regard to the design of the lifecycle(s) and their composition (selection and monitoring of underlying investments). Special attention should be paid to the process of changing the composition of the investments (replacement of investment funds). Such changes result in transition activities for the pension administrator and/or asset service provider/custodian. More specifically, if an investment product (which could be an investment fund, a virtual pool, or a mandate) is replaced, removed, or added, the pension administration organization will adjust and process this. If adjustments are made within an investment product, this is not relevant to the pension administration organization and only affects the provider of the product.

In the direct order model, a **cohort pool** consists of a group of participants who have the same investment allocation based on the lifecycle principle (less investment and interest rate risk as the retirement date/end of the investment horizon approaches). A cohort pool can be used to distinguish between groups of participants. This can be based on time (age, period until retirement, etc.) but also on a characteristic such as active, deferred, disabled, etc. The number of pools is basically unlimited; as many pools are created as are needed to distinguish the right participant groups that require their own investment mix. The administration of the cohort pool is optional and can be managed by the pension administration organization, the investment administrator/asset service provider, or elsewhere. The allocation of weights (percentages) is often determined by the fiduciary manager. A cohort pool is an administrative grouping of a group of participants who, for example, have the same investment allocation based on the lifecycle principle.

<u>Figure 3, showing an example of cohort pools and lifecycles, can be found in the official Dutch manual.</u>

The example in Figure 3 illustrates how birth years and thus ages can influence the allocation of investments within lifecycles.

When a participant ages by one year, an **age-based rebalance** is performed. Each participant is placed in the next cohort pool, and their investment mix is adjusted to that of the new cohort. In the example above (Figure 3), regardless of the chosen risk profile, the share of equities is reduced and the share of bonds is increased. This leads to concrete buy and sell orders to the product providers.

Another form of rebalancing is **target-weight rebalancing**. This can be performed when the actual allocation of investments falls outside pre-established bandwidths due to market movements. This form of rebalancing also leads to buy and sell orders.

A group (cohort) of participants can be composed in various ways. Generally, three aspects play a role:

*   Age (or period to retirement, birth year/month).
*   Status (e.g., accumulating vs. decumulating, active/deferred/disabled).
*   Investment profile.

Netting of investments takes place across the cohort pools according to the instructions for the investment transactions. In the direct order model, this happens "in the spaghetti" (see Figure 2) between the cohort pools and the investments. The risk-sharing reserve is considered a separate cohort pool that invests in investment products according to its own investment policy.

## 4.3 Model 2: More Extensive, Layered Order Model
In the "More extensive, layered model," investments can also consist of non-daily tradable and/or non-platform-tradable (illiquid) funds or investment mandates. This model is already applied for larger Collective Individual DC (CIDC) schemes.

<u>Figure 4, showing a schematic of the layered order model, can be found in the official Dutch manual.</u>

In this model:
*   Participants invest in **cohort pools** according to the chosen lifecycle. These cohort pools, in turn, invest in **investment pools**. The investment pools can consist of various underlying investments (liquid, illiquid, funds, and mandates). To make the allocation to participants robust and traceable, units are issued and unit values are calculated for the various (layered) pools. The participant's assets can thus be traced exactly to the pro-rata share of the underlying investments. The layer with cohort pools is optional; if this layer is absent, the pension administration organization must administer which participations in the various investment pools are held per participant.

*   The allocation of returns can be done by the **pension administration organization** or the **administrator of the cohort and investment pools**.
    *   The **pension administration organization** is responsible for explicitly allocating returns to personal pension assets, the risk-sharing reserve, etc., based on established rules.
    *   The **administrator of the cohort and investment pools** processes the allocation and administration of cohort pools as provided by the PUO. This role can be performed by the PUO, the investment administrator, or another specialized party. The participation values and the number of participations of the cohort pools form the basis for the PUO to explicitly allocate assets to participants.

*   There can be a **dual cohort administration**. The first is with the PUO (participant & cohort administration). The second is with "an administrator," which handles the relationship between the cohort pools and the investment pools. This second administration can be called a middle-office administration and is optional.

*   The **Fiduciary Manager** supports the pension administrator in establishing the integrated investment policy and directs the operational asset managers.

*   The **Investment Administrator/Asset Service Provider** (often a service from the custodian) handles the independent investment administration of the investment pools for the pension administrator.

In the process for "Model 2," a distinction is made between an accumulation phase and a payout phase. The payout phase executed by a pension administration organization is in-scope. In the payout phase, participants can choose between continuing to invest (with a variable pension benefit) or a fixed pension benefit.

For an individual payout phase, the data exchange can be set up similarly to the accumulation phase. For a collective payout phase (all retirees in one cohort), aligning the interest rate sensitivity of the investments with the collective projected benefits is important. It is possible for the accumulation phase to occur in model 1 and the payout phase in model 2. For the payout phase (executed by a PUO), the fiduciary manager will set up a matching portfolio. The necessary data exchange will be structured in accordance with data exchange 1b from the SPR.

## 4.4 Information Flows FPR - Model 1 (1a and 1b)
The information exchange for model 1 can be split into a variant 1a, where the pension administration organization invests directly, and a variant 1b, where the PUO invests via an order platform. Strictly speaking, from the PUO's perspective, there is no distinction between these variants, but for clarity, both are explained separately. This is schematically and simplified shown in Figures 5 and 6. For example, a PUO could trade ETFs on behalf of the pension fund via a broker if these are part of the agreed investment mix.

<u>Figure 5 - Model 1a, where the PUO invests directly with various market parties, can be found in the official Dutch manual.</u>

The data exchange, indicated as "scope" in Figure 5, takes place between the PUO on one side and the various types of market parties on the other.

<u>Figure 6 - Model 1b, where the PUO gives investment orders to an intermediary (order platform: custodian, fiduciary), can be found in the official Dutch manual.</u>

The data exchange ("scope") from Figure 6 occurs exclusively between the PUO and the order platform.
The data exchange for FPR model 1 (a and b) proceeds via the following 2 messages.

### 4.4.1 Message 5. Order Instruction (00541)
*Information flow from Pension Administration Organization to Brokers/Transfer Agents/Order Desks (model 1a and 1b)*

This information flow from the PUO to Brokers/Transfer Agents/Order Desks contains the minimum set of data required to send an order to an order processing party. A switch can also be executed with this message.
The PUO submits orders at the level of the investment fund. The provider of the fund executes the ordering in the underlying investments itself. This can include listed and illiquid investments, among others.

_For the functional elaboration into a message, see chapter 6, specifically section 6.4.6._

### 4.4.2 Message 6. Order Confirmation (00542)
*Information flow from Brokers/Transfer Agents/Order Desks to Pension Administration Organization (model 1a and 1b)*

The confirmation data of the order is returned from the order processing party to the pension administration organization.

## 4.5 Information Flows FPR - Model 2
The information exchange for model 2 (more extensive, layered order model) can be schematically simplified as follows.

<u>Figure 7, showing a schematic of the layered order investment process, can be found in the official Dutch manual.</u>

The scope outlined in Figure 7 leads to the exchange of various information flows. The standardized data exchanges that fall within the scope are indicated by red arrows in the process flow figures below. The data needed for these different information flows/processes is described in the following paragraphs. Note: The time indications in the figures below are indicative and can be filled in differently by each pension administrator. This document only covers the information flows.

The information flow of model 2 has several steps – see the (step) numbers below in two process flow diagrams (Figures 8 and 9).

<u>Figure 8 (Process flow & data exchange FPR 1) and Figure 9 (Process flow & data exchange FPR 2) can be found in the official Dutch manual.</u>

**Explanation of Figure 8: Process flow & data exchange FPR (1) - standard**
The process shown assumes one administrator for both cohort pools and investment pools. This administrator links the received aggregated data about participants (via cohort pools) to the investments (via investment pools).
In step 5 to 10, the PUO provides the mutations in the number of participations per cohort to the cohort pool administrator. This administrator determines the preliminary participation value based on the reconciled administration of the investment pools (step 8). By combining the supplied mutations with the preliminary participation value and rebalancing rules, the necessary transactions in investment pools can be calculated. These transactions are combined for all cohorts, resulting in one instruction in euros per investment pool to the fiduciary manager, who executes the transactions (step 11). These transactions flow via SWIFT to the investment administrator/asset service provider (step 15). The investment pool administrator calculates the final unit values for the investment pools (step 16), which forms the basis for calculating the participation value for cohort pools (step 17). These are shared with the PUO (step 18) so that the value for individual participants can be determined.

Several variations on this process are possible, depending on how the roles of cohort pool administrator and investment pool administrator are assigned (e.g., to the PUO or the investment administrator/asset service provider). These variations may require additional information exchanges.

**Explanation of Figure 9: Process flow & data exchange FPR (2)**
This process also assumes an administrator of cohort and investment pools. If the PUO fulfills the role of cohort pool administrator, several steps will shift to the PUO.

### 4.5.1 Message 7. Balance Adjustments (00551)
*Information flow from PUO to the administrator of cohort and investment pools in the FPR (5 ->10 in the diagram) on T-4:*

The first (expected monthly) information flow from the PUO to the administrator of cohort and investment pools concerns netted mutations (purchase, sale, and switches) at the total level per cohort pool. With this, the administrator can calculate the inflow or outflow for investment pools and instruct the fiduciary manager accordingly. The specific fields used are detailed in the message specifications.

_For the functional elaboration into a message, see chapter 6, specifically section 6.4.8._

### 4.5.2 Messages for reconciliation information
*Information flow between the administrator, Fiduciary manager, and investment administrator (6 -> 7 -> 8 in the diagram) on T-4:*

The administrator of cohort and investment pools monthly receives the positions from the leading administration of the investment administrator for the investment pools. This can be supplemented with data from the fiduciary manager's (shadow) administration. These positions, containing for example the market value (`marketValueAmount`) and number of units (`numberOfUnits`) per investment pool, are reconciled with the administrator's own administration.

#### 4.5.2.1 Message 8. Reconciliation Information (00552a)
This message is for the reconciliation between the administrator, fiduciary manager, and investment administrator.
_For the functional elaboration, see chapter 6, section 6.4.9._

#### 4.5.2.2 Message 9. PUO Reconciliation Information (00552b)
This message contains the necessary information for the situation where the PUO also fulfills the role of cohort pool administrator. In this case, an additional information exchange from the investment pool administrator to the PUO about the preliminary unit values (`preliminaryUnitValueAmount`) of the investment pools is needed.
_For the functional elaboration, see chapter 6, section 6.4.10._

### 4.5.3 Message 10. Control Information Investment Pools (00553)
*Information flow between Administrator and Fiduciary manager (10 -> 11 in the diagram) on T-4:*

The administrator of cohort and investment pools calculates the participation values and combines these with the given mutations to estimate the cash effects on the investment pools. The administrator sends these cash effects (with substantiation) to the fiduciary.
_For the functional elaboration, see chapter 6, section 6.4.11._

### 4.5.4 Message 11. Rebalancing Information (00554), Rebalancing cohort pools
*Information flow between Administrator and Fiduciary manager (20 -> 21 in the diagram) on T+3:*

The administrator rebalances the relevant age groups based on the unit values of the investment pools at time T to be invested according to the standard policy for all cohorts. The administrator sends all month-end transactions in the cohort and investment pools to the fiduciary manager.
_For the functional elaboration, see chapter 6, section 6.4.12._

### 4.5.5 Passing on values per investment pool and per cohort pool
*Information flow between various parties (15 -> 16 -> 17 -> 18 in the diagram) on T+3:*

The administrator calculates the unit value per unit in the investment pool and the participation value per participation in the cohort pool. The administrator passes the (participation) values of the cohort pools to the PUO and the fiduciary. If the PUO acts as the cohort pool administrator, it will receive the unit values of the investment pools and calculate the participation values itself.

#### 4.5.5.1 Message 12. Value Information Cohort Pool (00555a)
The fiduciary receives this from the PUO (when the PUO administers cohort pools).
_For the functional elaboration, see chapter 6, section 6.4.13._

#### 4.5.5.2 Message 13. Value Information Investment Pool (00555b)
The administrator of cohort and investment pools (also) passes on the (unit) values, the administrative price, of investment pools.
_For the functional elaboration, see chapter 6, section 6.4.14._

### 4.5.6 Message 14. Payment Information (00556)
*Information flow between Administrator and Fiduciary manager (22 -> 23 in the diagram), beginning of the month, on T+5:*

The administrator sends the payment instruction for withdrawals to the fiduciary manager.
_For the functional elaboration, see chapter 6, section 6.4.15._

## 4.6 Use of SPR Messages in FPR

Within a Flexible Premium Arrangement (FPR), in addition to the individual *unitized* cash flows, there are also collective premium flows.  
These are cash flows that do not belong to a single specific participant, such as risk premiums, contributions to reserves, or withdrawals from a collective benefit pool.  

The standard FPR messages (5 through 14) are purely aimed at the *unitized* world and do not support these collective flows.  
To address this, it has been agreed that parties will revert to the proven SPR messages 1, 2, 3, and/or 4 for the exchange of this information.  
This method applies to both the direct (Model 1) and the layered (Model 2) FPR order model.

## 4.7 Feedback Message & Resending - (FPR and SPR)
### Purpose and Function
When exchanging messages, it is essential for the sender to know if a message has been correctly received and processed. The feedback message is designed to provide this certainty in the following situations:

*   **For asynchronous processing:** To provide the final status (both success and failure) of a message after background processing is complete.
*   **For synchronous processing:** To provide immediate, detailed error information when a message cannot be accepted.

A feedback message is therefore mandatory to specify errors. In case of successful processing, it is only sent as part of an asynchronous process. For successful synchronous processing, an HTTP 200 OK status code is sufficient.

### Structure of the Feedback Message
The feedback message has a compact, fixed structure optimized for communicating status information. The image below (also available on GitHub in the message overview and in the MessageStructureView of the message) shows the hierarchical structure and the main entities.

![Feedback Message Structure](https://raw.githubusercontent.com/dma61/VBPUOdsk/refs/heads/main/VBPUO_Feedback_Message/MessageStructureView/Feedback_message.svg)

The core of the message is formed by the following components:

*   **commonTechnical:** Contains the technical identification of the feedback message itself, such as a new, unique `messageId`.
*   **commonFunctional:** Contains the functional metadata, including:
    *   `statusType`: The status of the original message: Accepted (8) or Rejected (0).
    *   `originalMessageId`: A mandatory reference to the `messageId` of the message to which this feedback pertains.
    *   `originalMessageType`: An optional field indicating the type of the original message, to simplify routing at the receiver.
*   **error:** An optional block that, in case of rejection, contains an `errorCode` and an `errorCodeExplanation`.
*   **party.pensionProvider:** Identifies the pension provider to whom the original message related.

For a detailed specification of all attributes and code lists, see sections 6.5 and 6.4.16.

### Interaction Patterns and Process Flow
The technical handling of the feedback is defined in the OpenAPI Specification (OAS) and follows six fixed scenarios. These describe both synchronous and asynchronous processing, including the handling of errors and "panic" situations where the feedback loop itself fails.

A visual overview of these scenarios can be found on GitHub:

![Feedback Sequence Diagram](https://raw.githubusercontent.com/dma61/VBPUOdsk/refs/heads/main/VBPUO_Feedback_Message/MessageStructureView/Feedback_sequencediagram.svg)

The scenarios are explained functionally below:

1.  **Synchronous validation - Success:** Immediate 200 OK.
2.  **Synchronous validation - Error:** Immediate 400 Bad Request with a feedback message in the body.
3.  **Asynchronous validation - Success:** First a 202 Accepted, later followed by a callback with an "Accepted" feedback message.
4.  **Asynchronous validation - Error:** First a 202 Accepted, later followed by a callback with a "Rejected" feedback message.
5.  **Panic scenario (after Error):** The callback with a "Rejected" feedback is not accepted by the recipient (400 Bad Request).
6.  **Panic scenario (after Success):** The callback with an "Accepted" feedback is not accepted by the recipient (400 Bad Request).

In panic scenarios (5 and 6), manual coordination via another channel is necessary.

### Protocol for Corrections and Resending
The feedback mechanism dictates the protocol for correcting messages. This protocol is based on the fundamental principle:

**"Once accepted messages are not unilaterally corrected."**

The received feedback message is the primary form of communication that determines how a correction should be handled.

**Scenario 1: Correction after an Error Message (Feedback "Rejected")**
If the receiving party has sent a feedback message with the status "Rejected," this serves as the official request for correction.

*   The receiving party expects a new, corrected message.
*   The sending party may and must send a corrected message without further, separate coordination.

**Scenario 2: Correction after Acceptance of a message**
This scenario occurs when a message has been successfully accepted (via a 200 OK), and the sending party subsequently discovers an error. Since there is no official trigger for a correction, unilaterally sending a new version of the message (a correction message) is not permitted.

In such situations, the sending party must contact the receiving party to discuss the situation. The outcome of this consultation determines the follow-up action. Possible solutions are:

*   Ad hoc agreement for resubmission.
*   Correction in the next regular delivery.
*   Following an agreed-upon incident procedure.

[See for additonal explanation issue #83 ](https://github.com/dma61/VBPUOdsk/issues/83#issuecomment-2701711063)

---
| <div align="left">[< Previous: Chapter 3: SPR Processes](chapter-3-spr-processes.md)</div> | <div align="right">[Next: Chapter 5: Data Standard Setup >](chapter-5-data-standard-setup.md)</div> |
|:---|---:|

