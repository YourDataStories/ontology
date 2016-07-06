Prefix | URL
-----------|-----------------
xsd: | http://www.w3.org/2001/XMLSchema#
elod: | http://linkedeconomy.org/ontology#
skos: | http://www.w3.org/2004/02/skos/core#
gr: | http://purl.org/goodrelations/v1#
dcterms: | http://purl.org/dc/terms/

###RDF example for input data of NSRF Projects
```xml
<http://linkedeconomy.org/resource/Subsidy/277637> a elod:Subsidy ;
        elod:subsidyMunicipality <http://linkedeconomy.org/resource/Municipality/9325>;
        elod:sector <http://linkedeconomy.org/resource/Taxonomy/OECD/CRS/21020>;
        elod:countryIsoCode <http://linkedeconomy.org/resource/Country/GR>;
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
                            gr:valueAddedTaxIncluded “true”^^xsd:Boolean;
                            elod:hasCurrency <http://linkedeconomy.org/resource/Currency/EUR>
                          ].
        <http://linkedeconomy.org/resource/Subsidy/SpendingItem/277637> 
               elod:hasExpenditureLine [ a elod:ExpenditureLine;
                       elod:amount [ a gr:UnitPriceSpecification;
                                     gr:hasCurrencyValue "8041839.00"^^xsd:float;
                                     gr:valueAddedTaxIncluded “true”^^xsd:boolean;
                                     elod:hasCurrency <http://linkedeconomy.org/resource/Currency/EUR>
                                   ]
  ]

<http://linkedeconomy.org/resource/Taxonomy/OECD/CRS/21020> skos:prefLabel "Road transport"xsd:string.

<http://linkedeconomy.org/resource/Municipality/9325> elodGeo:name "Municipality of Chania"@en.

<http://linkedeconomy.org/resource/Currency/EUR> skos:notation "EUR" ;
        skos:prefLabel "Euro"@en

<http://linkedeconomy.org/resource/Country/GR> skos:notation "GR" ;
        skos:prefLabel "Greece"@en
