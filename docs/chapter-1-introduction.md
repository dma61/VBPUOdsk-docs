# Chapter 1: Introduction
In this introduction, we discuss the context, purpose, and target audience of this manual. We also present (in considerable detail) the setup of the manual.

## 1.1 Context
### Final Report
In early September 2023, the final report "Research Results: Standard for data exchange between pension administration & asset management parties" was published.

With the introduction/implementation of the Future Pensions Act (Wtp), a tighter alignment between fund assets and the collective administration of personal pension assets is necessary. This increases the frequency of the required information exchange. In current practice, pension administrators and asset management parties arrange information exchange among themselves. Due to the intensification of information exchange, standardization of information exchange is desired. The aforementioned final report describes the functional data required for the exchange, the information flows, and the participant communication dependent on them. The data and information flows have been elaborated for both the solidarity premium scheme and the flexible premium scheme.

The final report is based on contributions from various organizations, including APG, AZL, Caceis, Capgemini, H&C, Van Lanschot Kempen IM, MN, Pensioenfederatie, SIVI, and TKP. Through a consultation round, various other implementing organizations, fiduciaries, custodians, and pension funds were involved. This consultation round has been completed, and the input received has been processed.

### Follow-up & Governance
SIVI is translating the final report into a data standard based on AFD 2.0 from SVI AFS. This data standard is accompanied by a base message from which we derive 14 messages. The messages are exchanged via REST-API endpoints. In addition to the 14 content-specific messages, a Feedback_Message is available for potential feedback on the 14 messages.

The standard represents a shared interest of pension administration and asset management, for which both governance and content management must be established. After the introduction of the standard, new requirements will arise that may or may not need to be included. It has been agreed that:
*   Ownership of the standard rests with the Pension Federation.
*   Content and governance management around the standard will be formally structured.
*   The standard will be managed by the SIVI management organization.
*   An advisory board will support the management and any further development.

## 1.2 Purpose
This manual provides an explanation of the standard for data exchange between asset management and pension administration. The manual offers:
*   Analysts and developers a guide to (facilitate) implementing the standard.
*   Stakeholders insight into the management of the standard.

## 1.3 Target Audience
This manual is intended for consultants, analysts, and developers involved in the implementation of the standard for data exchange between asset management and pension administration parties.

## 1.4 Setup & 1.5 Links
### 1.4.1 Attribute Name Notation
In the descriptive texts of this manual, you will encounter a dual naming convention for data fields, in the following format:
`technicalName` (Functional Name)
*   **`technicalName`**: This is the definitive, technical attribute name according to the SIVI AFD 2.0 standard, displayed in a monospace font. This is the name that must actually be used in the JSON messages.
*   **(Functional Name)**: This is the original, functional name as it was used during the requirements and design phase. This name is temporarily included to enhance recognition during the transition. It will be removed in a future release.

The complete Translation Table is in the appendices. Links in this document are colored blue.

### 1.6 Source of image on title page
[https://www.flaticon.com/free-icon/data-exchange_4995192](https://www.flaticon.com/free-icon/data-exchange_4995192)


---
<div style='display: flex; justify-content: space-between;'><div>[< Previous: Home](index.md)</div><div>[Next: Chapter 2: Principles>](chapter-2-principles.md)</div></div>