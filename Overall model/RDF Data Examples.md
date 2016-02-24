##RDF Data Examples per Dataset

###RDF example for input data of NSRF Projects
```xml
<http://linkedeconomy.org/resource/Subsidy/277637> a elod:Subsidy ;
        dcterms:title “'Βελτίωση Οδικού Άξονα Φουρνές-Λάκκοι-Ομαλός, στην….”@el;
        dcterms:subject “Το έργο αφορά στη βελτίωση της χάραξης της υπάρχου...”@el
        elod:projectId “277637”^^xsd:string;
        elod:completion “72”xsd:float;
        elod:countOfRelatedProjects “3”xsd:string;
        elod:startDate”2011-02-24T00:00:00”xsd:dateTime;
        elod:endDate”2014-08-20T00:00:00”xsd:dateTime;
        elod:hasRelatedBudgetItem <http://linkedeconomy.org/resource/Subsidy/BudgetItem/277637>;
        elod:hasRelatedSpendingItem <http://linkedeconomy.org/resource/Subsidy/SpendingItem/277637>.
        <http://linkedeconomy.org/resource/Subsidy/BudgetItem/277637> 
               elod:price [ a gr:UnitPriceSpecification;
                            gr:hasCurrencyValue "11194580.00"^^xsd:float;
                            gr:valueAddedTaxIncluded “true”^^xsd:Boolean
                          ].
        <http://linkedeconomy.org/resource/Subsidy/SpendingItem/277637> 
               elod:hasExpenditureLine [ a elod:ExpenditureLine;
                       elod:amount [ a gr:UnitPriceSpecification;
                                     gr:hasCurrencyValue "8041839.00"^^xsd:float;
                                     gr:valueAddedTaxIncluded “true”^^xsd:boolean.
                                   ]
  ]
```
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
