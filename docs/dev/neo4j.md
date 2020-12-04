# Neo4j: Getting Started

In order for Neo4j to run locally you will need to setup a few things.

## Setting a Database

1. Install [Neo4j Desktop](https://neo4j.com/download/)
   1. This application includes an installation of the Neo4j software.
2. Read through the [Getting Started Guide](https://neo4j.com/docs/getting-started/current/).
   1. This goes over a lot of the core concepts you will need to get up and running on this project.
3. Open Neo4j Desktop
4. Create a blank database
   1. Database name is just for your reference, it can be whatever you want (ex: 'Family Tree')
   2. Set whatever password you want, make sure to note it as you will need it later when setting up a development environment to inteact with the database. *Note:* For local development your password does not need to be "secure".
5. Start playing around. There are several built in graph structures you can load up to get familar writing queries.

### Helpful Cypher Queries to Help you on your Adventures

1. Get all nodes and their relationships in the database.

  ```cypher
  MATCH (n) RETURN n
  ```

2. Delete all nodes and their relationships in the database. **USE THIS WITH CAUTION**

  ```cypher
  MATCH (n) DETACH DELTE n
  ```

3. Find the shortest path between all of the nodes in the database.

  ```cypher
   MATCH (p:Person)
   WITH collect(p) AS nodes
   UNWIND nodes as n
   UNWIND nodes as m
   WITH * WHERE id(n) <> id(m)
   MATCH path = allShortestPaths( (n)-[*..4]-(m) )
   RETURN path
   ```

## Setting up you Development Environment

***If you are not cloning a repository make sure you are installing the recommended NPM packages when setting up a project.***

1. Your dev and live environments will have different database credentials! Make sure you properly setup a `.env` file.
   1. Recommended environmental variables:

    ```env
    // Neo4J DB Credentials
    N4J_HOST=bolt://localhost:7687
    N4J_USER=neo4j
    N4J_PASS=password
    ```

    The default Bolt port for connecting to Neo4j is `7687`, but this may get changed if something is already using that port. To double check your port return to the main Neo4J Desktop window, in the widget for your project database click the three dots and select 'Manage'. The Bolt port is listed near the bottom of the page.

    The default user is `neo4j`. It is highly unlikely this is changed as it requires additional configuration at startup.

   2. At the start of your script file that will handle your database queries, include the following after declaring your node modules:

    ```javascript
    const neo4jHost = process.env.N4J_HOST;
    const neo4jUser = process.env.N4J_USER;
    const neo4jPass = process.env.N4J_PASS
    let driver = neo4j.driver(neo4jHost, neo4j.auth.basic(neo4jUser, neo4jPass));
    ```

2. This is all you need to get up and running with Neo4j. At this point it is recommended to read through the [Neo4j Javascript Driver documentation](https://neo4j.com/docs/driver-manual/1.7/). *Note:* This project is using the v1.7 driver rather than the latest v4.* driver as some features are bugged in the latest driver that are required for this project.
