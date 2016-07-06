```xml
<http://linkedeconomy.org/resource/Dataset/Diavgeia> a dcat:Dataset ;
   dct:title "Greek Transparency Portal Diavgeia" ;
   dct:description "Greek Transparency Portal is a rich dataset with a large number of interconnected entities, taking part in all aspects of economic activity in Greece and covering all stages of public sector cash flow: from budgeting to contract formation and finally, to actual spending" ;
   dct:publisher <http://linkedeconomy.org/resource/Organization/YourDataStories> ;
   dcat:distribution [ a dcat:Distribution ;
  	 dct:description "The YourDataStories (YDS) SPARQL endpoint provides access to all YDS datasets. The Diavgeia dataset is represented in the form of the http://yourdatastories.eu/NSRF/Diavgeia." ;
  	 dct:license [
  		 a dct:LicenseDocument .
  	 ] ;
  	 dcat:accessURL <http://{Server IP}:8890/sparql> ;
  	 dct:modified "2015-12-31T11:01:31+0000" .
   ] ;
   dcat:keyword "Diavgeia", "Greece", "Decisions" ;
   dcat:contactPoint <http://linkedeconomy.org/resource/Organization/YourDataStories> ;
   dct:theme [
  	 a skos:Concept .
   ] .

<http://linkedeconomy.org/resource/Organization/YourDataStories>
a foaf:Organization, vcard:Organization ;
foaf:name “Your Data Stories” ;
dct:type [a skos:Concept] .

```
