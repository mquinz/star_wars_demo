# star_wars_demo

# Objective
 Demo cool Neo4j stuff using Star-Wars data from Kaggle

# Overview

# Data Model
This is what the data model should look like after we've loaded all of the CSV Files.

# Data Ingestion

The Neo4j LOAD CSV command is a perfectly adequate CSV file loader.
## Create Uniqeness Indexes

``` Cypher


```


## Load All nodes
Use the Cypher LOAD CSV command to load all nodes - 1 label at a time.

### Characters

``` Cypher
// LOAD Characters
LOAD CSV WITH HEADERS FROM
"https://raw.githubusercontent.com/mquinz/star_wars_demo/master/data/characters.csv"
AS row
MERGE (c:Character {name : row.name})
ON CREATE
   SET c.eyeColor = row.eye_color,
       c.gender = row.gender,
       c.weight = toInteger(row.mass),
       c.height = toInteger(row.height),
       c.birthYear = row.birth_year,
       c.skinColors = split(row.skin_color,','),
       c.hairColors = split(row.hair_color,',')

Return c
```


### Starships
name,model,manufacturer,cost_in_credits,length,max_atmosphering_speed,crew,passengers,cargo_capacity,consumables,hyperdrive_rating,MGLT,starship_class
Executor,Executor-class star dreadnought,"Kuat Drive Yards, Fondor Shipyards",1143350000,19000,n/a,279144,38000,250000000,6 years,2.0,40,Star dreadnought

``` Cypher

// LOAD Starships
LOAD CSV WITH HEADERS FROM
"https://raw.githubusercontent.com/mquinz/star_wars_demo/master/data/starships.csv"
AS row
MERGE (s:Starship {name : row.name})
ON CREATE
   SET s.model = row.model,
       s.mfg = row.manufacturer,
       s.class =  row.starship_class,
       s.cost = toInteger(row.cost_in_credits),
       s.crew = toInteger(row.crew),
       s.capacity = toInteger(row.cargo_capacity),
       s.cost = toInteger(row.cost_in_credits),
       s.length = toFloat(row.length),
       s.hyperdriveRating = toFloat(row.hyperdrive_rating),
       s.maxSpeed = toInteger(row.max_atmosphering_speed),
       s.mglt = toInteger(row.MGLT),
       s.consumables =  row.consumables

Return s

```


### Planets
``` Cypher

// LOAD Planets
LOAD CSV WITH HEADERS FROM
"https://raw.githubusercontent.com/mquinz/star_wars_demo/master/data/planets.csv"
AS row

MERGE (p:Planet {name : row.name})
ON CREATE
   SET p.rotationPeriod = toInteger(row.rotation_period),
       p.orbitalPeriod = toInteger (row.orbital_period),
       p.diameter = toInteger(row.diameter),
       p.gravity = toFloat(row.gravity),
       p.climate = row.climate,
       p.terrain = split(row.terrain,','),
       p.population = toInteger(row.population)

Return p

```


### Vehicles

``` Cypher

// LOAD Vehicles
LOAD CSV WITH HEADERS FROM
"https://raw.githubusercontent.com/mquinz/star_wars_demo/master/data/vehicles.csv"
AS row
MERGE (v:Vehicle {name : row.name})
ON CREATE
   SET v.model = row.model,
       v.mfg = row.manufacturer,
       v.class =  row.vehicle_class,
       v.cost = toInteger(row.cost_in_credits),
       v.crew = toInteger(row.crew),
       v.capacity = toInteger(row.cargo_capacity),
       v.cost = toInteger(row.cost_in_credits),
       v.length = toFloat(row.length),
       v.maxSpeed = toInteger(row.max_atmosphering_speed),
       v.consumables =  row.consumables

Return v

```


### Species
``` Cypher

// LOAD Species
LOAD CSV WITH HEADERS FROM
"https://raw.githubusercontent.com/mquinz/star_wars_demo/master/data/species.csv"
AS row

MERGE (s:Species {name : row.name})
ON CREATE
   SET s.classification = row.classification,
       s.designation =  row.designation,
       s.avgHeight = toInteger(row.average_height),
       s.avgLifespan = toInteger(row.average_lifespan),
       s.language = row.language,
       s.skinColors = split(row.skin_color,','),
       s.eyeColors = split(row.eye_color,','),
       s.hairColors = split(row.hair_color,',')

Return s

```

## Load Relationships Between nodes

### Characters and their home Planets
name,height,mass,hair_color,skin_color,eye_color,birth_year,gender,homeworld,species
Luke Skywalker,172,77,blond,fair,blue,19BBY,male,Tatooine,Human


``` Cypher
LOAD CSV WITH HEADERS FROM
"https://raw.githubusercontent.com/mquinz/star_wars_demo/master/data/characters.csv"
AS row
MATCH (c:Character {name : row.name}),
      (p:Planet {name : row.homeworld}),
      (s:Species {name : row.species}),
MERGE (c)-[:HAS_HOMEPLANET]->(p),
 (c)-[:IS]->(s)




```
