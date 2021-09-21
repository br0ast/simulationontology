# Formal Competency Questions

## CQ3.1

What are the simulations in which the simulacra are seen as a symbolical protection against reality counterparts?

```SPARQL

PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#> 

SELECT * WHERE {
?simulation a sim:ProtectionSimulation .

```

## CQ3.2

What are the simulations that have `charm` as a reality counterpart and other additional reality counterparts, and what specific relationship link  those simulations to their reality counterparts?

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

What are the simulations and their respective simulacra, contexts and reality counterparts in which their simulacrum is a symbolical cure for their reality counterpart?

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

What are the simulations that express a specific symbolic relationship and what is the specific relationship?

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

What are the reality counterparts that are not part of a specific type of simulation but that are not the direct symbolic meaning of a simulacrum?

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

What are the sources that contain simulations that express a symbolic protection against `plague`?

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#>  

SELECT distinct ?source where {
?simulation sim:preventedRealityCounterpart ex:plague ;
sim:hasSource ?source .
}
```