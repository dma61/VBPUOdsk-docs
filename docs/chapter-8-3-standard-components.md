## 8.3 Components of the Standard Asset Management Pension Administration

> **Note:** The table below is in Dutch. It describes the components of the VBPUO standard.
>
> **NL → EN Legend for table headers:**
>
> | Dutch | English |
> |-------|---------|
> | Nr. | No. |
> | Onderdeel standaard | Standard component |
> | Toelichting | Explanation |

In Figure 14 below, what SIVI will establish for the Standard Asset Management Pension Administration is indicated. The table that follows provides an explanation of the components.

<img src="../media/image23.svg" style="width:6.26806in;height:3.52569in" />

**Figure 14 - Components of the standard in context**

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 26%" />
<col style="width: 66%" />
</colgroup>
<thead>
<tr>
<th>Nr.</th>
<th>Onderdeel standaard</th>
<th>Toelichting</th>
</tr>
</thead>
<tbody>
<tr>
<th>1</th>
<td><strong>Uitgangspunten</strong></td>
<td>De belangrijkste uitgangspunten bij de ontwikkeling, opzet en besturing van de standaard.</td>
</tr>
<tr>
<th>2</th>
<td><strong>Procesbeschrijvingen</strong></td>
<td>Procesbeschrijvingen zijn gestructureerde beschrijvingen die de stappen, activiteiten en betrokken elementen van de specifieke ketenprocessen en informatiestromen in detail uitleggen. We gebruiken deze beschrijvingen om een duidelijk begrip te verschaffen van hoe de processen werken en welke informatiestromen aan de orde zijn. In dit geval is vooral het onderscheid tussen flexibele en solidaire premieregeling relevant.</td>
</tr>
<tr>
<th>3</th>
<td><strong>Governance</strong></td>
<td>Governance gaat over het optimaal inrichten van de organisatie van de community rond de standaard. Duidelijk moet zijn wie beslist over wat uitgevoerd wordt met betrekking tot standaarden, en wie beslist hoe dit wordt uitgevoerd. Onderdeel is het huishoudelijk reglement van de klankbordgroep en de eventuele tijdelijke werkgroepen.</td>
</tr>
<tr>
<th>4</th>
<td><strong>Organisatie beheer</strong></td>
<td>Beheer gaat in op de beheersmatige processen rondom de standaarden. Het omvat alle activiteiten gericht op het aanpassen, uitbreiden, doorontwikkelen, beschikbaar stellen en houden van een (set van) berichten die steeds past bij de actuele behoefte van de belanghebbenden.</td>
</tr>
<tr>
<th>5</th>
<td><strong>Wijzigingsprocedure</strong></td>
<td>Wijzigingen op de standaard raakt meerdere belanghebbenden. In de procedure van wijziging zijn hierom de belangen van alle deelnemende partijen vertegenwoordigd. Verzoeken en voorstellen voor wijzigingen zullen een afgesproken procedure worden behandeld.</td>
</tr>
<tr>
<th>6</th>
<td><strong>Gegevensspecificaties</strong></td>
<td><p>In de gegevensspecificaties is de betekenis van de gegevenselementen beschreven en zijn de onderlinge verbanden beschreven. Gegevenselementen zijn entiteiten, attributen en codelijsten.</p>
<p>In de gegevensspecificaties is de afbeelding naar AFD 2.0 opgenomen. Hierdoor is duidelijk wat ontbreekt. Voor de ontbrekende elementen is een voorzet gedaan in AFD 2.0 termen.</p></td>
</tr>
<tr>
<th>7</th>
<td><strong>Basisstructuur berichten</strong></td>
<td>Basisbericht met de basisstructuur voor een set berichten. In de basisstructuur staat een opsomming van de entiteiten/attributen en de bijbehorende hiërarchische structuur. De beschrijving van dit basisbericht kan gebruikt worden om een baseline te maken.</td>
</tr>
<tr>
<th>8</th>
<td><strong>Kruistabel basisstructuur en berichten</strong></td>
<td><p>Een kruistabel tussen de basisstructuur en de berichten.</p>
<p>Per bericht is in de tabel aangegeven welke entiteiten/attributen van toepassing zijn. Hierbij is het aantal herhalingen (entiteiten) aangegeven en ook welke attributen verplicht gevuld moeten worden. Het is tevens mogelijk selecties uit codelijsten te maken, dat wil zeggen aan te geven welke codewaarden van toepassing zijn.</p></td>
</tr>
<tr>
<th>9</th>
<td><strong>Berichtspecificaties</strong></td>
<td><p>De specificaties zijn gebaseerd op de gegevensspecificaties. In deze berichtspecificatie wordt dit vertaald naar een hiërarchische berichtstructuur.</p>
<p>Onderdeel van de set berichtspecificaties is het responsebericht. Dit moeten we nog opstellen.</p>
<p>Ieder bericht kent een algemene sectie waarin onder meer staat aangegeven wie de zender/ontvanger is van het bericht.</p></td>
</tr>
<tr>
<th>10</th>
<td><strong>Berichtcontroles</strong></td>
<td>Een specificatie van alle controles op de berichten, bijvoorbeeld verbandcontroles. Het is een optie deze controles in machine leesbare vorm uit te leveren, maar in eerste instantie is dit niet noodzakelijk.</td>
</tr>
<tr>
<th>11</th>
<td><strong>Uitbreiding AFD 2.0</strong></td>
<td>Uitbreiding van AFD 2.0 met gevraagde gegevenselementen. AFD 2.0 kan op verzoek van belanghebbenden maandelijks uitgebreid worden.</td>
</tr>
<tr>
<th>12</th>
<td><strong>Baseline</strong></td>
<td>Dit is het basisbericht dat in AOS wordt geïmporteerd. Daarna kunnen AFD-definities gemaakt worden.</td>
</tr>
<tr>
<th>13</th>
<td><strong>Schema's</strong></td>
<td><p>JSON-Schema of XML-Schema per bericht/basisstructuur. Onder meer om berichten te kunnen valideren.</p>
<p>AOS levert JSON-schema's op basis van AFD 2.0 berichten en AFD-definities.</p></td>
</tr>
<tr>
<th>14</th>
<td><strong>Handleiding events</strong></td>
<td><p>Voorbeelden van het afhandelen van specifieke situaties. De situaties laten zien hoe de standaard toegepast moet worden.</p>
<p>Voorbeeldberichten zijn onderdeel van de handleiding events.</p></td>
</tr>
<tr>
<th>15</th>
<td><strong>Koppelvlakspecificaties</strong></td>
<td><p>Bij geautomatiseerde koppelingen tussen gedistribueerde systemen (machine-‐machine) is sprake van een interface waarmee communicatie mogelijk wordt gemaakt. Zo'n interface wordt een koppelvlak genoemd. De beschrijving van een koppelvlak noemen we koppelvlakspecificaties.</p>
<p>Voorbeelden:</p>
<ul>
<li><p>Webservices</p></li>
<li><p>File transfer</p></li>
<li><p>Aanlevering via portaal</p></li>
</ul>
<p>Onderdeel van de koppelvlakspecificaties kunnen instructies zijn over de (data)beveiliging.</p>
<p>Opmerking:</p>
<p>koppelvlakspecificaties hebben Duco/Gerhard niet toegezegd. Als hier vraag naar ontstaat, dan pakken we dat op.</p></td>
</tr>
<tr>
<th>16</th>
<td><strong>Testvoorzieningen</strong></td>
<td><p>Voorzieningen om de ontwikkelaars te ondersteunen bij het implementeren van de berichten/koppelvlakspecificaties.</p>
<p>Onderdeel kan een generieke set zijn met testgegevens.</p></td>
</tr>
<tr>
<th>17</th>
<td><strong>Rekenvoorschriften</strong></td>
<td>Instructies om berekeningen uit te voeren. De berekeningen zijn van toepassing voor gegevenselementen in de berichten.</td>
</tr>
</tbody>
</table>

**Message validations**

Integrity constraints are recorded in JMESPath and apply to the message for which they are written. Validations that span multiple messages — where other messages or back-office information is needed — fall outside the scope of these validations.

**JSON schemas**

The JSON schemas are in principle self-explanatory, but some clarification may be useful because these schemas are also split in JSON technology. This means that in addition to the expected entities and entity types such as 'party' and 'pension.scheme', there are also certain key elements such as "$defs", "type", "properties", "additionalProperties" and "required".

From JSON Schema Draft 2020-12, this is called "$defs". In older versions (draft-07, 2019-09), the term "definitions" was used.

These properties and specifications that apply to, for example, 'commonFunctional', are not all grouped around 'commonFunctional', but are distributed across the JSON schema. The main thing to note is that this distribution is not arbitrary, but follows from the different types of properties.
