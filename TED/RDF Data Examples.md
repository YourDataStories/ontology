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
		elod:contractId "201531314"^^xsd:string ;
		dcterms:issued "2015-01-22"^^xsd:date ;
        pc:mainObject <http://linkedeconomy.org/resource/CPV/44163100-1> ;
		pc:duration "36.02"^^xsd:duration ; 
		pc:startDate "2015-04-01"^^xsd:date ; 
		pc:estimatedEndDate "2018-03-31”^^xsd:date ; 
		pc:tenderDeadline "2015-03-04T00:00:00"^^xsd:dateTime ;  
		pc:procedureType <http://purl.org/procurement/public-contracts-procedure-types#Restricted> ;
		pc:kind <="http://linkedeconomy.org/resource/Taxonomy/KindScheme/Supplies> ;
		pc:contractingAuthority [a gr:BusinessEntity; a org:Organization; a foaf:Organization; a rov:Organization ;
							gr:name "RWE GasNet- s.r.o." ;
							pc:authorityKind <http://purl.org/procurement/public-contracts-authority-kinds#LocalAuthority>;
						    vcard:hasAddress [ a vcard:Address ;
							vcard:postal-code "400 01"^^xsd:string ;
							vcard:street-address "Klíšská 940/96"^^xsd:string ;
							]
                            elod:countryIsoCode <http://linkedeconomy.org/resource/Country/CZ>
		] ;
        pc:estimatedPrice[ a gr:UnitPriceSpecification ;
                            gr:hasCurrencyValue "7331647"^^xsd:float ;
                            gr:valueAddedTaxIncluded “false”^^xsd:boolean ;
                            elod:hasCurrency <http://linkedeconomy.org/resource/Currency/EUR>
                          ];
		pc:awardCriteriaCombination [ a pc:AwardCriteriaCombination;
						pc:awardCriterion [ a pc:CriterionWeighting ;
							pc:criterionWeight "100"^^pcdt:percentage ;
							pc:weightedCriterion [ a skos:Concept
							] 						
					]
		]
]

```



##Award Notices

```xml
<http://linkedeconomy.org/resource/Contract/AwardNotice/6754729> [ a pc:Contract ;
		elod:contractId “6754729”^^xsd:string ;
		dcterms:title "Bukieciarz-florysta"^^xsd:string ;
		dcterms:issued "2015-03-12"^^xsd:date ;
		pc:awardDate “2015-03-10”^^xsd:date ; 
        pc:mainObject <http://linkedeconomy.org/resource/CPV/80530000-8> ;
		pc:procedureType <http://purl.org/procurement/public-contracts-procedure-types#Open> ;
		pc:kind <http://linkedeconomy.org/resource/Taxonomy/KindScheme/Services> ;
		elod:contractConcernsTender <http://linkedeconomy.org/resource/Contract/Notice/201552269> ;
        pc:agreedPrice[ a gr:UnitPriceSpecification ;
                            gr:hasCurrencyValue "37029.47"^^xsd:float ;
                            gr:valueAddedTaxIncluded “false”^^xsd:boolean ;
                            elod:hasCurrency <http://linkedeconomy.org/resource/Currency/EUR>
        ];		
		pc:contractingAuthority [a gr:BusinessEntity; a org:Organization; a foaf:Organization; a rov:Organization ;
							gr:name "Wielkopolska WojewÃ³dzka Komenda Ochotniczych HufcÃ³w Pracy" ;
							pc:authorityKind <http://purl.org/procurement/public-contracts-authority-kinds#{authorityKind}> ;
							vcard:hasAddress [ a vcard:Address ;
							vcard:postal-code "61-485"^^xsd:string ;
							vcard:street-address "ul. 28 Czerwca 1956r. nr 211"^^xsd:string .
							] ;
                            elod:countryIsoCode <http://linkedeconomy.org/resource/Country/{countryIsoCode}>						
		];						
		pc:awardedTender [ a pc:Tender;
					pc:bidder [ a gr:BusinessEntity; a org:Organization ; a foaf:Organization; a rov:Organization ;
								gr:name "ZakÅ‚ad Doskonalenia Zawodowego" ;
								vcard:hasAddress [ a vcard:Address
								vcard:postal-code "60-179"^^xsd:string ;
								vcard:street-address "ul. JeleniogÃ³rska 4/6"^^xsd:string ;
								]
					]
		
		];
		pc:awardCriteriaCombination [ a pc:AwardCriteriaCombination ;
						pc:awardCriterion [ a CriterionWeighting ;
							pc:criterionWeight 100^^pcdt:percentage ;
							pc:weightedCriterion [a skos:Concept
							]
			        ]		
		]
]
