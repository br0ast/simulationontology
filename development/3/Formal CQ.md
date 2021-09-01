# Formal Competency Questions

## CQ3.1

Retrieve all Protection Simulations.

```SPARQL

PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#> 

SELECT * WHERE {
?simulation a sim:ProtectionSimulation .

```

## CQ3.2

Retrieve all the simulations that have `charm` as a reality counterpart along with additional reality counterparts and their specific relationships.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#> 

SELECT distinct ?simulation ?rc ?p WHERE {
?simulation ?p1 ex:charm;
            ?p ?rc .
?rc a sim:RealityCounterpart .
filter (?p1 != ?p)

```


## CQ3.3

Retrieve all the Healing Simulations along with their simulacrum, context and the healed reality counterpart.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#> 

SELECT distinct ?simulation ?simulacrum ?context ?healedrc
where { ?simulation a sim:HealingSimulation ;
sim:healedRealityCounterpart ?healedrc ;
sim:hasSimulacrum ?simulacrum ;
sim:hasContext ?context .
} 
```

## CQ3.4

Retrieve all the Simulation that express a specific symbolic relationship along with the specific type of simulation.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#>  

SELECT distinct ?simulation ?simulationtype
where {
?simulation sim:hasSimulacrum ?simulacrum .
?simulation a ?simulationtype .
MINUS {?simulation a sim:Simulation}
}
```

## CQ3.5

Retrieve all the reality counterparts that are not part in a specific type of simulation and that are not the direct symbolic meaning of the simulacrum.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#>  

SELECT distinct ?rc where {
?rc ?p ?simulation ;
a sim:RealityCounterpart .
?simulation a sim:Simulation
FILTER (?p != sim:isRealityCounterpartOf)
}
```

## CQ3.6

Retrieve all sources that contain simulations that express a symbolic protection against `plague`.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#>  

SELECT distinct ?source where {
?simulation sim:preventedRealityCounterpart ex:plague ;
sim:hasSource ?source .
}
```