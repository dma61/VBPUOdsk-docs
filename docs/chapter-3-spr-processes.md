# 3 Processes & Information Flows – Solidarity Premium Scheme

## 3.1 Introduction

This section describes the necessary information exchange between the involved parties to robustly implement the Solidarity Premium Scheme[^1].

Figure 1 below schematically illustrates the information exchange between the involved parties. The Investment Administrator (BA) provides the Pension Administration Organization (PUO) with information independently of the Fiduciary Manager (FM) and can also fulfill a reviewing role. If this is not chosen and the fiduciary also maintains the leading investment administration, information flow 2 will run from the FM to the PUO.

<img src="../media/image2.png" style="width:6.49583in;height:3.47847in" alt="Scope information exchange SPR" />

**Figure 1 - Scope information exchange SPR**

Legend (information flows/messages):

1a - Assets per cohort

1b - Cash flow (contributions and withdrawals)

1c - Pension projections / projected cash flows

2 - Returns and assets

Below, the roles of the various parties in the scheme are further explained:

- The **Pension Administration Organization** (PUO) has the responsibility to allocate returns to the personal pension assets of participants (possibly via a collective payout phase), the solidarity reserve, any compensation deposit and possible other reserves, in accordance with the allocation rules set by the pension administrator.  
  Based on these personal pension assets, benefits are determined and projected in accordance with the pension administrator's principles.  
  The pension assets and projected benefits are delivered per cohort to the FM and/or the BA. The PUO processes premiums, benefits and changes in the participant base and handles participant communication.

- The **Fiduciary Manager** (FM) supports the pension administrator in establishing the integrated investment policy, ensures the execution of this investment policy and directs the operational asset managers. The FM will also maintain a (shadow) investment administration. For large pension administrators without an FM, the pension administrator itself is responsible for directing both internal and external asset managers.

- The operational **asset managers** manage parts of the portfolio and are directed by the FM. It is possible that (for certain parts) the FM and the operational asset manager belong to the same organization.

- The **Investment Administrator**/asset service provider (BA; usually additional services from the custodian) provides independent investment administration for the pension administrator. The BA calculates the total return on investments and (if needed) the return on various investment (sub)portfolios and delivers this to the PUO. As mentioned above, the FM can also maintain the leading investment administration. The investment administration is fed by the settlement of mutations in the portfolio, executed by the operational asset managers. This administration is reconciled with the FM if desired. The BA also often handles the preparation of regulatory reports or parts thereof.

## 3.2 SPR Information Flows

The information flows for SPR products between the FM, the BA and the PUO are:

- Information from the PUO about assets, inflow and outflow of cash, and projected cash flows to be hedged (optionally per cohort) to enable the FM and BA to fulfill their roles.

- Information from the BA or FM about returns that the pension administrator needs to arrive at a correct allocation to participants.

The information flow from the PUO to FM/BA (stream 1) is divided into three messages: 1a (assets), 1b (inflow and outflow) and 1c (projected benefits). Value and return information is sent to the PUO via Message 4. Return Information.

These messages are further detailed below.

### 3.2.1 Message 1. Assets (1a)

On a periodic (expected monthly) basis, the FM receives for a pension administrator (identified by `puvCode`) per scheme (identified by `refKey`) the total pension assets (`startAmount`) at the beginning of the period (`startDate`).

In addition to the information at the total level, the fiduciary can also receive per (age) cohort (identified by `refKey`) the pension assets (`startAmount`). For example, for the age cohort 25-29 years, the total of the personal pension assets at the start can be received.

With the cohort information, the FM can, if desired, make a total calculation and check the alignment with the information provided at the total/collective level against the fund's policy. This is useful for a robust transfer and audit trail depending on the agreements parties make. In accordance with the pension administrator's policy, rebalancing may be desirable in case of (large) deviations. This information can, in addition to the FM, also be provided to the BA/asset service provider to enable them to perform review and reporting activities using the leading investment administration.

**Allocation to Portfolios**

In addition to the total assets, the PUO can also communicate in this message the desired allocation of these assets across different portfolios to the asset manager. This provides the asset manager with important control information to act in accordance with the standard portfolio used by the PUO.

This allocation information can be provided at both the total level (under the pension scheme) and the cohort level. These are optional fields that can specify the exposure to, for example, a return or protection portfolio, both as an absolute amount (startExposureAmount) and as a percentage (startExposurePercentage). While the total level is particularly important for control, the information at the cohort level can be useful for reporting purposes.

Functional elaboration into a message: see chapter 6, specifically *0* Message structure 1. Assets (0001a).

The current message structure can be found on GitHub under "[Wiki/Berichtenoverzicht](https://github.com/dma61/VBPUOdsk/wiki/Berichten-overzicht#bericht-1-vermogen-0001a)"

For the date conventions regarding startDate, see the [explanation for financialInformation.reportingPeriod in §6.3](../chapter-6-functionele-specificaties/#entiteit-financialinformation-reportingperiod).

### 3.2.2 Message 2. Cashflow (1b, inflow and outflow)

On a periodic (expected monthly) basis, the FM receives for a pension administrator (`puvCode`) per scheme (`refKey`) the inflow (`contributionAmount`) during the period (on the `contributionDate`) and the outflow or as net cash flow (`netAmount`) during the period (on the `netDate`).

In addition to the information at the total level, the FM can also receive per (age) cohort (`refKey`) the inflow (`contributionAmount`) and outflow (`withdrawalAmount`) or as net cash flow (`netAmount`) over the period (`startDate` to `endDate`).

The inflow and outflow include not only premiums, value transfers and benefits, but also shifts between cohorts if applicable. A cohort can also be a birth year. An example is the personal pension assets of participants moving from the 25-29 age cohort to the 30-34 age cohort. The 'cohort' solidarity reserve, the 'cohort' compensation deposit and possibly other reserves will also be involved.

With the cohort information, the FM can, if desired, make a total calculation and check the alignment with the information provided at the total/collective level against the fund's policy. This is useful for a robust transfer and audit trail depending on the agreements parties make. This information can, in addition to the FM, also be provided to the BA/asset service provider to also enable them to perform review and reporting activities using the leading investment administration.

**Two alternative fill patterns in Message 2 — use one of them**

Message 0001b supports two mutually exclusive fill patterns per `pension.scheme`:

**SPR route** — the cash flow is included directly under `pension.scheme` as `financialTransaction.cashflow` (optional, `0..1`). Cohort breakdown runs via `pension.cohort`, including `netDate` at the cohort level. When cohort breakdown is applied, the sum of the cohort amounts matches the amount at the scheme level: `scheme.netAmount = sum(cohort.netAmount)`. See [§6.3.1](../chapter-6-functionele-specificaties/#verbandscontroles-cashflowbericht-0001b) for the integrity constraints.

**FPR route** — the cash flow is included per investment portfolio via `pension.scheme → investment.portfolio → financialTransaction.cashflow`. In this fill pattern, `netAmount` and `netDate` are mandatory at the portfolio level.

The two patterns are mutually exclusive: the presence of `investment.portfolio` excludes direct `financialTransaction.cashflow` under `pension.scheme`, and the presence of `pension.cohort` excludes the use of `investment.portfolio`.

**Applications of the Cashflow Message**

The standard offers the flexibility to use this message for two different purposes, which can coexist in practice:

1.  **Prospective Application (Forward-looking)**

    - Purpose: Liquidity management. In this application, an **estimate** of the expected net cash flow for the upcoming period is provided. The net amount (`netAmount`) serves as input for the actual monthly (de)allocation payment between the PUO and the asset manager.

    - Characteristics**:** Typically a net amount at the scheme total level.

2.  **Retrospective Application (Backward-looking)**

    - Purpose: Analysis and accountability. Here, the **actually realized** cash flows from a closed period are reported. This information is separate from the monthly allocation payment.

    - Characteristics: The cash flow can be provided as a net amount (`netAmount`) or broken down (`contributionAmount` / `withdrawalAmount`). This variant lends itself to providing details at the cohort level.

The FM is responsible for investing the inflow or freeing up funds to finance the outflow. Inflow and outflow can be provided separately or as a net cash flow. When provided separately, the inflow and outflow dates must also be filled in; when provided as a net amount, only the cash flow date is needed.

The calculation method for the amount of the inflow or outflow depends on the preference of the pension administrator and the working method of the PUO. The FM does not need to be informed about the calculation methodology or about the period to which the data relates. After all, investments can never be made retroactively. For the audit trail, it may be desirable to record the period in the information exchange.

Functional elaboration into a message: see chapter 6, specifically *6.4.3* Message structure 2. Cashflow (0001b).

The current message structure can be found on GitHub under "[Wiki/Berichtenoverzicht](https://github.com/dma61/VBPUOdsk/wiki/Berichten-overzicht#bericht-2-cashflow-0001b)"

### 3.2.3 Message 3. Pension Projection (1c, projected benefits)

On a periodic (expected monthly) basis (`projectionDate`), the FM receives from a pension administrator (`puvCode`) per scheme (`refKey`) and per (age) cohort (`refKey`) the projected benefits (`amount`) based on the accumulated assets for future periods (`expectedPensionPaymentDate`).

For example, for the 25-29 age cohort, this mainly concerns the projected retirement pension in 39 years (assuming the statutory retirement age). In the information flow as of December 31, 2022, the first (benefit) cash flow for this cohort is then expected in 2061. This information is important for the FM to set up (the management of) the protection portfolio and generate the intended protection returns. The desired protection per age cohort (e.g. 25% for 25-29 years and 100% from 70 years) is decisive for the interest rate sensitivity to be hedged. It is no longer sufficient to base a projection of benefits only on the entire population in a pension scheme, because the interest rate risk is no longer shared by the complete participant population. If desired, the 'cohort' solidarity reserve, possibly the 'cohort' compensation deposit and other possible reserves can also be allocated protection returns. In that case, a (fictitious) cash flow profile must be drawn up for these cohorts. In addition to the individual projected benefits per cohort (including the reserves), a total projected benefit across the entire population can also be provided (`amount`). This equals the sum of the projected benefits across all cohorts per future period (`expectedPensionPaymentDate`).

Finally, the data exchange contains the cash flows to be hedged per scheme (`hedgedExpectedPensionPaymentAmount`) per future period. This equals the sum of the weighted projected benefits per cohort. The weighting factor equals the protection percentage per cohort. For example: the protection of the 25-29 age cohort is 25% and the protection of the cohort from 70 years is 100%. The projected benefits of the 25-29 age cohort are multiplied by 25% and added to the full projected benefits of the cohort from 70 years multiplied by 100%. In this way, a profile of the cash flows to be hedged is created. This exchange avoids misunderstandings regarding cash flows to be hedged and can, if desired, introduce a check in the process.

Functional elaboration into a message: see chapter 6, specifically *6.4.4* Message structure 3. Pension Projection (0001c)

The current message structure can be found on GitHub under "[Wiki/Berichtenoverzicht](https://github.com/dma61/VBPUOdsk/wiki/Berichten-overzicht#bericht-3-pensioenprojectie-0001c)"

For the unambiguous application of projectionDate and expectedPensionPaymentDate, see the [explanation for financialInformation.reportingPeriod in §6.3](../chapter-6-functionele-specificaties/#entiteit-financialinformation-reportingperiod).

**Handling Empty Cohorts**

The standard allows two approaches for cohorts with a value of 0:

1. **Include** with an explicit value of `0` — makes the distinction clear between "value is 0" and "data is missing."
2. **Omit** — keeps messages compact.

Parties must be able to process both variants. Agreements on this are documented between chain parties (TOM / SLA). For large messages, the [chunking mechanism](../chapter-7-6-chunking/#761-fundamentele-uitgangspunten-van-chunking) can be helpful. See GitHub issue [#100](https://github.com/Stichting-SIVI/VBPUOdsk/issues/100).

### 3.2.4 Message 4. Return Information (2, Information Need of the PUO)

**Information flow from BA/asset service provider to the PUO (stream 2 from Figure 1) in the SPR.**

The PUO needs periodic (expected monthly) information about the achieved return to administer the Solidarity Premium Scheme.

Periodically, the PUO receives for the period (running from `startDate` to `endDate`) for a pension administrator (`puvCode`) per scheme (`refKey`) and per portfolio (`refKey`) the value at the beginning of the period (`startAmount`), the value at the end of the period (`endAmount`) and the return in portfolio currency and (optionally) expressed as a percentage (`returnPercentage`). The PUO is responsible for the allocation of returns to participants based on portfolio returns. Optionally, per cohort in the scheme (`refKey`), pension assets (`startAmount`), protection return (`protectionReturnAmount`) and excess return (`excessReturnAmount`) can also be shared with the PUO. Whether these optional elements are exchanged depends on the agreed roles and responsibilities between the cooperating parties. The starting point is that the PUO has the responsibility to allocate returns to the personal pension assets of participants, the solidarity reserve, any compensation deposit and possible other reserves, in accordance with the allocation rules set by the pension administrator.

The BA/asset service provider provides the necessary information to the PUO and bases itself on the independent investment administration. In an alternative governance model, the FM can provide this information to the PUO.

If the Solidarity Premium Scheme is structured with **indirect (theoretical) protection return**, information about the total return is in principle sufficient. The allocation of protection return is then not dependent on the realized return. The excess return to be allocated by the PUO can be calculated by the PUO based on the total return minus the allocated indirect (theoretical) protection return.

When the Solidarity Premium Scheme bases the protection return to be allocated on the **direct (actual) achieved return**, the PUO must have a breakdown of the achieved return. The BA/asset service provider must then provide the return for sub-portfolios (and optionally per cohort), with at least a distinction between the protection portfolio and the excess return portfolio. Depending on the way actual protection return is allocated to individual participants, a further breakdown of the protection portfolio into sub-portfolios may be desirable.

A (further) breakdown of portfolios may also be desirable for the purpose of communication about achieved returns to participants, reconciliation purposes and any legal obligations. This depends on the setup desired by the pension administrator.

The information exchange for the solidarity scheme based on the direct (actual) achieved return can also be used for an exchange in a specific implementation variant of the Flexible Premium Scheme. This choice will mainly be made by parties that use a similar method of return allocation for the Flexible Premium Scheme as in the Solidarity Premium Scheme based on actual returns. For each cohort, an actual protection return and excess return are then delivered to the PUO as an amount and optionally as a percentage.

**Return Information at Multiple Levels in a Single Message**

Within a single Message 4, multiple types of return can be included: total return (total), protection return (matching) and excess return (return). The `refKey` identifies per block which type of return or which portfolio is concerned. It is not necessary to send a separate message per type. The standard does not establish a formal relationship between the three types; the assumption that matching + return = total is not enforced.

See GitHub issue [#109](https://github.com/Stichting-SIVI/VBPUOdsk/issues/109).

[^1]: Note: the SPR data model, which is essentially a decomposition model, can also be used for FPR data exchange. This is logical when the implementation of an FPR scheme is not unitized but is also based on return decomposition, see 4.6.

Functional elaboration into a message: see chapter 6, specifically *6.4.5* Message structure 4. Return Information (00002)

A graphical overview of the message structure can be found on GitHub under "[Wiki/Berichtenoverzicht](https://github.com/dma61/VBPUOdsk/wiki/Berichten-overzicht#bericht-4-rendementsinformatie-00002)". The JSON schemas and this manual are, however, leading.
