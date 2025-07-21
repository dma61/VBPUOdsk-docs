# Chapter 6: Functional Specifications
This chapter contains the detailed functional specifications.

This chapter contains the functional specifications:

*   Data Dictionary
*   Base Message
*   Cross-reference: Base Message & Messages

## 6.1 Data Dictionary
An overview of all entities and their purpose. This section will link to detailed pages or files for each entity.

| Entity.entitytype                    |
| :----------------------------------- |
| commonTechnical.default              |
| party.sender                         |
| party.contact                        |
| party.receiver                       |
| commonFunctional.default             |
| party.pensionProvider                |
| pension.scheme                       |
| financialInformation.reportingPeriod |
| financialTransaction.payment         |
| party.creditor                       |
| financialTransaction.cashflow        |
| financialTransaction.expectedPayment |
| pension.cohort                       |
| pension.cohortPool                   |
| investment.pool                      |
| investment.portfolio                 |
| investment.investmentDetails         |
| financialTransaction.trade           |
| error.default                        |
| document.default                     |
| chunckMeta.default                   |

## 6.2 Entity Types
This section describes the various entities and the attributes within those entities.

Below is an explanation of the entities. This information is derived from AFD 2.0, which can be consulted via [this link](https://www.sivi.org/standaarden/sivi-all-finance-standaard/afd-online-2-0/).

**Note:** The entity type is mandatory.

| **Entity.entitytype** | **Description** |
| :--- | :--- |
| `commonTechnical.default` | This entity contains technical details about sending and storing messages. It forms the basis for the technical aspects within the messaging system. |
| `party.sender` | The "party.sender" entity refers to the sender of the message. |
| `party.contact` | The "party.contact" entity represents a contact person within a legal entity. |
| `party.receiver` | This entity represents the recipient of the message. |
| `commonFunctional.default` | This entity contains domain-specific information about the content of the message. |
| `party.pensionProvider` | This entity represents a pension provider (pension fund, insurer, or PPI). |
| `pension.scheme` | This entity contains data at the level of the pension scheme or plan. |
| `financialInformation.reportingPeriod` | This entity relates to reporting periods, time intervals, and other generic dates. |
| `financialTransaction.payment` | This entity/entity type combination contains data about a payment. |
| `party.creditor` | This entity represents the creditor; the recipient of the payments. |
| `financialTransaction.cashflow` | This entity deals with financial transactions related to pensions, specifically focusing on cash flows. |
| `financialTransaction.expectedPayment` | This entity contains information about projected future cash flows/payments. |
| `pension.cohort` | This entity contains information about specific target groups (cohorts) within the pension scheme. |
| `pension.cohortPool` | The pooled combination of investment pools for a cohort. Investments in a cohort pool are made for a group of participants with a similar investment allocation. |
| `investment.pool` | This entity (investment pool) represents collections of underlying investments (liquid, illiquid, funds, mandates). |
| `investment.portfolio` | This entity relates to investment portfolios, which represent the total managed assets (or a sub-portfolio). |
| `investment.investmentDetails` | This entity describes individual investments of a pension provider. |
| `financialTransaction.trade` | This entity relates to trading activities within the pension scheme. |
| `error.default` | In case of errors, this entity is used to generate error messages. |
| `document.default` | This entity is intended for adding any attachments to messages. |
| `chunkMeta.default` | This entity contains metadata for splitting and merging large messages (chunking). |

## 6.3 Attributes in Entities.Entity Types

The tables in this section detail the attributes per entity/entity type combination. Each entry includes the attribute's name, definition, data type, max length, and a link to any code list.

*Note: Attribute descriptions in the feedback message may differ from those in the 14 content messages.*

Data type descriptions are available in the SIVI All-Finance Standard manual.

**Interpretation rules:**

*   **`string`:** Max length is specified unless a code list applies (then 'length' is empty).
*   **`decimal`:** Defaults to 2 decimal places. Deviations are specified in the data type column.

Attribute names have been aligned with AFD 2.0 conventions and differ from the consultation document. See Appendix 8.4 for the translation table.

### `commonTechnical.default`
_The commonTechnical entity covers all information about sending or storing the message. This is typically technical information._

| Attribute Name     | Definition                     | Data Type | Length | Code List |
| :----------------- | :----------------------------- | :-------- | :----- | :-------- |
| `messageId`        | Unique message identification  | string    | 70     |           |
| `creationDateTime` | Creation date and time         | timestamp |        |           |
| `testMessage`      | Test message indicator         | boolean   |        |           |

### `party.sender`
_Sender of the message._

| Attribute Name            | Definition                                                     | Data Type | Length | Code List |
| :------------------------ | :------------------------------------------------------------- | :-------- | :----- | :-------- |
| `refKey`                  | Unique reference key assigned to an entity.                    | string    | 70     |           |
| `rsinNumber`              | Governmental identification number for legal entities (RSIN).  | string    | 9      |           |
| `organizationName`        | Organization name of the sender.                               | string    | 60     |           |
| `applicationSenderName`   | Name of the application that created the message.              | string    | 60     |           |

### `party.contact`
_A natural person who can be contacted within a legal entity for further information._

| Attribute Name      | Definition         | Data Type | Length | Code List |
| :------------------ | :----------------- | :-------- | :----- | :-------- |
| `emailWork`         | Work email address | string    | 60     |           |
| `workPhoneNumber`   | Work phone number  | string    | 60     |           |

### `party.receiver`
_Receiver of the message._

| Attribute Name     | Definition                                                    | Data Type | Length | Code List |
| :----------------- | :------------------------------------------------------------ | :-------- | :----- | :-------- |
| `refKey`           | Unique reference key assigned to an entity.                   | string    | 70     |           |
| `rsinNumber`       | Governmental identification number for legal entities (RSIN). | string    | 9      |           |
| `organizationName` | Name of the recipient organization(s).                        | string    | 60     |           |

### `commonFunctional.default`
_The commonFunctional entity covers all information about the content of the message. This is typically domain-specific information._

| Attribute Name         | Definition                                                                                             | Data Type | Length | Code List |
| :--------------------- | :----------------------------------------------------------------------------------------------------- | :-------- | :----- | :-------- |
| `function`             | Message function code.                                                                                 | string    |        | ADNFUN    |
| `statusType`           | Status of the original message processing (Accepted or Rejected).                                      | string    |        | ADNSTS    |
| `afdDefinitionName`    | Type of message, name of the message.                                                                  | string    | 80     |           |
| `afdDefinitionVersion` | Version of the `afdDefinition` of the message. See section 7.5.1 for details.                          | string    | 80     |           |
| `originalMessageId`    | The original `messageId` of the message being replaced or being responded to.                          | string    | 70     |           |
| `originalMessageType`  | Message type of the original request to which this message is a response. E.g. `0001a`, `0001b`, etc.   | string    |        |           |

### `party.pensionProvider`
_Information on the Pension Provider level (Pension Fund, Insurer, PPI, APF)._

| Attribute Name     | Definition                                                    | Data Type | Length | Code List |
| :----------------- | :------------------------------------------------------------ | :-------- | :----- | :-------- |
| `puvCode`          | ID of the pension provider (PUV-code).                        | string    |        | AFDIDP    |
| `rsinNumber`       | Governmental identification number for legal entities (RSIN). | integer   | 9      |           |
| `organizationName` | Name of the pension provider.                                 | string    | 60     |           |

### `pension.scheme`
_Data on the pension scheme level._

| Attribute Name         | Definition                                    | Data Type | Length | Code List |
| :--------------------- | :-------------------------------------------- | :-------- | :----- | :-------- |
| `refKey`               | ID of the pension scheme.                     | string    | 70     |           |
| `pensionschemeName`    | Name of the pension scheme.                   | string    | 60     |           |
| `StartAmount`          | Total pension assets as of the start date.    | decimal   |        |           |
| `tradingPortfolioId`   | Portfolio ID of the custodian.                | decimal   | 10     |           |

### `financialInformation.reportingPeriod`
_Reporting period information._

| Attribute Name                  | Definition                                                          | Data Type | Length | Code List |
| :------------------------------ | :------------------------------------------------------------------ | :-------- | :----- | :-------- |
| `startDate`                     | Start date of the data period or reference date.                    | date      |        |           |
| `endDate`                       | End date of the data period.                                        | date      |        |           |
| `tradeDate`                     | Desired trade date.                                                 | date      |        |           |
| `investmentOrderSettlementDate` | Date by which the investment order cycle must be settled.           | date      |        |           |
| `mutationValuationDate`         | Date for processing mutations per age group.                        | date      |        |           |
| `projectionDate`                | Date of the pension benefit projection.                             | date      |        |           |
| `instructionDate`               | Date of the instruction sent by the PUO.                            | date      |        |           |
| `unitValueEstimationDate`       | Date on which the preliminary unit value (investment pool) was determined. | date      |        |           |
| `participationValuationDate`    | Pricing date of the participation value (cohort pool).              | date      |        |           |
| `positionDate`                  | Date on which the positions in the investment administration were established. | date      |        |           |
| `valueDate`                     | Currency date.                                                      | date      |        |           |

### `financialTransaction.payment`
_Information about payments._

| Attribute Name                       | Definition                                 | Data Type | Length | Code List |
| :----------------------------------- | :----------------------------------------- | :-------- | :----- | :-------- |
| `refKey`                             | ID of the expected payment.                | string    | 70     |           |
| `amount`                             | Amount in currency / projected benefit.    | decimal   |        |           |
| `currencyType`                       | Currency code.                             | string    |        | ISOVAL    |
| `collectionAccountIban`              | IBAN of the debit account.                 | string    | 10     |           |
| `description`                        | Description of the transaction (payment).  | string    | 60     |           |
| `expectedPensionPaymentDate`         | Pension payment date.                      | date      |        |           |
| `hedgedExpectedPensionPaymentAmount` | Cash flow to be hedged.                    | decimal   |        |           |

### `party.creditor`
_The party that has a claim._

| Attribute Name                      | Definition                                | Data Type | Length | Code List |
| :---------------------------------- | :---------------------------------------- | :-------- | :----- | :-------- |
| `refKey`                            | Unique reference key assigned to an entity. | string    | 70     |           |
| `collectionAccountIban`             | IBAN of the credit account per scheme.    | string    | 10     |           |
| `collectionAccountInNameOf`         | Name of the counterparty per scheme.      | string    | 60     |           |
| `collectionAccountBic`              | Business Identifier Code (BIC) per scheme. | string    | 10     |           |
| `collectionAccountBicCorrespondent` | BIC correspondent per scheme.             | string    | 10     |           |

### `financialTransaction.cashflow`
_The sum of contributions and withdrawals on all cohorts._*

| Attribute Name     | Definition                                    | Data Type | Length | Code List |
| :----------------- | :-------------------------------------------- | :-------- | :----- | :-------- |
| `contributionAmount` | Sum of contributions.                         | decimal   |        |           |
| `contributionDate` | Date of receipt of the contribution.          | date      |        |           |
| `withdrawalAmount` | Sum of withdrawals.                           | decimal   |        |           |
| `withdrawalDate`   | Date by which funds for withdrawal are available. | date      |        |           |
| `netAmount`        | Net sum of contributions and withdrawals.     | decimal   |        |           |
| `netDate`          | Date on which the net cash flow is determined. | date      |        |           |

_*Note: The amount and date fields in `financialTransaction.cashflow` are optional. At least one pair must be used._

### `pension.cohort`
_Information on cohort (pension target audience) level._

| Attribute Name             | Definition                                      | Data Type     | Length | Code List |
| :------------------------- | :---------------------------------------------- | :------------ | :----- | :-------- |
| `refKey`                   | ID of the cohort.                               | string        | 70     |           |
| `description`              | Description of the cohort.                      | string        | 60     |           |
| `participationStatus`      | Status of the participants in a cohort.         | string        |        | ADNDNS    |
| `startAge`                 | Start age in months.                            | integer       |        |           |
| `endAge`                   | End age in months.                              | integer       |        |           |
| `reserveIndicator`         | Indicates if the cohort represents a reserve.   | boolean       |        |           |
| `reserveType`              | Type of reserve.                                | string        |        | AFDRES    |
| `reserveDescription`       | Description for "Other" reserve type.           | string        | 60     |           |
| `startAmount`              | Pension assets of the cohort at the start date. | decimal       |        |           |
| `netAmount`                | Net sum of contributions and withdrawals per cohort. | decimal       |        |           |
| `contributionAmount`       | Inflow to be invested by the fiduciary manager. | decimal       |        |           |
| `withdrawalAmount`         | Outflow to be invested by the fiduciary manager.| decimal       |        |           |
| `protectionReturnPercentage` | Achieved protection return as a percentage.     | Decimal (1E-12) |      |           |
| `excessReturnPercentage`   | Achieved excess return as a percentage.         | Decimal (1E-12) |      |           |
| `protectionReturnAmount`   | Achieved protection return in currency.         | decimal       |        |           |
| `excessReturnAmount`       | Achieved excess return in currency.             | decimal       |        |           |

### `pension.cohortPool`
_The pooled combination of investments (investment pools) for a cohort._

| Attribute Name                    | Definition                                           | Data Type | Length | Code List |
| :-------------------------------- | :--------------------------------------------------- | :-------- | :----- | :-------- |
| `refKey`                          | ID of the cohort pool.                               | string    | 70     |           |
| `cohortRef`                       | Reference to the cohort this pool belongs to.        | string    | 70     |           |
| `description`                     | Description.                                         | string    | 60     |           |
| `currencyType`                    | Currency of the cohort data.                         | string    |        | ISOVAL    |
| `inflowPremiumAmount`             | Premium contribution per cohort pool.                | decimal   |        |           |
| `inflowRebalanceAmount`           | Cash amount of rebalance transactions per cohort pool. | decimal   |        |           |
| `numberOfNewParticipations`       | New participations to be issued in the cohort pool.  | decimal   |        |           |
| `numberOfParticipations`          | Number of outstanding units (participations).        | decimal   |        |           |
| `numberOfRebalanceParticipations` | Rebalance participations per cohort pool.            | decimal   |        |           |
| `participationsSummedValueAmount` | Value per cohort pool (sum of participation value).  | decimal   |        |           |

### `investment.Pool`
_Investment pool / investment portfolio._

| Attribute Name                 | Definition                                   | Data Type | Length | Code List |
| :----------------------------- | :------------------------------------------- | :-------- | :----- | :-------- |
| `refKey`                       | ID of the investment pool per scheme.        | string    | 70     |           |
| `description`                  | Description.                                 | string    | 60     |           |
| `marketValueAmount`            | Market value.                                | decimal   |        |           |
| `unitsSummedValueAmount`       | Value per investment pool (unit value).      | decimal   |        |           |
| `preliminaryMarketValueAmount` | Preliminary market value of the portfolio.   | decimal   |        |           |
| `preliminaryUnitValueAmount`   | Preliminary unit value.                      | decimal   |        |           |
| `numberOfUnits`                | Number of units issued for the investment pool. | decimal   |      |           |
| `currencyType`                 | Currency of the pool.                        | string    |        | ISOVAL    |
| `dummyCashId`                  | ID for a dummy cash instrument.              | string    | 10     |           |
| `buySellId`                    | Buy/Sell indicator.                          | string    |        | sell; buy |
| `tradeQuantity`                | Number of units to be traded.                | decimal   |        |           |
| `unitPrice`                    | Unit value/price.                            | decimal   |        |           |
| `currencyExchangeRate`         | FX rate.                                     | integer   |        |           |

### `investment.portfolio`
_Investment portfolio._

| Attribute Name            | Definition                                       | Data Type     | Length | Code List |
| :------------------------ | :----------------------------------------------- | :------------ | :----- | :-------- |
| `refKey`                  | ID of the Investment Portfolio.                  | string        | 70     |           |
| `description`             | Description.                                     | string        | 60     |           |
| `startAmount`             | Total Market Value at the start of the period.   | decimal       |        |           |
| `netAmount`               | Net sum of contributions and withdrawals.        | decimal       |        |           |
| `endAmount`               | Total Market Value at the end of the period.     | decimal       |        |           |
| `returnPercentage`        | Achieved return as a percentage.                 | Decimal (1E-12) |      |           |
| `returnAmount`            | Achieved return in currency.                     | decimal       |        |           |
| `startExposureAmount`     | Allocation of pension assets to this portfolio.  | decimal       |        |           |
| `startExposurePercentage` | Relative share of `startExposureAmount`.         | decimal       |        |           |

### `investment.investmentDetails`
_An investment in either liquid or illiquid funds or pools thereof._

| Attribute Name         | Definition                                   | Data Type | Length | Code List |
| :--------------------- | :------------------------------------------- | :-------- | :----- | :-------- |
| `refKey`               | Identifier (e.g., ISIN or internal code).    | string    | 70     |           |
| `description`          | Name of the investment/fund/instrument.      | string    | 60     |           |
| `currencyType`         | Currency of the instrument.                  | string    |        | ISOVAL    |
| `numberOfUnits`        | Number of purchased units per instrument.    | decimal   |        |           |
| `numberOfHoldings`     | Number of holdings per instrument.           | decimal   |        |           |
| `localPrice`           | Price per instrument in original currency.   | decimal   |        |           |
| `localValueAmount`     | Total market value in original currency.     | decimal   |        |           |
| `Result`               | Unrealized result per instrument.            | decimal   |        |           |
| `accruedInterest`      | Accrued interest per instrument.             | decimal   |        |           |
| `poolPercentage`       | Weight in the portfolio per instrument.      | decimal   |        |           |
| `currencyExchangeRate` | FX rate per instrument.                      | decimal   |        |           |

### `financialTransaction.trade`
_Trading/ordering; Buying and selling._

| Attribute Name              | Definition                                       | Data Type | Length | Code List |
| :-------------------------- | :----------------------------------------------- | :-------- | :----- | :-------- |
| `tradeDate`                 | Desired trade date.                              | date      |        |           |
| `refKey`                    | Unique reference key assigned to an entity.      | string    | 70     |           |
| `adjustmentIndicator`       | Adjusted trade instruction.                      | boolean   | 1      |           |
| `buySellId`                 | Buy/Sell/Switch indicator.                       | string    | 3      | sell, buy, switch |
| `tradeAmount`               | Amount of the purchase in the investment's currency. | decimal |      |           |
| `tradeQuantity`             | Number of units to be traded.                    | decimal   |        |           |
| `tradePrice`                | Purchase price/rate.                             | decimal   |        |           |
| `switchType`                | Type of switch; one-day or sequential.           | string    |        | sequential, one-day |
| `financialInformationRef`   | On a switch, reference to the target identifier. | string    |        |           |
| `Counterparty`              | Transfer Agent; the party executing the trade.   | string    | 70     |           |
| `Broker`                    | Broker executing investment orders.              | string    | 70     |           |
| `interestAmount`            | Amount of applicable interest.                   | decimal   |        |           |
| `commissionAmount`          | Fee for executing the transaction.               | decimal   |        |           |
| `clearingBroker`            | Broker responsible for settlement.               | string    | 70     |           |
| `clearingBrokerCashAccount` | Cash account (IBAN) at the clearing broker.      | string    | 18     |           |

### `error.default`
_Error message._

| Attribute Name         | Definition                                   | Data Type | Length | Code List |
| :--------------------- | :------------------------------------------- | :-------- | :----- | :-------- |
| `refKey`               | Unique reference key assigned to an entity.  | string    | 70     |           |
| `errorCode`            | Error code type.                             | string    |        | ADNFTM    |
| `errorCodeExplanation` | Explanation of the error message.            | string    | 300    |           |

_See also the information about `error.default` in the SIVI All-Finance Standard._

### `document.default`
_Information about an attachment/document._

| Attribute Name  | Definition                               | Data Type | Length | Optional |
| :-------------- | :--------------------------------------- | :-------- | :----- | :------- |
| `refKey`        | Unique reference key assigned to an entity. | string    | 70     |          |
| `fileName`      | Name of the file for the attachment.     | string    | 60     |          |
| `fileExtension` | Extension of the file (e.g., pdf, csv, txt). | string    | 10     | pdf;csv;txt |

### `chunkMeta.default`
_"Chunking" (splitting large messages) into partial messages._

| Attribute Name        | Definition                                     | Data Type | Length | Code List |
| :-------------------- | :--------------------------------------------- | :-------- | :----- | :-------- |
| `currentChunkId`      | Unique reference (id) of the current chunk.    | string    | 70     |           |
| `chunkSequenceNumber` | Sequence number of the current chunk.          | integer   |        |           |
| `totalNumberOfChunks` | Total number of chunks the message is split into. | integer |      |           |
| `chunkFragmentPaths`  | Array of JMESPath references to the message fragments. | array |    |           |


## 6.4 Messages

The data exchange described in this document is supported by a set of 14 messages, supplemented by a feedback message. The messages are derived from the base message described below.

Below (in Figure 12) is an overview of the messages and the roles (sender/receiver) involved.

| Message Name | Type | PUO | FM | BA | ACB | BR |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: |
| 1. Vermogen (0001a) | SPR | from | to | | | |
| 2. Cashflow (0001b) | SPR | from | to | | | |
| 3. Pensioenprojectie (0001c) | SPR | from | to | | | |
| 4. Rendementsinformatie (00002) | SPR | to | | from | | |
| 5. Orderopdracht (00541) | FPR* | from | | | | to |
| 6. Orderconfirmation (00542) | FPR* | to | | | | from |
| 7. Mutatiesaldi (00551) | FPR** | from | | | to | |
| 8. Reconciliatie-informatie (00552a) | FPR** | | from | from | to | |
| 9. PUO-reconciliatie-informatie (00552b) | FPR** | from | | | to | |
| 10. Stuurinformatiebeleggingspools (00553) | FPR** | | to | | from | |
| 11. Rebalancinginformatie (00554) | FPR** | | to | | from | |
| 12. Waarde-informatie cohortenpool (00555a) | FPR** | from | to | | from | |
| 13. Waarde-informatie beleggingspool (00555b) | FPR** | to | to | | from | |
| 14. Betaalinformatie (00556) | FPR** | | to | | from | |
| Feedback Message*** | Beide | | | | | |

**Legend for the roles:**

*   **PUO:** Pension Administration Organizations
*   **FM:** Fiduciary Managers
*   **BA:** Investment Administrators / Asset Service Provider
*   **ACB:** Administrators of Cohort and Investment Pools
*   **BR:** Brokers / Transfer Agents

**Note:** Each receiving party receives its information directly from the sending party.

**Note:** Each receiving party/role gets its information directly from the sending party. In addition to the parties/roles mentioned in Figure 12, messages can also be sent to other parties, such as Liability-Driven Investment managers (LDIs). The transmission to unmentioned parties/roles is also direct. Received information is not forwarded to other parties.

The table below lists the message types and their meaning. In parentheses is the reference to the working group's final report: "Final Report Research Standard VB PUO (September 2023.pdf)".

*   **PMT** = `pensionMessageType` in AFD 2.0 (the descriptions of the message types are provided).
*   **TAG** = The identifier used for the message in the API.

| Type | Message Type | PMT/TAG | Description |
| :--- | :--- | :--- | :--- |
| **SPR** | **1a** (4.2.1.1) | Capital | **From PUO to Fiduciary Manager & Investment Administrator.**<br>On a periodic (expected monthly) basis, the fiduciary manager receives the total pension assets at the start of the period for a scheme. This can also be provided per cohort. With this information, the fiduciary manager can check alignment with the fund's policy and rebalance if necessary. |
| **SPR** | **1b** (4.2.1.3) | Cashflow | **From PUO to Fiduciary Manager & Investment Administrator.**<br>Periodically, the fiduciary manager receives the inflow and outflow for a scheme. This can be provided at a total level and per cohort. The cash flow includes premiums, value transfers, benefits, and shifts between cohorts. |
| **SPR** | **1c** (4.2.1.3) | PensionProjection | **From PUO to Fiduciary Manager & Investment Administrator.**<br>Periodically, the fiduciary manager receives the projected benefits per scheme and cohort based on the accrued assets. It also includes the cash flows to be hedged per scheme, calculated as the sum of weighted projected benefits per cohort. |
| **SPR** | **2** (4.2.2.) | ReturnOnInvestment | **From Investment Administrator to PUO.**<br>The PUO periodically receives information about the achieved investment return, including start and end values and the return percentage per portfolio. This is necessary for the PUO to allocate returns to participants, the solidarity reserve, etc. |
| **FPR** | **541** (5.4.1.) | Trade | **From PUO to Brokers/Transfer Agents/Order Desks.**<br>This message contains the minimum data set required to send an order or a switch to an order processing party. The PUO submits orders at the investment fund level. |
| **FPR** | **542** (5.4.2.) | Orderconfirmation | **From Brokers/Transfer Agents/Order Desks to PUO.**<br>The confirmation details of the order are returned from the order processing party to the PUO. |
| **FPR** | **551** (5.5.1) | BalanceAdjustments | **From PUO to Administrator of Cohort & Investment Pools.**<br>This first monthly information flow concerns netted mutations (purchases, sales, switches) per cohort pool. The administrator uses this to calculate cash flows for the investment pools and instruct the fiduciary manager. |
| **FPR** | **552a** (5.5.2) | InvestmentDetails | **Between Administrator, Fiduciary Manager, and Investment Administrator.**<br>The administrator receives monthly positions from the investment administrator and reconciles them with their own administration. |
| **FPR** | **552b** (5.5.2) | InvestmentDetailsPUO | **From Investment Pool Administrator to PUO.**<br>Additional information needed when the PUO also acts as the cohort pool administrator. This message provides the preliminary unit values of the investment pools to the PUO. |
| **FPR** | **553** (5.5.3) | ControlInformationInvestmentPools | **From Administrator to Fiduciary Manager.**<br>The administrator calculates participation values and combines them with mutations to estimate the cash effects on the investment pools. These effects are then sent to the fiduciary manager. |
| **FPR** | **554** (5.5.4) | RebalancingDetails | **From Administrator to Fiduciary Manager.**<br>The administrator rebalances the relevant cohorts based on the unit values at time T and sends all month-end transactions to the fiduciary manager. |
| **FPR** | **555a** (5.5.5) | ValueAmountCohortPool | **From PUO to Fiduciary Manager (when PUO administers cohort pools).**<br>The administrator (or PUO, if applicable) calculates and distributes the participation values of the cohort pools. |
| **FPR** | **555b** (5.5.5) | ValueAmountInvestmentPool | **Between Investment Administrator, Administrator, Fiduciary Manager, and PUO.**<br>The administrator calculates the unit value per unit in the investment pool and the participation value per participation in the cohort pool and distributes them to the PUO and fiduciary. |
| **FPR** | **556** (5.5.6) | PaymentDetailsCreditor | **From Administrator to Fiduciary Manager.**<br>At the beginning of the month, the administrator sends the payment instruction for withdrawals to the fiduciary manager. |
| **SPR/FPR** | Feedback | Feedback | **From the recipient of a content message (1-14) to the original sender.**<br>Provides feedback on errors or confirms the processability of a message. |

Unlike the Dutch manual, this documentation references the `MessageStructureView` folders on GitHub to illustrate the structure of each message. For example, the structure for **Message 11** can be viewed [here](https://github.com/dma61/VBPUOdsk/tree/main/VBPUO-Bericht_11._Rebalancinginformatie_(00554)/MessageStructureView).

Below is a diagram depicting the structure of **Message 11**:

![Message 11 Structure](https://raw.githubusercontent.com/dma61/VBPUOdsk/refs/heads/main/VBPUO-Bericht_11._Rebalancinginformatie_(00554)/MessageStructureView/20250630_083428-00554.svg)

These diagrams clearly visualize the relationships between entities. For detailed text-based specifications, please refer to the original Dutch manual.


## 6.5 Cross-Reference Attributes & Messages
please refer to the original Dutch manual.

---
| <div align="left">[< Previous: Chapter 5: Data Standard Setup](chapter-5-data-standard-setup.md)</div> | <div align="right">[Next: Chapter 7: Technical Specifications >](chapter-7-tech-specs.md)</div> |
|:---|---:|
