# Example Queries

## A. Geospatial Data

### Q1. All resources inside a bounding box
```xml
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
```xml
select distinct ?name ?street ?pcode from <http://yourdatastories.eu/NSRF/Diavgeia>
where {
  ?organization gr:legalName ?name ; vcard2006:hasAddress ?address . 
  ?address vcard2006:street-address ?street ;
  vcard2006:postal-code ?pcode .
}
```
### Q3. Postal Codes of Organizations and the Municipalities they belong to
```xml
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
```xml
SELECT distinct ?p ?o 
from <http://yourdatastories.eu/NSRF/Diavgeia>
WHERE {
	?s elod:hasCpv <http://linkedeconomy.org/resource/CPV/45233140-2>. 
	<http://linkedeconomy.org/resource/CPV/45233140-2> ?p ?o
}
```

## C. Project profile 

### Q1. Single Project Info NSRF
```xml
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
```xml
select distinct
((count(distinct ?decision)) + (count(distinct ?decisionFinancial)) as ?decisionCount) 
((sum(xsd:decimal(?am))) +  (sum(xsd:decimal(?amContr))) as ?amount2)
from <http://yourdatastories.eu/NSRF/Diavgeia>
where {
  {
    <http://linkedeconomy.org/resource/Subsidy/372069> elod:hasRelatedAdministrativeDecision ?decisionFinancial .
    ?decisionFinancial a elod:FinancialDecision ; elod:hasExpenditureLine ?expLine . 
    ?expLine elod:amount ?ups . ?ups gr:hasCurrencyValue ?am
  }
  union
  {
    <http://linkedeconomy.org/resource/Subsidy/372069> elod:hasRelatedAdministrativeDecision ?decisionFinancial .
    ?decisionFinancial a elod:FinancialDecision ;  pc:agreedPrice ?upsContr . ?upsContr gr:hasCurrencyValue ?amContr
  }
  union
  {
    <http://linkedeconomy.org/resource/Subsidy/372069> elod:hasRelatedAdministrativeDecision ?decision.
    ?decision a elod:NonFinancialDecision
  }
}
```

## D. Diavgeia Descriptive Stats 

### Q1. Financial Decisions of a specific Public Project
```xml
select distinct ?type (count(distinct ?decision) as ?count) (sum(xsd:decimal(?am)) as ?amount)
from <http://yourdatastories.eu/NSRF/Diavgeia>
where {
  <http://linkedeconomy.org/resource/Subsidy/372069> elod:hasRelatedAdministrativeDecision ?decision .
  ?decision a elod:FinancialDecision ; elod:decisionType ?type ;
  elod:hasExpenditureLine ?expLine . 
  ?expLine elod:amount ?ups . ?ups gr:hasCurrencyValue ?am
  filter (CONTAINS(?type, " "@el))
}
```

### Q2. Decisions of a specific decision type - Δ category
```xml
select distinct ?type (count(distinct ?decision) as ?count) (sum(xsd:decimal(?amContr)) as ?amount2)
from <http://yourdatastories.eu/NSRF/Diavgeia>
where {
  <http://linkedeconomy.org/resource/Subsidy/372069> elod:hasRelatedAdministrativeDecision ?decision .
  ?decision pc:agreedPrice ?ups ; elod:decisionType ?type . 
  ?ups gr:hasCurrencyValue ?amContr .
  filter (CONTAINS(?type, " "@el))
}
```

### Q3. Non-Financial Decisions of a specific Public Project
```xml
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
```xml
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
  filter (CONTAINS(?titleProject, " "@el))
}
```

## F. Subprojects

### Q1. Subprojects (connected to Diavgeia) - Diavgeia data | query 1
```xml
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
```xml
SELECT distinct *
WHERE {
	?s rdfs:subClassOf ?p
}
```

### Q2. Returns Properties of a specific Class
```xml
SELECT distinct ?property
WHERE {
	?subject a elod:Subsidy ; ?property ?object
}
```

### Q3. Domains of a Property
```xml
SELECT distinct ?class
WHERE {
	?subject a ?class ; elod:hasRelatedProject ?object
}
```

### Q4. NSRF descriptive stats for Public Projects which are related to Crete
```xml
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
```xml
prefix qb:<http://purl.org/linked-data/cube#>
select distinct * 
from <http://yourdatastories.eu/Diavgeia/DataCube>
where {
	?s a qb:DimensionProperty 
} 
```

### Q2. Return Information about Observations
```xml
prefix qb:<http://purl.org/linked-data/cube#>
select distinct ?p ?o
from <http://yourdatastories.eu/Diavgeia/DataCube> 
where {
	?s a qb:Observation ; ?p ?o
}
```
### Q3. Return Information about Data Strcucture Definition
```xml
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
```xml
select distinct ?title
from <http://yourdatastories.eu/NSRF/Diavgeia> 
where {
  ?project elod:sector ?sector ; dcterms:title ?title . 
  ?sector skos:prefLabel "Road transport"^^xsd:string
  filter (CONTAINS(?title, " "@el))
}
```
### Q2. Count of Public Projects per Sector
```xml
select distinct ?sector ?label (count(distinct ?project) as ?count) 
from <http://yourdatastories.eu/NSRF/Diavgeia> 
where { 
  ?project elod:sector ?sector  . 
  ?sector skos:prefLabel ?label
}
```
## J. Organizations

### Q1. Return the connection of Sellers from Projects to Organizations URIs and their related information
```xml
select distinct ?org ?vatId ?greekName ?engName
from <http://yourdatastories.eu/NSRF/Diavgeia>
where {
?subsidy elod:seller ?seller . ?seller rdfs:seeAlso ?org .
?org gr:vatID ?vatId ; gr:legalName ?greekName ; elod:translation ?engName
} 
```
