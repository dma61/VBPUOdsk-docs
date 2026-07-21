# 7 Technical Specifications

**The technical data specifications are made available based on AFD 2.0 from SIVI AFS. In this chapter the reader can take note of an explanation.**

## 7.1 Messages & Schemes

Each message can concern multiple schemes (pension.scheme). However, it always pertains to a single party.pensionProvider. The transmission is per message, and that message thus contains 1 pension.provider and 1 or more pension.scheme's.

## 7.2 Validations

The following validation rules can be implemented using the technical specifications:

- Check if the message structure is correct;

- Verify the data type (including numbers, strings);

- Check for minimum and maximum values;

- Validate the field length;

- Check for the presence of mandatory entities and mandatory attributes;

- Check the number of repetitions of entities;

- Ensure the use of allowed codes from code lists.

N.B.: Integrity constraints (validation rules between different data elements) are still in development. See also the JSON schemas.

## 7.3 JSON

1.  The SIVI AFS team follows the specifications below for AFD 2.0 in combination with JSON (derived from [Forum Standaardisatie](https://www.forumstandaardisatie.nl/open-standaarden/json)):

<table>
<colgroup>
<col style="width: 29%" />
<col style="width: 70%" />
</colgroup>
<thead>
<tr>
<th>Concern</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<th>Full Name</th>
<td>JavaScript Object Notation</td>
</tr>
<tr>
<th>Version</th>
<td>RFC8259, December 2017</td>
</tr>
<tr>
<th>Specification Document</th>
<td><a href="https://tools.ietf.org/html/rfc8259">JSON Specification Document</a></td>
</tr>
<tr>
<th>Managing Organization</th>
<td><p>Internet Engineering Task Force</p>
<p><a href="https://datatracker.ietf.org/doc/html/rfc7159">https://datatracker.ietf.org/doc/html/rfc7159</a></p></td>
</tr>
<tr>
<th>Functional Scope</th>
<td>Object notation for exchanging data structures. For example, in web applications that asynchronously retrieve data from the web server.</td>
</tr>
<tr>
<th>Typing</th>
<td>Exchange of data structures</td>
</tr>
<tr>
<th>Benefit</th>
<td>JSON (JavaScript Object Notation) is a subset of the JavaScript programming language. The simplicity of JSON has led to its great popularity, especially as a 'light' alternative to XML.</td>
</tr>
<tr>
<th>Operation</th>
<td><p>JavaScript Object Notation (JSON) is a format for storing and sending data, similar to XML. JavaScript is the programming language from which the basic syntax description was derived for use in JSON. JSON is used for exchanging data structures, particularly in web applications that asynchronously retrieve data from the web server. The standard is particularly aimed at efficient programming and has a compact notation, for example:</p>
<p>{</p>
<p>"name": Jan,</p>
<p>"born": 1983</p>
<p>}</p></td>
</tr>
<tr>
<th>Tools</th>
<td>Various online JSON validators and tools are available, also for different programming platforms. More information about the standard can also be found via <a href="http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf">publications from ECMA International</a></td>
</tr>
</tbody>
</table>

**Guideline**: If a non-mandatory attribute has no value, the attribute should be completely omitted from the JSON message. This is a recommended practice according to JSON conventions.

### 7.3.1 Use of JSON Schema

For validation of the message structures, the standard uses JSON Schema.

The JSON schemas are generated from AFD 2.0 / AOS and published via GitHub. These schemas support:
- validation of message structures;
- validation of mandatory fields;
- validation of code lists;
- validation of technical constraints.

### 7.3.2 Transition to JSON Schema Draft 2020-12

From release 2027, the VBPUO standard uses JSON Schema Draft 2020-12.

This change has been discussed and documented via GitHub issue:

[#104 JSON Schema Version](https://github.com/Stichting-SIVI/VBPUOdsk/issues/104)

The transition concerns a technical modernization of the JSON schemas. The functional meaning of the messages does not change as a result.

#### Differences Compared to JSON Schema Draft 2019-09

##### Main Schema

1. The schema dialect has changed from:

`http://json-schema.org/draft/2019-09/schema#`

to:

`https://json-schema.org/draft/2020-12/schema`

2. The container with definitions is no longer called `definitions` but `$defs`.

3. Internal references have been adjusted from:

`#/definitions/...`

to:

`#/$defs/...`

4. The external reference to the codelist now uses the 2020-12 path:

`https://www.sivi.org/afd-online-tool/json/2020-12/AFDIDP.json#/$defs/AFDIDP`

instead of:

`https://www.sivi.org/afd-online-tool/json/AFDIDP.json#/definitions/AFDIDP`

##### ValidationRules

1. No 2020-12-specific model differences have been identified.

2. The file remains a JSON structure with metadata and validation rules; no substantive changes have been identified as a result of the transition to Draft 2020-12.

##### AfdCodelists

1. The schema dialect has changed from:

`http://json-schema.org/draft-07/schema#`

to:

`https://json-schema.org/draft/2020-12/schema`

2. The container with definitions is no longer called `definitions` but `$defs`.
