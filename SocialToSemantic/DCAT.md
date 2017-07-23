```xml
<http://linkedeconomy.org/resource/Dataset/Social> 
   a dcat:Dataset ;
   dct:title "Social to Semantic" ;
   dct:description "The Social to Semantic dataset is based on publicly available web information from different publishing platforms, referring to public projects described in the various datasets included in the YDS platfrom " ;
dct:provenance "This dataset is derived from the harvesting of publicly available information within web publishing platforms like Twitter, blogs, and news sites, as well as, the official YDS accompanying mobile application." ;
   dct:publisher  <http://linkedeconomy.org/resource/Organization/YourDataStories> ;
   dcat:distribution [ a dcat:Distribution ;
  	 dct:description "The YourDataStories (YDS) SPARQL endpoint provides access to all YDS datasets. The TED dataset is represented in the form of the http://yourdatastories.eu/social graph." ;
	dct:identifier “http://yourdatastories.eu/social” ;
  	 dct:license [
  		 a dct:LicenseDocument ;
            rdfs:label “European Commission (https://ec.europa.eu/info/legal-notice_en)” ;
rdfs:comment “© European Union, 1995-2016.
Reuse is authorised, provided the source is acknowledged. The Commission's reuse policy is implemented by the Decision of 12 December 2011 - reuse of Commission documents. The general principle of reuse can be subject to conditions which may be specified in individual copyright notices. Therefore, users are advised to refer to the copyright notices on individual websites maintained under Europa and in individual documents. Reuse is not applicable to documents subject to intellectual property rights of third parties.” ;
  	 ] ;
  	 dcat:accessURL <http://yds.iit.demokritos.gr:8890/sparql> ;
  	 dct:modified "2017-07-23T00:00:00+0000" ;
   ] ;
dct:temporal [
	a dct:PeriodOfTime ;
	schema:startDate "2017-07-23" ;
	schema:endDate "2017-07-23" ;
] ;
   owl:versionInfo “v 0.1” ;
   adms:versionNotes “Initial ingestion of social content retrieved by the start date of the dataset” ;
   dct:accrualPeriodicity <http://purl.org/linked-data/sdmx/2009/code#freq-A> ;
   dcat:keyword "social";
   dcat:contactPoint <http://linkedeconomy.org/resource/Organization/YourDataStories> ;
   dct:theme <http://eurovoc.europa.eu/1810> .
