# Example Queries

## Q1. Aggregate daily traffic per site
```
PREFIX : <http://linkedeconomy.org/ontology/traffic#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dcterms: <http://purl.org/dc/terms/>

select ?site ?year ?mon ?day (sum(?cnt) as ?traffic)  where {
  ?o :observationStart ?dt;
     :trafficCnt ?cnt;
     :onPoint ?s .
   ?s dcterms:title ?site .
} GROUP BY ?site (year(?dt) AS ?year) (month(?dt) AS ?mon) (day(?dt) AS ?day) ORDER BY ?site ?year ?mon ?day
```

## Q2. Traffic per weekday accross years (per site)
```
PREFIX : <http://linkedeconomy.org/ontology/traffic#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dcterms: <http://purl.org/dc/terms/>

select ?site ?year ?day (sum(?cnt) as ?traffic) where {
    ?o :observationStart ?dt;
       :trafficCnt ?cnt;
       :dayOfWeek ?day;
       :onPoint ?p .
    ?p dcterms:title ?site .
} GROUP BY ?site (year(?dt) as ?year) ?day ORDER BY ?site ?day ?year
```
## Q3. Traffic per site per vehicle type per weekday across years
```
PREFIX : <http://linkedeconomy.org/ontology/traffic#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dcterms: <http://purl.org/dc/terms/>

select ?site ?l ?day ?year (sum(?cnt) as ?traffic) where {
    ?o :observationStart ?dt;
       :trafficCnt ?cnt;
       :dayOfWeek ?day;
       :onPoint ?p ;
       :vehicleType ?vt.
    ?p dcterms:title ?site .
    ?vt rdfs:label ?l.
} GROUP BY ?site (year(?dt) as ?year) ?day ?l ORDER BY ?site ?l ?day ?year
```
## Q4. Traffic each year per site per Vehicle Type
```
PREFIX : <http://linkedeconomy.org/ontology/traffic#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dcterms: <http://purl.org/dc/terms/>

select ?site ?type ?year (sum(?cnt) as ?traffic) where {
    ?o :observationStart ?dt;
       :trafficCnt ?cnt;
       :onPoint ?p ;
       :vehicleType ?vt.
    ?p dcterms:title ?site .
    ?vt rdfs:label ?type.
} GROUP BY ?site ?type (year(?dt) as ?year) ORDER BY ?site ?year ?type
```
## Q5. Aggregate yearly traffic per site
```
PREFIX : <http://linkedeconomy.org/ontology/traffic#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dcterms: <http://purl.org/dc/terms/>

select ?site ?year (sum(?cnt) as ?traffic) where {
    ?o :observationStart ?dt;
       :trafficCnt ?cnt;
       :onPoint ?p .
       
    ?p dcterms:title ?site .
} GROUP BY ?site (year(?dt) as ?year) ORDER BY ?site ?year
```
