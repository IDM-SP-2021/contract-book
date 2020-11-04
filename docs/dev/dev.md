# Development Overview

## External Links

### Project Repositories

- [View All](https://github.com/IDM-SP-2021)
- [Proof of Concept](https://github.com/IDM-SP-2021/heroku-test)

---

## NodeJS

- v12.18.3

### Usage

Node is incredibly powerful and allows for numerous package plugins. Additionally, Node serves as a common middleground for all developers on the team that may not be comfortable with server side languages. Node has available packages to connect to all of our backend structures.

### Dependencies

Unless otherwise noted, dependency is using the latest released version.

- [d3](https://www.npmjs.com/package/d3)
  - See D3 section below for more information.
- [d3-force](https://www.npmjs.com/package/d3-force)
  - See D3 section below for more information.
- [jquery](https://www.npmjs.com/package/jquery)
  - Required for some interaction functions.
- [neo4j-driver v1.7.7](https://www.npmjs.com/package/neo4j-driver/v/1.7.7)
  - Using previous release for multiple queries in one session functionality. Feature is bugged in current release.

### Development Dependencies

- [webpack v4.44.2](https://www.npmjs.com/package/webpack/v/4.44.2)
  - Using previous version as v5 was recently released and realworld documentation and forums have not updated to use the latest updates.
- [webpack-cli](https://www.npmjs.com/package/webpack-cli)
  - Used to run Webpack commands on the command line. Necessary for building and running the development server.
- [webpack-dev-server](https://www.npmjs.com/package/webpack-dev-server)
  - Used to run a development server with live update on document save.
- [dotenv-webpack](https://www.npmjs.com/package/dotenv-webpack)
  - Compile environmental variables with Webpack. Necessary to prevent port access issues on dev machines.
- [html-webpack-plugin](https://www.npmjs.com/package/html-webpack-plugin)
  - Simplifies bundling HTML files in Webpack build process.
- [rimraf](https://www.npmjs.com/package/rimraf)
  - Used in `npm run clean` script to remove contents of build directory.
- [path-browserify](https://www.npmjs.com/package/path-browserify)
  - Implements Node `path` module for browsers. (*Note:* This dependency may not be necessary, during Proof of Concept development there were compilation issues that needed this to resolve.)
- [css-loader](https://www.npmjs.com/package/css-loader)
  - Webpack loader necessary for bundling CSS files.
- [source-map-loader](https://www.npmjs.com/package/source-map-loader)
  - Extracts source maps so that debugging is easier. (*Note:* This loader may not be necessary, during Poof of Concept development source maps would not load correctly.)

### Possible Future Dependencies

- [lodash](https://www.npmjs.com/package/lodash)
  - Useful JavaScript library to make working with arrays, numbers, objects, strings, etc. easier.
- [postcss](https://www.npmjs.com/package/postcss)
  - Powerful css preprocessor with multiple plugin options. Reduce our need to worry about backwards browswer compatibilty.

---

## D3.js lasdjfl;kdsjflksd

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
- [Neo4j Driver v1.7 Documentation](https://neo4j.com/docs/driver-manual/1.7/)
- [Cypher Manual](https://neo4j.com/docs/cypher-manual/current/)
- [Cypher Refcard](https://neo4j.com/docs/cypher-refcard/current/)

### Software Requirements

For local development, the Neo4j Desktop application is *required*. This is available on MacOS and Windows and can be downloaded from the [Neo4j downloads page](https://neo4j.com/download/).