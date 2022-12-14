# star_wars_demo

## Load Data Using CSV


## Load All nodes
Use the Cypher LOAD CSV command to load all nodes - 1 label at a time.  After the nodes are loaded, we will connect them by creating relationships between them.

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

### Add Social Network names to existing Characters

``` Cypher
LOAD CSV WITH HEADERS FROM
"https://raw.githubusercontent.com/mquinz/star_wars_demo/master/data/social/characterNames.csv"
AS row

 match (c:Character {name:row.characterName})
set c.socialName = row.socialName

```
### Add new Characters from Social Media

This will create Character nodes using the information from the social network feed for characters that do not match any of the existing nodes.  It will MERGE/CREATE nodes only for the rows with 'none' as the characterName.  For example, the Character Boba Fett already has a socialName so it will be skipped, but the socialName CAMIE does not match any existing Character so they will be added during this step.

```
LOAD CSV WITH HEADERS FROM
"https://raw.githubusercontent.com/mquinz/star_wars_demo/master/data/social/characterNames.csv"
AS row
with row where row.characterName = "none"

MERGE (c:Character {name:row.socialName})
set c.socialName = row.socialName
```
## Load Relationships Between Nodes
By loading the nodes first, creating the relationships use a simple pattern of using MATCH statements to get the From and To nodes, then doing a MERGE for the relationship name.

### Characters -> home Planets , and Characters -> Species

With a single pass through the characters, we can create relationships to both their home planets and to their Species

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

### Character Interactions

The interactions.csv file contains relationships between the characters.  This file was created based on script analysis to identify when one character speaks to another.  The source of this data is the Social Network so the keys used here will be the socialName fields.

``` Cypher
LOAD CSV WITH HEADERS FROM
"https://raw.githubusercontent.com/mquinz/star_wars_demo/master/data/social/interactions.csv"
AS row
MATCH (char1:Character {socialName : row.source}),
      (char2:Character {socialName : row.target})
MERGE (char1)-[i:INTERACTED_WITH]->(char2)
     SET i.count = toInteger(row.count)

```
