## 8.4 Translation Table from Functional Attributes to AFD 2.0 Attributes

> **Note:** The translation table below is in Dutch. It maps functional attribute names from the consultation report to the final AFD 2.0 data element names.
>
> **NL → EN Legend for table headers:**
>
> | Dutch | English |
> |-------|---------|
> | Attribuutnaam Functioneel | Functional Attribute Name |
> | AFD 2.0 entity.entitytype | AFD 2.0 entity.entitytype |
> | AFD 2.0 attribuutnaam | AFD 2.0 attribute name |
> | Omschrijving | Description |

In the consultation report, different attribute names were used in various places than in the final AFD 2.0 model. Below is an overview of the functional attribute names and the final AFD 2.0 data element names.

<table>
<colgroup>
<col style="width: 19%" />
<col style="width: 13%" />
<col style="width: 21%" />
<col style="width: 45%" />
</colgroup>
<thead>
<tr>
<th><strong>Attribuutnaam Functioneel</strong></th>
<th><strong>AFD 2.0 entity.entitytype</strong></th>
<th><strong>AFD 2.0 attribuutnaam</strong></th>
<th><strong>Omschrijving</strong></th>
</tr>
</thead>
<tbody>
<tr>
<th>Transfer ID</th>
<td>commonTechnical.default</td>
<td>messageId</td>
<td>Unieke berichtidentificatie</td>
</tr>
<tr>
<th>Pensionfund ID</th>
<td>party.pensionProvider</td>
<td>puvCode</td>
<td>ID van het pensioenuitvoerder (PUV-code) / Unique reference key assigned to an entity. (NL: Entiteitsreferentie is een unieke referentie sleutel die aan een entiteit wordt toegekend.)</td>
</tr>
<tr>
<th>Pension scheme ID i</th>
<td>pension.scheme</td>
<td>refKey</td>
<td>ID van de pensioenregeling / (Unique reference key assigned to an entity. (NL: Entiteitsreferentie is een unieke referentie sleutel die aan een entiteit wordt toegekend.))</td>
</tr>
<tr>
<th>Capital i</th>
<td>pension.scheme</td>
<td>startAmount</td>
<td>Totaal pensioenvermogen per startdatum</td>
</tr>
<tr>
<th>Portfolio</th>
<td>pension.scheme</td>
<td>tradingPortfolioId</td>
<td>Portefeuille ID van de custodian (bewaren en beheren van financiële activa)</td>
</tr>
<tr>
<th>Capital date i / Start date PUO admin / Start date Investment Report</th>
<td>financialInformation.reportingPeriod</td>
<td>startDate</td>
<td>Begindatum van de gegevensperiode waarop de aanlevering vanuit de PUO wordt gebaseerd of Peildatum</td>
</tr>
<tr>
<th>End date PUO admin</th>
<td>financialInformation.reportingPeriod</td>
<td>endDate</td>
<td>Einddatum van de gegevensperiode waarop de aanlevering vanuit de PUO wordt gebaseerd</td>
</tr>
<tr>
<th>Mutations date</th>
<td>financialInformation.reportingPeriod</td>
<td>mutationValuationDate</td>
<td>Datum verwerking mutaties per leeftijdsgroep</td>
</tr>
<tr>
<th>End date​ Investment Report</th>
<td>financialInformation.reportingPeriod</td>
<td>endDate</td>
<td>Einddatum van de gegevensperiode waarover rendement wordt gerapporteerd</td>
</tr>
<tr>
<th>Trade date</th>
<td>financialInformation.reportingPeriod</td>
<td>tradeDate</td>
<td>Gewenste handelsdatum</td>
</tr>
<tr>
<th>Settlement date</th>
<td>financialInformation.reportingPeriod</td>
<td>investmentOrderSettlementDate</td>
<td>Datum waarop de volledige cyclus van de beleggingsorder afgewikkeld moet zijn</td>
</tr>
<tr>
<th>Projection date</th>
<td>financialInformation.reportingPeriod</td>
<td>projectionDate</td>
<td>Datum van de projectie van pensioenuitkeringen</td>
</tr>
<tr>
<th>instruction date</th>
<td>financialInformation.reportingPeriod</td>
<td>instructionDate</td>
<td>Instructiedatum (datum van de bestelling verzonden door de PUO)</td>
</tr>
<tr>
<th>Estimation date</th>
<td>financialInformation.reportingPeriod</td>
<td>unitValueEstimationDate</td>
<td>Geeft de datum aan waarop de voorlopige unitwaarde (belegginspool) is bepaald</td>
</tr>
<tr>
<th>Valuation date</th>
<td>financialInformation.reportingPeriod</td>
<td>participationValuationDate</td>
<td>Prijsdatum participatiewaarde (cohortpool)</td>
</tr>
<tr>
<th>value date</th>
<td>financialInformation.reportingPeriod</td>
<td>valueDate</td>
<td>Currency date. (NL: Valutadatum)</td>
</tr>
<tr>
<th>Date</th>
<td>financialInformation.reportingPeriod</td>
<td>positionDate</td>
<td>De datum waarop de posities in de beleggingsadministratie zijn vastgesteld</td>
</tr>
<tr>
<th>Value</th>
<td>financialTransaction.payment</td>
<td>amount</td>
<td>Bedrag in valuta</td>
</tr>
<tr>
<th>currency i</th>
<td>financialTransaction.payment</td>
<td>currencyType</td>
<td>Valuta</td>
</tr>
<tr>
<th>IBAN debet i</th>
<td>financialTransaction.payment</td>
<td>collectionAccountIban</td>
<td>IBAN-nummer van debet rekening</td>
</tr>
<tr>
<th>Description i</th>
<td>financialTransaction.payment</td>
<td>description</td>
<td>Omschrijving van de transactie (betaling)</td>
</tr>
<tr>
<th>IBAN credit i</th>
<td>party.creditor</td>
<td>collectionAccountIban</td>
<td>IBAN-nummer van credit rekening per regeling</td>
</tr>
<tr>
<th>Counterparty i</th>
<td>party.creditor</td>
<td>collectionAccountInNameOf</td>
<td>Naam van de tegenpartij per regeling</td>
</tr>
<tr>
<th>BIC i</th>
<td>party.creditor</td>
<td>collectionAccountBic</td>
<td>Business Identifier Code (BIC) per regeling</td>
</tr>
<tr>
<th>BIC-correspondent i</th>
<td>party.creditor</td>
<td>collectionAccountBicCorrespondent</td>
<td>BIC-correspondent per regeling</td>
</tr>
<tr>
<th>Contribution i</th>
<td>financialTransaction.cashflow</td>
<td>contributionAmount</td>
<td>Som van inleg</td>
</tr>
<tr>
<th>Contribution date i</th>
<td>financialTransaction.cashflow</td>
<td>contributionDate</td>
<td>Datum van ontvangst van de inleg</td>
</tr>
<tr>
<th>Withdrawal i</th>
<td>financialTransaction.cashflow</td>
<td>withdrawalAmount</td>
<td>Som van de uitstroom</td>
</tr>
<tr>
<th>Withdrawal date i</th>
<td>financialTransaction.cashflow</td>
<td>withdrawalDate</td>
<td>Datum waarop (uiterlijk) de liquiditeiten ten behoeve van de onttrekking zijn vrijgemaakt</td>
</tr>
<tr>
<th>Net contribution/withdrawal i</th>
<td>financialTransaction.cashflow</td>
<td>netAmount</td>
<td>Som van inleg en onttrekkingen per regeling (net). Een negatief bedrag is een (netto) withdrawal. / Verschil tussen inleg en onttrekking. Een negatief bedrag is een (netto) onttrekking.)</td>
</tr>
<tr>
<th>Net contribution/withdrawal<br />
date i</th>
<td>financialTransaction.cashflow</td>
<td>netDate</td>
<td>Datum waarop gesaldeerde instroom en uitstroom wordt gefaciliteerd / Datum waarop het saldo van inleg en onttrekking is bepaald</td>
</tr>
<tr>
<th>Cohort ID i, k</th>
<td>financialTransaction.payment</td>
<td>refKey</td>
<td>ID van de expected payment</td>
</tr>
<tr>
<th>Expected pension payment Date i, k</th>
<td>financialTransaction.payment</td>
<td>expectedPensionPaymentDate</td>
<td>Pensioenuitkeringsmoment</td>
</tr>
<tr>
<th>Hedged expected pension payment i,k</th>
<td>financialTransaction.payment</td>
<td>hedgedExpectedPensionPaymentAmount</td>
<td>Af te dekken kasstroom over alle cohorten</td>
</tr>
<tr>
<th>Cohort expected pension payment i,j,k</th>
<td>financialTransaction.payment</td>
<td>amount</td>
<td>Geprojecteerde uitkering over alle cohorten</td>
</tr>
<tr>
<th>Cohort ID i, k</th>
<td>pension.cohort</td>
<td>refKey</td>
<td>ID van het cohort</td>
</tr>
<tr>
<th>Cohort Capital i,k</th>
<td>pension.cohort</td>
<td>startAmount</td>
<td>Pensioenvermogen van het cohort per begindatum</td>
</tr>
<tr>
<th>Net contribution/withdrawal I,k</th>
<td>pension.cohort</td>
<td>netAmount</td>
<td>Som van inleg en onttrekkingen per cohort. Een negatief bedrag is een (netto) onttrekking.)</td>
</tr>
<tr>
<th>Cohort contribution i,k</th>
<td>pension.cohort</td>
<td>contributionAmount</td>
<td>Instroom te beleggen door de fiduciair manager</td>
</tr>
<tr>
<th>Cohort withdrawal i,k</th>
<td>pension.cohort</td>
<td>withdrawalAmount</td>
<td>Uitstroom te beleggen door de fiduciair manager</td>
</tr>
<tr>
<th>Cohort return rate protection i,k</th>
<td>pension.cohort</td>
<td>protectionReturnPercentage</td>
<td>Het behaalde beschermingsrendement in percentage over gegevensperiode per regeling en per cohort</td>
</tr>
<tr>
<th>Cohort return rate excess i,k</th>
<td>pension.cohort</td>
<td>excessReturnPercentage</td>
<td>Het behaalde overrendement in percentage over gegevensperiode per regeling en per cohort</td>
</tr>
<tr>
<th>Cohort return protection i,k</th>
<td>pension.cohort</td>
<td>protectionReturnAmount</td>
<td>Het behaalde beschermingsrendement in valuta van de regeling over gegevensperiode per regeling en per cohort</td>
</tr>
<tr>
<th>Cohort return excess i,k</th>
<td>pension.cohort</td>
<td>excessReturnAmount</td>
<td>Het behaalde overrendement in valuta van de regeling over gegevensperiode per regeling en per cohort</td>
</tr>
<tr>
<th>Hedged expected pension payment i,k</th>
<td>financialTransaction.payment</td>
<td>hedgedExpectedPensionPaymentAmount</td>
<td>Af te dekken kasstroom</td>
</tr>
<tr>
<th>Cohort expected pension payment i,j,k</th>
<td>financialTransaction.payment</td>
<td>amount</td>
<td>Geprojecteerde uitkering</td>
</tr>
<tr>
<th>Cohort ID i, k</th>
<td>pension.cohortPool</td>
<td>cohortRef</td>
<td>Geeft aan op welk cohort in de regeling de cohortpool-gegevens betrekking hebben</td>
</tr>
<tr>
<th>Cohort Inflow i-k (1)</th>
<td>pension.cohortPool</td>
<td>inflowPremiumAmount</td>
<td>Premie-inleg per cohortpool per regeling</td>
</tr>
<tr>
<th>Cohort Inflow i-k (2)</th>
<td>pension.cohortPool</td>
<td>inflowRebalanceAmount</td>
<td>Geldbedrag van rebalance transacties per cohortpool per regeling</td>
</tr>
<tr>
<th>Cohort withdrawal i,k</th>
<td>pension.cohortPool</td>
<td>numberOfNewParticipations</td>
<td>Nieuwe uit te geven participaties in cohortpool per regeling (instroom)</td>
</tr>
<tr>
<th>Number of units, i,k</th>
<td>pension.cohortPool</td>
<td>numberOfParticipations</td>
<td>Aantal uitstaande units (participaties) in de Cohortpool</td>
</tr>
<tr>
<th>Cohort rebalance i,k</th>
<td>pension.cohortPool</td>
<td>numberOfRebalanceParticipations</td>
<td>Rebalance participaties per cohortpool per regeling (bij overgang van een cohortpool naar een ander cohort)</td>
</tr>
<tr>
<th>Cohort Capital i,k / Cohort value i, k</th>
<td>pension.cohortPool</td>
<td>participationsSummedValueAmount</td>
<td>Waarde per cohortpool (som participatiewaarde) per participationValuationDate</td>
</tr>
<tr>
<th>Pool ID i,j</th>
<td>investment.pool</td>
<td>refKey</td>
<td>ID van de beleggingspool per regeling</td>
</tr>
<tr>
<th>Market value portfolio</th>
<td>investment.pool</td>
<td>marketValueAmount</td>
<td>Marktwaarde per portefeuille per regeling in currencyType</td>
</tr>
<tr>
<th>Pool value i, k</th>
<td>investment.pool</td>
<td>unitsSummedValueAmount</td>
<td>Waarde per beleggingspool(unitwaarde)</td>
</tr>
<tr>
<th>Market value instrument</th>
<td>investment.pool</td>
<td>marketValueAmount</td>
<td>Marktwaarde van de beleggingspool in currencyType van de pool</td>
</tr>
<tr>
<th>Preliminary market value i, k</th>
<td>investment.pool</td>
<td>preliminaryMarketValueAmount</td>
<td>Voorlopige Marktwaarde per portefeuille per regeling in currencyType van de pool</td>
</tr>
<tr>
<th>Preliminary pool value i, k</th>
<td>investment.pool</td>
<td>preliminaryUnitValueAmount</td>
<td>Dagelijks vastgestelde unitprijs/NAV in currencyType van de pool</td>
</tr>
<tr>
<th>number of units investment pool i,k</th>
<td>investment.pool</td>
<td>numberOfUnits</td>
<td>Aantal units uitgegeven voor de beleggingspool,</td>
</tr>
<tr>
<th>currency i,j</th>
<td>investment.pool</td>
<td>currencyType</td>
<td>Valuta van de pool</td>
</tr>
<tr>
<th>Transaction description i,j, k /Description</th>
<td>investment.pool</td>
<td>description</td>
<td>Beschrijving</td>
</tr>
<tr>
<th>Dummy cash ID</th>
<td>investment.pool</td>
<td>dummyCashId</td>
<td>ID voor dummy cash instrument per beleggingspool per regeling per cohort(pool)</td>
</tr>
<tr>
<th>Sell buy ID i,j, k</th>
<td>investment.pool</td>
<td>buySellId</td>
<td>Aan- verkoopindicator; ID voor aan-/verkoop per beleggingspool per regeling per cohort</td>
</tr>
<tr>
<th>Amount i,j, k</th>
<td>investment.pool</td>
<td>tradeQuantity</td>
<td>Aantal te verhandelen stukken (units) van de transactie</td>
</tr>
<tr>
<th>Unit value i,j, k</th>
<td>investment.pool</td>
<td>unitPrice</td>
<td>Unitwaarde (/prijs) per beleggingspool per regeling per cohort</td>
</tr>
<tr>
<th>FX rate i,j, k</th>
<td>investment.pool</td>
<td>currencyExchangeRate</td>
<td>FX rate per beleggingspool per regeling per cohort</td>
</tr>
<tr>
<th>Value i,k</th>
<td>investment.pool</td>
<td>tradeValueAmount</td>
<td>Waarde transactie per beleggingspool per regeling (gesommeerd over cohorten)</td>
</tr>
<tr>
<th>portfolio ID i,n</th>
<td>investment.portfolio</td>
<td>refKey</td>
<td>ID Beleggingsportefeuille / Unique reference key assigned to an entity. (NL: Entiteitsreferentie is een unieke referentie sleutel die aan een entiteit wordt toegekend.)</td>
</tr>
<tr>
<th>Total Market Value start I,n</th>
<td>investment.portfolio</td>
<td>startAmount</td>
<td>De waarde van de Total Market Value aan het begin van de gegevensperiode</td>
</tr>
<tr>
<th>Net contribution/withdrawal I, n</th>
<td>investment.portfolio</td>
<td>netAmount</td>
<td>Som van inleg en onttrekkingen per regeling (net). Een negatief bedrag is een (netto) withdrawal</td>
</tr>
<tr>
<th>Total Market Value end I,n</th>
<td>investment.portfolio</td>
<td>endAmount</td>
<td>De waarde van de Total Market Value aan het eind van de gegevensperiode. Per regeling en beleggingsportefeuille</td>
</tr>
<tr>
<th>Return rate i,n​</th>
<td>investment.portfolio</td>
<td>returnPercentage</td>
<td>Het behaalde rendement in percentage over gegevensperiode per regeling en per beleggingsportefeuille</td>
</tr>
<tr>
<th>Return i,n​</th>
<td>investment.portfolio</td>
<td>returnAmount</td>
<td>Het behaalde rendement in valuta van de regeling over gegevensperiode per regeling en per beleggingsportefeuille</td>
</tr>
<tr>
<th>Identifier</th>
<td>investment.investmentDetails</td>
<td>refKey</td>
<td>Identifier (bijvoorbeeld ISIN of interne code)</td>
</tr>
<tr>
<th>Fund Name i</th>
<td>investment.investmentDetails</td>
<td>description</td>
<td>De naam van de belegging / de officiële naam van het fonds / van het instrument</td>
</tr>
<tr>
<th>Local Price i,j, k</th>
<td>investment.investmentDetails</td>
<td>currencyType</td>
<td>Valuta van het instrument</td>
</tr>
<tr>
<th>Total holdings i,j, k</th>
<td>investment.investmentDetails</td>
<td>numberOfHoldings</td>
<td>Aantal holdings per instrument per regeling per beleggingsportefeuille</td>
</tr>
<tr>
<th>Local Price i,j, k</th>
<td>investment.investmentDetails</td>
<td>localPrice</td>
<td>Prijs per instrument in originele valuta per regeling per beleggingsportefeuille</td>
</tr>
<tr>
<th>Local Value instrument i,j, k</th>
<td>investment.investmentDetails</td>
<td>localValueAmount</td>
<td>Totale marktwaarde in originele valuta per instrument per regeling per beleggingsportefeuille</td>
</tr>
<tr>
<th>Result i,j, k</th>
<td>investment.investmentDetails</td>
<td>result</td>
<td>Ongerealiseerd resultaat per instrument per regeling per beleggingsportefeuille</td>
</tr>
<tr>
<th>Accrued Interest i,j, k</th>
<td>investment.investmentDetails</td>
<td>accruedInterest</td>
<td>Opgelopen rente per instrument per regeling per beleggingsportefeuille</td>
</tr>
<tr>
<th>Portfolio weight i,j, k</th>
<td>investment.investmentDetails</td>
<td>poolPercentage</td>
<td>Gewicht in de portefeuille per instrument per regeling per beleggingsportefeuille</td>
</tr>
<tr>
<th>FX rate i,j, k</th>
<td>investment.investmentDetails</td>
<td>currencyExchangeRate</td>
<td>FX rates per instrument per regeling per beleggingsportefeuille / koers per positionDate</td>
</tr>
<tr>
<th>Trade date / Transaction date</th>
<td>financialTransaction.trade</td>
<td>tradeDate</td>
<td>Gewenste handelsdatum</td>
</tr>
<tr>
<th>Adj Trade i, j</th>
<td>financialTransaction.trade</td>
<td>adjustmentIndicator</td>
<td>Aangepaste trade instructie</td>
</tr>
<tr>
<th>Buy/Sell i,j</th>
<td>financialTransaction.trade</td>
<td>buySellId</td>
<td>Aan- verkoop- switchindicator</td>
</tr>
<tr>
<th>Amount</th>
<td>financialTransaction.trade</td>
<td>tradeAmount</td>
<td>Bedrag van de aankoop in de valuta waarin de belegging luidt</td>
</tr>
<tr>
<th>Quantity</th>
<td>financialTransaction.trade</td>
<td>tradeQuantity</td>
<td>Aantal te verhandelen stukken (units) van de transactie</td>
</tr>
<tr>
<th>Price i,j</th>
<td>financialTransaction.trade</td>
<td>tradePrice</td>
<td>Aankoopprijs / koers</td>
</tr>
<tr>
<th>Switch type</th>
<td>financialTransaction.trade</td>
<td>switchType</td>
<td>Type switch; one-day of sequential</td>
</tr>
<tr>
<th>Counterparty i,j</th>
<td>financialTransaction.trade</td>
<td>counterparty</td>
<td>Transfer Agent; de partij die de aankoop/verkoop verricht</td>
</tr>
<tr>
<th>Broker i,j</th>
<td>financialTransaction.trade</td>
<td>broker</td>
<td>Effectenmakelaar die beleggingsorders uitvoert namens klanten op de markt</td>
</tr>
<tr>
<th>Interest i,j</th>
<td>financialTransaction.trade</td>
<td>interestAmount</td>
<td>Bedrag aan van toepassing zijnde rente</td>
</tr>
<tr>
<th>Commission i, j</th>
<td>financialTransaction.trade</td>
<td>commissionAmount</td>
<td>Vergoeding voor het uitvoeren van de transactie</td>
</tr>
<tr>
<th>Clearing broker i,j</th>
<td>financialTransaction.trade</td>
<td>clearingBroker</td>
<td>Effectenmakelaar verantwoordelijk administratieve en financiële afwikkeling van de transactie</td>
</tr>
<tr>
<th>Cash account i,j</th>
<td>financialTransaction.trade</td>
<td>clearingBrokerCashAccount</td>
<td>Geldrekening (IBAN) bij de clearingbroker op naam van de Pensioenuitvoerder</td>
</tr>
</tbody>
</table>
