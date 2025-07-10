# Chapter 7: Technical Specifications

            ## 7.1-7.3 Messages, Validations, and JSON
            Each message concerns one pension provider but can span multiple schemes. Validations check structure, data types, and mandatory fields. The standard uses **JSON (RFC 8259)**. A non-mandatory attribute without a value should be omitted from the message.

            ## 7.4 Transport / OpenAPI
            A standard **OpenAPI specification** defines the transport layer via a **RESTful API**. Communication is initiated by the sender (push model). The standard only supports this API; other exchange methods are out of scope. Security is handled via mutual-TLS, API keys, and optional digital signatures.

            ## 7.5 Versioning and Publication
            The `afdDefinitionVersion` field links a message to a specific version of the JSON schema. Releases on GitHub are tagged, but this tag is not part of the message payload.

            ## 7.6 Processing Protocol for Partial Messages (Chunking)
            For messages over ~4 MB, a chunking mechanism is provided.
            *   **Principles**: Each chunk is a valid JSON message, all chunks share a `messageId`, and failure of one chunk invalidates the entire logical message.
            *   **Splitting (Sender)**: The sender divides large arrays and adds metadata to a `chunkMeta` block in each chunk.
            *   **Reconstruction (Receiver)**: The receiver uses the `messageId` to collect chunks and reconstructs the original message using `chunkFragmentPaths`.

---
<div style='display: flex; justify-content: space-between;'><div>[< Previous: Chapter 6: Functional Specifications](chapter-6-functional-specs.md)</div><div></div></div>