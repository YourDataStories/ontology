Prefix | URL
-----------|-----------------
rdf: | http://www.w3.org/1999/02/22-rdf-syntax-ns#
elod: | http://linkedeconomy.org/ontology#
tr: | http://linkedeconomy.org/ontology/traffic#
rdfs: | http://www.w3.org/2000/01/rdf-schema#
pc: | http://purl.org/procurement/public-contracts#
geo: | http://www.opengis.net/ont/geosparql#

## RDF example for input data of Traffic Observation Data
```xml
 <tr:TrafficObservation rdf:about="http://linkedeconomy.org/ontology/traffic/resource/TrafficObservation/14995">
    <tr:trafficCnt rdf:datatype="http://www.w3.org/2001/XMLSchema#integer">46</tr:trafficCnt>
    <tr:observationEnd rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">2015-03-22T07:45:00Z</tr:observationEnd>
    <tr:observationStart rdf:datatype="http://www.w3.org/2001/XMLSchema#dateTime">2015-03-22T07:30:00Z</tr:observationStart>
    <tr:vehicleType rdf:resource="http://linkedeconomy.org/ontology/traffic/resource/VehicleType/2"/>
    <tr:directed rdf:resource="http://linkedeconomy.org/ontology/traffic/resource/Direction/1"/>
    <tr:onPoint rdf:resource="http://linkedeconomy.org/ontology/traffic/resource/ObservationPoint/1"/>
  </tr:TrafficObservation>
  <tr:TrafficSite rdf:about="http://linkedeconomy.org/ontology/traffic/resource/TrafficSite/1">
    <tr:includesObservationPoint rdf:resource="http://linkedeconomy.org/ontology/traffic/resource/ObservationPoint/1"/>
    <tr:underWork rdf:resource="http://linkedeconomy.org/resource/Contract/AwardNotice/2013208591/5795646"/>
  </tr:TrafficSite>
