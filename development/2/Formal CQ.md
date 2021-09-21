# Formal Competency Questions

## CQ2.1

What are the simulations and which sources support their existence?

```SPARQL

PREFIX ex: <https://example.org/> 
PREFIX sim: <https://w3id.org/simulation/ontology/> 

SELECT * WHERE {
?simulation sim:hasSource ?source .
}

```

## CQ2.2

What are the simulations and respective reality counterparts that have the same simulacrum but a different source?

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <https://w3id.org/simulation/ontology/> 

SELECT distinct ?simulation ?rc ?source WHERE {
?simulation1 sim:hasSimulacrum ?simulacrum ;
             sim:hasSource ?source1 .
?simulation2 sim:hasSimulacrum ?simulacrum ;
             sim:hasSource ?source2 .
filter (?simulation1 != ?simulation2 && ?source1 != ?source2) .
?simulacrum sim:isSimulacrumOf ?simulation .
?simulation sim:hasRealityCounterpart ?rc ;
            sim:hasSource ?source .
}
```


## CQ2.3

What are the reality counterparts of the simulations with `rose` as a
simulacrum or its variants?

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <https://w3id.org/simulation/ontology/> 

SELECT distinct ?simulation
where { {
ex:rose sim:isSimulacrumOf ?simulation .} UNION {ex:rose sim:hasVariant ?variant.
?variant sim:isSimulacrumOf ?simulation}
} 
```

## CQ2.4

What are the variants of `man`?

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <https://w3id.org/simulation/ontology/>  

PREFIX ex: <https://example.org/> 
PREFIX sim: <https://w3id.org/simulation/ontology/>  

SELECT distinct ?variant
where {
ex:man sim:hasVariant ?variant .
}
```

## CQ2.5

What are the contexts of the simulations listed in `dictionaryOfSymbols1`?

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <https://w3id.org/simulation/ontology/>  

SELECT distinct ?context
where {
?simulation sim:hasSource ex:dictionaryOfSymbols1 ;
            sim:hasContext ?context .
} 
```

## CQ2.6

Are there simulations that do not have a source?

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <https://w3id.org/simulation/ontology/>  

ASK {
?simulation a sim:Simulation .
MINUS {?simulation sim:hasSource ?source}
}
```

