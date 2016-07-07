Prefix | URL
-----------|-----------------
xsd: | http://www.w3.org/2001/XMLSchema#
elod: | http://linkedeconomy.org/ontology#
gr: | http://purl.org/goodrelations/v1#

###RDF example for input data of Greek Transparency Portal

```xml
<http://linkedeconomy.org/resource/ExpenseApprovalItem/773ΨΦ-8Η5> a elod:ExpenseApprovalItem;
        elod:decisionTypeId “B.2.1”;
        elod:documentType “ΠΡΑΞΗ”;
        elod:buyer <http://linkedeconomy.org/resource/Organization/090166291>;
        elod:hasExpenditureLine [ a elod:ExpenditureLine;
        elod:seller <http://linkedeconomy.org/resource/Organization/055812251>;
        elod:hasKae<http://linkedeconomy.org/resource/KaeCodes/2009ΣΕ01980013>;
        elod:hasCPV <http://publicspending.net/resource/CPV/50750000-7>.
                  elod:amount [ a gr:UnitPriceSpecification;
                                elod:hasCurrency <http://linkedeconomy.org/resource/Currency/EUR>;
                                gr:hasCurrencyValue "36.34"^^xsd:float;
                                gr:valueAddedTaxIncluded “true”^^xsd:boolean.
                              ]
]