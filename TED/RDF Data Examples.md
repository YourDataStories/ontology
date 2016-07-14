Prefix | URL
-----------|-----------------
xsd: | http://www.w3.org/2001/XMLSchema#
elod: | http://linkedeconomy.org/ontology#
skos: | http://www.w3.org/2004/02/skos/core#
gr: | http://purl.org/goodrelations/v1#
dcterms: | http://purl.org/dc/terms/
vcard: | http://www.w3.org/2006/vcard/ns#
pc: | http://purl.org/procurement/public-contracts#

###RDF example for input data of TED
```xml
<http://linkedeconomy.org/resource/Contract/294257> a pc:Contract ;
        elod:sector <http://linkedeconomy.org/resource/Taxonomy/OECD/CRS/21020>;
        dcterms:title “N3 Mulhuddart interchange upgrade.”@en;
        dcterms:description “Construction of a new road bridge adjacent to the existing over the N3...”@el ;
        dcterms:issued "2012-11-16"^^xsd:date;
        elod:contractId “294257”^^xsd:string;
        pc:awardDate ”2012-07-31”^^xsd:date;
        elod:documentUrl "http://ted.europa.eu/udl?uri=TED:NOTICE:366795-2012:TEXT:EN:HTML"^^xsd:string;
        elod:documentType "Contract award"^^xsd:string;
        pc:mainObject <http://linkedeconomy.org/resource/CPV/45233120-6> ;
        pc:additionalObject <http://linkedeconomy.org/resource/CPV/45221111-3> ;
        pc:contractingAuthority <http://linkedeconomy.org/resource/Organization/{authority id}>;
        pc:awardedTebder <http://linkedeconomy.org/resource/Organization/{tender id}>;
        pc:kind <http://linkedeconomy.org/resource/Taxonomy/KindScheme/WORKS> ;
               pc:estimatedPrice [ a gr:UnitPriceSpecification;
                            gr:hasCurrencyValue "5200000"^^xsd:float;
                            gr:valueAddedTaxIncluded “false”^^xsd:Boolean;
                            elod:hasCurrency <http://linkedeconomy.org/resource/Currency/EUR>
                          ].
                          
pc:Tender pc:bidder <http://linkedeconomy.org/resource/Organization/{authority id}>.

<http://linkedeconomy.org/resource/Organization/{authority id}> vcard:hasAddress <http://linkedeconomy.org/resource/Address/{authority id}>;
        gr:legalName "Fingal County Council"@en.

<http://linkedeconomy.org/resource/Organization/{tender id}> vcard:hasAddress <http://linkedeconomy.org/resource/Address/{tender id}>;
        gr:legalName "BAM Civil Ltd"@en.

<http://linkedeconomy.org/resource/Taxonomy/OECD/CRS/21020> skos:prefLabel "Road transport"^^xsd:string.

<http://linkedeconomy.org/resource/CPV/45221111-3> skos:notation "45221111-3";
        skos:prefLabel "Road bridge construction work"@en.
        
<http://linkedeconomy.org/resource/CPV/45233120-6> skos:notation "45233120-6";
        skos:prefLabel "Road construction works"@en.

<http://linkedeconomy.org/resource/Currency/EUR> skos:notation "EUR";
        skos:prefLabel "Euro"@en.
        
<http://linkedeconomy.org/resource/Taxonomy/KindScheme/WORKS> skos:prefLabel "Works"@en.

<http://linkedeconomy.org/resource/Address/{authority id}> vcard:street-address "Fingal County Hall, Main Street"^^xsd:string;
        vcard:locality "Swords"^^xsd:string.

<http://linkedeconomy.org/resource/Address/{tender id}> vcard:street-address "Kill, C. Kildare"^^xsd:string.