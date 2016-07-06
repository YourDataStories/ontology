```xml
<http://linkedeconomy.org/resource/Dataset/NSRF> a dcat:Dataset ;
   dct:title "National Strategic Reference Framework (NSRF)" ;
   dct:description "This data source provides detailed information for each NSRF project, which is a group of activities aimed at implementing an integrated and functionally independent object. The project is implemented by one or more entities called beneficiaries. If the beneficiary is a public body either projects implemented by contractors or by beneficiary itself." ;
   dct:publisher  <http://linkedeconomy.org/resource/Organization/YourDataStories> ;
   dcat:distribution [ a dcat:Distribution ;
  	 dct:description "The YourDataStories (YDS) SPARQL endpoint provides access to all YDS datasets. The NSRF dataset is represented in the form of the http://yourdatastories.eu/NSRF/Diavgeia." ;
  	 dct:license [
  		 a dct:LicenseDocument .
  	 ] ;
  	 dcat:accessURL <http://{Server IP}:8890/sparql> ;
  	 dct:modified "2015-12-31T11:01:31+0000" .
   ] ;
   dcat:keyword "NSRF", "Greece", "Subsidies", "Beneficiaries" ;
   dcat:contactPoint <http://linkedeconomy.org/resource/Organization/YourDataStories> ;
   dct:theme [
  	 a skos:Concept .
   ] .
   
<http://linkedeconomy.org/resource/Organization/YourDataStories>
a foaf:Organization, vcard:Organization ;
foaf:name “Your Data Stories” ;
dct:type [a skos:Concept] .