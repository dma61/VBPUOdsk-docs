## 7.4 Transport / OpenAPI

### 7.4.1 OpenAPI Model

Starting in early 2024, work began on a standard for the transport of messages. A number of PUOs and asset managers, in collaboration with SIVI, took steps in developing an OpenAPI specification within the previously outlined technical framework.

This effort aimed both to support all parties that will implement the RESTful API and to promote uniform application. The specification can be found on [GitHub](https://github.com/Stichting-SIVI/VBPUOdsk/tree/main/VBPUO%20OAS%20(Open%20API%20Specificatie)). The proposed OpenAPI specification helps parties exchange message structures uniformly, for both SPR and FPR. In addition to the content messages, a feedback message has been implemented to respond to content messages.

The API functions as a digital service point through which the various PUO and asset management parties can receive data. **Communication takes place on the initiative of the sending party (push model); the sending party delivers messages to the receiving party without the latter actively requesting them.** The specification starts with general information containing the name, description and version of the API.

The core of the API describes the specific services available. For each service, a clear path is defined on which messages can be delivered. This includes, for example, providing information or performing certain actions. Each path provides a description of what the service does and how it can be used.

Note that in practice, not every party will offer all services from the OAS. Parties that only handle SPR can, for example, offer only the feedback message and SPR messages 1, 2, 3 and 4.

Furthermore, the specification contains reusable building blocks, such as messages and entities. This ensures the API is consistent and easy to understand and use. By reusing these messages and entities, development becomes simpler and the chance of errors is reduced.

To safeguard the completeness and integrity of messages, a mechanism has been introduced that enables verification of modifications during transport. This involves a so-called x-jws-signature header, which contains a digital signature of the payload. This provides a reliable basis for parties to trust that received messages exactly match what was sent. The use of this mechanism is optional, not mandatory. Parties may make alternative choices.

**It is important that the standard exclusively supports the OAS API; <u>other forms of data exchange are not supported</u>.** This means that all communication between parties must follow the specified OpenAPI specification, and alternative methods fall outside the scope of the standard.

**API Security Measures:**

The main security measures are as follows:

| **Security Measure** | **Description** |
|----|----|
| Authentication with API key | Each request must contain a valid API key in the x-api-key header. This prevents unauthorized access to the API. |
| OAuth 2.0 Client Credentials Flow | The API uses OAuth 2.0 for authentication and authorization. Clients must obtain an access token via the token endpoint using their client ID and secret. |
|  | Specific scopes are used to control access to various API functions, ensuring that only authorized actions can be performed. |
| Digital Signatures with x-jws-signature (optional) | When this mechanism is used, each request contains a digital signature of the payload in the x-jws-signature header. This enables the recipient to verify that the message has not been modified during transport. |
| Encrypted Communication via HTTPS | All communication takes place via HTTPS, which provides encryption of data during transmission and protection against interception. |

### 7.4.2 API Implementation and Backup

Deployment and operational maintenance of the APIs is the responsibility of the party offering the API and falls outside the scope of the standard. (Temporary) outage of the API data transport facility may occur. The risk of this is lower with an approach in which multiple replicas of the API run simultaneously (in different environments and/or locations). Ultimately, this is a cost/benefit trade-off; guaranteeing 99.9% uptime is more costly than a 98% uptime guarantee.

The assumption is that outages will always be short-lived. In exceptional cases, email may serve as a "backup" transport mechanism.
