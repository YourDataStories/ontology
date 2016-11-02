### PREFIXES ###
Prefix | URL
-----------|-----------------
base | http://linkedeconomy.org/resource/
skos: | http://www.w3.org/2004/02/skos/core#
elod: |  http://linkedeconomy.org/ontology#


### DESCRIPTION OF A STATISTICAL INDICATOR ###
```xml
:ZWE/SH.STA.BRTC.ZS/2009 a elod:NonFinancialIndicator;
                    elod:financialYear “2009-01-01”^^xsd:gYear;
                    elod:hasValue “60.2”^^xsd:string;
                    elod:concerns
	                    [ a skos:Concept;
						  skos:prefLabel "Births attended by skilled health staff (% of total)"^^xsd:string;
						  skos:note "UNICEF, State of the World's Children, Childinfo, and Demographic and Health Surveys."^^xsd:string;
						  skos:notation "SH.STA.BRTC.ZS"^^xsd:string;
						  skos:definition "Births attended by skilled health staff are the percentage of deliveries attended by personnel trained to give the necessary supervision, care, and advice to women during pregnancy, labor, and the postpartum period; to conduct deliveries on their own; and to care for newborns."^^xsd:string;
		                  skos:inScheme
		                      [ a skos:ConceptScheme;
                                skos:prefLabel "World Development Indicators code list"^^xsd:string;
                              ];
                         ];
```

### DESCRIPTION OF A FINANCIAL INDICATOR ###
```xml
:AFG/BN.GSR.MRCH.CD/2009 a elod:FinancialIndicator;
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
