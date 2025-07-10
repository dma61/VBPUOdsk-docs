# Chapter 7: Technical Specifications
The technical data specifications are based on AFD 2.0 from SIVI AFS.

## 7.1 Messages & Schemes
Each message can concern multiple schemes (`pension.scheme`) but always relates to a single pension provider (`party.pensionProvider`).

## 7.2 Validations
Validation rules check for correct structure, data types, and mandatory fields.

## 7.3 JSON
The standard uses **JSON (RFC 8259)**. A non-mandatory attribute with no value should be omitted from the JSON message.

## 7.4 Transport / OpenAPI
### 7.4.1 OpenAPI Model
A standard **OpenAPI specification** defines the transport layer via a **RESTful API**. Communication is initiated by the sender (push model).

### 7.4.2 API Implementation and Backup
The deployment of the API is the responsibility of the providing party. Security is handled via mutual-TLS and API keys.

## 7.5 Versioning and Publication
The `afdDefinitionVersion` field links a message to a specific version of the JSON schema.

## 7.6 Processing Protocol for Partial Messages (Chunking)
For messages over ~4 MB, a chunking mechanism is provided.
*   **Principles**: Each chunk is a valid JSON message, and failure of one chunk invalidates the entire logical message.
*   **Splitting (Sender)**: The sender divides large arrays and adds metadata to a `chunkMeta` block.
*   **Reconstruction (Receiver)**: The receiver uses the `messageId` to reconstruct the original message.


---
[< Previous: Chapter 6: Functional Specifications](chapter-6-functional-specs.md)