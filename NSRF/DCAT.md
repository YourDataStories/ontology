```xml
<http://linkedeconomy.org/resource/Dataset/NSRF> a dcat:Dataset ;
   dct:title "NSRF" ;
   dct:description "https://www.espa.gr"^^xsd:anyURI ;
   dct:publisher <http://linkedeconomy.org/resource/Publisher/YourDataStories> ;
   dcat:distribution [ a dcat:Distribution ;
       dct:description "The dataset is part of the http://yourdatastories.eu/data/NSRF/ graph." ;
       dct:license [
           a dct:LicenseDocument .
       ] ;
       dcat:accessURL <http://143.233.226.61:8890/sparql> ;
       dc:modified "2015-12-31T11:01:31+0000" .
   ] ;
   dcat:keyword "NSRF", "Greece", "Subsidies" ;
   dcat:contactPoint [
       a vcard:Kind .
   ] ;
   dct:theme [
       a skos:Concept .
   ] .

<http://linkedeconomy.org/resource/Publisher/YourDataStories> a foaf:Group;
   foaf:name "Your Data Stories" ;
   dct:type [a skos:Concept] .
