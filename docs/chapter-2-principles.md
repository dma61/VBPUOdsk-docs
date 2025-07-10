# Chapter 2: Principles
            This chapter discusses the most important principles for the development, setup, and governance of the standard.

            ## 2.1 Reason
            The Future Pensions Act (Wtp) intensifies the need for standardized information exchange between pension administrators and asset managers. For the solidarity premium scheme (SPR), a new data stream is required. For the flexible premium scheme (FPR), the needs are similar to current DC schemes but will align with the SPR during the collective payout phase.

            ## 2.2 Out of Scope
            The standard does not cover:
            *   Contractual agreements between parties.
            *   Existing, unchanged processes (e.g., internal reconciliation).
            *   Information used by only one party.
            *   Policy documents (investment policy, etc.).
            *   Information on costs (which will likely follow existing J402 processes).
            *   "Lookthrough" information on underlying assets.
            *   Specifics for insurer-based premium-benefit agreements.
            *   The periodicity of exchange, which is flexible.
            *   The specific role division or governance model between parties.

            ## 2.3 Principles of Data Exchange
            *   The standard is usable for **any governance model**.
            *   An independent investment administrator receives the **same information** as the fiduciary manager.
            *   The fiduciary manager receives the necessary information to invest according to the **policy frameworks**.
            *   The pension administrator provides participants with **insight into their assets**.
            *   Parties receive their data **directly from the source**.
            *   **Once-accepted messages are not unilaterally corrected**; any correction requires bilateral agreement.

            ## 2.4 Clarification of Principles
            *   **Data Model**: Contains only the data necessary for the exchange.
            *   **Roles (not prescriptive)**: The roles described are illustrative; parties can combine roles.
            *   **Periodicity**: The mentioned monthly frequency is an example, not a requirement.
            *   **Costs**: Assumed to build upon existing processes (e.g., J402 DNB annual statement).
            *   **Language**: The standard is in Dutch, but variable names are in English for international understanding.

            ## 2.5 - 2.8 Technology, Governance, and Transport
            The technical implementation uses **RESTful Web services** and **JSON**, conforming to **AFD 2.0**. Message processing is asynchronous. Security is handled via **mutual-TLS** and digital signatures.

            **Handling Large Messages (Chunking)**: A chunking mechanism is provided for messages over ~4 MB.

            **Transport**: The standard supports a **RESTful API/webservice** based on the SIVI-API framework.

            **Governance and Releases**: The standard follows an annual release cycle (prerelease in June, final in September), with continuous development on GitHub. The two preceding annual releases remain supported.


---
<div style='display: flex; justify-content: space-between;'><div>[< Previous: Chapter 1: Introduction](chapter-1-introduction.md)</div><div>[Next: Chapter 3: SPR Processes>](chapter-3-spr-processes.md)</div></div>