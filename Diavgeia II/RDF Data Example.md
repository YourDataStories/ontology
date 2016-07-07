Prefix | URL
-----------|-----------------
xsd: | http://www.w3.org/2001/XMLSchema#
elod: | http://linkedeconomy.org/ontology#
gr: | http://purl.org/goodrelations/v1#
dcterms: | http://purl.org/dc/terms/

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