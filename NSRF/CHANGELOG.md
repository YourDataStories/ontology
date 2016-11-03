# Change Log
All notable changes to the data model will be documented in this file.

## [1.1.1] - 2016-11-03
### Added
- Add classes: elod:Aggregate, pc:Contract, elod:PublicWork
- Add Object properties: elod:hasSpendingAggregate, elod:hasBudgetAggregate, elod:hasContractAggregate, elod:buyer, elod:hasRelatedContract, elod:hasOperationalCode, elod:hasProjectStatus.
- Add datatype properties: pc:actualEndDate, pc:startDate, elod:countOfRelatedContracts, elod:completionOfPayments, elod:completionOfContracts

### Updated
- Update RDF data example.
- Update Ontology Specification.
- Update UML Class Diagram.

### Changed
- Change rdfs:comment of elod:Subsidy and elod:PublicProject

### Removed
- Remove class elod:Subproject.
- Remove Object properties: elod:hasRelatedProject, elod:hasRelatedSpendingItem, elod:hasRelatedBudgetItem
- Remove Datatype properties: elod:completion, elod:countOfRelatedProjects
