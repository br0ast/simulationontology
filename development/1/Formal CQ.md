# Formal Competency Questions

## CQ1.1

Retrieve all the symbolic meanings of `ashTree`.

```SPARQL

PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#> 

SELECT ?rc WHERE {
?simulation sim:hasSimulacrum ex:ashTree;
            sim:hasRealityCounterpart ?rc .
}

```

## CQ1.2

Retrieve all the simulations that have `flowerLanguage` as the context.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#> 

SELECT ?simulation WHERE {
?simulation sim:hasContext ex:flowerLanguage
}
```


## CQ1.3

Retrieve all the simulations in which `odin` is present as either a simulacrum or a reality counterpart.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#> 

SELECT distinct ?simulation
where {
?simulation sim:hasSimulacrum|sim:hasRealityCounterpart ex:Odin
} 
```

## CQ1.4

Retrieve all the simulacra and their reality counterparts that take part in a simulation in a `generalOrUnknown` context.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#>  

SELECT distinct ?simulacrum ?realitycounterpart
where {
?simulation sim:hasSimulacrum ?simulacrum ;
            sim:hasRealityCounterpart ?realitycounterpart ;
            sim:hasContext ex:generalOrUnknown .
}
```

## CQ1.5

Retrieve all the simulacra that have a common reality counterpart in a simulation along with the context of the simulation.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#>  

SELECT distinct ?simulacrum ?context where {
?simulation1 sim:hasRealityCounterpart ?rc .
?simulation2 sim:hasRealityCounterpart ?rc .
?rc sim:isRealityCounterpartOf ?simulation .
?simulation sim:hasSimulacrum ?simulacrum ;
            sim:hasContext ?context
filter (?simulation1 != ?simulation2)
}
```

## CQ1.6

Retrieve all the reality counterparts that have `ashTree` as a simulacrum along with the context of the simulation that links these two elements.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#>  

SELECT distinct ?rc ?context where {
?simulation sim:hasRealityCounterpart ?rc;
            sim:hasSimulacrum ex:ashTree;
            sim:hasContext ?context .
}
```

## CQ1.7

Retrieve all the simulations that have multiple simulacra.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#>  

SELECT ?simulation where {
?simulation sim:hasSimulacrum ?simulacrum1;
            sim:hasSimulacrum ?simulacrum2 .
FILTER (?simulacrum1 != ?simulacrum2)
}
```