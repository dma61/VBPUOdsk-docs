# 1 Introduction

**In this introduction we discuss the context, purpose and target audience of this manual. We also present (in some detail) the structure of the manual.**

## 1.1 Context

**Final Report**

In early September 2023, the final report ''[Results of research: Standard for data exchange pension administration & asset management parties''](https://www.pensioenfederatie.nl/cms/streambin.aspx?documentid=18380) was published.

With the introduction/implementation of the Future Pensions Act (Wtp), tighter alignment between fund assets and collective administration of personal pension assets is necessary. This increases the frequency of the required information exchange. In current practice, pension administration organizations and asset management parties arrange information exchange among themselves. Due to the intensification of information exchange, standardization of this exchange is desirable.

The aforementioned final report describes the functional data needed for the exchange, the information flows and the, partly dependent, participant communication.

The data and information flows have been elaborated for both the Solidarity Premium Scheme (SPR) and the Flexible Premium Scheme (FPR).

The final report is based on contributions from various organizations, including APG, AZL, Caceis, Capgemini, H&C, Van Lanschot Kempen IM, MN, Pensioenfederatie, SIVI and TKP. Through a consultation round, various other administration organizations, fiduciary managers, custodians and pension funds were also involved. This consultation round has been completed and the input from it has been incorporated.

**Continuation**

The final report is translated by SIVI into a data standard based on AFD 2.0 from SIVI AFS. This data standard includes a base message from which we derived the original 14 messages. The messages are exchanged via REST API endpoints. In addition to those messages, a Feedback Message is available for status feedback. For asynchronous processing, the feedback message is the mandatory mechanism for status and error reporting (see §4.7). The message set has since been modified, although the message names have been retained.

**Governance and Management**

The standard represents a shared interest of pension administration and asset management for which administrative and substantive management must be assigned. After the introduction of the standard, new requirements will arise that may or may not need to be incorporated into the standard.

It has been agreed that:

- Ownership of the standard rests with the Pensioenfederatie.

- Substantive and administrative management around the standard will be established.

- The standard is managed by management organization SIVI.

- An advisory group supports the management and possible further development.

## 1.2 Purpose

This manual provides an explanation of the standard for data exchange between asset management and pension administration. The manual provides:

- Analysts and developers a guide to implement (or have implemented) the standard;

- Stakeholders insight into the management of the standard.

## 1.3 Target Audience

This manual is intended for consultants, analysts and developers involved in the implementation of the standard for data exchange between asset management and pension administration parties.

## 1.4 Structure

### 1.4.1 Notation of Attribute Names

In the descriptive texts of this manual you will encounter dual naming for data fields, in the following format:

technicalName (Functional Name)

- **technicalName**: This is the **definitive, technical attribute name** conforming to the SIVI AFD 2.0 standard, displayed in a monospace font. This is the name that must actually be used in the JSON messages.

- **(Functional Name)**: This is the **original, functional name** as used during the requirements and design phase. This name is temporarily mentioned between parentheses and in a slightly smaller, normal font to enhance recognition during the transition. In a future release of this manual, this functional name will be removed.

The complete Translation Table from functional attributes to AFD 2.0 attributes is included in 8.4.

<table>
<colgroup>
<col style="width: 13%" />
<col style="width: 86%" />
</colgroup>
<thead>
<tr>
<th>Chapter</th>
<th>Contents</th>
</tr>
</thead>
<tbody>
<tr>
<th>1</th>
<td><p><strong>Introduction</strong></p>
<p>In this introduction we discuss the context, purpose and target audience of this manual. We also present (in some detail) the structure of the manual.</p></td>
</tr>
<tr>
<th>2</th>
<td><p><strong>Principles</strong></p>
<p>In this chapter we discuss the key principles for the development, design and governance of the standard. This is primarily based on <strong><a href="https://www.pensioenfederatie.nl/cms/streambin.aspx?documentid=18380">Results of research: Standard for data exchange pension administration &amp; asset management parties''</a>.</strong></p></td>
</tr>
<tr>
<th>3</th>
<td><p><strong>Processes &amp; information flows – Solidarity Premium Scheme</strong></p>
<p>The processes &amp; information flows are described in detail in the report ''<strong><a href="https://www.pensioenfederatie.nl/cms/streambin.aspx?documentid=18380">Results of research: Standard for data exchange pension administration &amp; asset management parties''</a>:</strong></p>
<p>Chapter 4: Solidarity Premium Scheme.</p></td>
</tr>
<tr>
<th>4</th>
<td><p><strong>Processes &amp; information flows – Flexible Premium Scheme</strong></p>
<p>The processes &amp; information flows are described in detail in the report ''<strong><a href="https://www.pensioenfederatie.nl/cms/streambin.aspx?documentid=18380">Results of research: Standard for data exchange pension administration &amp; asset management parties''</a>:</strong></p>
<p>Chapter 5: Flexible Premium Scheme.</p></td>
</tr>
<tr>
<th>5</th>
<td><p><strong>Approach/Setup of the data standard</strong></p>
<p>In this chapter we explain how we arrive at the specifications of the messages.</p>
<p>Steps to arrive at the functional specifications of the messages:</p>
<ul>
<li><p>Create descriptions of the processes and information flows.</p></li>
<li><p>Compile a list of entities and associated attributes.</p></li>
<li><p>Determine the base structure of the messages.</p></li>
<li><p>Indicate which messages are needed.</p></li>
<li><p>Create a cross-reference table between the base structure and the messages.</p>
<p>We explain the relationship with SIVI AFS. We use the building blocks from SIVI AFS (AFD 2.0) to arrive at technical specifications.</p></li>
</ul></td>
</tr>
<tr>
<th>6</th>
<td><p><strong>Functional specifications</strong></p>
<p>In this chapter the functional specifications follow:</p>
<ul>
<li><p>Data dictionary;</p></li>
<li><p>Base message;</p></li>
<li><p>Cross-reference base message &amp; messages.</p></li>
</ul></td>
</tr>
<tr>
<th>7</th>
<td><p><strong>Technical specifications</strong></p>
<p>The technical data specifications are made available based on AFD 2.0 from SIVI AFS. In this chapter the reader can take note of an explanation.</p></td>
</tr>
<tr>
<th>10</th>
<td><p><strong>Appendices</strong></p>
<p>In the appendices you will find the:</p>
<ul>
<li><p>Glossary/Abbreviation list Asset Management &amp; Pension Administration;</p></li>
<li><p>Glossary data exchange based on standards.</p></li>
</ul></td>
</tr>
</tbody>
</table>

## 1.5 Links

This manual contains links, mostly source references. These are colored **blue**. By clicking a link, the reader is taken to the relevant webpage or report/article.

## 1.6 Source of Title Page Image

<https://www.flaticon.com/free-icon/data-exchange_4995192>
