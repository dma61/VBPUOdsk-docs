# Chapter 7: Technical Specifications
The technical data specifications are based on AFD 2.0 from SIVI AFS.

## 7.1 Messages & Schemes
Each message can concern multiple schemes (`pension.scheme`) but always relates to a single pension provider (`party.pensionProvider`).

## 7.2 Validations
Validation rules can be implemented to check for correct message structure, data types, mandatory fields, number of repetitions, and use of allowed codes from code lists. Relational checks (validation rules between different data elements) are still under development.

## 7.3 JSON
The standard uses **JSON (JavaScript Object Notation)**, as specified in **RFC 8259**. It's a lightweight format for structuring data.
*Guideline: If a non-mandatory attribute has no value, it should be completely omitted from the JSON message. This is a recommended practice according to JSON conventions.*

## 7.4 Transport / OpenAPI
### 7.4.1 OpenAPI Model
A standard for transporting messages has been developed using an **OpenAPI specification**. This supports all parties implementing the RESTful API and promotes uniform application. The API acts as a digital gateway. Communication is initiated by the **sender (push model)**. To guarantee integrity, a digital signature of the payload can be included in an `x-jws-signature` header (optional). The standard only supports the OpenAPI API; other forms of data exchange are not supported.

### 7.4.2 API Implementation and Backup
The deployment and operation of the API are the responsibility of the providing party. The standard assumes that any downtime will be brief. Email can serve as a "backup" transport mechanism in exceptional cases. The main security measures are authentication via API key, authorization via OAuth 2.0, optional digital signatures, and encrypted communication via HTTPS.

## 7.5 Message Composition, Versioning, and Publication
### 7.5.1 Explanation of using "afdDefinitionVersion"
The `afdDefinitionVersion` field in a message must be filled with the version number of the VBPUO JSON schema used to create it. These schemas are maintained in SIVI's "AFD Online Samenstellen (AOS)" tool.

### 7.5.2 Publication on GitHub Version Number and Tag
When releasing on GitHub, the release gets a Name and a Tag (e.g., "2024_Juli" with tag `v1.1.0`). These are not present in the message payload itself.

## 7.6 Processing Protocol for Partial Messages (Chunking)
This protocol describes how to split (sender) and process (receiver) large messages that exceed a pre-agreed size limit (default: 4 MB).
*   **Principles**: Each chunk must be a standalone, valid JSON message. All chunks of a single logical message share the same `messageId`. Failure of one chunk invalidates the entire logical message.
*   **Splitting (Sender)**: The sender creates multiple chunks by dividing the data from large, repeating arrays. Each chunk gets a `chunkMeta` block with metadata.
*   **Reconstruction (Receiver)**: The receiver uses the shared `messageId` to collect chunks and reconstructs the original message using `chunkFragmentPaths`.


---
<div style='display: flex; justify-content: space-between;'><div>[< Previous: Chapter 6: Functional Specifications](chapter-6-functional-specs.md)</div><div></div></div>