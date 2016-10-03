# Change Log
All notable changes to the data model will be documented in this file.

## [1.1.3] - 2016-10-03
### Added
- Add rfds:comment of elod:hasRelatedBudgetItem Object property in OWL file
- Add rfds:comment of elod:hasRelatedCommittedItem Object property in OWL file
- Add rfds:comment of elod:hasRelatedDecision Object property in OWL file
- Add rfds:comment of elod:hasRelatedDisbursedItem Object property in OWL file
- Add rfds:comment of elod:hasRelatedExpenseApprovalItem Object property in OWL file
- Add rfds:comment of elod:hasRealatedFeature Object property in OWL file
- Add rfds:comment of elod:hasRelatedProject Object property in OWL file
- Add rfds:comment of elod:hasRelatedSpendingItem Object property in OWL file
- Add elod:DisbursedItem as a rdfs:SubClassOf elod:FinancialDecision Class in OWL file

### Changed
- Change rdfs:domain of elod:decisionMuniciplity Object property in OWL file
- Change rdfs:domain of elod:decisionStatus Object property in OWL file
- Change rdfs:domain of elod:hasAttachement Object property in OWL file
- Change rdfs:domain of elod:hasBudgetCategory Object property in OWL file
- Change rdfs:domain of elod:hasBudgetKind Object property in OWL file
- Change rdfs:domain of elod:hasExpenditureLine Object property in OWL file
- Change rdfs:domain of elod:ada Datatype property in OWL file
- Change rdfs:domain of elod:countOfRelatedProjects Datatype property in OWL file
- Change rdfs:domain of elod:decisionType Datatype property in OWL file
- Change rdfs:domain of elod:decisionTypeId Datatype property in OWL file
- Change rdfs:domain of elod:documentType Datatype property in OWL file
- Change rdfs:domain of elod:documentUrl Datatype property in OWL file
- Change rdfs:domain of elod:privateData Datatype property in OWL file
- Change rdfs:domain of gr:legalName Datatype property in OWL file
- Change rdfs:domain of elod:regulatoryActNumber Datatype property in OWL file
- Change rdfs:domain of elod:valueAddedTaxIncluded Datatype property in OWL file
- Change rdfs:comment of elod:beneficiary Object property in OWL file
- Change rdfs:comment of elod:budgetRefersTo Object property in OWL file
- Change rdfs:comment of elod:collaborationType Object property in OWL file
- Change rdfs:comment of elod:financeType Object property in OWL file
- Change rdfs:comment of elod:concerns Object property in OWL file
- Change rdfs:comment of elodGeo:hasPart Object property in OWL file
- Change rdfs:comment of elod:relatedLaw Object property in OWL file
- Change rdfs:comment of elod:relatedFek Object property in OWL file
- Change rdfs:comment of elod:completion Datatype property in OWL file
- Change rdfs:comment of elod:endDate Datatype property in OWL file
- Change rdfs:comment of elod:financialYear Datatype property in OWL file
- Change rdfs:comment of elod:lawNumber Datatype property in OWL file
- Change rdfs:comment of elod:numberOfPeople Datatype property in OWL file
- Change rdfs:comment of elod:startDate Datatype property in OWL file
- Change rdfs:comment of elod:submissionTimeStamp Datatype property in OWL file
- Change rdfs:domain and rdfs:comment of elod:hasThematicCategory Object property in OWL file
- Change rdfs:domain and rdfs:comment of elod:signer Object property in OWL file
- Change rdfs:domain and rdfs:comment of elod:interCountryLaw Datatype property in OWL file
- Change rdfs:domain and rdfs:comment of elod:projectId Datatype property in OWL file
- Change rdfs:domain and rdfs:comment of elod:versionId Datatype property in OWL file
- Change rdfs:domain and rdfs:comment of elod:proceedingNumber Datatype property in OWL file
- Change rdfs:comment of elod:amount Object property in OWL file
- Change rdfs:range of elod:benefactor Object property in OWL file
- Change rdfs:range of dcterms:publisher Object property in OWL file
- Change rdfs:range of elod:fekYear Datatype property in OWL file
- Change rdfs:range of rov:orgStatus Object property in OWL file
- Change rdfs:domain, rdfs:range and rdf:comment of elod:hasCorrectedDecision Object property in OWL file
- Change rdfs:domain and rdfs:range of elod:hasCurrency Object property in OWL file
- Change rdfs:domain and rdfs:range of elod:hasRelatedAdministrativeDecision Object property in OWL file

### Removed
- Remove rdfs:domain of elod:amount Object property in OWL file
- Remove rdfs:domain of elod:benefactor Object property in OWL file
- Remove rdfs:domain of elod:beneficiary Object property in OWL file
- Remove rdfs:domain of elod:budgetRefersTo Object property in OWL file
- Remove rdfs:domain of elod:buyer Object property in OWL file
- Remove rdfs:domain of elod:collaborationType Object property in OWL file
- Remove rdfs:domain of elod:concerns Object property in OWL file
- Remove rdfs:domain of elod:countryIsoCode Object property in OWL file
- Remove rdfs:domain of elod:hasCpv Object property in OWL file
- Remove rdfs:domain and rdfs:range of elodGeo:hasPart Object property in OWL file
- Remove rdfs:domain of elod:price Object property in OWL file
- Remove rdfs:domain of dctemrs:publisher Object property in OWL file
- Remove rdfs:domain of elod:regionCode Object property in OWL file
- Remove rdfs:domain of elod:relatedLaw Object property in OWL file
- Remove rdfs:domain of elod:sector Object property in OWL file
- Remove rdfs:domain of elod:seller Object property in OWL file
- Remove rdfs:domain of elod:timePeriod Object property in OWL file
- Remove rdfs:domain of elod:hasTransaction Object property in OWL file
- Remove rdfs:domain of elod:completion Datatype property in OWL file
- Remove Datatype property elod:cpvCode from OWL file
- Remove Datatype property elod:cpvGreekSubject from OWL file
- Remove Datatype property elod:cpvEnglishSubject from OWL file
- Remove rdfs:domain of dctemrs:description  Datatypeproperty in OWL file
- Remove rdfs:domain of elod:endDate Datatype property in OWL file
- Remove rdfs:domain of elod:financialYear Datatype property in OWL file
- Remove rdfs:domain of dctemrs:issued Datatype property in OWL file
- Remove rdfs:domain of elod:plannedStartDate Datatype property in OWL file
- Remove rdfs:domain of elod:plannedEndDate Datatype property in OWL file
- Remove rdfs:domain of elod:startDate Datatype property in OWL file
- Remove rdfs:domain of elodGeo:name Datatype property in OWL file
- Remove rdfs:domain and rdfs:range of dcterms:subject Datatype property in OWL file
- Remove rdfs:domain of elod:submissionTimeStamp Datatype property in OWL file
- Remove rdfs:domain of dcterms:title Datatype property in OWL file
- Remove one of rdfs:comment of elod:referenceCode Datatype property in OWL file
- Remove prefixes from comments
- Remove the following Object properties which are not used : elod:accountRefersTo, elod:accountType, elod:assetGrantee, elod:assetGrantor, elod:collectiveBodyKind, elod:collectiveBodyType, elod:competentMinistry,elod:competentUnit, elod:decisionMunicipality, elod:employerOrg, elod:donationGiver, elod:donationReceiver, elod:timePeriod, elod:relatedLaw, elod:regulatoryAct, elod:hasVacancyType, elod:hasSpatialType, elod:hasPositionType, elod:hasPosition, elod:hasOpinionOrgType, elod:haOfficialAdministrativeDecision, elod:budgetRefersTo
- Remove the following Datatype properties which are not used : elod:accountApprovalForOtherOrg, elod:asset, elod:budgetApprovalForOrg, elod:coFinancedProject, elod:decisionNumber, elod:duration, elod:europeanLaw, elod:instruction, elod:interCountryLaw, lawNumber, lawYear, elod:numberOfPeople, elod:passAuthority, elod:primaryOfficer, elod:proceedingNumber, elod:refersTo, elod:regulatoryActNumber, elod:secondaryOfficer, rov:orgCategory
- Remove the following Classes which are not used : elod:AccountType, elod:CollectiveBodyKind, elod:CollectiveBodyType, elod:Law, elod:OfficialAdministrativeChange, elod:OpinionOrgType, elod:Position, elod:PositionType, elod:RegulatoryAct, elod:SpatialType, elod:TimePeriod, elod:VacancyType



## [1.1.2] - 2016-09-16
### Added
- Representation of Common Procurement Vocabulary(CPV) in a SKOS concept scheme.

### Changed
- Change rdfs:range of elod:countOfRelatedProjects property from xsd:string to xsd:integer.

### Update
- Update OWL file, Input data Example and RDF data Example of Overall model.

## [1.1.1] - 2016-04-16
### Added
- Add elod:subsidyMunicipality property which links "elod:Subsidy" to "elodGeo:Municipality".
- Add new range class elod:PublicProject for elod:countryIsoCode property.
- Add pc:estimatedPrice to OWL file.

### Removed
- Remove elod:currencyId property.

## [1.1.0] - 2016-03-30
### Added
- More informations for Organizations.
- SPARQL queries for Organizations.
- Add org:hasUnit property to OWL file and pilot 1 graph.
- Add connection of Organizations from NSRF to Organizations from Diavgeia through property rdfs:seeAlso.
- Create Google Spreadsheet with SPARQL query results for pilot 1.

### Changed
- UUIDs of update.

### Removed
- Remove elod:countryId property.


## [1.0.0] - 2016-03-16
### Added
- Add some T-box information for classes and object properies to pilot 1 graph.
- Add Geospatial information for pilot 1 to OWL file and SPARQL Queries.

### Changed
- UUIDs of new harvesting with new namespace.
- Change class of address instances.
- Change URI of a specific Subproject.

### Removed
- Remove postal codes with names instead of their codes.
