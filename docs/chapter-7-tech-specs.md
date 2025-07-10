# Chapter 7: Technical Specifications

            The technical data specifications are based on AFD 2.0 from SIVI AFS.

            ## 7.1 Messages & Schemes
            Each message can concern multiple schemes (`pension.scheme`) but always relates to a single pension provider (`party.pensionProvider`).

            ## 7.2 Validations
            Validation rules check for correct structure, data types, mandatory fields, and allowed codes. Relational checks are still under development.

            ## 7.3 JSON
            The standard uses **JSON (RFC 8259)**. A non-mandatory attribute with no value should be completely omitted from the JSON message.

            ## 7.4 Transport / OpenAPI
            ### 7.4.1 OpenAPI Model
            A standard for transporting messages has been developed using an **OpenAPI specification**. This supports all parties implementing the RESTful API. Communication is initiated by the **sender (push model)**. The standard only supports this API; other forms of data exchange are not supported.

            ### 7.4.2 API Implementation and Backup
            The deployment and operation of the API are the responsibility of the providing party. Security is handled via mutual-TLS, API keys, and optional digital signatures. Email can serve as a "backup" transport mechanism.

            ## 7.5 Message Composition, Versioning, and Publication
            The `afdDefinitionVersion` field in a message must be filled with the version number of the VBPUO JSON schema. Releases on GitHub are tagged, but this tag is not part of the message payload itself.

            ## 7.6 Processing Protocol for Partial Messages (Chunking)
            This protocol describes how to split (by the sender) and process (by the receiver) large messages that exceed a pre-agreed size limit (default: 4 MB).
            *   **Principles**: Each chunk must be a valid JSON message, all chunks of a single logical message share the same `messageId`, and failure of one chunk invalidates the entire logical message.
            *   **Splitting (Sender)**: The sender creates multiple chunks by dividing the data from large, repeating arrays. Each chunk gets a `chunkMeta` block with metadata.
            *   **Reconstruction (Receiver)**: The receiver uses the shared `messageId` to collect chunks and reconstructs the original message using `chunkFragmentPaths`.


---
<div style='display: flex; justify-content: space-between;'><div>[< Previous: Chapter 6: Functional Specifications](chapter-6-functional-specs.md)</div><div></div></div>