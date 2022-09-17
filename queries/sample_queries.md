# Sample Queries for Star-wars demo

## Get all Planet nodes

``` Cypher

// Get All Planet nodes
MATCH (p:Planet)   
    RETURN p
```
## List the names of the 10 most populous Planet nodes

``` Cypher


MATCH (p:Planet)
    WHERE p.population is not null
    RETURN p.name as planet, p.population as pop
    ORDER BY pop  DESC
    LIMIT 10
```

## Find node using Character Name
``` Cypher

MATCH (c:Character)
WHERE c.name  = 'Han Solo'  
    RETURN c
```

## Show related node for Character node
``` Cypher

MATCH (c:Character)-[:IS]->(s:Species)
WHERE c.name  = 'Han Solo'  
    RETURN c,s
```
## Which Characters INTERACTED_WITH Han Solo
``` Cypher

MATCH (c:Character)-[i:INTERACTED_WITH]->(other:Character)
WHERE c.name  = 'Han Solo'  
    RETURN c,other
```

## Which Characters INTERACTED_WITH Han Solo and what Species are they
``` Cypher

MATCH (c:Character)-[i:INTERACTED_WITH]->(other:Character)-[:IS]->(s:Species)
WHERE c.name  = 'Han Solo'  
    RETURN c,other,s

```


## Which Species have the most Characters
``` Cypher

MATCH (c:Character)-[:IS]->(s:Species)
    RETURN s.name as specieName,count(c) as count
    ORDER BY count DESC limit 4

```


## Which Characters do Han Solo and Palpatine (The Emperor) both INTERACTED_WITH?
``` Cypher

MATCH (han:Character {name:"Han Solo"})-[h:INTERACTED_WITH]->(c:Character) <-[i:INTERACTED_WITH]-(emperor:Character {name:"Palpatine"})
    RETURN han,emperor,c

```

## Which Characters does C-3PO INTERACTED_WITH that R2-D2 does not
``` Cypher
MATCH (c:Character {name:"C-3PO"}),(r:Character {name:"R2-D2"})
MATCH (c)-[:INTERACTED_WITH]-(others)
WHERE NOT (others)-[:INTERACTED_WITH]-(r)
return c,others
```


## Which Character has the most diverse group of INTERACTED_WITH nodes.
``` Cypher
MATCH (c:Character)-[:INTERACTED_WITH]-(other)-[:IS]->(s:Species)
WITH c.name as char, count (DISTINCT s.name) as count
where count > 1
return * order by count DESC, char ASC
```
