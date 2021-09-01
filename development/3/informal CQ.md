# Informal Competency Questions (first iteration)

## Question 1

### Identifier

CQ3.1

### General Question

Retrieve all Protection Simulations.

### Example Applied Question

Retrieve all Protection Simulations.

#### Expected Outcome

A list of Simulations

#### Results

* `acorn-plague`

#### Based on

E3

## Question 2

### Identifier

CQ3.2

### General Question

Retrieve all the simulations that have a specific reality counterpart along with additional reality counterparts and their specific relationships.

### Example Applied Question

Retrieve all the simulations that have `charm` as a reality counterpart along with additional reality counterparts and their specific relationships.

#### Expected Outcome

A table with simulations, reality counterparts, specific relationships.

#### Results

| Simulation               | Reality Counterpart | Specific Reality Counterpart Relationship Type |
|--------------------------|---------------------|------------------------------------------------|
| `agate-charm-healthyBlood` | `healthyBlood`        | `elicitedRealityCounterpart`                    |
| `aloe-charm-longevity`     | `longevity`          | `elicitedRealityCounterpart`                     |

#### Based on

E3

## Question 3

### Identifier

CQ3.3

### General Question

Retrieve all the Healing Simulations along with their simulacrum, context and the healed reality counterpart.

### Example Applied Question

Retrieve all the Healing Simulations along with their simulacrum, context and the healed reality counterpart.

#### Expected Outcome

A table with simulations, simulacra, contexts and healed reality counterparts.

#### Results

| simulation             | simulacrum      | context    | healed reality counterpart |
|------------------------|-----------------|------------|--------------------------|
| `amberStone-jaundice`    | `amberStone`      | `islamic`   | `jaundice`                 |
| `ashLeavesInWine-poison` | `ashLeavesInWine` | `grecoRoman` | `poison`                   |

#### Based on

E3

## Question 4

### Identifier

CQ3.4

### General Question

Retrieve all the Simulation that express a specific symbolic relationship along with the specific type of simulation.

### Example Applied Question

Retrieve all the Simulation that express a specific symbolic relationship along with the specific type of simulation.

#### Expected Outcome

A table composed by simulations and their specific type

#### Results

| simulation             | type of simulation      |
|------------------------|-------------------------|
| `acorn-plague`           | `ProtectionSimulation`    |
| `amberStone-jaundice`    | `HealingSimulation`       |
| `ashLeavesInWine-poison` | `HealingSimulation`       |
| `acaciaThors-neith`      | `EmblematicSimulation`    |
| `bird-theGods`           | `ManifestationSimulation` |

#### Based on

E3

## Question 5

### Identifier

CQ3.5

### General Question

Retrieve all the reality counterparts that are not part in a specific type of simulation and that are not the direct symbolic meaning of the simulacrum.

### Example Applied Question

Retrieve all the reality counterparts that are not part in a specific type of simulation and that are not the direct symbolic meaning of the simulacrum.

#### Expected Outcome

A list of reality counterparts

#### Results

* `healthyBlood`
* `longevity`

#### Based on

E3

## Question 6

### Identifier

CQ3.6

### General Question

Retrieve all sources that contain simulations that express a symbolic protection against a specific reality counterpart.

### Example Applied Question

Retrieve all sources that contain simulations that express a symbolic protection against `plague`.

#### Expected Outcome

A list of sources

#### Results

* `dictionaryOfSymbols1`

#### Based on

E3