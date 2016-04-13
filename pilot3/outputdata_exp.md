### PREFIXES ###
Prefix | URL
-----------|-----------------
base | http://linkedeconomy.org/resource/
gr | http://purl.org/goodrelations/v1#
sc | http://schema.org/
dcterms | http://purl.org/dc/terms/
dc | http://purl.org/dc/elements/1.1/
rev | http://purl.org/stuff/rev#
cpsv | http://purl.org/vocab/cpsv#
skos | http://www.w3.org/2004/02/skos/core#
dbpedia | http://dbpedia.org/ontology/
pc | http://purl.org/procurement/public-contracts#
vcard | http://www.w3.org/2006/vcard/ns#
elod | http://linkedeconomy.org/ontology#
foaf | http://xmlns.com/foaf/0.1/
rov | http://www.w3.org/ns/regorg#
org | http://www.w3.org/ns/org#

### DESCRIPTION OF AN Contract ###
```xml
<http://linkedeconomy.org/resource/Taxonomy/AuthorityKindScheme> a skos:ConceptScheme .

<http://linkedeconomy.org/resource/Taxonomy/ProcedureTypeScheme> a skos:ConceptScheme .

<http://linkedeconomy.org/resource/Contract/53650> pc:agreedPrice <http://linkedeconomy.org/resource/UnitPriceSpecification/6f39b86> ;
	pc:awardDate "2012-11-30T00:00:00.000+0000"^^<http://www.w3.org/2001/XMLSchema#dateTime> ;
	elod:documentUrl "http://ted.europa.eu/udl?uri=TED:NOTICE:402119-2012:TEXT:DE:HTML" ;
	pc:additionalObject <http://linkedeconomy.org/resource/CPV/45315300> ;
	dcterms:coverage "PlankstraÃe 1, 64291 Darmstadt." ;
	dcterms:description "Die FAIR GmbH plant im Rahmen eines internationalen" ;
	a pc:Contract ;
	dcterms:title "Innere BaustraÃen Projekt FAIR." ;
	pc:additionalObject <http://linkedeconomy.org/resource/CPV/45233221> ;
	pc:mainObject <http://linkedeconomy.org/resource/CPV/45233120> ;
	elod:documentType "Contract award" ;
	elod:contractId "53650"^^<http://www.w3.org/2001/XMLSchema#ID> ;
	pc:awardCriteriaCombination <http://linkedeconomy.org/resource/AwardCriteriaCombination/efc101d> ;
	pc:authorityKind <http://linkedeconomy.org/resource/Taxonomy/AuthorityKindScheme/Body_governed_by_public_law> ;
	pc:awardedTender <http://linkedeconomy.org/resource/Tender/5163944> ;
	elod:financialYear "2012"^^<http://www.w3.org/2001/XMLSchema#gYear> ;
	dcterms:issued "2012-12-17T00:00:00.000+0000"^^<http://www.w3.org/2001/XMLSchema#dateTime> ;
	pc:contractingAuthority <http://linkedeconomy.org/resource/Organization/1463716048> ;
	pc:additionalObject <http://linkedeconomy.org/resource/CPV/45232150> ;
	pc:kind <http://linkedeconomy.org/resource/Taxonomy/KindScheme/WORKS> ;
	pc:procedureType <http://linkedeconomy.org/resource/Taxonomy/ProcedureTypeScheme/Open> ;
	dc:publisher <http://linkedeconomy.org/resource/Organization/1463716048> ;
	pc:additionalObject <http://linkedeconomy.org/resource/CPV/45233222> .

<http://linkedeconomy.org/resource/Taxonomy/KindScheme/WORKS> skos:inScheme <http://linkedeconomy.org/resource/Taxonomy/KindScheme> ;
	skos:prefLabel "WORKS" ;
	a skos:Concept .

<http://linkedeconomy.org/resource/Address/2b41631> elod:countryIsoCode <http://linkedeconomy.org/resource/Country/DE> ;
	vcard:street-address "IndustriestraÃe 9" ;
	a vcard:Address .

<http://linkedeconomy.org/resource/CriterionWeighting/31661e7> pc:weightedCriterion <http://linkedeconomy.org/resource/SelectionCriterion/MostEconomicalOffer> ;
	pc:criterionWeight "100"^^<http://www.w3.org/2001/XMLSchema#positiveInteger> ;
	a pc:CriterionWeighting .

<http://linkedeconomy.org/resource/UnitPriceSpecification/6f39b86> gr:hasCurrencyValue "8565101.47"^^<http://www.w3.org/2001/XMLSchema#float> ;
	elod:hasCurrency <http://linkedeconomy.org/resource/Currency/EUR> ;
	a gr:UnitPriceSpecification .

<http://linkedeconomy.org/resource/CPV/45233120> elod:cpvCode "45233120"^^<http://www.w3.org/2001/XMLSchema#string> ;
	a elod:CPV .

<http://linkedeconomy.org/resource/Tender/5163944> pc:bidder <http://linkedeconomy.org/resource/Organization/1710261154> ;
	a pc:Tender .

<http://linkedeconomy.org/resource/Organization/1710261154> vcard:hasAddress <http://linkedeconomy.org/resource/Address/2b41631> ;
	elod:isRegisteredAt <http://linkedeconomy.org/resource/Address/2b41631> ;
	gr:name "Bickhardt Bau AG" ;
	a org:Organization , rov:RegisteredOrganization , foaf:Organization , gr:BusinessEntity .

<http://linkedeconomy.org/resource/Taxonomy/ProcedureTypeScheme/Open> skos:inScheme <http://linkedeconomy.org/resource/Taxonomy/ProcedureTypeScheme> ;
	skos:prefLabel "Open procedure" ;
	a skos:Concept .

<http://linkedeconomy.org/resource/Organization/1463716048> vcard:country-name "Germany" ;
	gr:name "FAIR GmbH" ;
	a org:Organization , rov:RegisteredOrganization , foaf:Organization , gr:BusinessEntity .

<http://linkedeconomy.org/resource/AwardCriteriaCombination/efc101d> pc:awardCriterion <http://linkedeconomy.org/resource/CriterionWeighting/31661e7> ;
	a pc:AwardCriteriaCombination .

<http://linkedeconomy.org/resource/Taxonomy/AuthorityKindScheme/Body_governed_by_public_law> skos:inScheme <http://linkedeconomy.org/resource/Taxonomy/AuthorityKindScheme> ;
	skos:prefLabel "Body governed by public law" ;
	a skos:Concept .

<http://linkedeconomy.org/resource/Taxonomy/KindScheme> a skos:ConceptScheme .
