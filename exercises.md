
# Exercises for Star-Wars Demo

# Exercise 1 - Arrows Modeling Exercise

## Neo4j Data Modeling tool

https://neo4j.com/labs/arrows/
Watch the 3-minute training video (optional)

Go to the Arrows App
https://arrows.app/

_____________________________

## Experiment On a New Model
- Create some nodes and relationships to get a hang of the tool.  
- Give each node a Label and some properties.
- Give each relationship a type


## Import an Existing Model
1. Click on the Gold Arrow at the top left corner of the screen.
1. Click on the Import menu option.
1. Cut and paste the following json text into the text import box.
1. Choose a theme for displaying the Model.

``` json
{
  "style": {
    "font-family": "Nunito Sans",
    "background-color": "#F2F2F2",
    "background-image": "",
    "background-size": "100%",
    "node-color": "#4C8EDA",
    "border-width": 0,
    "border-color": "#000000",
    "radius": 75,
    "node-padding": 5,
    "node-margin": 2,
    "outside-position": "auto",
    "node-icon-image": "",
    "node-background-image": "",
    "icon-position": "inside",
    "icon-size": 64,
    "caption-position": "inside",
    "caption-max-width": 200,
    "caption-color": "#ffffff",
    "caption-font-size": 20,
    "caption-font-weight": "normal",
    "label-position": "inside",
    "label-display": "bare",
    "label-color": "#ffffff",
    "label-background-color": "#848484",
    "label-border-color": "#848484",
    "label-border-width": 3,
    "label-font-size": 20,
    "label-padding": 5,
    "label-margin": 4,
    "directionality": "directed",
    "detail-position": "above",
    "detail-orientation": "parallel",
    "arrow-width": 3,
    "arrow-color": "#848484",
    "margin-start": 5,
    "margin-end": 5,
    "margin-peer": 20,
    "attachment-start": "normal",
    "attachment-end": "normal",
    "relationship-icon-image": "",
    "type-color": "#848484",
    "type-background-color": "#F2F2F2",
    "type-border-color": "#848484",
    "type-border-width": 0,
    "type-font-size": 21,
    "type-padding": 5,
    "property-position": "outside",
    "property-alignment": "colon",
    "property-color": "#848484",
    "property-font-size": 20,
    "property-font-weight": "normal"
  },
  "nodes": [
    {
      "id": "n1",
      "position": {
        "x": 525.9565373574089,
        "y": 790.1486066193784
      },
      "caption": "",
      "labels": [
        "Character"
      ],
      "properties": {
        "name": "Han Solo",
        "birthYear": "aby20",
        "pilot": "true",
        "occupation": "smuggler"
      },
      "style": {}
    },
    {
      "id": "n2",
      "position": {
        "x": 624.752688094361,
        "y": 280.34818746197885
      },
      "caption": "",
      "labels": [
        "Character"
      ],
      "properties": {
        "name": "Leia Organa",
        "birthYear": "aby25"
      },
      "style": {}
    },
    {
      "id": "n3",
      "position": {
        "x": 925.5089357851191,
        "y": 581.1044351527369
      },
      "caption": "",
      "labels": [
        "Character"
      ],
      "properties": {
        "name": "Luke Skywalker",
        "birthYear": "aby25",
        "jedi": "true"
      },
      "style": {}
    },
    {
      "id": "n4",
      "position": {
        "x": 173.4997800498739,
        "y": 314.2629784784658
      },
      "caption": "",
      "labels": [
        "Character"
      ],
      "properties": {
        "name": "Jabba the Hutt",
        "wt": "1000"
      },
      "style": {}
    },
    {
      "id": "n5",
      "position": {
        "x": 75,
        "y": 628.5949587219344
      },
      "caption": "",
      "labels": [
        "Starship"
      ],
      "properties": {
        "name": "Millennium Falcom",
        "length": "77"
      },
      "style": {
        "node-color": "#68bc00"
      }
    },
    {
      "id": "n6",
      "position": {
        "x": 133.74615966996345,
        "y": 922.7076511955595
      },
      "caption": "",
      "labels": [
        "Character"
      ],
      "properties": {
        "name": "Chewbacca",
        "birthYear": "bby5",
        "pilot": "true"
      },
      "style": {}
    }
  ],
  "relationships": [
    {
      "id": "n0",
      "fromId": "n1",
      "toId": "n2",
      "type": "MARRIED_TO",
      "properties": {
        "year": "aby55"
      },
      "style": {
        "detail-position": "inline"
      }
    },
    {
      "id": "n1",
      "fromId": "n2",
      "toId": "n3",
      "type": "TWIN_OF",
      "properties": {},
      "style": {
        "detail-position": "inline"
      }
    },
    {
      "id": "n2",
      "fromId": "n1",
      "toId": "n4",
      "type": "WORKED_FOR",
      "properties": {
        "year": "aby50"
      },
      "style": {
        "detail-position": "inline"
      }
    },
    {
      "id": "n3",
      "fromId": "n1",
      "toId": "n5",
      "type": "OWNS",
      "properties": {},
      "style": {
        "detail-position": "below"
      }
    },
    {
      "id": "n4",
      "fromId": "n1",
      "toId": "n5",
      "type": "PILOT_OF",
      "properties": {},
      "style": {
        "detail-position": "above"
      }
    },
    {
      "id": "n5",
      "fromId": "n4",
      "toId": "n2",
      "type": "IMPRISONED",
      "properties": {},
      "style": {}
    },
    {
      "id": "n6",
      "fromId": "n1",
      "toId": "n6",
      "type": "FRIEND_OF",
      "properties": {},
      "style": {}
    },
    {
      "id": "n7",
      "fromId": "n6",
      "toId": "n5",
      "type": "CO_PILOT_OF",
      "properties": {},
      "style": {}
    }
  ]
}

```

## Adding a New Node
1. Add a new node with and give it a Character Label.
1. Give your new Character node some Properties.
1. Create a relationship between your node and another node.
1. Give the relationship a Type and a direction.


# Exercise 2 - Using the Data Importer tool

Follow the instructions in
[Star_Wars_Data_Preparation.md](/Star_Wars_Data_Preparation)


# Exercise 3 - Simple Queries

## Finding Nodes using Key

Using the following Cypher statement as an  example, Find the node with name= Luke Skywalker.

``` Cypher
MATCH (c:Character)
WHERE c.name = "Han Solo"
RETURN c
```

## Finding Nodes by Indexed Fields

Using the following Cypher statement as an  example, Find the Character nodes with blond hair

``` Cypher
MATCH (n:Character)
WHERE n.gender = 'male'
RETURN n.name as name, n.birth_year as birthYear, n.hair_color as hair
```

## Sorting and Limiting Output

Everyone knows that Chewbacca is pretty tall.  Is he the tallest?  This query will find the 5 tallest Characters.  Run it to find the answer.  

##### Bonus Query:  
Modify the query to find the 3 smallest Characters

``` Cypher

MATCH (n:Character)
WHERE n.height IS NOT NULL
RETURN n.name, n.height as height_in_cm
ORDER BY height_in_cm DESC LIMIT 5

```

## Traversing Basics

A traversal is when Neo4j follows a relationship to 1 or more additional nodes.  It is similar in concept to a join in RDBMS but executes much differently.

The following query will find all of the Character nodes that have a HOMEWORLD relationship to the Planet with name = Naboo.

Using it as a model, find the Species that have an ORIGINATED relationship to Naboo.

``` Cypher

MATCH (p:Planet)<-[r:HOMEWORLD]-(o:Character)
WHERE p.name = 'Naboo'
 RETURN  p,r,o
```
##### Bonus Query:
Return only the names of the Characters

### Relationship Counts
Find the 2 Characters with the most interactions

``` Cypher
MATCH (c1:Character  )-[i:INTERACTS_WITH]-(c2:Character)
RETURN c1.name as char1, c2.name as char2, i.count as interactions
ORDER by interactions DESC LIMIT 1
```

### Relationship properties

Who does Han Solo interact with the most?

Start with finding the Han Solo node and then use
the INTERACTS_WITH relationship to find the name of the other Character.

``` Cypher
MATCH (c:Character {name:'Han Solo'})-[i:INTERACTS_WITH]-(otherChar)
RETURN  otherChar.name, i.count AS interactions
ORDER BY interactions DESC LIMIT 10
```

#### Bonus Query:  
Add a relationship from the otherChar Node to a Species node to get the names of the otherChar's species.

### Variable Length (Recursive) queries

Which characters Interact with the characters that Han Solo Interacts with?

This adds the syntax ''* 0..2' on the INTERACTS_WITH relationship to indicate that it is variable with a minimum of 0 and a maximum of 2 'hops' away.

``` Cypher
MATCH p=(c:Character {name:'Han Solo'})-[i:INTERACTS_WITH* 0..2]-(otherChar)
RETURN p

```
How many nodes?  How many relationships?

#### Bonus Query:  
Change the maximum of 2 to 3.  It may take a few seconds.  How many nodes?  How many relationships?


### Intersection of Related nodes

Which characters interact with both Han Solo and Luke Skywalker?

This query starts with  Han Solo AND  Luke Skywalker nodes and then finds their interactions.  The otherNodes are the ones that satisfy both relationship filters.
``` Cypher
MATCH  (c1:Character {name:'Han Solo'})-[i:INTERACTS_WITH]-(otherChar)-[:INTERACTS_WITH]-(c2:Character {name:'Luke Skywalker'})
return *
```

#### Bonus Query:  
Change the names of the 2 characters.  
##### HINT:
Use a simple query to get some names if you need to
``` Cypher
MATCH (c:Character) RETURN c.name
```

### Recommendations Query
Which characters does C-3PO interact with that R2-D2 does not?  This is typical of a collaborations recommendation engine.

It first finds the 2 nodes of interest, then finds all of the characters that C-3PO interacts with that are not interacting with R2-D2

``` Cypher
MATCH (c3po:Character {name:"C-3PO"}),(r2:Character {name:"R2-D2"})
MATCH (c3po)-[:INTERACTS_WITH]-(others)
WHERE NOT (others)-[:INTERACTS_WITH]-(r2)
return c3po,others
```


### Aggregation query
Which Character has the most diverse group of interactions?  Count the number of Species that each Character INTERACTS_WITH.

``` Cypher
MATCH (c:Character  )-[:INTERACTS_WITH]-(:Character)-[:IS]-(s:Species)
RETURN c.name as character,  count(s) as count
ORDER BY count DESC, character
```

#### Bonus Query:  
Add a level of aggregation to show how many of each Species a Character INTERACTS_WITH.
``` Cypher
MATCH (c:Character  )-[:INTERACTS_WITH]-(:Character)-[:IS]-(s:Species)

return c.name as character, s.name as species, count(s) as count
ORDER BY character,species
```
### Shortest Path query

Find the shortest path between 2 nodes.  This is an unweighted approach that finds the smallest number of hops between 2 characters.
```Cypher
MATCH (c1:Character {name: 'Ackbar'}),(c2:Character {name:"CLONE COMMANDER CODY"})
match p =allShortestPaths((c1)-[:INTERACTS_WITH*..10]-(c2))
return p
 ```

# Queries to Create data

## Insert a New Node

 This uses the CREATE command which will try to insert the new record without first looking to see if the record already exists.   Duplicate Records are possible unless there is an integrity constraint defined.

 ``` Cypher
CREATE (c:Character)
SET c.name = 'markq'
    c.hairColor='skintone'
RETURN c
```
## Insert a New Node (Safely)

This uses the MERGE command which will check to see if a matching node already exists.  If an existing node matches all of the selection criteria, that existing node is returned, otherwise a new node is created and the new node is returned.

Use this template to create your own node
``` Cypher
MERGE (c:Character {name: 'markq'})
ON CREATE
  SET c.hairColor='skintone'
RETURN c
```
#### Bonus query
Change the name to a Character that already exists to see if the hairColor is updated.


## Insert a New Relationship (Safely)

Creating a new relationship between 2 existing nodes is a very simple process.  First, use MATCH statements to obtain the starting and ending nodes, then CREATE/MERGE a relationship using a direction and a Type.  Relationship properties are optional.


Use this template to create your own relationship
``` Cypher
MATCH (c1:Character {name: 'markq'}),(c2:Character {name: 'Han Solo'})
MERGE (c1)-[f:FOLLOWS]->(c2)
RETURN c1,f,c2
```
#### Bonus query


## Updating a Node

To update a node, use MATCH statements to obtain the nodes that will be updated, then use SET statements to apply the new values.   Don't forget to use local variable names in order to reference the nodes/relationships to be changed.

Be very careful when crafting the MATCH statement. Neo4j WILL update every record that matches the criteria - even when you think you are only updating a single row.  In the example below, if the where clause did not exist, ALL Characters would be updated.

``` Cypher

MATCH (c:Character)
WHERE c.name = 'markq'
SET c.nationality = 'US',
    c.birthYear = '2022'

```

Choose a character and give them a new property

#### Bonus query
Use a map to give your node multiple key/value pairs at once.  Using the += syntax will merge the existing properties with the ones you supply.  Using the = syntax will replace the existing properties with your map.

``` Cypher
// example
MATCH (c:Character)
WHERE c.name = 'markq'
SET  c+= {nationality:'US',
          birthYear:'2022',
        }

```

# APOC Functions
APOC (Awesome Procedures on Cypher) is a utility library created by Neo4j engineers to provide 400+ functions and procedures to simplify Cypher expressions.  They are also used to batch Update/delete transactions into smaller chunks so that Java Out-of-Memory exceptions are minimized.

APOC procedures and functions are invoked in Cypher statements by using their full signature and passing any necessary arguments.  

The following example will find the percentile values of an attribute.
``` Cypher
MATCH (char:Character)
RETURN apoc.agg.percentiles(char.pagerank, [0.25, 0.5, 0.75, 1.0]) AS percentiles;
```
