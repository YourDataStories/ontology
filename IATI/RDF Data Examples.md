### PREFIXES ###
Prefix | URL
-----------|-----------------
base | http://linkedeconomy.org/resource/
foaf: | http://xmlns.com/foaf/0.1/
elod: |  http://linkedeconomy.org/ontology#
org: | http://www.w3.org/ns/org#
rov: | http://www.w3.org/ns/regorg#
gr: | http://purl.org/goodrelations/v1#

### DESCRIPTION OF AN AID ACTIVITY ###
```xml
:Aid/XM-DAC-7-PPR-24653 a elod:AidActivity;
                    elod:projectId “XM-DAC-7-PPR-24653”^^xsd:string;
                    dct:title “HIVOS II”^^xsd:string;
                    dct:description “Strengthening Politics and Civil Society ultimate phase” ^^xsd:string;
                    dct:modified “2015-08-13T14:39:48”^^xsd:dateTime
                    elod:countryIsoCode :Country/ZW;
                    elod:benefactor :Organization/XM-DAC-7
                    elod:beneficiary :Organization/ZEN
                    elod:sector :Taxonomy/OECD/CRS/15160;
                    elod:plannedStartDate	“2012-09-01T00:00:00”^^xsd:dateTime
                    elod:plannedEndDate	“2014-08-31T00:00:00”^^xsd:dateTime
                    elod:startDate	“2012-09-12T00:00:00”^^xsd:dateTime
                    elod:endDate	“2014-05-14T00:00:00”^^xsd:dateTime
                    elod:aidType :Taxonomy/IATI/AidType/C01
                    elod:flowType :Taxonomy/IATI/FlowType/10
                    elod:financeType :Taxonomy/IATI/FinanceType/110
                    elod:activityStatusType :Taxonomy/IATI/ActivityStatusType/4
                    elod:collaborationType :Taxonomy/IATI/CollaborationType/1
                    elod:hasRelatedCommittedItem
	                    [ a elod:CommittedItem;
		                  elod:amount
		                      [ a elod:Amount;
                                elod:hasCurrency :Currency/EUR;
                                elod:hasCurrencyValue "124978"^^xsd:float;
                              ];
                         ];
                    elod:hasRelatedDisbursedItem
						[ a elod:CommittedItem;
		                  elod:amount
		                      [ a elod:Amount;
                                elod:hasCurrency :Currency/EUR;
                                elod:hasCurrencyValue "124978"^^xsd:float;
                              ];
                         ];
                    elod:hasTransaction :Transaction/dabeae51e88f
                    elod:hasTransaction :Transaction/c256d0999629
```

### DESCRIPTION OF AN ORGANIZATION (BENEFACTOR) ###
```xml
:Organization/XM-DAC-7 a foaf:Organization, gr:BusinessEntity, org:Organization, rov:RegisteredOrganization;
                   foaf:name "Ministry of Foreign Affairs (DGIS)^^xsd:string";
                   rov:orgType :Taxonomy/IATI/OrganizationType/10;
                   elod:refCode "XM-DAC-7"^^xsd:string.
```

### DESCRIPTION OF AN AID ACTIVITY RELATED TRANSACTION ###
```xml
:Transaction/c256d0999629 a elod:Transaction
						  elod:benefactor :Organization/XM-DAC-7
	                      elod:beneficiary :Organization/ZEN
					      elod:transactionType :Taxonomies/IATI/TransactionType/2
						  elod:transactionDate	“2012-10-12T00:00:00”^^xsd:dateTime
						  elod:valueDate	“2012-10-12T00:00:00”^^xsd:dateTime
						  elod:amount
			                  [ a elod:Amount;
                                elod:hasCurrency :Currency/EUR;
                                elod:hasCurrencyValue "25000"^^xsd:float;
                              ];
                         ];
```