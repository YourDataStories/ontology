# Example Queries

### Query results can be retrieved by [this google spreadsheet] (https://docs.google.com/spreadsheets/d/1I_CWEx8qXDdbUjYKPT61sWwEiDnz_HuHRyl3wJw13Y8/edit?usp=sharing).

## Q1: Notices of Austria - Count of notices

SELECT (count(distinct ?notice) AS ?countNotices)
FROM <<http://yourdatastories.eu/TEDUpdate>>
WHERE {
?notice elod:documentType "Contract notice"^^<<http://www.w3.org/2001/XMLSchema#string>> ;
elod:buyer ?buyer .
?buyer elod:countryIsoCode <<http://linkedeconomy.org/resource/Country/AT>>
}

## Q2: Award notices of Belgium  - Count of contracts

SELECT (count (distinct ?awardNotice) AS ?countContracts)
FROM <<http://yourdatastories.eu/TEDUpdate>>
WHERE {
?awardNotice  elod:documentType "Contract award notice"^^<<http://www.w3.org/2001/XMLSchema#string>> ;
elod:buyer ?buyer .
?buyer elod:countryIsoCode <<http://linkedeconomy.org/resource/Country/BE>>
}

## Q3: Notices of Bulgaria - Top 100 buyers

SELECT (SAMPLE(?name) as ?nameBuyer) (count(distinct ?notice) as ?countOfNotices) (sum(xsd:decimal(?currencyValue)) as ?sumOfAmounts)
FROM <<http://yourdatastories.eu/TEDUpdate>>
WHERE {
?notice elod:documentType "Contract notice"^^<<http://www.w3.org/2001/XMLSchema#string>> ;
elod:buyer ?buyer ;
pc:estimatedPrice ?estimatedPrice .
?estimatedPrice gr:hasCurrencyValue ?currencyValue .
?buyer elod:countryIsoCode <<http://linkedeconomy.org/resource/Country/BG>> ;
skos:prefLabel ?name .
}
GROUP BY ?buyer
ORDER BY DESC(?sumOfAmounts)
LIMIT 100

## Q4: Award notices of Croatia - Top 100 buyers 

SELECT (SAMPLE(?name) as ?nameBuyer) (count(distinct ?awardNotice ) as ?countOfContracts) (sum(xsd:decimal(?currencyValue)) as ?sumOfAmounts)
FROM <<http://yourdatastories.eu/TEDUpdate>>
WHERE {
?awardNotice elod:documentType "Contract award notice"^^<<http://www.w3.org/2001/XMLSchema#string>> ;
elod:buyer ?buyer ;
pc:agreedPrice ?agreedPrice .
?agreedPrice gr:hasCurrencyValue ?currencyValue .
?buyer elod:countryIsoCode <<http://linkedeconomy.org/resource/Country/HR>> ;
 skos:prefLabel ?name .
}
GROUP BY ?buyer
ORDER BY DESC(?sumOfAmounts)
LIMIT 100

## Q5: Award notices of Cyprus - Top 100 sellers

SELECT (SAMPLE(?name) as ?nameSeller) (count(distinct ?awardNotice) AS ?countOfContracts)  (sum(xsd:decimal(?currencyValue)) as ?sumOfAmounts)
FROM <<http://yourdatastories.eu/TEDUpdate>>
WHERE {
?awardNotice elod:documentType "Contract award notice"^^<<http://www.w3.org/2001/XMLSchema#string>> ;
elod:buyer ?buyer ;
elod:seller ?seller ;
pc:agreedPrice ?agreedPrice .
?agreedPrice gr:hasCurrencyValue ?currencyValue .
?seller skos:prefLabel ?name .
?buyer elod:countryIsoCode <<http://linkedeconomy.org/resource/Country/CY>> .
}
GROUP BY ?seller
ORDER BY DESC(?sumOfAmounts)
LIMIT 100

## Q6:  Notices of Czech Republic - Sum of amounts 

SELECT (sum(xsd:decimal(?currencyValue)) as ?sumOfAmounts)
FROM <<http://yourdatastories.eu/TEDUpdate>>
WHERE {
?notice elod:documentType "Contract notice"^^<<http://www.w3.org/2001/XMLSchema#string>> ;
elod:buyer ?buyer ;
pc:estimatedPrice ?estimatedPrice .
?estimatedPrice gr:hasCurrencyValue ?currencyValue .
?buyer elod:countryIsoCode <<http://linkedeconomy.org/resource/Country/CZ>> .
}

## Q7: Award notices of Denmark - Sum of amounts 

SELECT (sum(xsd:decimal(?currencyValue)) as ?sumOfAmounts)
FROM <<http://yourdatastories.eu/TEDUpdate>>
WHERE {
?awardNotice elod:documentType "Contract award notice"^^<<http://www.w3.org/2001/XMLSchema#string>> ;
elod:buyer ?buyer ;
pc:agreedPrice ?agreedPrice .
?agreedPrice gr:hasCurrencyValue ?currencyValue .
?buyer elod:countryIsoCode <<http://linkedeconomy.org/resource/Country/DK>> .
}

## Q8: Notices of Estonia - Top 100 CPV  

SELECT (SAMPLE(STR(?cpvNameEnglish)) as ?cpvNameEnglish) (count(distinct ?notice) as ?countOfNotices) (sum(xsd:decimal(?currencyValue)) as ?sumOfAmounts)
FROM <<http://yourdatastories.eu/TEDUpdate>>
FROM <<http://yourdatastories.eu/taxonomies>>
WHERE {
?notice elod:documentType "Contract notice"^^<<http://www.w3.org/2001/XMLSchema#string>> ;
elod:buyer ?buyer ;
pc:mainObject ?mainObject ;
pc:estimatedPrice ?estimatedPrice .
?estimatedPrice gr:hasCurrencyValue ?currencyValue .
?buyer elod:countryIsoCode <<http://linkedeconomy.org/resource/Country/EE>> .
?mainObject skos:prefLabel ?cpvNameEnglish .
FILTER langMatches( lang(?cpvNameEnglish), "en" ) .
}
GROUP BY ?mainObject
ORDER BY DESC(?sumOfAmounts)
LIMIT 100

## Q9: Award notices of Finland - Top 100 CPV 

SELECT (SAMPLE(STR(?cpvNameEnglish)) as ?cpvNameEnglish) (count(distinct ?awardNotice) as ?countOfContracts) (sum(xsd:decimal(?currencyValue)) as ?sumOfAmounts)
FROM <<http://yourdatastories.eu/TEDUpdate>>
FROM <<http://yourdatastories.eu/taxonomies>>
WHERE {
?awardNotice elod:documentType "Contract award notice"^^<<http://www.w3.org/2001/XMLSchema#string>> ;
elod:buyer ?buyer ;
pc:mainObject ?mainObject ;
pc:agreedPrice ?agreedPrice .
?agreedPrice gr:hasCurrencyValue ?currencyValue .
?buyer elod:countryIsoCode <<http://linkedeconomy.org/resource/Country/FI>> .
?mainObject skos:prefLabel ?cpvNameEnglish .
FILTER langMatches( lang(?cpvNameEnglish), "en" ) .
}
GROUP BY ?mainObject
ORDER BY DESC(?sumOfAmounts)
LIMIT 100

## Q10: Notices of France - Top 100 contracts 

SELECT (STR(?contractId) AS ?id) (STR(?financialYear)as ?financialYear) (STR(?issued) AS ?issued) (STR(?duration) AS ?duration) (STR(?startDate)as ?startDate) (STR(?estimatedEndDate)as ?estimatedEndDate) (STR(?tenderDeadline)as ?tenderDeadline)  (STR(?cpvNameEnglish) AS ?cpvNameEnglish)(xsd:decimal(?estimatedPriceValue) AS ?estimatedPriceValue) (STR(?labelKindOfContract) AS ?labelKindOfContract) (STR(?labelProcedureType) AS ?labelProcedureType) (STR(?labelAwardCriterion) AS ?labelAwardCriterion) (STR(?weightOfCriterion)AS ?weightOfCriterion)
FROM <<http://yourdatastories.eu/TEDUpdate>>
FROM <<http://yourdatastories.eu/taxonomies>>
FROM <<http://yourdatastories.eu/countries>>
WHERE {
?notice elod:documentType "Contract notice"^^<<http://www.w3.org/2001/XMLSchema#string>> ;
elod:contractId ?contractId ;
elod:buyer ?buyer .
?buyer elod:countryIsoCode <<http://linkedeconomy.org/resource/Country/FR>> .
OPTIONAL {
?notice dcterms:issued ?issued
} .
OPTIONAL {
?notice elod:financialYear ?financialYear
} .
OPTIONAL {
?notice pc:kind ?kindOfContract .
?kindOfContract skos:prefLabel ?labelKindOfContract
FILTER langMatches( lang(?labelKindOfContract), "en" )
} .
OPTIONAL {
?notice pc:procedureType ?procedureType.
?procedureType skos:prefLabel ?labelProcedureType
FILTER langMatches( lang(?labelProcedureType), "en" )
} .
OPTIONAL {
?notice pc:mainObject ?mainObject .
?mainObject skos:prefLabel ?cpvNameEnglish .
FILTER langMatches( lang(?cpvNameEnglish), "en" )
} .
OPTIONAL {
?notice pc:estimatedPrice ?ups .
?ups gr:hasCurrencyValue ?estimatedPriceValue
} .
OPTIONAL {
?notice pc:awardCriteriaCombination  ?awardCriteriaCombination .
?awardCriteriaCombination pc:awardCriterion ?awardCriterion .
?awardCriterion pc:weightedCriterion ?weightedCriterion .
?weightedCriterion skos:prefLabel ?labelAwardCriterion .
?awardCriterion pc:criterionWeight ?weightOfCriterion.
?awardCriterion pc:weightedCriterion ?criterion .
FILTER langMatches( lang(?labelAwardCriterion), "en" )
}
OPTIONAL {
?notice pc:duration ?duration .
}
OPTIONAL {
?notice pc:startDate ?startDate
} .
OPTIONAL {
?notice pc:estimatedEndDate ?estimatedEndDate
} .
OPTIONAL {
?notice pc:tenderDeadline ?tenderDeadline .
}
}
ORDER BY DESC(?estimatedPriceValue)
LIMIT 100

## Q11: Award notices of Germany - Top 100 contracts 

SELECT (STR(?contractId) AS ?id) ?issued (STR(?cpvNameEnglish) AS ?cpvNameEnglish) (STR(?title) AS ?title) (xsd:decimal(?agreedPriceValue) AS ?value)  (STR(?labelKindOfContract) AS ?labelKindOfContract)  (STR(?labelProcedureType) AS ?labelProcedureType)?numberOfTenders ?documentUrl
FROM <<http://yourdatastories.eu/TEDUpdate>>
FROM <<http://yourdatastories.eu/taxonomies>>
WHERE {
?awardNotice elod:documentType "Contract award notice"^^<<http://www.w3.org/2001/XMLSchema#string>> ;
elod:buyer ?buyer ;
elod:documentUrl ?documentUrl;
elod:contractId ?contractId .
?buyer elod:countryIsoCode <<http://linkedeconomy.org/resource/Country/DE>> .
OPTIONAL {
?awardNotice dcterms:issued ?issued
} .
OPTIONAL {
?awardNotice dcterms:title ?title
} .
OPTIONAL {
?awardNotice elod:awardConcernsNotice ?awardConcernsNotice
} .
OPTIONAL {
?awardNotice pc:kind ?kindOfContract .
?kindOfContract skos:prefLabel ?labelKindOfContract .
FILTER langMatches( lang(?labelKindOfContract), "en" )
} .
OPTIONAL {
?awardNotice pc:procedureType ?procedureType.
?procedureType skos:prefLabel ?labelProcedureType.
FILTER langMatches( lang(?labelProcedureType), "en" ).
} .
OPTIONAL {
?awardNotice pc:numberOfTenders ?numberOfTenders  .
} .
OPTIONAL {
?awardNotice pc:agreedPrice ?ups .
?ups gr:hasCurrencyValue ?agreedPriceValue
} .
OPTIONAL {
?awardNotice pc:mainObject ?mainObject .
?mainObject skos:prefLabel ?cpvNameEnglish .
FILTER langMatches( lang(?cpvNameEnglish), "en" ) .

} .
}
ORDER BY DESC(?agreedPriceValue)
LIMIT 100

## Q12: Buyers who appear with multiple names - Greece

SELECT SAMPLE(?name) AS ?Name count(distinct(?name)) AS ?countNames
FROM <<http://yourdatastories.eu/TEDGreece>>
WHERE {
?buyer foaf:name ?name .
?buyer elod:countryIsoCode <<http://linkedeconomy.org/resource/Country/GR>> .
?contract elod:buyer ?buyer .
}
GROUP BY ?buyer
HAVING count(distinct(?name))>1
ORDER BY DESC (?countNames)

## Q13: Sellers who appear with multiple names - Hungary

SELECT SAMPLE(?name) AS ?Name count(distinct(?name)) AS ?countNames
FROM <<http://yourdatastories.eu/TEDUpdate>>
WHERE {
?seller foaf:name ?name .
?contract elod:seller ?seller ;
elod:buyer ?buyer .
?buyer elod:countryIsoCode <<http://linkedeconomy.org/resource/Country/HU>> .
}
GROUP BY ?seller
HAVING count(distinct(?name))>1
ORDER BY DESC (?countNames)

## Q14: Names of "EvoBus GmbH" - Germany

SELECT ?name 
FROM <<http://yourdatastories.eu/TEDUpdate>>
WHERE {
<<http://linkedeconomy.org/resource/Organization/TEDS_2127631>> foaf:name ?name
}
