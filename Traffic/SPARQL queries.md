# Example Queries

## Q1. Aggregate daily traffic (all vehicle types)
```
PREFIX : <http://linkedeconomy.org/ontology/traffic#>

select concat(?year, "-", ?mon, "-", ?day) as ?date sum(?cnt) as ?traffic  where {
  ?o :observationStart ?dt;
     :trafficCnt ?cnt.
} GROUP BY (year(?dt) AS ?year) (month(?dt) AS ?mon) (day(?dt) AS ?day) ORDER BY ?date
```

## Q2. Traffic per day of the week across years (all vehicle types)
```
PREFIX : <http://linkedeconomy.org/ontology/traffic#>

select ?year ?day (sum(?cnt) as ?traffic) where {
    ?o :observationStart ?dt;
       :trafficCnt ?cnt;
       :dayOfWeek ?day.
} GROUP BY (year(?dt) as ?year) ?day ORDER BY ?day ?year
```
## Q3. Traffic per vehicle type per day of the week across years
```
PREFIX : <http://linkedeconomy.org/ontology/traffic#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

select ?l ?day ?year (sum(?cnt) as ?traffic) where {
    ?o :observationStart ?dt;
       :trafficCnt ?cnt;
       :dayOfWeek ?day;
       :vehicleType ?vt.
    ?vt rdfs:label ?l.
} GROUP BY (year(?dt) as ?year) ?day ?l ORDER BY ?l ?day ?year
```
## Q4. Traffic each year per Vehicle Type
```
PREFIX : <http://linkedeconomy.org/ontology/traffic#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

select ?type ?year (sum(?cnt) as ?traffic) where {
    ?o :observationStart ?dt;
       :trafficCnt ?cnt;
       :vehicleType ?vt.
    ?vt rdfs:label ?type.
} GROUP BY ?type (year(?dt) as ?year) ORDER BY ?year ?type
```
