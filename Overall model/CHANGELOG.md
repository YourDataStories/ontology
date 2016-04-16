# Change Log
All notable changes to the data model will be documented in this file.

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
