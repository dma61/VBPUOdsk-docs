## 7.6 Processing Protocol for Sub-messages (Chunking)

This section describes the protocol for splitting (by the sender) and processing (by the recipient) of large messages. The use of sub-messages (chunks) is an optional mechanism applied when the size of a message exceeds the agreed limits.

### 7.6.1 Fundamental Principles of Chunking

Before describing the splitting and reassembly process, the following fundamental rules apply to the chunking mechanism:

- Validity per Chunk: Each chunk must be a self-contained, fully JSON-schema-compliant message. This means each chunk contains all mandatory "header" blocks, such as commonTechnical and commonFunctional.

- Shared messageId: All chunks that form part of one logical message share the exact same messageId in the commonTechnical block. This is the unique identifier of the overarching logical message.

- Mandatory chunking attributes: If the chunking.default entity is present to indicate that chunking is applied, all attributes within this entity are mandatory. This is essential for a robust and deterministic reconstruction process on the recipient's side.

- Integrity of the logical message: An error in a single chunk (e.g. a validation error or non-arrival of the chunk) renders the entire logical message invalid. The message must then be resubmitted in its entirety, with a new messageId.

### 7.6.2 Splitting a Large Message (Sender Side)

**1. Determining the Need**  
Splitting is required when a message exceeds the agreed maximum size (default: 4 MB). The sender is responsible for correctly dividing the data.

**2. The Splitting Process**  
The sender creates multiple chunks by distributing data from large, repeating arrays (such as the list of cohorts). Each chunk receives a chunking block with the appropriate metadata (chunkSequenceNumber, totalNumberOfChunks, etc.) and the chunkFragmentPaths describing the contents of that specific chunk.

**3. Use of JMESPath in chunkFragmentPaths**  
The chunkFragmentPaths field contains the essential instructions for the recipient to correctly reconstruct the original message. The JMESPath can indicate a specific range (slice) (e.g. pension\[0:100\]), which guarantees that the recipient can place the data back in the exact correct order, even if the chunks are received out of order.

### 7.6.3 Processing Received Chunks (Recipient Side)

**1. The Reconstruction Process**

The recipient uses the shared messageId to collect chunks.

- Start with the First Chunk: The chunk with chunkSequenceNumber: 1 serves as the basis or 'template' for the reconstruction.

- Place Data Fragments: For all subsequent chunks, data fragments are placed at the correct position in the template, guided by the chunkFragmentPaths.

- Determine Completeness: The message is complete when the number of received chunks equals totalNumberOfChunks.

**2. Processing Strategies**  
After conceptual completeness, the recipient may choose:

- Reconstruct-first (Batch approach): Build the complete message in memory and validate it afterwards.

- Streaming processing (Direct processing): Store data fragments per chunk directly and perform overarching validations later on the database.

**3. Error Handling and Incompleteness**

The integrity of the complete logical message is crucial.

- If a single chunk fails (for example due to a technical validation error, or if it is not received within a certain time), the entire logical message is considered failed and unprocessable.

- In that case the sender, after possible consultation, must resubmit the complete message with a new messageId, split into a new set of chunks.
