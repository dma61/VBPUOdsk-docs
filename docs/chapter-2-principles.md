# Chapter 2: Principles
This chapter discusses the most important principles for the development, setup, and governance of the standard.

## 2.1 Reason
With the introduction of the Wtp, information needs will change and the frequency of exchange will increase. For the solidarity premium scheme (SPR), an entirely new data stream is required for both accumulation and payout phases. For the flexible premium scheme (FPR), the information need will largely align with current 'defined contribution' schemes.

> ## PREAMBLE: PRINCIPLES OF STANDARDIZATION VBPUO
>
> The purpose of standardization is seamless and efficient information exchange between all parties in the chain.  
> The VBPUO standard is based on the following principles:
>
> - **Pragmatism and flexibility**  
>   The standard is not a requirement for uniformity, but a framework for interoperability.  
>   Chain partners can retain their own internal processes and systems.  
>   The focus is on streamlining external communication.
>
> - **Interoperability as the ultimate goal**  
>   The value of the standard becomes evident in practice. The test: an organization must be able to switch smoothly to another chain partner, without significant adjustments to the data interface.
>
> - **Manageable degrees of freedom**  
>   Flexibility is not unlimited. For predictability and reliability, the allowed variations are explicitly defined and deliberately limited.
>
> - **Supported by the chain**  
>   Adjustments and variations are not one-sided. Broad support is required to prevent fragmentation and to sustainably preserve the value of the standard.
>
> *Thus, the VBPUO standard remains a shared instrument for efficiency, predictability, and future-proof cooperation within the chain.*

## 2.2 Out of Scope

The following aspects are out of scope:

*   **Contractual agreements** regarding the overall asset management process.
*   **Existing processes** that do not fundamentally change, such as reconciliation between the fiduciary manager and the investment administrator.
*   **Information used by only one party** in the chain.
*   **Policy documents** like strategic investment plans.
*   **Information on costs**: It is expected that existing processes for compiling the DNB annual statement J402 will continue to form the basis for this.
*   **"Lookthrough" information**: Ad hoc requests for details on underlying investments are not part of regular exchange.
*   **Specifics for insurer-based premium-benefit agreements**.
*   **Periodicity of the exchange**: This is flexible and agreed upon by the parties.
*   **Task/Role division**: The governance model is not prescribed by the standard.

## 2.3 Principles of Data Exchange
*   The data standard is usable for **any governance model**.
*   An independent investment administrator receives the **same information** as the fiduciary manager to ensure independent reporting.
*   The fiduciary manager receives the necessary information to invest collective assets according to the investment policy.
*   The pension administration organization provides participants with insight into their pension assets.
*   Parties receive their data **directly from the sending party**.
*   **Once-accepted messages are not unilaterally corrected**. If a sender discovers an error, coordination with the recipient is mandatory before sending a corrected message.

## 2.4 Clarification of Principles
*   **Data Model**: Contains only the data necessary for the exchange.
*   **Roles (not prescriptive)**: The roles described are illustrative; parties can combine or separate functions.
*   **Periodicity**: The mentioned monthly frequency is an example, not a requirement.
*   **Language**: The report is in Dutch, but variable names in the standard are in English for international understanding.

## 2.5 - 2.8 Technology, Governance, and Transport
### Technology
The technical implementation uses **RESTful Web services** and **JSON**, conforming to **AFD 2.0**. Message processing is asynchronous. Security is handled via **mutual-TLS** and digital signatures.

### Handling Large Messages (Chunking)
For messages over ~4 MB, a "chunking" mechanism is provided to split them into smaller, valid JSON parts, which are reassembled by the recipient.

### Transport
The standard supports a **RESTful API/webservice**. Other solutions are considered bilateral and are not supported.

### Governance and Releases
The standard is owned by the Pension Federation and managed by SIVI. It follows an annual release cycle (prerelease in June, final in September), with continuous development on GitHub. The two preceding annual releases remain supported.

---
| <div align="left">[< Previous: Chapter 1: Introduction](chapter-1-introduction.md)</div> | <div align="right">[Next: Chapter 3: SPR Processes >](chapter-3-spr-processes.md)</div> |
|:---|---:|
