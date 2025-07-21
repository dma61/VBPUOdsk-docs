# Chapter 3: Processes & Information Flows – Solidarity Premium Scheme (SPR)

## 3.1 Introduction
This section describes the necessary information exchange between the involved parties to robustly implement the solidarity premium scheme.

Figure 1, which can be found in the official Dutch manual available for download at [sivi.org](https://www.sivi.org/pensioen/standaard-data-uitwisseling-vermogensbeheer-en-pensioenuitvoering/), schematically illustrates the information exchange between the involved parties. The investment administrator provides the pension administration organization with information independently of the fiduciary manager and can also perform a reviewing role. If this is not chosen and the fiduciary also conducts the leading investment administration, information flow 2 will run from the fiduciary manager to the pension administration organization.

**Legend (information flows/messages):**

*   1a - Assets per cohort
*   1b - Cash flow (contributions and withdrawals)
*   1c - Pension projections / projected cash flows
*   2 - Returns and assets

The roles of the various parties in the scheme are further explained below:

*   The **Pension Administration Organization (PUO)** is responsible for allocating returns to participants' personal pension assets (possibly via a collective payout phase), the solidarity reserve, any compensation deposit, and other possible reserves, in accordance with the allocation rules set by the pension administrator. Based on these personal pension assets, benefits are determined and projected in line with the pension administrator's principles. The pension assets and projected benefits are delivered per cohort to the fiduciary manager and/or the investment administrator. The PUO processes premiums, benefits, and changes in the participant base and handles participant communication.
*   The **Fiduciary Manager** supports the pension administrator in establishing the integrated investment policy, ensures its execution, and directs the operational asset managers. The fiduciary manager will also maintain a (shadow) investment administration. For large pension administrators without a fiduciary manager, the pension administrator itself is responsible for directing both internal and external asset managers.
*   The **Operational Asset Managers** manage parts of the portfolio and are directed by the fiduciary manager. It is possible that (for certain parts) the fiduciary manager and the operational asset manager belong to the same organization.
*   The **Investment Administrator/Asset Service Provider** (usually an additional service from the custodian) provides independent investment administration for the pension administrator. The investment administrator calculates the total return on investments and (if necessary) the return on various investment (sub)portfolios, delivering this to the PUO. As mentioned above, the fiduciary manager can also conduct the leading investment administration. The investment administration is fed by the settlement of mutations in the portfolio, executed by the operational asset managers. This administration is reconciled with the fiduciary manager if desired. The investment administrator is also often responsible for preparing regulatory reports or parts thereof.

## 3.2 SPR Information Flows
The information flows for SPR products between the fiduciary manager, the investment administrator, and the pension administration organization are:

*   Information from the PUO about assets, cash inflow and outflow, and projected cash flows to be hedged (optionally per cohort) to enable the fiduciary manager and investment administrator to fulfill their roles.
*   Information from the investment administrator or fiduciary manager about returns that the pension administrator needs to correctly allocate to participants.

The information flow from the PUO to the fiduciary/investment administrator (stream 1) is divided into three messages: 1a (assets), 1b (inflow and outflow), and 1c (projected benefits). Value and return information is sent to the PUO via message 4 (Return Information).

These messages are further detailed below.

### 3.2.1 Message 1. Assets (1a)
_Note: For readability, this manual temporarily uses a dual naming convention for attributes. See section 1.4.1 for an explanation of the notation._

On a periodic (expected to be monthly) basis, the fiduciary manager receives for a pension administrator (identified by `puvCode` (Pensionfund ID)), per scheme (identified by `refKey` (Pension scheme ID i)), the total pension assets (`startAmount` (Capital i)) at the beginning of the period (`startDate` (Capital date i)).

In addition to the total level information, the fiduciary can also receive the pension assets (`startAmount` (Cohort capital i,k)) per (age) cohort (identified by `refKey` (Cohort ID i,k)). For example, for the 25-29 age cohort, the total of the personal pension assets at the start can be received.

With the cohort information, the fiduciary manager can, if desired, make a total calculation and check the alignment with the information provided at the total/collective level against the fund's policy. This is useful for a robust transfer and audit trail, depending on the agreements made between parties. In case of (large) deviations, rebalancing may be desirable according to the pension administrator's policy. This information can also be provided to the investment administrator/asset service provider to enable them to perform review and reporting activities using the leading investment administration.

**Allocation to Portfolios**
In addition to the total assets, the Pension Administration Organization (PUO) can also communicate the desired allocation of these assets across different portfolios to the asset manager in this message. This provides the asset manager with important control information to act in accordance with the standard portfolio used by the PUO. This allocation information can be provided at both the total level (under the pension scheme) and the cohort level. These are optional fields that can specify the exposure to, for example, a return or protection portfolio, both as an absolute amount (`startExposureAmount`) and as a percentage (`startExposurePercentage`). While the total level is particularly important for control, the cohort-level information can be useful for reporting purposes.

_For the functional elaboration into a message, see chapter 6, specifically Message Structure 1. Assets (0001a). The current message structure can be found on GitHub under "Wiki/Berichtenoverzicht"._

### 3.2.2 Message 2. Cashflow (1b, inflow and outflow)
On a periodic (expected to be monthly) basis, the fiduciary manager receives for a pension administrator (`puvCode` (Pensionfund ID)), per scheme (`refKey` (Pension scheme ID i)), the inflow (`contributionAmount` (Contribution i)) during the period (on the `contributionDate` (Contribution date i)) and the outflow or net cash flow (`netAmount` (Net contribution/withdrawal i)) during the period (on the `netDate` (Net contribution/withdrawal date i)).

In addition to the total level information, the fiduciary can also receive the inflow (`contributionAmount` (Cohort contribution i,k)) and outflow (`withdrawalAmount` (Cohort withdrawal i,k)) or the net cash flow (`netAmount` (Net contribution/withdrawal i,k)) per (age) cohort (`refKey` (Cohort ID i,k)) over the period (`Start date PUO admin` to `End date PUO admin`).

The inflow and outflow include not only premiums, value transfers, and benefits, but also shifts between cohorts if applicable. A cohort can also be a birth year. An example is the personal pension assets of participants moving from the 25-29 age cohort to the 30-34 age cohort. The 'cohort' solidarity reserve, the 'cohort' compensation deposit, and possibly other reserves will also be involved.

**Applications of the Cashflow Message**
The standard offers the flexibility to use this message for two different purposes, which can coexist in practice:

1.  **Prospective Application (Forward-looking):**

    *   **Purpose:** Liquidity management. An estimate of the expected net cash flow for the upcoming period is provided. The net amount (`netAmount`) serves as input for the actual monthly (de)allocation payment between the PUO and the asset manager.
    *   **Characteristics:** Typically a net amount at the total scheme level.

2.  **Retrospective Application (Backward-looking):**

    *   **Purpose:** Analysis and accountability. The actual realized cash flows from a closed period are reported. This information is separate from the monthly allocation payment.
    *   **Characteristics:** The cash flow can be provided as a net amount (`netAmount`) or split (`contributionAmount` / `withdrawalAmount`). This variant is suitable for providing details at the cohort level.

The fiduciary manager is responsible for investing the inflow or freeing up funds to finance the outflow. The calculation method for the inflow or outflow amount depends on the preference of the pension administrator and the working method of the PUO. Investments can never be made retroactively. For the audit trail, it may be desirable to record the period in the information exchange.

_For the functional elaboration into a message, see chapter 6, specifically Message Structure 2. Cashflow (0001b)._

### 3.2.3 Message 3. Pension Projection (1c, projected benefits)
On a periodic (expected to be monthly) basis (`projectionDate` (Projection date)), the fiduciary manager receives from a pension administrator (`puvCode` (Pensionfund ID)), per scheme (`refKey` (Pension scheme ID i)) and per (age) cohort (`refKey` (Cohort ID i,j)), the projected benefits (`amount` (Cohort expected pension payment i,j,k)) based on the accumulated assets for future periods (`expectedPensionPaymentDate` (Expected pension payment date i,k)).

For example, for the 25-29 age cohort, this mainly concerns the projected retirement pension in 39 years (assuming the statutory retirement age). This information is important for the fiduciary manager to set up the protection portfolio and generate the intended protection returns. The desired protection per age cohort is decisive for the interest rate sensitivity to be hedged. A projection based on the entire population is no longer sufficient because the interest rate risk is no longer shared by the entire participant population.

Finally, the data exchange includes the cash flows to be hedged per scheme (`hedgedExpectedPensionPaymentAmount` (Hedged expected pension payment i,k)) per future period. This is equal to the sum of the weighted projected benefits per cohort. The weighting factor is the protection percentage per cohort. This creates a profile of the cash flows to be hedged and avoids misunderstandings.

_For the functional elaboration into a message, see chapter 6, specifically Message Structure 3. Pension Projection (0001c)._

### 3.2.4 Message 4. Return Information (2, Information need of the PUO)
This is the information flow from the investment administrator/asset service provider to the PUO (stream 2 from Figure 1) in the SPR.

Periodically, the PUO receives for a period (from `startDate` to `endDate`) for a pension administrator (`puvCode`), per scheme (`refKey`), and per portfolio (`refKey`), the start value (`startAmount`), end value (`endAmount`), and the return (`returnPercentage`). The PUO is responsible for allocating these returns to participants. Optionally, assets and returns per cohort can also be shared with the PUO, depending on the agreed roles and responsibilities.

The investment administrator/asset service provider provides the necessary information based on the independent investment administration. In an alternative governance model, the fiduciary manager can provide this information.

If the SPR is designed with **indirect (theoretical) protection returns**, information on the total return is generally sufficient. The PUO can calculate the excess return to be allocated based on the total return minus the allocated theoretical protection return.

If the SPR bases the protection return on the **direct (actual) achieved return**, the PUO must have a breakdown of the achieved return. The investment administrator must then provide the return for sub-portfolios, at least distinguishing between the protection portfolio and the excess return portfolio.

_For the functional elaboration into a message, see chapter 6, specifically Message Structure 4. Return Information (00002). A graphical overview of the message structure can be found on GitHub, but the JSON schemas and this manual are leading.

---
| <div align="left">[< Previous: Chapter 2: Principles](chapter-2-principles.md)</div> | <div align="right">[Next: Chapter 4: FPR Processes >](chapter-4-fpr-processes.md)</div> |
|:---|---:|

