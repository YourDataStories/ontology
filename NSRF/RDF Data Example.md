Prefix | URL
-----------|-----------------
xsd: | http://www.w3.org/2001/XMLSchema#
elod: | http://linkedeconomy.org/ontology#
skos: | http://www.w3.org/2004/02/skos/core#
gr: | http://purl.org/goodrelations/v1#
dcterms: | http://purl.org/dc/terms/
geo: | http://www.opengis.net/ont/geosparql#

###RDF example for input data of NSRF Projects
```xml
<http://linkedeconomy.org/resource/PublicWork/277637> a elod:PublicWork ;
        elod:subsidyMunicipality <http://linkedeconomy.org/resource/Municipality/9325>;
        elod:sector <http://linkedeconomy.org/resource/Taxonomy/OECD/CRS/21020>;
        elod:countryIsoCode <http://linkedeconomy.org/resource/Country/GR>;
        elod:hasRelatedFeature <http://linkedeconomy.org/resource/PlaceOfInterest/277637>;
        dcterms:title “'Βελτίωση Οδικού Άξονα Φουρνές-Λάκκοι-Ομαλός, στην….”@el;
        dcterms:subject “Το έργο αφορά στη βελτίωση της χάραξης της υπάρχου...”@el
        elod:projectId “277637”^^xsd:string;
        elod:completionOfPayments “72”^^xsd:float;
        elod:countOfRelatedContracts “3”^^xsd:integer;
        elod:startDate”2011-02-24T00:00:00”^^xsd:dateTime;
        elod:endDate”2014-08-20T00:00:00”^^xsd:dateTime;
        elod:hasBudgetAggregate <http://linkedeconomy.org/resource/Aggregate/Budget/277637>;
        elod:hasSpendingAggregate <http://linkedeconomy.org/resource/Aggregate/Payment/277637>.
        <http://linkedeconomy.org/resource/Aggregate/Budget/277637> a elod:Aggregate;
                            elod:aggregatedAmount "11194580.00"^^xsd:float;
                            elod:hasCurrency <http://linkedeconomy.org/resource/Currency/EUR>
                          ].
        <http://linkedeconomy.org/resource/Aggregate/Payment/277637> a elod:Aggregate;
                                     elod:aggregatedAmount "8041839.00"^^xsd:float;
                                     elod:hasCurrency <http://linkedeconomy.org/resource/Currency/EUR>
                                   ]
  ]

<http://linkedeconomy.org/resource/Taxonomy/OECD/CRS/21020> skos:prefLabel "Road transport"^^xsd:string.

<http://linkedeconomy.org/resource/Municipality/9325> elodGeo:name "Municipality of Chania"@en.

<http://linkedeconomy.org/resource/Currency/EUR> skos:notation "EUR";
        skos:prefLabel "Euro"@en.

<http://linkedeconomy.org/resource/Country/GR> skos:notation "GR";
        skos:prefLabel "Greece"@en.

<http://linkedeconomy.org/resource/PlaceOfInterest/277637> geo:hasGeometry <http://linkedeconomy.org/resource/LineString/277637>.
<http://linkedeconomy.org/resource/LineString/277637> geo:asWKT "LINESTRING(23.940968 35.436570,23.940956 35.436543 ....."^^<http://www.openlinksw.com/schemas/virtrdf#Geometry>.