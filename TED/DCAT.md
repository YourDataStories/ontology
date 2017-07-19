```xml
<http://linkedeconomy.org/resource/Dataset/TED> 
   a dcat:Dataset ;
   dct:title "Tenders Electronic Daily(TED)" ;
   dct:description "TED (Tenders Electronic Daily) is the 'Supplement to the Official Journal of the EU ("OJ S"), dedicated to European public procurement. There is information on public procurement contracts, according to the EU rules on public procurements, of notices published in EU Member States, European Economic Area (EEA) and beyond. There is also the ability to browse, search and sort procurement notices by country, region, business sector and more." ;
dct:provenance ”This dataset is derived from CSV files provided by European Union Open Data Portal (https://data.europa.eu/euodp/en/data/dataset/ted-csv).” ;
   dct:publisher  <http://linkedeconomy.org/resource/Organization/YourDataStories> ;
   dcat:distribution [ a dcat:Distribution ;
  	 dct:description "The YourDataStories (YDS) SPARQL endpoint provides access to all YDS datasets. The TED dataset is represented in the form of the http://yourdatastories.eu/TEDUpdate, http://yourdatastories.eu/TEDGreece, http://yourdatastories.eu/TEDIreland graphs." ;
	dct:identifier “http://yourdatastories.eu/TED”, “http://yourdatastories.eu/TEDGreece”, “http://yourdatastories.eu/TEDIreland” ;
  	 dct:license [
  		 a dct:LicenseDocument ;
            rdfs:label “European Commission (https://ec.europa.eu/info/legal-notice_en)” ;
rdfs:comment “© European Union, 1995-2016.
Reuse is authorised, provided the source is acknowledged. The Commission's reuse policy is implemented by the Decision of 12 December 2011 - reuse of Commission documents. The general principle of reuse can be subject to conditions which may be specified in individual copyright notices. Therefore, users are advised to refer to the copyright notices on individual websites maintained under Europa and in individual documents. Reuse is not applicable to documents subject to intellectual property rights of third parties.” ;
  	 ] ;
  	 dcat:accessURL <http://yds.iit.demokritos.gr:8890/sparql> ;
  	 dct:modified "2017-04-24T00:00:00+0000" ;
   ] ;
dct:temporal [
	a dct:PeriodOfTime ;
	schema:startDate "2005-08-06" ;
	schema:endDate "2015-12-30" ;
] ;
   owl:versionInfo “v 0.1” ;
   adms:versionNotes “Add full data of all years about Contract Notices and Contract Award Notices per Country” ;
   dct:accrualPeriodicity <http://purl.org/linked-data/sdmx/2009/code#freq-A> ;
   dcat:keyword "TED", "Tenders", "Contracts", "Buyers";
   dcat:contactPoint <http://linkedeconomy.org/resource/Organization/YourDataStories> ;
   dct:theme <http://eurovoc.europa.eu/1810> .
