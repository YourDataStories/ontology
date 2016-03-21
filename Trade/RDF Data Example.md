Prefix | URL
-----------|-----------------
base | http://linkedeconomy.org/resource/
elod: | http://linkedeconomy.org/ontology#
skos: | http://www.w3.org/2004/02/skos/core#


### DESCRIPTION OF A TRADED COMMODITY BETWEEN NL AND ZW  ###
```xml
:TradeActivity/NL/ZW/2000/0101210019
                    a :TradeActivity ;
                    elod:concerns :Taxonomy/HS/0101210019 ;
                    elod:financialYear "2010"^^xsd:gYear ;
					elod:hasOrigin :GroupNationalAgent/NL ;
                    elod:hasDestination :GroupNationalAgent/ZW ;
                    elod:amount
								[ a elod:Amount ;
                                  elod:hasCurrency :Currency/USD ;
                                  elod:hasCurrencyValue "168442.0"
								] .                    
```

### DESCRIPTION OF A GROUP NATIONAL AGENT ###
```xml
:GroupNationalAgent/NL a elod:GroupNationalAgent ;
                    elod:countryIsoCode :Taxonomy/ISO-3166-1/Country/NL .
```

### DESCRIPTION OF A HARMONIZED COMMODITY DESCRIPTION AND CODING SYSTEM CODE ###
```xml
:Taxonomy/HS/0101210019
                    skos:notation "0101210019" ;
                    skos:prefLabel "Horses; Live, Pure-bred Breeding Animals, Thoroughbred, Sport Breeding Stock, Excluding Race Breeding Stock, Mares" ;
                    a skos:Concept ;
                    skos:inScheme :Taxonomy/HS/scheme ;
                    skos:broader :Taxonomy/HS/010121 .
```