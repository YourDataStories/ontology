# Example Queries

##Geospatial Data

###All Lines within the specified lines
PREFIX geo: <<http://www.opengis.net/ont/geosparql#>>
PREFIX geof: <<http://www.opengis.net/def/geosparql/function/>>

SELECT distinct *
WHERE {
?shape geo:hasGeometry ?g .
?g geo:asWKT ?gWKT .
FILTER (bif:st_within(?gWKT, "LINESTRING(24.472662 35.367233, 24.472588 35.367252)"^^geo:wktLiteral)) 
}


###Addresses and postal codes for Organizations
select distinct ?name ?street ?pcode from <<http://yourdatastories.eu/NSRF/Diavgeia>>
where {
?organization gr:name ?name ; vcard2006:hasAddress ?address . 
?address vcard2006:street-address ?street ;
vcard2006:postal-code ?pcode .
}


##CPV Queries

###Information for specific CPV
SELECT distinct ?p ?o 
from <<http://yourdatastories.eu/NSRF/Diavgeia>> 
WHERE {
?s elod:hasCpv <<http://linkedeconomy.org/resource/CPV/45233140-2>>. 
<<http://linkedeconomy.org/resource/CPV/45233140-2>> ?p ?o
}


##project profile 

###Single Project Info | query 1
select distinct ?project ?percComplete (xsd:decimal(?prBudget) as ?priceBudget)
from <<http://yourdatastories.eu/NSRF/Diavgeia>>
where {
?project elod:hasRelatedAdministrativeDecision ?decision ; dcterms:title ?title ;
elod:hasRelatedBudgetItem ?revBudget ;  elod:completion ?percComplete . 
?revBudget elod:price ?revUps . 
?revUps gr:hasCurrencyValue ?prBudget. 
} 
group by ?project


###Single Project Info | query 2
select distinct
((count(distinct ?decision)) + (count(distinct ?decisionFinancial)) as ?decisionCount) 
((sum(xsd:decimal(?am))) +  (sum(xsd:decimal(?amContr))) as ?amount2)
from <<http://yourdatastories.eu/NSRF/Diavgeia>>
where {
{
<<http://linkedeconomy.org/resource/Subsidy/372069>> elod:hasRelatedAdministrativeDecision ?decisionFinancial .
?decisionFinancial a elod:FinancialDecision ; elod:hasExpenditureLine ?expLine . 
?expLine elod:amount ?ups . ?ups gr:hasCurrencyValue ?am
}
union
{
<<http://linkedeconomy.org/resource/Subsidy/372069>> elod:hasRelatedAdministrativeDecision ?decisionFinancial .
?decisionFinancial a elod:FinancialDecision ;  pc:agreedPrice ?upsContr . ?upsContr gr:hasCurrencyValue ?amContr
}
union
{
<<http://linkedeconomy.org/resource/Subsidy/372069>> elod:hasRelatedAdministrativeDecision ?decision.
?decision a elod:NonFinancialDecision
}
}


##Diavgeia Descriptive Stats 

###Financial Decisions of a specific Public Project
select distinct ?type (count(distinct ?decision) as ?count) (sum(xsd:decimal(?am)) as ?amount)
from <<http://yourdatastories.eu/NSRF/Diavgeia>>
where {
<<http://linkedeconomy.org/resource/Subsidy/372069>> elod:hasRelatedAdministrativeDecision ?decision .
?decision a elod:FinancialDecision ; elod:decisionType ?type ;
elod:hasExpenditureLine ?expLine . 
?expLine elod:amount ?ups . ?ups gr:hasCurrencyValue ?am
filter (CONTAINS(?type, " "@el))
}


###Decisions of a specific decision type - Δ category
select distinct ?type (count(distinct ?decision) as ?count) (sum(xsd:decimal(?amContr)) as ?amount2)
from <<http://yourdatastories.eu/NSRF/Diavgeia>>
where {
<<http://linkedeconomy.org/resource/Subsidy/372069>> elod:hasRelatedAdministrativeDecision ?decision .
?decision pc:agreedPrice ?ups ; elod:decisionType ?type . 
?ups gr:hasCurrencyValue ?amContr .
filter (CONTAINS(?type, " "@el))
}


###Non-Financial Decisions of a specific Public Project
select distinct (str(?type) as ?type1) (count(distinct ?decision) as ?count)
from <<http://yourdatastories.eu/NSRF/Diavgeia>>
where {
<<http://linkedeconomy.org/resource/Subsidy/372069>> elod:hasRelatedAdministrativeDecision ?decision .
?decision a elod:NonFinancialDecision ; elod:decisionType ?type .
}
order by desc (?count)


##NSRF descriptive Stats

###Detailed information of a Public Project
select distinct ?titleProject ?description ?percComplete
(xsd:decimal(?prBudget) as ?priceBudget) (xsd:decimal(?prSpend) as ?priceSpend) 
(str(?startDate) as ?starts) (str(?endDate) as ?ends) 
from <<http://yourdatastories.eu/NSRF/Diavgeia>> 
where {
<<http://linkedeconomy.org/resource/Subsidy/372069>> dcterms:title ?titleProject ; 
dcterms:description ?description ;
elod:hasRelatedBudgetItem ?revBudget ; elod:hasRelatedSpendingItem ?revSpend ; 
elod:completion ?percComplete ; elod:startDate ?startDate ; elod:endDate ?endDate. 
?revBudget elod:price ?revUps . ?revUps gr:hasCurrencyValue ?prBudget. 
?revSpend elod:hasExpenditureLine ?expSpend . 
?expSpend elod:amount ?upsSpend . ?upsSpend gr:hasCurrencyValue ?prSpend
filter (CONTAINS(?titleProject, " "@el))
}


##Subprojects

###Subprojects (connected to Diavgeia) - Diavgeia data | query 1
select distinct ?subproject
(count(distinct ?decisionFinancial) as ?decisionFinancial)
(count (distinct ?decision) as ?nonFinancial)
(sum(xsd:decimal(?am)) as ?totalAmount)
from <<http://yourdatastories.eu/NSRF/Diavgeia>>
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


##Overall Information of Data Model

###Class treemap
SELECT distinct *
WHERE {
?s rdfs:subClassOf ?p
}


###Returns Properties of a specific Class
SELECT distinct ?property
WHERE {
?subject a elod:Subsidy ; ?property ?object
}


###Domains of a Property
SELECT distinct ?class
WHERE {
?subject a ?class ; elod:hasRelatedProject ?object
}


###NSRF descriptive stats for Public Projects which are related to Crete
select distinct ?project ?percComplete (str(?titleProject) as ?title)
(xsd:decimal(?prBudget) as ?priceBudget) (xsd:decimal(?prSpend) as ?priceSpend) 
(str(?startDate) as ?starts) (str(?endDate) as ?ends) 
from <<http://yourdatastories.eu/NSRF/Diavgeia>> 
where {
?project dcterms:title ?titleProject ; dcterms:description ?description ;
elod:hasRelatedBudgetItem ?revBudget ; elod:hasRelatedSpendingItem ?revSpend ; 
elod:completion ?percComplete ; elod:startDate ?startDate ; elod:endDate ?endDate. 
?revBudget elod:price ?revUps . ?revUps gr:hasCurrencyValue ?prBudget. ?revSpend 
elod:hasExpenditureLine ?expSpend . ?expSpend elod:amount ?upsSpend . ?upsSpend 
gr:hasCurrencyValue ?prSpend
FILTER regex(?titleProject, "Κρήτη", "i")
}


##Data Cube Implementation

###Return Dimension Properties
prefix qb:<<http://purl.org/linked-data/cube#>>
select distinct * 
from <<http://yourdatastories.eu/Diavgeia/DataCube>>
where {?s a qb:DimensionProperty 
} 

###Return Information about Observations
prefix qb:<<http://purl.org/linked-data/cube#>>
select distinct ?p ?o
from <<http://yourdatastories.eu/Diavgeia/DataCube>> 
where {?s a qb:Observation ; ?p ?o
}

###Return Information about Data Strcucture Definition
prefix qb:<<http://purl.org/linked-data/cube#>>
select distinct ?attribute ?compRequired ?attachment
from <<http://yourdatastories.eu/Diavgeia/DataCube>>
where {?s qb:attribute ?attribute ; 
qb:componentRequired ?compRequired ; 
qb:componentAttachment ?attachment  .
} 

##Sector of NSRF Public Projects

###Return public projects of a specific Sector
select distinct ?title
from <<http://yourdatastories.eu/NSRF/Diavgeia>> 
where {
?project elod:sector ?sector ; dcterms:title ?title . 
?sector skos:prefLabel "Road transport"^^xsd:string
filter (CONTAINS(?title, " "@el))
}

###Count of Public Projects per Sector
select distinct ?sector ?label (count(distinct ?project) as ?count) 
from <<http://yourdatastories.eu/NSRF/Diavgeia>> 
where { 
?project elod:sector ?sector  . 
?sector skos:prefLabel ?label
}
