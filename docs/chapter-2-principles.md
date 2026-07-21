# 2 Principles

**In this chapter we discuss the key principles for the development, design and governance of the standard. This is primarily based on [Results of research: Standard for data exchange pension administration & asset management parties''](https://www.pensioenfederatie.nl/cms/streambin.aspx?documentid=18380).**

## 2.1 *Preamble: Principles of VBPUO Standardization*

*The purpose of standardization is seamless and efficient information exchange between all parties in the chain. The VBPUO standard rests on the following principles:*

- *Pragmatism and flexibility  
  The standard is not a requirement for uniformity, but a framework for interoperability. Chain partners retain their own internal processes and systems. The focus is on streamlining external communication.*

- *Interoperability as the ultimate goal  
  The value of the standard becomes evident in practice. The test: an organization must be able to switch seamlessly to another chain partner, without significant adjustments to the data interface.*

- *Manageable degrees of freedom  
  Flexibility is not unlimited. For predictability and reliability, the allowed variations are explicitly defined and deliberately limited.*

- *Supported by the chain  
  Adjustments and variations do not arise unilaterally. They require broad support to prevent fragmentation and to sustainably preserve the value of the standard.*

  *Thus, the VBPUO standard remains a shared instrument for efficiency, predictability, and future-proof cooperation in the chain.*

## 2.2 Background

Pension Administration Organizations (PUOs) regularly need information from Fiduciary Managers (FMs) and/or Investment Administrators (BAs) to correctly administer participant records for pension schemes. Conversely, FMs (and asset managers) need information to invest the assets for various pension administrators within the framework of the agreed investment policy. The required data exchange between PUOs, FMs and BAs (and asset managers) is expected to be very similar in all cases.

With the introduction of the Wtp, information needs will change and the frequency of desired information exchange will increase. The information needs for PUOs, FMs and BAs for servicing pension administrators are fundamentally very similar. Any differences in information exchange will primarily depend on the type of scheme being administered.

In the accumulation phase of the Flexible Premium Scheme (FPR), the information need will largely correspond to that of current 'defined contribution' schemes, possibly supplemented with data on the risk-sharing reserve. Regarding the exchange of data during the collective payout phase, this will in many respects be comparable to the payout phase of the Solidarity Premium Scheme.

For the Solidarity Premium Scheme (SPR), an entirely new data stream must be set up, for both the accumulation and payout phases. There must be tighter alignment between the fund assets managed by the FM and the collective administration of personal pension assets by the PUO.

## 2.3 Out of Scope

Out of scope of the elaboration of information exchange are:

- Contractual agreements regarding the overall process around asset management between parties. The standard provides for the necessary information exchange, the data needs, between PUOs and asset management parties at the various process moments. The standard provides for the data needs for both the Solidarity Premium Scheme (SPR) and the Flexible Premium Scheme (FPR). However, the exact implementation of the data exchange between parties is determined by contractual agreements between the cooperating pension administrator and its asset management partners.

- Processes that are already running and fundamentally do not change, such as the reconciliation of the investment administration between the FM and the BA/asset service provider.

- Information that does not need to be exchanged because it is only used by one party in the chain.

- Information regarding investment policy, protection and allocation rules and cohort composition. This information is shared by the pension administrator with involved parties through various policy documents, such as the strategic investment policy, the annual investment plan and investment guidelines.

- Information exchange between pension participant, pension administrator and/or PUO.

  Allocation of returns to participants.

- Information about costs:

  - For the time being, there is no crystallized and unambiguous process in cooperation chains to arrive at cost allocation (and also the communication about costs). Experiences so far seem to indicate that this is difficult to standardize. Different parties make different trade-offs regarding processing, granularity, actual versus budgeted, provisioning, timeliness, division of responsibilities in providing different components, etc.

  - It is expected that existing processes for compiling the DNB annual statement J402 will continue to form the basis for cost-related information exchange, for both the SPR and the FPR.

- Insight into/look-through to the actual investments, usually referred to as "Lookthrough" information. Ad hoc requests for additional information from BA/asset service provider or FM may be necessary but fall outside regular data exchange in the context of the exchange described in this manual.

- Any specific information exchange required for a premium-benefit agreement as offered by insurers.

- The periodicity of the exchange. Not every process within pension administration leads to necessary actions within asset management. However, the consequences of processes that do lead to asset management actions must be exchanged on a periodic basis. The periodicity of the exchange of the related messages can be flexibly arranged between parties.

- Coverage ratio. The calculation and reporting of the coverage ratio falls under the responsibility of the PUO or BA. The VBPUO standard does not provide a separate message for this. See GitHub issue [#118](https://github.com/Stichting-SIVI/VBPUOdsk/issues/118).

- Task/Role division. The way parties cooperate, the division of roles or governance, is <u>not</u> part of the standard.

## 2.4 Principles of Data Exchange

To make the data exchange as practical as possible, the following principles apply:

- The data standard is usable for any (governance) division between pension administration and asset management.

- If the asset service provider fulfills an independent role as leading BA and/or tests the execution of policy, it receives the same information as the FM in order to independently report to pension funds on the followed and realized investment policy in relation to the objectives.

- The FM role receives the necessary information to invest the collective assets in accordance with the framework of the investment policy, taking into account inflow and outflow (from premiums, benefits and value transfers) and projected benefits.

- The PUO provides the participant with insight into the development of assets designated for pension benefits (SPR) and/or capital designated for pension (FPR) including the allocation of returns and expected benefits.

- Parties receive the data intended for them directly from the sending party. An FM therefore does not need to forward information received from a PUO to another party selected by the pension fund, such as an asset service provider and/or a Liability-Driven Investment (LDI) manager.

- <u>Once-accepted messages are not unilaterally corrected</u>. Messages that have been accepted by the receiving party may directly lead to irreversible operational processes, such as investment transactions or the allocation of returns to participants. If a sending party discovers an error in an already accepted message, coordination with the receiving party is mandatory before any correction message is sent. The specific procedures for this are further explained in section 4.6.

## 2.5 Clarification of Data Exchange Principles

During the substantive consultation round in May/June 2023, several issues recurred that did not lead to changes in the substantive part of the [report](https://www.pensioenfederatie.nl/cms/streambin.aspx?documentid=18380) but did need to be clarified to prevent misunderstandings.

- **Data Model**: The data model contains only the data needed to send and/or receive the required information about investing pension assets and to share information about realized investment results.

- **Roles (not prescriptive)**: To support the elaboration of the data model, data exchange between various parties in the chain is described. To support understanding of the data model, for both the SPR and the FPR, a role division in the chain has been outlined in which the governance model provides for certain function separations. In an alternative arrangement, roles can be performed by the same party; for example, the FM can also maintain the leading investment administration. It is not the intention of this manual to prescribe the form of cooperation between parties and thus the governance model.

- **Periodicity**: For a number of processes, it has been indicated that these are expected to have monthly periodicity. This periodicity is not prescribed. The mentioned exchange moments and periods are examples that can be filled in differently in the agreements between parties.

- **Process description**: For the FPR, it is possible to start from already existing processes (including indicative timelines and role division) for (collective) individual DC schemes. For the SPR, this is not yet the case.

- **Costs**: The information exchange about costs falls outside the scope of this standard. For the time being, we assume that existing processes will be built upon, which also form the basis for, for example, the J402 DNB annual statement.

- **The term Asset Management**: When this manual uses the term "asset management," it refers to the parties: FM, BA/asset service provider, custodian and Liability-Driven Investment manager. For "pension administration," this refers to the combination of the statutory pension administrator and the PUOs that administer on their behalf.

- **Language**: This report has been prepared for the data exchange between PUOs and asset managers within the Dutch Wtp context. The report and the standard are delivered in the Dutch language. The names of the variables used in the standards are, however, in English so that the conceptual framework is also understandable for non-Dutch speakers who are familiar with asset management.

## 2.6 Participant Communication

See chapter 6 in the previously mentioned [final report](https://www.pensioenfederatie.nl/cms/streambin.aspx?documentid=18380) in the introduction.

## 2.7 Technology

Regarding the use and technical implementation of the data standard, a number of principles have been formulated:

- The data exchange is "sustainable," meaning not tied to technological trends (or hypes).

- The documentation is clear and transparent.

- The data set can be adjusted in consultation with the involved parties.

- Open technical standards are used as much as possible (e.g. REST, JSON, SOAP, ODATA, OAuth).

For the technical implementation of the message exchange, the following has been agreed:

- Data exchange: RESTful Web services.

- Data format: JSON.

- For the data format, we conform within this standard to AFD 2.0. This has consequences for, among other things, the naming of attributes and entities.

- AFD 2.0 defines the data type of an attribute, **but does not restrict the string length or the number of decimal places**. Any restriction on the number of positions can be agreed upon between parties. See <https://www.manula.com/manuals/sivi/sivi-all-finance-standard/1/en/topic/data-types-and-formats>

- Message processing is asynchronous. The message exchange conforms to REST synchronously. The frequency of information exchange is periodic (e.g. monthly) and processing by the recipient is in principle on a daily basis; synchronous (real-time) is not necessary.

- Message initiative lies with the sender of the information, who pushes the message to the recipient.

- Service window: recommendation is office hours. Parties can make their own bilateral agreements about this.

- Security aspects:

  - During the transport of information, two-way authentication (mutual-TLS) is used.

  - Authentication of the sender at the receiving server is required.

  - The data must be guaranteed to arrive unmodified at the recipient (are non-repudiable). They are therefore digitally signed.

Agreements on the aspects below are elaborated and handled within the framework of the governance structure around the standard.

- The complete technical data standard and the various messages based on it.

- Maximum size (quantities and/or file size) of the message. See below under "Handling Large Messages."

- Granularity of the message exchange.

- A lower granularity indicates that at a certain level fewer details are exchanged.

- Processing time of received messages.

- Message feedback: response messages (acknowledgment and correct or error message — substantive and technical — or warning). The rules for this must be described.

- Response time (server).

**Handling Large Messages (Sub-messages or Chunking)**

Although the number of transactions per day may be relatively low, the size of individual messages (particularly Message 3 — Pension Projection) can be considerable. Messages larger than approximately 4 MB can in practice cause problems during transport and processing via modern cloud infrastructures.

To address this, the standard offers a mechanism to split large messages into multiple, smaller sub-messages (chunks).

- Mechanism: The splitting is done via an optional chunking.default block at the highest level of a message. This block contains metadata about the splitting, such as the sequence number and the total number of chunks.

- Applicability: This mechanism applies to all functional messages, but not to the feedback message.

- Validity: Each sub-message is a self-contained, valid JSON message.

- Processing: The recipient can only merge the sub-messages into the complete, logical message after receiving all parts. An error in one sub-message means the entire logical message is considered failed.

- Limits: The standard does not prescribe a maximum number of chunks. The maximum message size and the number of chunks are agreements between chain parties (TOM / SLA). See GitHub issue [#127](https://github.com/Stichting-SIVI/VBPUOdsk/issues/127).

  The detailed specifications of this mechanism can be found in Chapter 6.

## 2.8 Transport of Data

(Some) standardization of the transport of data, an interface, is of great importance. Standardization makes life much simpler for the sending and receiving parties and prevents all cooperating parties from having to reinvent the wheel bilaterally each time. The elaboration is limited to one solution, namely a RESTful API/webservice. The SIVI API framework provides support for this. Parties that cannot or do not want to work with the RESTful API/webservice solution can develop bilateral solutions themselves. No support is provided for this from the working groups around the standard.

The webservice solution is preferred because the information flow can then be better managed (faster through the (internal) chain, better versioning, better verifiability). A portal solution involves manual work and is therefore undesirable.

See also: *7.4* Transport / OpenAPI.

## 2.9 Governance, Management and Releases

### 2.9.1 Roles and Responsibilities

The use of the standard forms part of the individual agreements between pension administrators and asset management parties. Parties use the standard in accordance with the agreements that apply to the standard and are laid down in their contracts.

The standard is owned by the Pensioenfederatie. Management is placed with SIVI, acting on behalf of the Steering Group DSO. Substantive further development takes place in consultation with the sector via an Advisory Group (KBG).

The precise organization of management, the roles, the change procedure and the working method of the Advisory Group are laid down in the document "Organization Management Standard Asset Management Pension Administration." This document is the leading source for all governance-related agreements.

### 2.9.2 Release Policy and Version Management

To make the further development of the standard predictable and manageable, the following release policy applies:

- Annual Release Cycle: Each year, a pre-release appears at the end of June, which is converted into the definitive annual release at the end of September (e.g. "Release 2026").

- Continuous Development: Changes that are approved during the year are made available on GitHub as soon as they are finalized.

- Version Support: In addition to the current annual release, the two preceding annual releases remain available. For 2026 these are: Release 2026, Release "2024 November" and Release "Juli 2024."

### JSON Schema Draft 2020-12

From release 2027, the VBPUO standard uses JSON Schema Draft 2020-12 for the JSON schemas published via GitHub.

The transition to Draft 2020-12 primarily concerns:
- modernization of the JSON Schema dialect;
- harmonization with current tooling and IDE support;
- adjustment of internal and external schema references.

As a result of this technical migration, the functional message structures and business meaning of the messages remain unchanged.
