## 6.4 Messages

> **Note:** The tables and detailed message structures below are in Dutch. Technical field names (entity.entitytype, attributes) are identical in both languages.
>
> **NL → EN Legend for table headers and terms:**
>
> | Dutch | English |
> |-------|---------|
> | Berichten | Messages |
> | Berichtnaam | Message name |
> | Berichtsoort | Message type |
> | Soort | Type |
> | Omschrijving | Description |
> | Basisbericht | Base message |
> | Berichtstructuur | Message structure |
> | Kardinaliteit | Cardinality |
> | V (Verplicht) | R (Required) |
> | O (Optioneel) | O (Optional) |
> | Maximumaantal iteraties | Maximum number of iterations |
> | Vervallen | Discontinued |
> | Van → Naar | From → To |
> | Zie ook | See also |
> | Pensioenuitvoeringsorganisaties (PUO) | Pension Administration Organizations (PUO) |
> | Fiduciair managers (FM) | Fiduciary Managers (FM) |
> | Beleggingsadministrateurs (BA) | Investment Administrators (BA) |
> | Vermogen | Assets |
> | Cashflow | Cash flow |
> | Pensioenprojectie | Pension Projection |
> | Rendementsinformatie | Return Information |
> | Orderopdracht | Trade Order |
> | Betaalinformatie | Payment Information |
> | Stuurinformatiebeleggingspools | Control Information Investment Pools |
> | Waarde-informatie beleggingspool | Value Information Investment Pool |
> | Mutatiesaldi | Balance Adjustments |
> | Reconciliatie-informatie | Reconciliation Information |
> | Rebalancinginformatie | Rebalancing Details |
> | Waarde-informatie cohortenpool | Value Information Cohort Pool |
> | Corporate Actions | Corporate Actions |
> | Feedbackbericht | Feedback Message |

The base message is further elaborated into specific messages. From release 2027, 10 content messages and the Feedback Message are active; 5 messages from the FPR layered order model have been discontinued (see marking in Table 12).

Table 12 below provides an overview of these messages and between which roles they are exchanged:

| Berichtnaam | PUO | FM | BA | LDI |
|----|----|----|----|----|
| 1\. Vermogen (0001a) | van | naar |  |  |
| 2\. Cashflow (0001b) | van | naar |  |  |
| 3\. Pensioenprojectie (0001c) | van | naar |  | naar |
| 4\. Rendementsinformatie (00002) | naar |  | van |  |
| 5\. Orderopdracht (00541) | van |  | naar |  |
| 6\. Orderconfirmation (00542) | naar |  | van |  |
| 10\. Stuurinformatiebeleggingspools (00553) |  | naar | van |  |
| 13\. Waarde-informatie beleggingspool (00555b) | naar |  | van |  |
| 14\. Betaalinformatie (00556) | van | naar | van |  |
| 15\. Corporate Actions (00557) | naar | van | van |  |
| Feedback Message |  |  |  |  |

The Feedback Message can be used for both FPR and SPR and is always a response to a received message; one of the other messages.

**Tabel 12 – Overzicht berichten tussen zenders en ontvangers**

**Legenda**

- Pensioenuitvoeringsorganisaties (PUO) — hieronder vallen ook Zelf Administrerende Fondsen (ZAF)

- Fiduciair managers (FM)

- Beleggingsadministrateurs / asset serviceprovider (BA)

- Liability-Driven Investment-managers (LDI)

**Toelichting: Administrateur cohorten- en beleggingspools (ACB) — vervallen**

De rol ACB is als zelfstandige actor vervallen uit dit overzicht. In de praktijk wordt deze rol ingevuld door de BA of soms de PUO. Omdat de ACB-rol per juli 2026 niet meer als afzonderlijke partij voorkwam, is de kolom uit de matrix verwijderd. Mocht de ACB-rol in de toekomst opnieuw als expliciete partij optreden, dan biedt het berichtenschema via de aanwezige berichten nog steeds de mogelijkheid om daar invulling aan te geven. Zie GitHub issue [#131](https://github.com/Stichting-SIVI/VBPUOdsk/issues/131).

**Let op:** Elke ontvangende partij/rol krijgt zijn **informatie rechtstreeks** van de verzendende partij. Ook de verzending naar niet in Tabel 12 genoemde partijen/rollen is rechtstreeks. Ontvangen informatie wordt niet doorgestuurd aan andere partijen.

In onderstaande tabel de berichtsoorten en de betekenis. Berichten die vanaf release 2027 zijn vervallen, zijn doorgehaald weergegeven. Tussen haakjes de verwijzing naar het eindrapport van de werkgroep[^7]: "Eindrapport onderzoek standaard VB PUO (september 2023.pdf".

PMT = pensionMessageType in AFD 2.0 (aangegeven zijn de omschrijvingen van de berichttypes).

TAG = de in de API[^8] gebruikte aanduiding voor het bericht.

<table>
<colgroup>
<col style="width: 9%" />
<col style="width: 14%" />
<col style="width: 25%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr>
<th>Soort</th>
<th>Berichtsoort</th>
<th>PMT/<br />
TAG</th>
<th>Omschrijving</th>
</tr>
</thead>
<tbody>
<tr>
<th>SPR</th>
<td><p>1. Vermogen (0001a)</p>
<p>(4.2.1.1)</p></td>
<td>Vermogen/<br />
Capital</td>
<td><p><strong>Van 🡪 Naar</strong></p>
<p>Van PUO naar FM en BA/asset serviceprovider.</p>
<p>Op periodieke (naar verwachting maandelijkse) basis ontvangt de FM over een pensioenuitvoerder per regeling het totale pensioenvermogen bij aanvang van de periode.</p>
<p>Naast de informatie op totaalniveau kan de FM ook per cohort het pensioenvermogen ontvangen. Zo kan bijvoorbeeld voor het leeftijdscohort 25-29 jaar het totaal van de persoonlijke pensioenvermogens bij aanvang worden ontvangen.</p>
<p>Met de cohortinformatie kan de FM desgewenst een totaalberekening maken en de aansluiting bij de geleverde informatie op totaal/collectief niveau toetsen aan het beleid van het fonds. Dit is nuttig voor een robuuste overdracht en audittrail afhankelijk van afspraken die partijen maken. Conform het beleid van de pensioenuitvoerder kan bij (grote) afwijkingen herbalancering wenselijk zijn. Deze informatie kan behalve aan de FM desgewenst ook worden verstrekt aan de BA/asset serviceprovider om deze ook in staat te stellen toetsings- en rapportage-activiteiten uit te voeren met behulp van de leidende beleggingsadministratie.</p></td>
</tr>
<tr>
<th>SPR</th>
<td><p>2. Cashflow (0001b)</p>
<p>(4.2.1.3)</p></td>
<td>Cashflow/<br />
Cashflow</td>
<td><p>Instroom en uitstroom</p>
<p><strong>Van 🡪 Naar</strong></p>
<p>Van PUO naar FM en BA/asset serviceprovider.</p>
<p>Op periodieke (naar verwachting maandelijkse) basis ontvangt de FM over een pensioenuitvoerder per regeling de instroom in de periode en de uitstroom. Naast op totaalniveau kan ook per cohort instroom en uitstroom aangeleverd worden.</p>
<p>De in- en uitstroom bevat naast premies, waardeoverdrachten en uitkeringen ook de verschuivingen over cohorten als daar sprake van is. Een cohort kan ook een geboortejaar zijn. Ook het 'cohort' solidariteitsreserve, het 'cohort' compensatiedepot en mogelijk andere reserves zullen hierbij betrokken worden.</p>
<p>Met de cohortinformatie kan de FM desgewenst een totaalberekening maken en de aansluiting bij de geleverde informatie op totaal/collectief niveau toetsen aan het beleid van het fonds. Dit is nuttig voor een robuuste overdracht en audittrail afhankelijk van afspraken die partijen maken. Deze informatie kan behalve aan de FM desgewenst ook worden verstrekt aan de BA/asset serviceprovider om ook deze in staat te stellen toetsings- en rapportage-activiteiten uit te voeren met behulp van de leidende beleggingsadministratie.</p></td>
</tr>
<tr>
<th>SPR</th>
<td><p>3. Pensioenprojectie (0001c)</p>
<p>(4.2.1.3)</p></td>
<td>Pensioenprojectie/<br />
PensionProjection</td>
<td><p>Geprojecteerde uitkeringen</p>
<p><strong>Van 🡪 Naar</strong></p>
<p>Van PUO naar FM en BA/asset serviceprovider.</p>
<p>Op periodieke (verwachting is maandelijkse) basis ontvangt de FM van een pensioenuitvoerder per regeling en per cohort de geprojecteerde uitkeringen op basis van de opgebouwde vermogens naar toekomstige periodes.</p>
<p>Tevens bevat de gegevensuitwisseling de af te dekken kasstromen per regeling per toekomstige periode. Dit is gelijk aan de som van de gewogen geprojecteerde uitkeringen per cohort. De wegingsfactor is gelijk aan het percentage bescherming per cohort. Op deze manier ontstaat een profiel van de af te dekken kasstromen. Deze uitwisseling vermijdt misverstanden ten aanzien van af te dekken kasstromen en kan desgewenst een toets in het proces introduceren.</p></td>
</tr>
<tr>
<th>SPR</th>
<td><p>4. Rendementsinformatie (00002)</p>
<p>(4.2.2.)</p></td>
<td>Rendementsinformatie/<br />
ReturnOnInvestment</td>
<td><p>Informatiebehoefte PUO</p>
<p><strong>Van 🡪 Naar</strong></p>
<p>Informatiestroom van BA/asset serviceprovider naar de PUO.</p>
<p>De PUO heeft voor het uitvoeren van de solidaire premieregeling periodiek (naar verwachting maandelijks) informatie nodig over het behaalde rendement.</p>
<p>Periodiek ontvangt de PUO over de periode voor een pensioenuitvoerder per regeling en per portefeuille de waarde aan het begin van de periode, de waarde aan het einde van de periode en het rendement in portefeuille valuta en (eventueel) uitgedrukt als percentage. De PUO draagt zorg voor de toedeling van rendementen naar deelnemers op basis van portefeuillerendementen. Optioneel kunnen ook per cohort in de regeling pensioenvermogen, beschermingsrendement en overrendement worden gedeeld met de PUO. Of deze optionele elementen worden uitgewisseld hangt af van de overeengekomen rollen en verantwoordelijkheden tussen de samenwerkende partijen.</p>
<p>Daarbij is het uitgangspunt dat de PUO de verantwoordelijkheid heeft om conform de door de pensioenuitvoerder vastgestelde toedelingsregels rendementen toe te delen naar de persoonlijke pensioenvermogens van deelnemers, de solidariteitsreserve, een eventueel compensatiedepot en mogelijk andere reserves.</p></td>
</tr>
<tr>
<th>FPR</th>
<td><p>5. Orderopdracht (00541)</p>
<p>(5.4.1.)</p></td>
<td>Orderopdracht/<br />
Trade</td>
<td><p>Direct order (PUO belegt zelf)</p>
<p><strong>Van 🡪 Naar</strong></p>
<p>Informatiestroom van PUO naar Brokers/Transfer Agents/Order Desks.</p>
<p>Dit is de minimale set aan gegevens die benodigd is om een order te kunnen sturen aan een order verwerkende partij. Tevens kan er een switch mee worden uitgevoerd.</p>
<p>De PUO stuurt orders in op het hoogste niveau van het beleggingsfonds. De aanbieder van het fonds voert zelf de ordering uit in de onderliggende beleggingen. Dat kan onder andere genoteerde en illiquide beleggingen betreffen.</p></td>
</tr>
<tr>
<th>FPR</th>
<td><p>6. Orderconfirmation (00542)</p>
<p>(5.4.2.)</p></td>
<td>Orderconfirmation</td>
<td><p>Direct order (PUO belegt via een order platform)</p>
<p><strong>Van 🡪 Naar</strong></p>
<p>Van brokers/transfer agents/order desks naar PUO.</p>
<p>Vanuit de order verwerkende partij komen de confirmationtgegevens van de order terug naar de PUO.</p></td>
</tr>
<tr>
<th><del>FPR</del></th>
<td><del><p>7. Mutatiesaldi (00551)</p>
<p>(5.5.1)</p></del></td>
<td><del>Mutatiesaldi/<br />
BalanceAdjustments</del></td>
<td><p><strong>Vervallen vanaf release 2027.</strong></p>
<p><del>Informatiebehoefte administrateur cohortenpools en beleggingspools</del></p>
<p><del><strong>Van 🡪 Naar</strong></del></p>
<p><del>Van PUO naar administrateur van cohortenpools en beleggingspools.</del></p>
<p><del>De eerste (naar verwachting maandelijkse) informatiestroom van de PUO naar de administrateur van cohortenpools en beleggingspools betreft gesaldeerde mutaties, zijnde aankoop, verkoop en switches op totaalniveau per cohortenpool welke worden doorgegeven aan de administrateur cohortenpools en beleggingspools. Deze administrateur kan hiermee de in- of uitstroom voor beleggingspools berekenen en daarmee de FM instrueren.</del></p></td>
</tr>
<tr>
<th><del>FPR</del></th>
<td><del><p>8. Reconciliatie-informatie (00552a)</p>
<p>(5.5.2)</p></del></td>
<td><del>Reconciliatie-informatie/<br />
InvestmentDetails</del></td>
<td><p><strong>Vervallen vanaf release 2027.</strong></p>
<p><del>Reconciliatie administrateur van cohortenpools en beleggingspools, FM en BA.</del></p>
<p><del><strong>Van 🡪 Naar</strong></del></p>
<p><del>Informatiestroom tussen administrateur van cohortenpools en beleggingspools, FM en BA.</del></p>
<p><del>De administrateur cohortenpools en beleggingspools ontvangt maandelijks de posities uit de leidende administratie van de BA van de beleggingspools, mogelijk aangevuld uit de (schaduw) administratie van de FM. Deze posities worden gereconcilieerd met de posities in de eigen administratie van de administrateur van cohortenpools en beleggingspools.</del></p></td>
</tr>
<tr>
<th><del>FPR</del></th>
<td><del><p>9. PUO-reconciliatie-informatie (00552b)</p>
<p>(5.5.2)</p></del></td>
<td><del>PUO-reconciliatie-informatie/<br />
InvestmentDetailsPUO</del></td>
<td><p><strong>Vervallen vanaf release 2027.</strong></p>
<p><del>Additionele informatie als de PUO (ook) de rol van administrateur van cohortenpools vervuld.</del></p>
<p><del><strong>Van 🡪 Naar</strong></del></p>
<p><del>Administrateur beleggingspools naar de PUO.</del></p>
<p><del>Indien de PUO de rol van administrateur cohortenpools vervult dan is een additionele informatie-uitwisseling nodig van de administrateur beleggingspools naar de PUO over de voorlopige unitwaarden van de beleggingspools. Deze is in de onderstaande tabel weergegeven. Door ook het aantal uitgegeven units per beleggingspool te delen wordt de PUO in staat gesteld om de aansluiting bij het aantal gehouden units in de beleggingspools door alle cohortenpools te reconciliëren.</del></p></td>
</tr>
<tr>
<th>FPR</th>
<td><p>10. Stuurinformatie beleggingspools (00553)</p>
<p>(5.5.3)</p></td>
<td><p>Stuurinformatie</p>
<p>Beleggingspools/<br />
ControlInformationInvestmentPools</p></td>
<td><p>Informatie aansturen beleggingspools</p>
<p><strong>Van 🡪 Naar</strong></p>
<p>Van PUO en/of BA naar FM (zie Figuur 8 en 9, stappen D en E).</p>
<p>De PUO en/of de BA berekent de participatiewaarden van actieve leeftijdsgroepen en combineert deze waarden met de opgegeven mutaties om de casheffecten op de beleggingspools te schatten. De stuurinformatie op de beleggingspool (met onderbouwing) wordt verstuurd naar de FM in het volgende format.</p></td>
</tr>
<tr>
<th><del>FPR</del></th>
<td><del><p>11. Rebalancinginformatie (00554)</p>
<p>(5.5.4)</p></del></td>
<td><del>Rebalancinginformatie/<br />
RebalancingDetails</del></td>
<td><p><strong>Vervallen vanaf release 2027.</strong></p>
<p><del>Rebalancing cohortenpools</del></p>
<p><del><strong>Van 🡪 Naar</strong></del></p>
<p><del>Informatiestroom tussen administrateur van cohortenpools en beleggingspools en FM.</del></p>
<p><del>De administrateur van cohortenpools en beleggingspools herbalanceert de relevante leeftijdsgroepen om op basis van de unitwaarden van de beleggingspools van tijdstip T conform het normbeleid belegd te zijn voor alle cohorten.</del></p>
<p><del>De administrateur van cohortenpools en beleggingspools verstuurt alle maandultimo transacties in de cohortenpools en beleggingspools in het afgesproken format naar de FM.</del></p></td>
</tr>
<tr>
<th><del>FPR</del></th>
<td><del><p>12. Waarde-informatie cohortenpool (00555a)</p>
<p>(5.5.5)</p></del></td>
<td><del>Waarde-informatie cohortenpool/<br />
ValueAmountCohortPool</del></td>
<td><p><strong>Vervallen vanaf release 2027.</strong></p>
<p><del>Doorgeven waardes per beleggingspool en per cohortenpool</del></p>
<p><del>(Fiduciair ontvangt van de PUO)</del></p>
<p><del><strong>Van 🡪 Naar</strong></del></p>
<p><del>Fiduciair ontvangt van de PUO (PUO administreert cohortenpools)</del></p>
<p><del>De administrateur van cohortenpools en beleggingspools berekent de unitwaarde per unit in de beleggingspool en de participatiewaarde per participatie in de cohortenpool.</del></p>
<p><del>Indien de PUO de rol van de administrateur cohortenpools vervult dan zal deze de unitwaarden van de beleggingspools ontvangen van de administrateur beleggingspools maar zelf zorgdragen voor de berekening van de participatiewaarden van de cohortenpools. De FM zal deze dan ook ontvangen van de PUO.</del></p>
<p><del>De administrateur van cohortenpools en beleggingspools geeft daarnaast de gesommeerde (unit)waarden van beleggingspools door aan partijen.</del></p></td>
</tr>
<tr>
<th>FPR</th>
<td><p>13. Waarde-informatie beleggingspool (00555b)</p>
<p>(5.5.5)</p></td>
<td>Waarde-informatie Beleggingspool/<br />
ValueAmountInvestmentPool</td>
<td><p>Doorgeven waardes per beleggingspool en per cohortenpool</p>
<p><strong>Van 🡪 Naar</strong></p>
<p>Informatiestroom tussen BA, PUO en FM (zie Figuur 8 en 9, stap J).</p>
<p>De BA berekent de unitwaarde per unit in de beleggingspool en de participatiewaarde per participatie in de cohortenpool.</p>
<p>De BA geeft de (participatie)waarden van de cohortenpools door aan de PUO en aan de FM.</p></td>
</tr>
<tr>
<th>FPR</th>
<td><p>14. Betaalinformatie (00556)</p>
<p>(5.5.6)</p></td>
<td>Betaalinformatie/<br />
PaymentDetailsCreditor</td>
<td><p>Betaalinstructies onttrekkingen</p>
<p><strong>Van 🡪 Naar</strong></p>
<p>Informatiestroom van PUO of BA naar FM, begin van de maand (zie Figuur 8 en 9, stappen K en L).</p>
<p>De PUO of de BA verstuurt de betaalinstructie voor onttrekkingen naar de FM.</p></td>
</tr>
<tr>
<th>FPR</th>
<td><p>15. Corporate Actions (00557)</p></td>
<td>Corporate Actions/<br />
CorporateActions</td>
<td><p>Doorgeven corporate-action gebeurtenissen op beleggingsproducten</p>
<p><strong>Van 🡪 Naar</strong></p>
<p>Informatiestroom van de vermogensbeheerketen naar de PUO.</p>
<p>Bericht 15 wordt gebruikt voor het doorgeven van corporate-action gebeurtenissen op beleggingsproducten vanuit de vermogensbeheerketen aan de PUO. Het bericht is bedoeld voor situaties waarin dergelijke gebeurtenissen wel binnen de vermogensbeheeradministratie worden verwerkt, maar niet automatisch zichtbaar zijn binnen de administratie van de PUO.</p></td>
</tr>
<tr>
<th>SPR/ FPR</th>
<td>Feedback Message</td>
<td>Feedback Message/<br />
Feedback</td>
<td><p>Terugkoppeling van fouten of bevestigen van verwerkbaarheid.</p>
<p><strong>Van 🡪 Naar</strong></p>
<p>De ontvanger van het inhoudelijke bericht, de berichten 1 tot en met 15, is de verzender van de feedback message.</p></td>
</tr>
</tbody>
</table>

### 6.4.1 Base Message

The base structure for messages (transaction) shows the hierarchical relationships between different entities in the data model. The entities and entity types form a coherent hierarchy. By definition, it is necessary to establish a hierarchy in exchanged messages, and the transaction structure forms the basis for this. The structure indicates, among other things, which child entity belongs to which parent entity.

In the "Kardinaliteit" (Cardinality) column, it is shown how many times that entity can occur at minimum and maximum. With R (required) or O (optional), it is indicated under Cardinality whether an entity.entitytype must or may occur. Within the base message, all entities have been left optional.

From the table below, the following can be derived:

1)  Per party.sender multiple party.contact are possible

2)  Per party.pensionProvider

    1)  maximally 1 financialInformation.reportingPeriod occurs and possibly

    2)  multiple pension.schema's

| **Entity.entitytype**                | **Kardinaliteit** |
|--------------------------------------|-------------------|
| commonTechnical.default              | 1..1, V           |
| party.sender                         | 1..1, V           |
| party.contact                        | 0..\*, O          |
| party.receiver                       | 1..1, V           |
| commonFunctional.default             | 1..1, V           |
| party.pensionProvider                | 1..1, V           |
| pension.scheme                       | 1..\*, V          |
| financialInformation.reportingPeriod | 1..1, V           |
| financialTransaction.payment         | 0..\*, O          |
| party.creditor                       | 1..\*, V          |
| financialTransaction.cashflow        | 0..1, O           |
| pension.cohort                       | 0..\*, O          |
| financialTransaction.payment         | 0..\*, O          |
| pension.cohortPool                   | 0..\*, O          |
| investment.pool                      | 1..\*, V          |
| investment.pool                      | 0..\*, O          |
| investment.investmentDetails         | 1..\*, V          |
| investment.corporateAction           | 1..\*, V          |
| investment.portfolio                 | 0..\*, O          |
| investment.investmentDetails         | 0..\*, O          |
| financialTransaction.trade           | 1..\*, V          |
| error.default                        | 0..\*, O          |
| document.default                     | 0..\*, O          |
| chunking.default                     | 0..1, O           |

N.B. In the technical implementation, the number of repetitions (\*) is limited. See the overview below:

<table>
<colgroup>
<col style="width: 70%" />
<col style="width: 29%" />
</colgroup>
<thead>
<tr>
<th><strong>Entity.entitytype</strong></th>
<th style="text-align: right;"><strong>Maximum iterations</strong></th>
</tr>
</thead>
<tbody>
<tr>
<th>commonTechnical.default</th>
<td style="text-align: right;">1</td>
</tr>
<tr>
<th>party.sender</th>
<td style="text-align: right;">1</td>
</tr>
<tr>
<th>party.contact</th>
<td style="text-align: right;">9</td>
</tr>
<tr>
<th>party.receiver</th>
<td style="text-align: right;">1</td>
</tr>
<tr>
<th>commonFunctional.default</th>
<td style="text-align: right;">1</td>
</tr>
<tr>
<th>party.pensionProvider</th>
<td style="text-align: right;">1</td>
</tr>
<tr>
<th>pension.scheme</th>
<td style="text-align: right;">999</td>
</tr>
<tr>
<th>financialInformation.reportingPeriod</th>
<td style="text-align: right;">1</td>
</tr>
<tr>
<th>party.creditor</th>
<td style="text-align: right;">1</td>
</tr>
<tr>
<th>financialTransaction.cashflow</th>
<td style="text-align: right;">1</td>
</tr>
<tr>
<th>financialTransaction.payment</th>
<td style="text-align: right;">9999 or 99999[^1]</td>
</tr>
<tr>
<th>pension.cohort</th>
<td style="text-align: right;">99999</td>
</tr>
<tr>
<th>pension.cohortPool</th>
<td style="text-align: right;">99</td>
</tr>
<tr>
<th>investment.pool</th>
<td style="text-align: right;">99</td>
</tr>
<tr>
<th>investment.portfolio</th>
<td style="text-align: right;">99</td>
</tr>
<tr>
<th>investment.investmentDetails</th>
<td style="text-align: right;">999</td>
</tr>
<tr>
<th>investment.corporateAction</th>
<td style="text-align: right;">99</td>
</tr>
<tr>
<th>financialTransaction.trade</th>
<td style="text-align: right;">99</td>
</tr>
<tr>
<th>error.default</th>
<td style="text-align: right;">99</td>
</tr>
<tr>
<th>document.default</th>
<td style="text-align: right;">99</td>
</tr>
<tr>
<th>chunking.default</th>
<td style="text-align: right;">1</td>
</tr>
</tbody>
</table>

[^1]: The maximum number of financialTransaction.payment under pension.cohort is 9999 and under pension.scheme remains 99999.

**APF circles: two common scenarios**

For a General Pension Fund (APF) with multiple circles, there is one `pension.scheme` per circle under one `party.pensionProvider`. Two scenarios exist side by side in the market:

**Scenario 1 — Circle has its own PUV code**
Each circle is identified with its own `puvCode` in `party.pensionProvider`. Buffer capital above circle level is pragmatically handled via a cohort construction, because no separate PUV code exists for this.

**Scenario 2 — Circle does not have its own PUV code**
There is one PUV code at APF/provider level. The distinction between circles runs via references at `pension.scheme` level.

Both scenarios are supported by the standard. Parties record the chosen approach in agreements between chain parties (TOM / SLA). See GitHub issue [#114](https://github.com/Stichting-SIVI/VBPUOdsk/issues/114).

### 6.4.2 – 6.4.17 Message Structures

The detailed message structure tables are hosted as interactive HTML tables. Each iframe below loads the Dutch-language table from the official docs-prepare site; the technical field names (entity.entitytype, attributes) are the same in both languages.

#### 6.4.2 Message structure 1. Assets (0001a)

See also [3.2.1](../chapter-3-spr-processes/#321-message-1-assets-1a).

<iframe
  src="https://stichting-sivi.github.io/VBPUOdsk-docs-prepare/assets/berichtstructuur-01-vermogen.html"
  width="100%"
  height="380"
  style="border: 1px solid #ddd; border-radius: 4px; display: block;"
  title="Message structure 1. Assets (0001a)">
</iframe>

#### 6.4.3 Message structure 2. Cashflow (0001b)

See also [3.2.2](../chapter-3-spr-processes/#322-message-2-cashflow-1b-inflow-and-outflow).

<iframe
  src="https://stichting-sivi.github.io/VBPUOdsk-docs-prepare/assets/berichtstructuur-02-cashflow.html"
  width="100%"
  height="380"
  style="border: 1px solid #ddd; border-radius: 4px; display: block;"
  title="Message structure 2. Cashflow (0001b)">
</iframe>

#### 6.4.4 Message structure 3. Pension Projection (0001c)

See also [3.2.3](../chapter-3-spr-processes/#323-message-3-pension-projection-1c-projected-benefits).

<iframe
  src="https://stichting-sivi.github.io/VBPUOdsk-docs-prepare/assets/berichtstructuur-03-pensioenprojectie.html"
  width="100%"
  height="380"
  style="border: 1px solid #ddd; border-radius: 4px; display: block;"
  title="Message structure 3. Pension Projection (0001c)">
</iframe>

#### 6.4.5 Message structure 4. Return Information (00002)

See also [3.2.4](../chapter-3-spr-processes/#324-message-4-return-information-2-information-need-of-the-puo).

<iframe
  src="https://stichting-sivi.github.io/VBPUOdsk-docs-prepare/assets/berichtstructuur-04-rendementsinformatie.html"
  width="100%"
  height="380"
  style="border: 1px solid #ddd; border-radius: 4px; display: block;"
  title="Message structure 4. Return Information (00002)">
</iframe>

#### 6.4.6 Message structure 5. Trade Order (00541)

See also [4.2](../chapter-4-fpr-processes/#42-model-1-simpler-direct-order-model) & [4.4.1](../chapter-4-fpr-processes/#441-message-5-trade-order-00541).

<iframe
  src="https://stichting-sivi.github.io/VBPUOdsk-docs-prepare/assets/berichtstructuur-05-orderopdracht.html"
  width="100%"
  height="380"
  style="border: 1px solid #ddd; border-radius: 4px; display: block;"
  title="Message structure 5. Trade Order (00541)">
</iframe>

#### 6.4.7 Message structure 6. Order Confirmation (00542)

See also [4.2](../chapter-4-fpr-processes/#42-model-1-simpler-direct-order-model) & [4.4.2](../chapter-4-fpr-processes/#442-message-6-order-confirmation-00542).

<iframe
  src="https://stichting-sivi.github.io/VBPUOdsk-docs-prepare/assets/berichtstructuur-06-orderconfirmation.html"
  width="100%"
  height="380"
  style="border: 1px solid #ddd; border-radius: 4px; display: block;"
  title="Message structure 6. Order Confirmation (00542)">
</iframe>

The following fields under `financialTransaction.trade` have been changed from required to optional: `tradeQuantity`, `tradePrice`, `counterparty`, `broker`, `interestAmount`, `commissionAmount`, `clearingBroker` and `clearingBrokerCashAccount`. `tradeAmount` remains required. See GitHub issue [#105](https://github.com/Stichting-SIVI/VBPUOdsk/issues/105).

#### 6.4.8 – 6.4.10 Messages 7, 8, 9 (Discontinued)

**Discontinued from release 2027.** Messages 7 (Balance Adjustments / 00551), 8 (Reconciliation Information / 00552a) and 9 (PUO Reconciliation Information / 00552b) are no longer active in the release 2027 message set. See GitHub issues [#99](https://github.com/Stichting-SIVI/VBPUOdsk/issues/99), [#119](https://github.com/Stichting-SIVI/VBPUOdsk/issues/119), [#121](https://github.com/Stichting-SIVI/VBPUOdsk/issues/121).

#### 6.4.11 Message structure 10. Control Information Investment Pools (00553)

From release 2027, the `cohortPool` layer has been removed from this message; data lands directly at `investment.pool` level. See GitHub issue [#124](https://github.com/Stichting-SIVI/VBPUOdsk/issues/124).

Additionally, the following fields of entity `investment.pool` have been removed from message 00553: `dummyCashId`, `tradeQuantity`, `unitPrice` and `currencyExchangeRate`. The fields `buySellId`, `tradeValueAmount` and `currencyType` remain active. See GitHub issue [#133](https://github.com/Stichting-SIVI/VBPUOdsk/issues/133).

See also [4.3](../chapter-4-fpr-processes/#43-model-2-extended-layered-order-model) & [4.5.3](../chapter-4-fpr-processes/#453-message-10-control-information-investment-pools-00553).

<iframe
  src="https://stichting-sivi.github.io/VBPUOdsk-docs-prepare/assets/berichtstructuur-10-stuurinformatiebeleggingspools.html"
  width="100%"
  height="380"
  style="border: 1px solid #ddd; border-radius: 4px; display: block;"
  title="Message structure 10. Control Information Investment Pools (00553)">
</iframe>

#### 6.4.12 – 6.4.13 Messages 11, 12 (Discontinued)

**Discontinued from release 2027.** Messages 11 (Rebalancing Details / 00554) and 12 (Value Information Cohort Pool / 00555a) are no longer active in the release 2027 message set. See GitHub issues [#99](https://github.com/Stichting-SIVI/VBPUOdsk/issues/99), [#119](https://github.com/Stichting-SIVI/VBPUOdsk/issues/119), [#121](https://github.com/Stichting-SIVI/VBPUOdsk/issues/121).

#### 6.4.14 Message structure 13. Value Information Investment Pool (00555b)

See also [4.3](../chapter-4-fpr-processes/#43-model-2-extended-layered-order-model) & [4.5.5.2](../chapter-4-fpr-processes/#4552-message-13-value-information-investment-pool-00555b).

<iframe
  src="https://stichting-sivi.github.io/VBPUOdsk-docs-prepare/assets/berichtstructuur-13-waarde-informatie-beleggingspool.html"
  width="100%"
  height="380"
  style="border: 1px solid #ddd; border-radius: 4px; display: block;"
  title="Message structure 13. Value Information Investment Pool (00555b)">
</iframe>

#### 6.4.15 Message structure 14. Payment Information (00556)

See also [4.3](../chapter-4-fpr-processes/#43-model-2-extended-layered-order-model) & [4.5.6](../chapter-4-fpr-processes/#456-message-14-payment-information-00556).

<iframe
  src="https://stichting-sivi.github.io/VBPUOdsk-docs-prepare/assets/berichtstructuur-14-betaalinformatie.html"
  width="100%"
  height="400"
  style="border: 1px solid #ddd; border-radius: 4px; display: block;"
  title="Message structure 14. Payment Information (00556)">
</iframe>

#### 6.4.16 Message structure 15. Corporate Actions (00557)

<iframe
  src="https://stichting-sivi.github.io/VBPUOdsk-docs-prepare/assets/berichtstructuur-15-corporate-actions.html"
  width="100%"
  height="380"
  style="border: 1px solid #ddd; border-radius: 4px; display: block;"
  title="Message structure 15. Corporate Actions (00557)">
</iframe>

#### 6.4.17 Message structure Feedback Message

See also [4.7](../chapter-4-fpr-processes/#47-feedback-message).

<iframe
  src="https://stichting-sivi.github.io/VBPUOdsk-docs-prepare/assets/berichtstructuur-feedback-message.html"
  width="100%"
  height="300"
  style="border: 1px solid #ddd; border-radius: 4px; display: block;"
  title="Message structure Feedback Message">
</iframe>

Notes:

- The initial message is not sent along with the feedback message.
- In the feedback message, a reference is **always** made to the messageId (via **originalMessageId**) of the message to which the feedback message is a response, and **may** reference the messageType (via **originalMessageType**).

[^7]: Eindrapport onderzoek standaard VB PUO (september 2023.pdf. zie: [SIVI/Downloads](https://www.sivi.org/pensioen/standaard-data-uitwisseling-vermogensbeheer-en-pensioenuitvoering/)

[^8]: [Zie: OAS (Open API Specificaties)](https://github.com/dma61/VBPUOdsk/tree/main/OAS%20(Open%20API%20Specificaties)%20IN%20ONTWIKKELING)
