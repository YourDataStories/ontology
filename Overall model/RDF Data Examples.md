Prefix | URL
-----------|-----------------
xsd: | http://www.w3.org/2001/XMLSchema#
elod: | http://linkedeconomy.org/ontology#
skos: | http://www.w3.org/2004/02/skos/core#
gr: | http://purl.org/goodrelations/v1#
dcterms: | http://purl.org/dc/terms/
geo: | http://www.opengis.net/ont/geosparql#

##RDF Data Examples per Dataset

###RDF example for input data of NSRF Projects
```xml
<http://linkedeconomy.org/resource/PublicWork/277637> a elod:Subsidy ;
        elod:subsidyMunicipality <http://linkedeconomy.org/resource/Municipality/9325>;
        elod:sector <http://linkedeconomy.org/resource/Taxonomy/OECD/CRS/21020>;
        elod:countryIsoCode <http://linkedeconomy.org/resource/Country/GR>;
        elod:hasRelatedFeature <http://linkedeconomy.org/resource/PlaceOfInterest/277637>;
        dcterms:title “'Βελτίωση Οδικού Άξονα Φουρνές-Λάκκοι-Ομαλός, στην….”@el;
        dcterms:description “Το έργο αφορά στη βελτίωση της χάραξης της υπάρχου...”@el
        elod:projectId “277637”^^xsd:string;
        elod:completionOfPayments “72”^^xsd:float;
        elod:countOfRelatedContracts “3”^^xsd:integer;
        elod:startDate”2011-02-24T00:00:00”^^xsd:dateTime;
        elod:endDate”2014-08-20T00:00:00”^^xsd:dateTime;
        elod:hasBudgetAggregate <http://linkedeconomy.org/resource/Aggregate/Budget/277637>;
        elod:hasSpendingAggregate <http://linkedeconomy.org/resource/Aggregate/Payment/277637>.
        <http://linkedeconomy.org/resource/Aggregate/Budget/277637> 
                            elod:aggregatedAmount "11194580.00"^^xsd:float;
                            elod:hasCurrency <http://linkedeconomy.org/resource/Currency/EUR>.
                          
        <http://linkedeconomy.org/resource/Aggregate/Payment/277637> 
                                     elod:aggregatedAmount "8041839.00"^^xsd:float;
                                     elod:hasCurrency <http://linkedeconomy.org/resource/Currency/EUR>.
                                   

<http://linkedeconomy.org/resource/Taxonomy/OECD/CRS/21020> skos:prefLabel "Road transport"^^xsd:string.

<http://linkedeconomy.org/resource/Municipality/9325> elodGeo:name "Municipality of Chania"@en.

<http://linkedeconomy.org/resource/Currency/EUR> skos:notation "EUR";
        skos:prefLabel "Euro"@en.

<http://linkedeconomy.org/resource/Country/GR> skos:notation "GR";
        skos:prefLabel "Greece"@en.

<http://linkedeconomy.org/resource/PlaceOfInterest/277637> geo:hasGeometry <http://linkedeconomy.org/resource/LineString/277637>.
<http://linkedeconomy.org/resource/LineString/277637> geo:asWKT "LINESTRING(23.940968 35.436570,23.940956 35.436543 ....."^^<http://www.openlinksw.com/schemas/virtrdf#Geometry>.
```
###RDF example for input data of Greek Transparency Portal

```xml
<http://linkedeconomy.org/resource/SpendingItem/Ω6Η2ΟΡΡ9-Β9Ω> a elod:SpendingItem;
a elod:FinancialDecision;
elod:ada “Ω6Η2ΟΡΡ9-Β9Ω”^^xsd:string;
dcterms:subject “ΠΛΗΡΩΜΗ ΠΟΣΟΥ 104.354,00€ ΓΙΑ ΤΟ ΕΡΓΟ 2010ΝΑ04980000”@el;
elod:decisionTypeId “B.2.2”^^xsd:string;
elod:documentType “ΠΡΑΞΗ”^^xsd:string;
elod:protocolNumber “2522”^^xsd:string;
dcterms:issued “2014-06-30T00:00:00Z”^^xsd:dateTime;
elod:submissionTimestamp “2014-07-22T07:27:20.017Z”^^xsd:dateTime;
elod:versionId “0cfc67e7-9340-4940-b8cb-0706be45131e”^^xsd:string
elod:documentUrl “https://diavgeia.gov.gr/luminapi/api/decisions/Ω6Η2ΟΡΡ9-Β9Ω/document”^^xsd:string;
elod:privateData “false”^^xsd:boolean;
elod:signer 
    <http://linkedeconomy.org/resource/Signer/120044>;
elod:hasThematicCategory 
        <http://linkedeconomy.org/resource/ThematicCategory/20>;
elod:decisionStatus 
            <http://linkedeconomy.org/resource/DecisionStatus/Published>;
  elod:buyer 
                <http://linkedeconomy.org/resource/Organization/090252840/94627>;
        elod:hasExpenditureLine [ a elod:ExpenditureLine;
        elod:seller 
                    <http://linkedeconomy.org/resource/Organization/094311152>;
                  elod:amount [ a gr:UnitPriceSpecification;
                                elod:hasCurrency 
                        <http://linkedeconomy.org/resource/Currency/EUR>;
                                gr:hasCurrencyValue "101.022,19"^^xsd:float;
                                gr:valueAddedTaxIncluded “true”^^xsd:boolean.
                              ]
]
```

###RDF example of interlinking Greek Transparency Portal and NSRF Dataset

```xml
<http://linkedeconomy.org/resource/PublicWork/277637> elod:hasRelatedAdministrativeDecision <http://linkedeconomy.org/resource/SpendingItem/Ω6Η2ΟΡΡ9-Β9Ω>.