```xml
<http://yourdatastories.eu/pilot3> a dcat:Dataset ;
   dct:title "OpenTED(Tenders Electronic Daily)" ;
   dct:description "http://ted.openspending.org/"^^xsd:anyURI ;
   dct:publisher <http://linkedeconomy.org/resource/Publisher/YourDataStories> ;
   dcat:distribution [ a dcat:Distribution ;
  	 dct:description "The dataset is part of the http://yourdatastories.eu/pilot3/ graph." ;
  	 dct:license [
  		 a dct:LicenseDocument .
  	 ] ;
  	 dcat:accessURL <http://143.233.226.61:8890/sparql> ;
  	 dc:modified "2016-04-13T18:20:04+0000" .
   ] ;
   dcat:keyword "Tenders", "Contracts", "Construction", "Decisions", "Roadworks";
   dcat:contactPoint [
  	 a vcard:Kind .
   ] ;
   dct:theme [
  	 a skos:Concept .
   ] .
```
