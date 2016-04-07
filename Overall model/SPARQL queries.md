# Example Queries

## Query results can be retrieved by the following google spreadsheet,
https://docs.google.com/spreadsheets/d/1pbxI1_ScQhLCAavwFg68RLxhAs0QNHpyOx9SKb5Wm54/edit

## A. Geospatial Data

### Q1. All resources inside a bounding box
```
PREFIX geo: <http://www.opengis.net/ont/geosparql#>
PREFIX elod: <http://linkedeconomy.org/ontology#>

SELECT distinct ?subject ?gWKT
WHERE {
    ?subject elod:hasRelatedFeature ?feature .
    ?feature geo:hasGeometry ?geometry .
    ?geometry geo:asWKT ?gWKT .
    FILTER (bif:st_within(?gWKT, "POLYGON ((23.533692 41.095936,23.613343 41.089727,23.671021 41.063846,23.730073 41.042098))"^^geo:wktLiteral)) 
}
```

### Q2. Addresses and postal codes for Organizations
```
select distinct ?name ?street ?pcode from <http://yourdatastories.eu/NSRF/Diavgeia>
where {
  ?organization gr:legalName ?name ; vcard2006:hasAddress ?address . 
  ?address vcard2006:street-address ?street ;
  vcard2006:postal-code ?pcode .
}
```
### Q3. Postal Codes of Organizations and the Municipalities they belong to
```
PREFIX vcard2006: <http://www.w3.org/2006/vcard/ns#>
PREFIX elodGeo: <http://linkedeconomy.org/geoOntology#>

SELECT DISTINCT ?pcode ?nameMunicipality
FROM <http://yourdatastories.eu/NSRF/Diavgeia>
WHERE {
  ?organization vcard2006:hasAddress ?address .
  ?address vcard2006:postal-code ?pcode.
  ?codeArea elodGeo:postalCode ?pcode .
  ?municipality elodGeo:hasPart ?codeArea ; elodGeo:name ?nameMunicipality . 
}
```
## B. CPV Queries

### Q1. Information for specific CPV
```
SELECT distinct ?p ?o 
from <http://yourdatastories.eu/NSRF/Diavgeia>
WHERE {
	?s elod:hasCpv <http://linkedeconomy.org/resource/CPV/45233140-2>. 
	<http://linkedeconomy.org/resource/CPV/45233140-2> ?p ?o
}
```

### Q2. CPV codes from Decisions of NSRF Projects 
```
select distinct ?cpv (str(?code) as ?cpvCode) (str(?subject) as ?cpvSubject)
from <http://yourdatastories.eu/NSRF/Diavgeia> 
where {
?cpv a elod:CPV. 
?cpv elod:cpvCode ?code ; elod:cpvEnglishSubject ?subject
}
```

## C. Project profile 

### Q1. Single Project Info NSRF
```
select distinct ?project ?percComplete (xsd:decimal(?prBudget) as ?priceBudget)
from <http://yourdatastories.eu/NSRF/Diavgeia>
where {
  ?project elod:hasRelatedAdministrativeDecision ?decision ; dcterms:title ?title ;
  elod:hasRelatedBudgetItem ?revBudget ;  elod:completion ?percComplete . 
  ?revBudget elod:price ?revUps . 
  ?revUps gr:hasCurrencyValue ?prBudget. 
} 
group by ?project
```

### Q2. Single Project Info Diavgeia
```
select distinct ((count(distinct ?decision)) + (count(distinct ?decisionFinancial)) 
+ (count(distinct ?decisionFinancialb13))
+ (count(distinct ?decisionFinancial2))  
+(count(distinct ?decisionFinancial3))
as ?decisionCount) 
((sum(xsd:decimal(?am))) + (sum(xsd:decimal(?amContr))) 
+ (sum(xsd:decimal(?amContr2)))
+ (sum(xsd:decimal(?amb13))) 
as ?amount)
from <http://yourdatastories.eu/NSRF/Diavgeia>
where {
{
<http://linkedeconomy.org/resource/Subsidy/372069> elod:hasRelatedAdministrativeDecision ?decisionFinancial .
?decisionFinancial a elod:FinancialDecision ; elod:hasExpenditureLine ?expLine . 
?expLine elod:amount ?ups . ?ups gr:hasCurrencyValue ?am
filter not exists {?decisionFinancial elod:hasCorrectedDecision ?corrected}
}
union
{
<http://linkedeconomy.org/resource/Subsidy/372069> elod:hasRelatedAdministrativeDecision ?decisionFinancialb13 .
?decisionFinancialb13 a elod:FinancialDecision ;  elod:price ?upsb13 . ?upsb13 gr:hasCurrencyValue ?amb13
filter not exists {?decisionFinancialb13 elod:hasCorrectedDecision ?correctedb13}
}
union
{
<http://linkedeconomy.org/resource/Subsidy/372069> elod:hasRelatedAdministrativeDecision ?decisionFinancial2 .
?decisionFinancial2 a elod:FinancialDecision ;  pc:agreedPrice ?upsContr . ?upsContr gr:hasCurrencyValue ?amContr
filter not exists {?decisionFinancial2 elod:hasCorrectedDecision ?corrected2}
}
union
{
<http://linkedeconomy.org/resource/Subsidy/372069> elod:hasRelatedAdministrativeDecision ?decisionFinancial3 .
?decisionFinancial3 a elod:FinancialDecision ;  pc:documentsPrice ?upsContr2 . ?upsContr2 gr:hasCurrencyValue ?amContr2
filter not exists {?decisionFinancial3 elod:hasCorrectedDecision ?corrected3}
}
union
{
<http://linkedeconomy.org/resource/Subsidy/372069> elod:hasRelatedAdministrativeDecision ?decision.
?decision a elod:NonFinancialDecision
filter not exists {?decision elod:hasCorrectedDecision ?corrected5}
}
}
```

## D. Diavgeia Descriptive Stats 

### Q1. Financial Decisions of a specific Public Project
```
select distinct ?type (count(distinct ?decision) as ?count) (sum(xsd:decimal(?am)) as ?amount)
from <http://yourdatastories.eu/NSRF/Diavgeia>
where {
  <http://linkedeconomy.org/resource/Subsidy/372069> elod:hasRelatedAdministrativeDecision ?decision .
  ?decision a elod:FinancialDecision ; elod:decisionType ?type ;
  elod:hasExpenditureLine ?expLine . 
  ?expLine elod:amount ?ups . ?ups gr:hasCurrencyValue ?am
  filter langMatches(lang(?type),'el')
}
```

### Q2. Decisions of a specific decision type - Δ category
```
select distinct ?type (count(distinct ?decision) as ?count) (sum(xsd:decimal(?amContr)) as ?amount2)
from <http://yourdatastories.eu/NSRF/Diavgeia>
where {
  <http://linkedeconomy.org/resource/Subsidy/372069> elod:hasRelatedAdministrativeDecision ?decision .
  ?decision pc:agreedPrice ?ups ; elod:decisionType ?type . 
  ?ups gr:hasCurrencyValue ?amContr .
  filter langMatches(lang(?type),'el')
}
```

### Q3. Non-Financial Decisions of a specific Public Project
```
select distinct (str(?type) as ?type1) (count(distinct ?decision) as ?count)
from <http://yourdatastories.eu/NSRF/Diavgeia>
where {
  <http://linkedeconomy.org/resource/Subsidy/372069> elod:hasRelatedAdministrativeDecision ?decision .
  ?decision a elod:NonFinancialDecision ; elod:decisionType ?type .
}
order by desc (?count)
```

## E. NSRF descriptive Stats

### Q1. Detailed information of a Public Project
```
select distinct ?titleProject ?description ?percComplete
(xsd:decimal(?prBudget) as ?priceBudget) (xsd:decimal(?prSpend) as ?priceSpend) 
(str(?startDate) as ?starts) (str(?endDate) as ?ends) 
from <http://yourdatastories.eu/NSRF/Diavgeia>
where {
  <http://linkedeconomy.org/resource/Subsidy/372069> dcterms:title ?titleProject ; 
  dcterms:description ?description ;
  elod:hasRelatedBudgetItem ?revBudget ; elod:hasRelatedSpendingItem ?revSpend ; 
  elod:completion ?percComplete ; elod:startDate ?startDate ; elod:endDate ?endDate. 
  ?revBudget elod:price ?revUps . ?revUps gr:hasCurrencyValue ?prBudget. 
  ?revSpend elod:hasExpenditureLine ?expSpend . 
  ?expSpend elod:amount ?upsSpend . ?upsSpend gr:hasCurrencyValue ?prSpend
  filter langMatches(lang(?titleProject),'el')
  filter langMatches(lang(?description),'el')
}
```

## F. Subprojects

### Q1. Subprojects (connected to Diavgeia) - Diavgeia data | query 1
```
select distinct ?subproject
(count(distinct ?decisionFinancial) as ?decisionFinancial)
(count (distinct ?decision) as ?nonFinancial)
(sum(xsd:decimal(?am)) as ?totalAmount)
from <http://yourdatastories.eu/NSRF/Diavgeia>
where {
  {
    ?subproject a elod:Subproject ; elod:hasRelatedAdministrativeDecision ?decisionFinancial .
    ?decisionFinancial a elod:FinancialDecision ; elod:hasExpenditureLine ?expLine . 
    ?expLine elod:amount ?ups . ?ups gr:hasCurrencyValue ?am .
  }
  union
  {
    ?subproject a elod:Subproject ; elod:hasRelatedAdministrativeDecision ?decision .
    ?decision a elod:NonFinancialDecision 
  }
}
```

## G. Overall Information of Data Model

### Q1. Class treemap
```
SELECT distinct *
WHERE {
	?s rdfs:subClassOf ?p
}
```

### Q2. Returns Properties of a specific Class
```
SELECT distinct ?property
WHERE {
	?subject a elod:Subsidy ; ?property ?object
}
```

### Q3. Domains of a Property
```
SELECT distinct ?class
WHERE {
	?subject a ?class ; elod:hasRelatedProject ?object
}
```

### Q4. NSRF descriptive stats for Public Projects which are related to Crete
```
select distinct ?project ?percComplete (str(?titleProject) as ?title)
(xsd:decimal(?prBudget) as ?priceBudget) (xsd:decimal(?prSpend) as ?priceSpend) 
(str(?startDate) as ?starts) (str(?endDate) as ?ends) 
from <http://yourdatastories.eu/NSRF/Diavgeia>
where {
  ?project dcterms:title ?titleProject ; dcterms:description ?description ;
  elod:hasRelatedBudgetItem ?revBudget ; elod:hasRelatedSpendingItem ?revSpend ; 
  elod:completion ?percComplete ; elod:startDate ?startDate ; elod:endDate ?endDate. 
  ?revBudget elod:price ?revUps . ?revUps gr:hasCurrencyValue ?prBudget. ?revSpend 
  elod:hasExpenditureLine ?expSpend . ?expSpend elod:amount ?upsSpend . ?upsSpend 
  gr:hasCurrencyValue ?prSpend
  FILTER regex(?titleProject, "Κρήτη", "i")
}
```

## H. Data Cube Implementation

### Q1. Return Dimension Properties
```
prefix qb:<http://purl.org/linked-data/cube#>
select distinct * 
from <http://yourdatastories.eu/Diavgeia/DataCube>
where {
	?s a qb:DimensionProperty 
} 
```

### Q2. Return Information about Observations
```
prefix qb:<http://purl.org/linked-data/cube#>
select distinct ?p ?o
from <http://yourdatastories.eu/Diavgeia/DataCube> 
where {
	?s a qb:Observation ; ?p ?o
}
```
### Q3. Return Information about Data Strcucture Definition
```
prefix qb:<http://purl.org/linked-data/cube#>
select distinct ?attribute ?compRequired ?attachment
from <http://yourdatastories.eu/Diavgeia/DataCube>
where {?s qb:attribute ?attribute ; 
  qb:componentRequired ?compRequired ; 
  qb:componentAttachment ?attachment  .
} 
```

## I. Sector of NSRF Public Projects

### Q1. Return public projects of a specific Sector
```
select distinct ?title
from <http://yourdatastories.eu/NSRF/Diavgeia> 
where {
  ?project elod:sector ?sector ; dcterms:title ?title . 
  ?sector skos:prefLabel "Road transport"^^xsd:string
  filter langMatches(lang(?title),'el')
}
```
### Q2. Count of Public Projects per Sector
```
select distinct ?sector ?label (count(distinct ?project) as ?count) 
from <http://yourdatastories.eu/NSRF/Diavgeia> 
where { 
  ?project elod:sector ?sector  . 
  ?sector skos:prefLabel ?label
}
```

### Q3. OECD CRS Code of NSRF Projects
```
select distinct *
from <http://yourdatastories.eu/NSRF/Diavgeia> 
where {
?project a elod:Subsidy ; elod:sector ?sector . 
?sector skos:prefLabel ?o
}
```

## J. Organizations

### Q1. Return the connection of Sellers from Projects to Organizations URIs and their related information
```
select distinct ?org ?vatId ?greekName ?engName
from <http://yourdatastories.eu/NSRF/Diavgeia>
where {
?subsidy elod:seller ?seller . ?seller rdfs:seeAlso ?org .
?org gr:vatID ?vatId ; gr:legalName ?greekName ; elod:translation ?engName
} 
```

### Q2. Return basic information of Spending Items and the connection of them to Public Projects and Subprojects
```
select distinct ?project ?date (str(?decisionType) as ?type)  (STR(SAMPLE(?buyerName)) as ?nameBuyer) (STR(SAMPLE(?sellerName)) as ?nameSeller)
(str(?subject) as ?decisionSubject) (xsd:decimal(?am) as ?amount) (str(?ada) as ?decisionAda)
from <http://yourdatastories.eu/NSRF/Diavgeia> 
where {
?project elod:hasRelatedAdministrativeDecision ?decision .
?decision elod:decisionTypeId ?type ; elod:ada ?ada ; elod:decisionType ?decisionType ; 
dcterms:subject ?subject ; dcterms:issued ?date ;
dcterms:publisher ?orgUnit .
OPTIONAL{?buyer org:hasUnit ?orgUnit OPTIONAL{?buyer gr:legalName ?buyerName .}}
OPTIONAL{?decision elod:hasExpenditureLine ?expLine OPTIONAL{?expLine elod:seller ?seller ; elod:amount ?ups . } 
OPTIONAL{?seller gr:legalName ?sellerName . }}
?ups gr:hasCurrencyValue ?am.
filter(?type = "Β.2.2"^^xsd:string) 
filter langMatches(lang(?decisionType),'el')
filter not exists {?decision elod:hasCorrectedDecision ?corrected}
} limit 100
```

## K. Official Development Aid
### Q1. How much did the NL spend on ODA related to Zimbabwe in the time frame 2009-2012?

```
PREFIX elod: <http://linkedeconomy.org/ontology#>

SELECT (SUM(?value) AS ?totalDisbursement)
FROM <http://yourdatastories.eu/pilot2>
WHERE {
    ?activity elod:startDate ?startDate;
              elod:benefactor ?benefactor;
              elod:beneficiary ?beneficiary;
              elod:countryIsoCode <http://linkedeconomy.org/resource/Country/ZW>;
              elod:hasRelatedDisbursedItem ?disbursement.
    ?benefactor elod:countryIsoCode <http://linkedeconomy.org/resource/Country/NL>.
    ?disbursement elod:amount ?amount.
    ?amount elod:hasCurrencyValue ?value.
FILTER (?startDate >= "2009-01-01"^^xsd:date && ?startDate < "2013-01-01"^^xsd:date)
}
```

### Q2.1 What sectors was this money spent on (e.g., human rights, infrastructure, health, etc.)...

```
PREFIX elod: <http://linkedeconomy.org/ontology#>
PREFIX dct: <http://purl.org/dc/terms/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT ?activityId ?activityTitle ?sector
FROM <http://yourdatastories.eu/pilot2> 
WHERE {
    ?activity elod:countryIsoCode <http://linkedeconomy.org/resource/Country/ZW>;
              elod:benefactor ?benefactor;          
              elod:projectId ?activityId;
              dct:title ?activityTitle;
              elod:startDate ?startDate;
              elod:sector ?sectorCode.
    ?benefactor elod:countryIsoCode <http://linkedeconomy.org/resource/Country/NL>.
    ?sectorCode skos:prefLabel ?sector.
    FILTER (?startDate >= "2009-01-01"^^xsd:date && ?startDate < "2013-01-01"^^xsd:date)
}
```
### Q2.2 ...and in which relation (e.g., was there a focus on health, or did all sectors get the same?)?
```
PREFIX elod: <http://linkedeconomy.org/ontology#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT ?sector ?numberOfProjects (?numberOfProjects*100/xsd:float(?total) AS  ?percentage)
FROM <http://yourdatastories.eu/pilot2>
WHERE {
  {
    SELECT (COUNT(?activity) AS ?total)
    WHERE{
      ?activity elod:countryIsoCode <http://linkedeconomy.org/resource/Country/ZW>;
              elod:benefactor ?benefactor;          
              elod:startDate ?startDate.
      ?benefactor elod:countryIsoCode <http://linkedeconomy.org/resource/Country/NL>.
      FILTER (?startDate >= "2009-01-01"^^xsd:date && ?startDate < "2013-01-01"^^xsd:date)
    }
  }
  {
    SELECT (COUNT(?activity) AS ?numberOfProjects) ?sectorCode  ?sector
    WHERE{
      ?activity elod:countryIsoCode <http://linkedeconomy.org/resource/Country/ZW>;
              elod:benefactor ?benefactor;          
              elod:startDate ?startDate;
              elod:sector ?sectorUri.
      ?benefactor elod:countryIsoCode <http://linkedeconomy.org/resource/Country/NL>.
      ?sectorUri skos:prefLabel ?sector.
      FILTER (?startDate >= "2009-01-01"^^xsd:date && ?startDate < "2013-01-01"^^xsd:date)
    }
  }
}
```
### Q3. Who actually received the money (e.g., the Zimbabwean government, local NGOs, Dutch NGOs, international organisations)?

```
PREFIX ro: <http://purl.org/wf4ever/ro#>
PREFIX rov: <http://www.w3.org/ns/regorg#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX elod: <http://linkedeconomy.org/ontology#>

SELECT ?activityId ?beneficiaryName ?orgType
FROM <http://yourdatastories.eu/pilot2>
WHERE {
    ?activity elod:countryIsoCode <http://linkedeconomy.org/resource/Country/ZW>;
              elod:beneficiary ?beneficiary;
              elod:benefactor ?benefactor;
              elod:startDate ?startDate;
              elod:projectId ?activityId.
    ?benefactor elod:countryIsoCode <http://linkedeconomy.org/resource/Country/NL>.
    ?beneficiary foaf:name ?beneficiaryName;
                 rov:orgType ?orgTypeUri.
    ?orgTypeUri skos:prefLabel ?orgType.
    FILTER (?startDate >= "2009-01-01"^^xsd:date && ?startDate < "2013-01-01"^^xsd:date)
}
```

## L. International Trade 
### Q1. How did NL's trade relations with Zimbabwe develop during the same time frame?

#### A. Export:

```
PREFIX elod: <http://linkedeconomy.org/ontology#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT ?harmonizedSystemCommodity ?year ?value
FROM <http://yourdatastories.eu/pilot2>
WHERE {
    ?s a elod:TradeActivity;
        elod:hasOrigin <http://linkedeconomy.org/resource/GroupNationalAgent/NL>;
    	elod:hasDestination <http://linkedeconomy.org/resource/GroupNationalAgent/ZW>;
    	elod:financialYear ?year;
    	elod:concerns ?commodity;
    	elod:amount ?amount.
	?commodity skos:prefLabel ?harmonizedSystemCommodity.
	?amount elod:hasCurrencyValue ?value.
	FILTER (?year >= "2009"^^xsd:gYear && ?year < "2013"^^xsd:gYear)
} ORDER BY ?year

```
#### B. Import:
```
PREFIX elod: <http://linkedeconomy.org/ontology#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT ?harmonizedSystemCommodity ?year ?value
FROM <http://yourdatastories.eu/pilot2>
WHERE {
    ?s a elod:TradeActivity;
        elod:hasOrigin <http://linkedeconomy.org/resource/GroupNationalAgent/ZW>;
    	elod:hasDestination <http://linkedeconomy.org/resource/GroupNationalAgent/NL>;
    	elod:financialYear ?year;
    	elod:concerns ?commodity;
    	elod:amount ?amount.
	?commodity skos:prefLabel ?harmonizedSystemCommodity.
	?amount elod:hasCurrencyValue ?value.
	FILTER (?year >= "2009"^^xsd:gYear && ?year < "2013"^^xsd:gYear)
} ORDER BY ?year
```
