### PREFIXES ###
Prefix | URL
-----------|-----------------
base | http://linkedeconomy.org/resource/
skos: | http://www.w3.org/2004/02/skos/core#
elod: |  http://linkedeconomy.org/ontology#


### DESCRIPTION OF A NON-FINANCIAL STATISTICAL INDICATOR ###
```xml
:AFG/AG.CON.FERT.PT.ZS/2009 a elod:StatisticalIndicator;
                    elod:financialYear “2009-01-01”^^xsd:gYear;
                    elod:hasValue “258.9739821”^^xsd:string;
                    elod:concerns
	                    [ a skos:Concept;
						  skos:prefLabel "Fertilizer consumption (% of fertilizer production)"^^xsd:string;
						  skos:note "Food and Agriculture Organization, electronic files and web site."^^xsd:string;
						  skos:notation "AG.CON.FERT.PT.ZS"^^xsd:string;
						  skos:definition "Fertilizer consumption measures the quantity of plant nutrients used per unit of arable land. Fertilizer products cover nitrogenous, potash, and phosphate fertilizers (including ground rock phosphate). Traditional nutrients--animal and plant manures--are not included. For the purpose of data dissemination, FAO has adopted the concept of a calendar year (January to December). Some countries compile fertilizer data on a calendar year basis, while others are on a split-year basis."^^xsd:string;
		                  skos:inScheme
		                      [ a skos:ConceptScheme;
                                skos:prefLabel "World Development Indicators code list"^^xsd:string;
                              ];
                         ];
```

### DESCRIPTION OF A FINANCIAL STATISTICAL INDICATOR ###
```xml
:AFG/BN.GSR.MRCH.CD/2009 a elod:StatisticalIndicator;
                    elod:financialYear “2009-01-01”^^xsd:gYear;
                    elod:concerns
	                    [ a skos:Concept;
						  skos:prefLabel "Net trade in goods (BoP, current US$)"^^xsd:string;
						  skos:note "International Monetary Fund, Balance of Payments Statistics Yearbook and data files."^^xsd:string;
						  skos:notation "BN.GSR.MRCH.CD"^^xsd:string;
						  skos:definition "Net trade in goods is the difference between exports and imports of goods. Trade in services is not included. Data are in current U.S. dollars."^^xsd:string;
		                  skos:inScheme
		                      [ a skos:ConceptScheme;
                                skos:prefLabel "World Development Indicators code list"^^xsd:string;
                              ];
                         ];
				    elod:amount
			                  [ a elod:Amount;
                                elod:hasCurrency :Currency/USD;
                                elod:hasCurrencyValue "-3204358093"^^xsd:float;
                              ];
                         ];
```