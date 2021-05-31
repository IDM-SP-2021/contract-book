# Development Overview

## External Links

### Project Repositories

- [View All](https://github.com/IDM-SP-2021)
- [Proof of Concept](https://github.com/IDM-SP-2021/heroku-test)
- [Full Application](https://github.com/IDM-SP-2021/afiye)

## Proof of Concept

![afiye Proof of Concept](../_media/poc_screenshot.png)

We created a very basic application that demonstrates our ability to work with our core concepts, maintaining a family tree and collecting memories.

This application allows users to create a new family member and add it to the database. The form only requires that one connection be established and the application will automatically generate connections to the remaining nodes in the database. This mirrors our intended functionality in the final product.

Additionally, users can create a memory. The Proof of Concept only allows for text information to be added to a memory, however the final version will allow for users to upload a variety of media formats and documents in addition to basic text content. To create a memory, give it a title, set a date that this memory happened, add some content, and then select the family members in the database that you wish to tag.

*Note:* The live version of this proof of concept is no longer active as the database host, GrapheneDB, has discontinued their relationship with the application host, Heroku. To interact with the proof of concept, please follow the installation instructions available in the repository below

Clone the [repository](https://github.com/IDM-SP-2021/heroku-test) and run the project locally.

---

## NodeJS

- v14.15.0

### Usage

Node is incredibly powerful and allows for numerous package plugins. Additionally, Node serves as a common middleground for all developers on the team that may not be comfortable with server side languages. Node has available packages to connect to all of our backend structures.

---

## D3.js

- v6.2.0 (latest)

### Usage

JavaScript library for visualizing data. D3 takes the data retrieved from our Neo4J database and builds an interactable SVG using HTML Canvas. The added benefit is that the library is free and open source. The next best alternative, gojs, which is better documented and seems more featured, but costs $7,000 for a team. Currently, we are intending to implement two views built on D3, one will be a traditional family tree diagram and the other will be a node network diagram that provides a more abstract visualization of the user's family network. The additional package, D3 Force, is being used to add physics based interactions to the node network diagram such as collision.

D3 is loaded into the application via a [node package](https://www.npmjs.com/package/d3).

### Documentation

D3 is fairly straighforward to work with, but it is recommended to read over the documentation prior to jumping into development.

- [D3 Documentation](https://observablehq.com/@d3/learn-d3)

### Examples

The following examples are the basis for our D3 implementation.

- [Force Directed Graph](https://observablehq.com/@d3/force-directed-graph): Basis for the node network view.
- [Family Tree](https://github.com/trongthanh/family-tree-fork): Basis for the family tree view. [Live demo](https://trongthanh.github.io/family-tree/)

---

## Neo4j

- v4.1.3 (Community Edition)

### Usage

Neo4j is a native graph database that is built to leverage data and data relationships. Rather than maintaining an increasingly complex relational database structure as a family grows, a graph database grows more organically. Neo4j allows us to create infinite types of nodes and relationships between them. With the Community Edition we are losing out on some admin features, as well as being "limited" to 34 billion nodes in the database. Version 4.0 has introduced the ability to run mutliple database instances within a single Neo4j cluster, we may not leverage this feature, but it is good to know that we have the option there if we seek to isolate data. Neo4j uses Cypher as its query language. Cypher often allows for simpler and easier to write and understand queries since its syntax is built specifically for working with nodes and relationships instead of tables. Neo4j can also interface directly with Node through its official JavaScript driver, making it easy to integrate with our application.

### Documentation

Neo4j can be pretty easy to pick up the basics, but it is highly recommended to read over the documentation prior to jumping into development.

- [Neo4j Documentation](https://neo4j.com/docs/operations-manual/current/)
- [Neo4j Developer Guides](https://neo4j.com/developer/get-started/)
- [Neo4j Driver Documentation](https://neo4j.com/docs/driver-manual/current/)
- [Cypher Manual](https://neo4j.com/docs/cypher-manual/current/)
- [Cypher Refcard](https://neo4j.com/docs/cypher-refcard/current/)

### Software Requirements

For local development, the Neo4j Desktop application is *required*. This is available on MacOS and Windows and can be downloaded from the [Neo4j downloads page](https://neo4j.com/download/).

### Additional Information

For additional information related to how to use Neo4j and usage cases for our project please see [Neo4j: Getting Started](/dev/neo4j.md)

---

## MongoDB

MongoDB is a general purpose database. It was selected for ease of use with our NodeJS environment. MongoDB is used to store user and post data for the application.

MongoDB is connected to the NodeJS application through the Mongoose package.

### Documentation

- [MongoDB Server Documentation](https://docs.mongodb.com/manual/)
- [Mongoose Documentaion](https://mongoosejs.com/docs/guide.html)

### Software Requirements

For local development, MongoDB can either be used or installed using the MongoDB Shell for a command line interface or the MongoDB Compass for a GUI interface.

Either of these tools can be downloaded and installed from the [MongoDB downloads page](https://www.mongodb.com/try/download/tools).
