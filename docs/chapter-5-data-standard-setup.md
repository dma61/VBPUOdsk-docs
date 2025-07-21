# Chapter 5: Approach/Setup of the Data Standard

This chapter explains how the message specifications are derived. The steps to arrive at the functional specifications are:

1.  **Create descriptions of the processes and information flows.**
2.  **Create a list of entities and associated attributes.**
3.  **Determine the basic structure of the messages.**
4.  **Indicate which messages are needed.**
5.  **Create a cross-reference table** between the basic structure and the messages.

## 5.1-5.5 The Process
The process starts with describing the business processes (as done in Chapters 3 and 4). From these descriptions, the required data elements (entities and attributes) are identified. These are then organized into a hierarchical base structure. Specific messages are defined as subsets of this base structure. A cross-reference table (see section 6.5) shows which attributes are used in which message.

## 5.6 Relationship with SIVI AFS
This standard is built using components from the **SIVI All Finance Standard (AFD 2.0)**. AFD 2.0 is an English-language standard that provides building blocks (entities, attributes, code lists) for the financial sector. Where necessary, this standard proposes new elements to be added to AFD 2.0. The use of JSON is a core principle of AFD 2.0.

---
| <div align="left">[< Previous: Chapter 4: FPR Processes](chapter-4-fpr-processes.md)</div> | <div align="right">[Next: Chapter 6: Functional Specifications >](chapter-6-functional-specs.md)</div> |
|:---|---:|
