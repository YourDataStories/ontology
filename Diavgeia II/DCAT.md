```xml
<http://linkedeconomy.org/resource/Dataset/DiavgeiaII> a dcat:Dataset ;
   dct:title "Diavgeia" ;
   dct:description "https://diavgeia.gov.gr"^^xsd:anyURI ;
   dct:publisher <http://linkedeconomy.org/resource/Publisher/YourDataStories> ;
   dcat:distribution [ a dcat:Distribution ;
  	 dct:description "The dataset is part of the http://yourdatastories.eu/data/DiavgeiaII/ graph." ;
  	 dct:license [
  		 a dct:LicenseDocument .
  	 ] ;
  	 dcat:accessURL <http://143.233.226.61:8890/sparql> ;
  	 dc:modified "2015-12-31T11:01:31+0000" .
   ] ;
   dcat:keyword "Diavgeia", "Greece", "Decisions" ;
   dcat:contactPoint [
  	 a vcard:Kind .
   ] ;
   dct:theme [
  	 a skos:Concept .
   ] .

