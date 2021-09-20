# Formal Competency Questions

## CQ1.1

What are the reality counterparts of the simulations that have `ashTree` as a simulacrum?

```SPARQL

PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#> 

SELECT ?rc WHERE {
?simulation sim:hasSimulacrum ex:ashTree;
            sim:hasRealityCounterpart ?rc .
}

```

## CQ1.2

What are the simulations that exist within a  `flowerLanguage` context?

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#> 

SELECT ?simulation WHERE {
?simulation sim:hasContext ex:flowerLanguage
}
```


## CQ1.3

What are the simulations in which `odin` participates as either the simulacrum or reality counterpart?

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#> 

SELECT distinct ?simulation
where {
?simulation sim:hasSimulacrum|sim:hasRealityCounterpart ex:Odin
} 
```

## CQ1.4

What are the simulacra and reality counterparts that take part in simulations of a `generalOrUnknown` context?

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

What are the simulacra that share the same reality counterpart in their respective simulations and what is the context in which their simulations exist?

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

What are the reality counterparts that take part in simulations with `ashTree` as a simulacrum and what is the context of those simulations?

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

Are there simulations that have multiple simulacra?

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#>  

ASK {
?simulation sim:hasSimulacrum ?simulacrum1;
            sim:hasSimulacrum ?simulacrum2 .
FILTER (?simulacrum1 != ?simulacrum2)
}
```