# Chapter 7: Technical Specifications
The technical data specifications are based on AFD 2.0 from SIVI AFS. This chapter provides an explanation.

## 7.1 Messages & Schemes
Each message can concern multiple schemes (`pension.scheme`). However, it always pertains to a single `party.pensionProvider`. The transmission is per message, and that message thus contains 1 `pension.provider` and 1 or more `pension.scheme`'s.

## 7.2 Validations
The following validation rules can be implemented using the technical specifications:

*   Check if the message structure is correct;
*   Verify the data type (including numbers, strings);
*   Check for minimum and maximum values;
*   Validate the field length;
*   Check for the presence of mandatory entities and attributes;
*   Check the number of repetitions of entities;
*   Ensure the use of allowed codes from code lists.

*N.B.: Relational checks (validation rules between different data elements) are still in development. See also the JSON schemas.*

## 7.3 JSON
The SIVI AFS team follows the specifications below for AFD 2.0 in combination with JSON (derived from Forum Standaardisatie):

| Concern | Description |
| :--- | :--- |
| **Full Name** | JavaScript Object Notation |
| **Version** | RFC8259, December 2017 |
| **Specification Document** | [JSON Specification Document](https://datatracker.ietf.org/doc/html/rfc8259) |
| **Managing Organization** | Internet Engineering Task Force (IETF) |
| **Functional Scope** | Object notation for exchanging data structures, for example, in web applications that retrieve data asynchronously from a web server. |
| **Typing** | Exchange of data structures |
| **Benefit** | JSON (JavaScript Object Notation) is a subset of the JavaScript programming language. The simplicity of JSON has led to its great popularity, especially as a 'light' alternative to XML. |
| **Operation** | JSON is a format for storing and sending data, similar to XML. It is used for exchanging data structures, particularly in web applications. The standard is aimed at efficient programming and has a compact notation. |
| **Tools** | Various online JSON validators and tools are available, also for different programming platforms. More information about the standard can also be found in publications from ECMA International. |

**Guideline:** If a non-mandatory attribute has no value, the attribute should be completely omitted from the JSON message. This is a recommended practice according to JSON conventions.

## 7.4 Transport / OpenAPI

### 7.4.1 OpenAPI Model
Since early 2024, work has been done on a standard for the transport of messages. A number of PUOs and asset managers, in collaboration with SIVI, have taken steps to develop an OpenAPI specification within the previously outlined technical contours.
This effort aimed to support all parties that will implement the RESTful API and to promote its uniform application. The specification can be found on GitHub. The proposed OpenAPI specification helps parties to unambiguously exchange the 14 message structures, for both SPR and FPR. In addition to the 14 content-based messages, a feedback message has also been realized to respond to the content-based messages.

The API acts as a digital gateway, through which the various PUO and asset management parties can receive data. Communication is initiated by the sending party (push-model); the sending party delivers the messages to the receiving party without the latter having to actively request them. The specification begins with general information, stating the name, description, and version of the API.

The core of the API describes the specific services that are available. For each service, a clear path is defined where messages can be delivered. This includes, for example, supplying information or performing certain actions. Each path provides a description of what the service does and how it can be used.

Please note that in practice, not every party will offer all services from the OAS. For instance, parties that only handle SPR can, in addition to the feedback message, offer the SPR messages 1, 2, 3, and 4.

Furthermore, the specification contains reusable building blocks, such as messages and entities. This ensures that the API is consistent and easy to understand and use. The reuse of these messages and entities simplifies development and reduces the chance of errors.

To ensure the completeness and integrity of the messages, a mechanism has been introduced that allows for checking for changes during transport. This is the `x-jws-signature` header, which contains a digital signature of the payload. This provides a reliable basis for parties to trust that received messages exactly match what was sent. The use of this mechanism is an option, not a requirement. Parties can make different choices.

**Important:** The standard only supports the OAS API; other forms of data exchange are not supported. This means that all communication between parties must proceed according to the specified OpenAPI specification, and alternative methods fall outside the scope of the standard.

**API Security Measures:**

| Security Measure | Description |
| :--- | :--- |
| **Authentication with API key** | Each request must contain a valid API key in the `x-api-key` header. |
| **OAuth 2.0 Client Credentials Flow** | The API uses OAuth 2.0. Clients must obtain an access token using their client ID and secret. Specific scopes are used to control access to different API functions. |
| **Digital Signatures with x-jws-signature (option)** | If used, each request contains a digital signature of the payload in the `x-jws-signature` header to verify message integrity. |
| **Encrypted Communication via HTTPS** | All communication is via HTTPS, ensuring data encryption during transmission. |

### 7.4.2 API Implementation and Backup
The deployment and operational maintenance of the APIs are the responsibility of the party offering the API and fall outside the scope of this standard. Temporary outages of the API data transport facility may occur. The risk of this is lower with an approach where multiple replicas of the API run simultaneously (on different environments and/or locations). Ultimately, this is a cost-benefit analysis; guaranteeing 99.9% uptime is more expensive than a 98% uptime guarantee.

The assumption is that any outage will always be short-lived. In exceptional cases, email can serve as a "backup" transport mechanism.

## 7.5 Message Composition, Versioning, and Publication
### 7.5.1 Explanation of using "afdDefinitionVersion"
`afdDefinitionVersion` is filled with the version number (from the "Schema Name") of the VBPUO JSON schema. The VBPUO JSON schema is maintained by SIVI using "AFD Online Samenstellen (AOS)" with the following metadata:

| AOS Schema Metadata | Values (example) |
| :--- | :--- |
| SIVI community | AFD 2.0 |
| Message Type: | Protocol PUO Asset Management |
| Domain: | General |
| Schema Name: | VBPUO-###.## |

In the (AOS) VBPUO schema, the 14 VBPUO message structures are defined as "functions," for example, the function: "Bericht_9._PUO-reconciliatie-informatie_(00552b)". For each "function," three JSON schemas are subsequently generated and published ("committed") to GitHub. These JSON schemas serve the following purposes:

#### Table 2: JSON Schemas (from AOS) Explained

| Purpose | Detailed Description | Example Filename |
| :--- | :--- | :--- |
| **Message Structure** | Defines the structure, mandatory elements, and field validations, with internal and external references to ensure data consistency and standardization. | `VBPUO-001.00-Bericht_1._Vermogen_(0001a).json` |
| **Code Lists/Tables** | Defines the code lists (e.g., pension provider and currency codes) used as references in the JSON schema for field validation. | `VBPUO-001.00-Bericht_1._Vermogen_(0001a)-afdCodelists.json` |
| **Relational Checks** | Defines the rules for relational checks within the JSON schema to ensure the validity and consistency of data relationships. | `VBPUO-001.00-Bericht_1._Vermogen_(0001a)-validationRules.json` |

### 7.5.1.1 Version Number / `afdDefinitionVersion` in a GitHub release
The version number of an AOS schema must be included in every message that is sent. This number can be found in the Message Structure as a constant under `afdDefinitionVersion`.

The JSON Schemas can be found under this number at [https://portal.sivi.org/organisationschemas](https://portal.sivi.org/organisationschemas). The messages created with this schema – which are defined as functions within the VBPUO schema – are published on GitHub.

### 7.5.2 Publication on GitHub: Version Number and Tag
When releasing on GitHub, the release gets a Name and a Tag (e.g., "2024_Juli" with tag `v1.1.0`). All JSON schemas, example messages, and the OAS fall under that release/tag. The GitHub release name and tag number are not found in the payload of the messages.

## 7.6 Processing Protocol for Partial Messages (Chunking)

This section describes the protocol for splitting (by the sender) and processing (by the receiver) of large messages. The use of partial messages (chunks) is an optional mechanism that is applied when the size of a message exceeds the agreed-upon limits.

### 7.6.1 Fundamental Principles of Chunking
Before we describe the splitting and merging process, the following fundamental rules apply to the chunking mechanism:

*   **Validity per Chunk:** Each chunk must be a standalone, fully JSON-schema-compliant message. This means that each chunk contains all mandatory "header" blocks, such as `commonTechnical` and `commonFunctional`.
*   **Shared `messageId`:** All chunks that are part of one logical message share the exact same `messageId` in the `commonTechnical` block. This is the unique identifier of the overarching, logical message.
*   **Mandatory `chunkMeta` attributes:** If the `chunkMeta.default` entity is present to indicate that chunking is being used, all attributes within this entity are mandatory. This is essential for a robust and deterministic reconstruction process on the receiver's side.
*   **Integrity of the logical message:** An error in a single chunk (e.g., a validation error or the non-arrival of the chunk) invalidates the entire logical message. The message must then be resubmitted in its entirety, with a new `messageId`.

### 7.6.2 Splitting a Large Message (Sender's Side)

#### 1. Determining the Necessity
Splitting is required when a message exceeds the agreed-upon maximum size (default: 4 MB). The sender is responsible for correctly partitioning the data.

#### 2. The Splitting Process
The sender creates multiple chunks by distributing the data from large, repeating arrays (such as a list of cohorts). Each chunk is assigned a `chunkMeta` block with the appropriate metadata (`chunkSequenceNumber`, `totalNumberOfChunks`, etc.) and the `chunkFragmentPaths` that describe the content of that specific chunk.

#### 3. Use of JMESPath in `chunkFragmentPaths`
The `chunkFragmentPaths` field contains the essential instructions for the receiver to correctly reconstruct the original message. The JMESPath can specify a particular range (slice), for example `pension[0:100]`, which guarantees that the receiver can place the data back in the exact correct order, even if the chunks are received in a different sequence.

### 7.6.3 Processing Received Chunks (Receiver's Side)

#### 1. The Reconstruction Process

The receiver uses the shared `messageId` to collect the chunks.
*   **Start with the First Chunk:** The chunk with `chunkSequenceNumber: 1` serves as the base or 'template' for the reconstruction.
*   **Place Data Fragments:** For all subsequent chunks, the data fragments are placed into the correct position within the template, guided by their respective `chunkFragmentPaths`.
*   **Determine Completeness:** The message is considered complete when the number of received chunks equals the `totalNumberOfChunks`.

#### 2. Processing Strategies

Once conceptually complete, the receiver can choose one of the following strategies:
*   **Reconstruct-first (Batch approach):** Build the entire message in memory and then validate it.
*   **Streaming processing (Direct processing):** Save data fragments from each chunk directly and perform overarching validations later on the database.

#### 3. Error Handling and Incompleteness

The integrity of the complete logical message is crucial.

*   If a single chunk fails (for example, due to a technical validation error, or if it is not received within a certain timeframe), the entire logical message is considered failed and unprocessable.
*   In such a case, the sender must, after potential consultation, resubmit the entire message with a new `messageId`, split into a new set of chunks.

---
| <div align="left">[< Previous: Chapter 6: Functional Specifications](chapter-6-functional-specs.md)</div> | <div align="right"></div> |
|:---|---:|

*   
