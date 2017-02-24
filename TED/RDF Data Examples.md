Prefix | URL
-----------|-----------------
xsd: | http://www.w3.org/2001/XMLSchema#
elod: | http://linkedeconomy.org/ontology#
skos: | http://www.w3.org/2004/02/skos/core#
gr: | http://purl.org/goodrelations/v1#
dcterms: | http://purl.org/dc/terms/
vcard: | http://www.w3.org/2006/vcard/ns#
pc: | http://purl.org/procurement/public-contracts#
pcdt: | http://purl.org/procurement/public-contracts-datatypes#

###RDF example for input data of TED

##Notices
```xml
<http://linkedeconomy.org/resource/Contract/Notice/201531314> [ a pc:Contract ;
        elod:documentType "Contract notice"^^xsd:string ;
		elod:contractId "201531314"^^xsd:string ;
		elod:financialYear "2015"^^xsd:gYear ;
		dcterms:issued "2015-01-22T00:00:00"^^xsd:dateTime ;
        pc:mainObject <http://linkedeconomy.org/resource/CPV/44163100-1> ;
		pc:additionalObject <http://linkedeconomy.org/resource/CPV/{additionalObject}>
		pc:duration "36"^^xsd:duration ; 
		pc:startDate "2015-04-01"^^xsd:date ; 
		pc:estimatedEndDate "2018-03-31”^^xsd:date ; 
		pc:tenderDeadline "2015-03-04T00:00:00"^^xsd:dateTime ;  
		pc:procedureType <http://purl.org/procurement/public-contracts-procedure-types#Restricted> ;
		pc:kind <="http://linkedeconomy.org/resource/Taxonomy/KindScheme/Supplies> ;
	    elod:hasNutsCode <http://nuts.geovocab.org/id/CZ0>;
		elod:documentUrl "http://www.ted.europa.eu/udl?uri=TED:NOTICE:31314-2015:TEXT:EN:HTML&tabId=0"^^xsd:string ;
		elod:buyer [a gr:BusinessEntity; a org:Organization; a foaf:Organization; a rov:RegisteredOrganization ;
							skos:prefLabel "RWE GasNet- s.r.o." ;	
							gr:name "RWE GasNet- s.r.o." ;
							pc:authorityKind <http://purl.org/procurement/public-contracts-authority-kinds#LocalAuthority>;
						    vcard:hasAddress [ a vcard:Address ;
							vcard:locality "Ústí nad Labem"^^xsd:string ;
							vcard:postal-code "40001"^^xsd:string ;
							vcard:street-address "Klíšská 940/96"^^xsd:string ;
							]
                            elod:countryIsoCode <http://linkedeconomy.org/resource/Country/CZ> ;
							elod:isMatched "true"^^xsd:boolean
		] ;
        pc:estimatedPrice[ a gr:UnitPriceSpecification ;
                            gr:hasCurrencyValue "7331647"^^xsd:float ;
                            gr:valueAddedTaxIncluded “false”^^xsd:boolean ;
                            elod:hasCurrency <http://linkedeconomy.org/resource/Currency/EUR>
                          ];
		pc:awardCriteriaCombination [ a pc:AwardCriteriaCombination;
						pc:awardCriterion [ a pc:CriterionWeighting ;
							pc:criterionWeight "100"^^pcdt:percentage ;
							pc:weightedCriterion <http://purl.org/procurement/public-contracts-criteria#LowestPrice>	
					]
		]
]

```



##Award Notices

```xml
<http://linkedeconomy.org/resource/Contract/AwardNotice/201593094/6754729> [ a pc:Contract ;
        elod:documentType "Contract award notice"^^xsd:string ;
	    elod:financialYear "2015"^^xsd:gYear ;
		elod:contractId “6754729”^^xsd:string ;
		dcterms:title "Bukieciarz-florysta"^^xsd:string ;
		dcterms:issued "2015-03-12T00:00:00"^^xsd:dateTime ;
		pc:awardDate “2015-03-10”^^xsd:date ; 
        pc:mainObject <http://linkedeconomy.org/resource/CPV/80530000-8> ;
		pc:additionalObject <http://linkedeconomy.org/resource/CPV/{additionalObject}> ;
		pc:procedureType <http://purl.org/procurement/public-contracts-procedure-types#Open> ;
		pc:kind <http://linkedeconomy.org/resource/Taxonomy/KindScheme/Services> ;
		elod:contractConcernsTender <http://linkedeconomy.org/resource/Contract/Notice/201552269> ;
		pc:numberOfTenders "6"^^xsd:nonNegativeInteger ;
		elod:documentUrl "http://www.ted.europa.eu/udl?uri=TED:NOTICE:93094-2015:TEXT:EN:HTML&tabId=0"^^xsd:string ;
        pc:agreedPrice[ a gr:UnitPriceSpecification ;
                            gr:hasCurrencyValue "37029.47"^^xsd:float ;
                            gr:valueAddedTaxIncluded “false”^^xsd:boolean ;
                            elod:hasCurrency <http://linkedeconomy.org/resource/Currency/EUR>
        ];		
		elod:buyer [a gr:BusinessEntity; a org:Organization; a foaf:Organization; a rov:RegisteredOrganization ;
							skos:prefLabel "Wielkopolska WojewÃ³dzka Komenda Ochotniczych HufcÃ³w Pracy" ;	 
							gr:name "Wielkopolska WojewÃ³dzka Komenda Ochotniczych HufcÃ³w Pracy" ;
							pc:authorityKind <http://purl.org/procurement/public-contracts-authority-kinds#{authorityKind}> ;
							vcard:hasAddress [ a vcard:Address ;
							vcard:locality "Poznań"^^xsd:string ;
							vcard:postal-code "61485"^^xsd:string ;
							vcard:street-address "ul. 28 Czerwca 1956r. nr 211"^^xsd:string .
							] ;
                            elod:countryIsoCode <http://linkedeconomy.org/resource/Country/PL>	
							elod:isMatched "true"^^xsd:boolean							
		];		
		elod:seller [a gr:BusinessEntity; a org:Organization; a foaf:Organization; a rov:RegisteredOrganization ;
							skos:prefLabel "Zakład Doskonalenia Zawodowego"
							gr:name "Zakład Doskonalenia Zawodowego"
							vcard:hasAddress [ a vcard:Address ;
							vcard:locality "Poznań"^^xsd:string ;
							vcard:postal-code "60179"^^xsd:string ;
							vcard:street-address "ul. Jeleniogórska 4/6"^^xsd:string ;
							] ;
                            elod:countryIsoCode <http://linkedeconomy.org/resource/Country/{countryIsoCode}>	
							elod:isMatched "true"^^xsd:boolean							
		];			
		pc:awardCriteriaCombination [ a pc:AwardCriteriaCombination ;
						pc:awardCriterion [ a CriterionWeighting ;
							pc:criterionWeight 100^^pcdt:percentage ;
							pc:weightedCriterion <http://purl.org/procurement/public-contracts-criteria#LowestPrice>	
							]
			        ]		
		]
]
