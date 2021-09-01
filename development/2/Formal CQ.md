# Formal Competency Questions

## CQ2.1

Retrieve all simulations along with their sources.

```SPARQL

PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#> 

SELECT * WHERE {
?simulation sim:hasSource ?source .
}

```

## CQ2.2

Retrieve all the simulations and respective reality counterparts and sources that have the same simulacrum but a different source.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#> 

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

Retrieve all the simulations that have `rose` as a simulacrum along with the simulations of the variants of `rose`.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#> 

SELECT distinct ?simulation
where { {
ex:rose sim:isSimulacrumOf ?simulation .} UNION {ex:rose sim:hasVariant ?variant.
?variant sim:isSimulacrumOf ?simulation}
} 
```

## CQ2.4

Retrieve all the variants of `man`.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#>  

PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#>  

SELECT distinct ?variant
where {
ex:man sim:hasVariant ?variant .
}
```

## CQ2.5

Retrieve all the contexts of the simulations listed in `dictionaryofsymbols1`.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#>  

SELECT distinct ?context
where {
?simulation sim:hasSource ex:dictionaryOfSymbols1 ;
            sim:hasContext ?context .
} 
```

## CQ2.6

Retrieve all the simulations without a source.

```SPARQL
PREFIX ex: <https://example.org/> 
PREFIX sim: <http://www.semanticweb.org/bruno/ontologies/2021/3/simulationontology#>  

SELECT distinct ?rc ?context where {
?simulation a sim:Simulation .
MINUS {?simulation sim:hasSource ?source}
}
```

