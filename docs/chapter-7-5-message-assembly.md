## 7.5 Message Assembly, Versioning and Publication

### 7.5.1 Explanation of the Use of "afdDefinitionVersion"

"afdDefinitionVersion" is populated with the version number (from the "Schema Name") of the VBPUO JSON schema.

The **VBPUO JSON schema** for the functional messages and the VBPUO_Feedback_Message is maintained by SIVI using "[AFD Online Samenstellen](https://www.sivi.org/afd-online-samenstellen) (AOS)" and is administered therein with the following metadata:

| **AOS Schema Metadata** | **Values (example)**             |
|--------------------------|----------------------------------|
| SIVI community           | AFD 2.0                          |
| Message type:            | Protocol PUO Asset Management    |
| Domain:                  | General                          |
| Schema name:             | VBPUO-**<u>\###.##</u>**        |

Table: Metadata (AOS) VBPUO schema

In the (AOS) VBPUO schema, the VBPUO message structures are defined as **"functions"**, for example the function: "Bericht_1.\_Vermogen\_(0001a)". From release 2027, 10 content messages and the Feedback Message are active; 5 messages from the FPR layered order model have been discontinued (see §6.4). For each "function", 3 **JSON schemas** are generated and published ("committed") on GitHub. These JSON schemas serve the following purposes:

JSON Schema Explained

| **Purposes** | **Further description** | **Example filename** |
|----|----|----|
| Message structure | Definition of the structure, mandatory elements and field validations, with internal and external references to ensure data consistency and standardization. | VBPUO-001.00-Bericht_1.\_Vermogen\_(0001a).json |
| Code lists/tables: | Defines the code lists (e.g. pension administration organization and currency codes) used as references in the JSON schema for field validation. | VBPUO-001.00-Bericht_1.\_Vermogen\_(0001a)-afdCodelists.json |
| Integrity constraints | Defines the rules for integrity constraints in the JSON schema to ensure the validity and consistency of data relationships. | VBPUO-001.00-Bericht_1.\_Vermogen\_(0001a)-validationRules.json |

Table: JSON Schemas (from AOS) explained

#### 7.5.1.1 Version Number / afdDefinitionVersion in a GitHub Release

The version number of an AOS schema must be included in every message sent. This number can be found in the Message Structure as a constant under afdDefinitionVersion.

Under this number, the JSON Schemas can be found at <https://portal.sivi.org/organisationschemas>. The messages created with this schema — within the VBPUO schema these are defined as functions — are published on GitHub.

##### Filename versus afdDefinitionVersion

The filenames of the JSON schemas contain a version number as part of the name, for example `VBPUO-001.00-Bericht_1._Vermogen_(0001a).json`. This version number is frozen at the value that applied at first publication and is not updated in later releases.

The reason for this is the coupling with the OpenAPI Specification (OAS). The OAS refers to the JSON schemas via a direct file path reference (`$ref`):

`$ref: 'VBPUO-Bericht_1._Vermogen_(0001a)/VBPUO-001.00-Bericht_1._Vermogen_(0001a).json'`

If the version number in the filename were updated with each release, all `$ref` references in the OAS would also need to be adjusted. Because implementing parties (PUOs and asset managers) base their API implementations on the OAS, every filename change would require a modification in all implemented APIs in the sector. This has been deliberately avoided.

The consequence is that filename and content can diverge: the filename states `001.00` while the field `afdDefinitionVersion` inside the schema contains the current value, such as `001.02`.

> **Note:** for implementation and validation, always use the value of `afdDefinitionVersion` — not the version number in the filename.

See also: [GitHub issue #58](https://github.com/Stichting-SIVI/VBPUOdsk/issues/58)

### 7.5.2 Publication on GitHub: Version Number and Tag

When releasing on GitHub, the release receives a Name and a Tag. All JSONs, example messages and the OAS fall under that release/tag.

The name of the July 2024 release was for example "[2024_Juli](media/v1.1.0)" with tag [v1.1.0](media/v1.1.0). The GitHub release name and tag number are not included in the payload of the messages. Both the messages and the OAS have their own release number.

### 7.5.3 JSON Schema Versions

Per message, multiple JSON-related files are published:
- message structure;
- code lists;
- validation rules.

From release 2027, these files are published conforming to JSON Schema Draft 2020-12.

The following applies:
- message structures use `$defs`;
- internal references use `#/$defs/...`;
- external AFD references point to the `2020-12` path;
- validation rules remain unchanged in content.
