## GraphQL

Their website says it best:

```
GraphQL is a query language for APIs and a runtime 
for fulfilling those queries with your existing data. 
GraphQL provides a complete and understandable description 
of the data in your API, gives clients the power to 
ask for exactly what they need and nothing more, makes it 
easier to evolve APIs over time, and enables powerful 
developer tools.
```

[These](https://landscape.graphql.org/category=graph-ql-adopter&format=card-mode&grouping=category) companies are using GraphQL. Very in demand!

## Graphs

Graphs are a powerful data structure. They consist of a set of nodes and edges which connect pairs of nodes. Here's an example:

![diagram of GraphQL nodes and edges](https://miro.medium.com/max/3780/1*z0-1RpRpVn_i-92AMR_2BA.png)

## The benefits of RESTful routing

RESTful routes let us use a simple API for accessing/modifying data using HTTP requests (GET, POST, PATCH, DELETE, & PUT). REST has 6 architectual constraints:

* **Uniform Interface:** When a developer is familiar with one of your API's they are familiar with all of your APIs

* **Client-Server:** The client and server are seperate from one another. They can evolve independently.

* **Stateless:** The client manages state. Not the server!

* **Cacheable:** Caching is applied to resources to make application more efficient

* **Layered System:** The client cannot tell whether it is connected directly to the end system of some intermediary (enhanced security)

* **Code on demand:** Optional constraint. Lets server return executable code.

## The drawbacks of RESTful routing 

Modern apps have HIGHLY relational data (many edges relative to # of nodes). **Fetching highly relational data with a REST API leads to repetitive requests to the backend (expensive).**

Additionally, the bulk of REST processing is dependent on the server. When REST was created user devices were slow and unreliable. However, **our devices have evolved and are much more powerful now - REST does not give us the ability to utilize this increased power!**

## Enter GraphQL 

They're several advantages to using GraphQL. They include:

**Single Request/Response:** Queries are packaged into a single request to the backend (This makes data delivery more efficient and gives the client more power).

**Precision:** When querying with GraphQL we specify which data we want to return from the server.. so we never overfetch/fetch content that we don't need! 

**Server Client Balance:** GraphQL makes use of our evolved hardware by giving power back to the client.. reducing the burden we place on the server.

**GraphQL lets us model relationships between our data (appreciates in value as apps become more and more relational). When using GraphQL we make less requests and are way more efficient!**

## JSON

GraphQL query results come back in JSON (JavaScript Object Notation is easy for both humans and machines to read). 

JSON syntax:

* Data is in name/value pairs
* Data is separated by commas
* Curly braces hold objects
* Square brackets hold arrays
* String values must be written with double quotes

Example:

```json
{
    "name": "Jeff Bezos",
    "age": 55,
    "children": 4,
    "height": 5.6,
    "wealth": 137000000000,
    "commendations": ["National Merit Scholar", "Silver Knight Award"],
    "companies": {
        "Amazon": {
            "founded": 1994,
            "description": "Online marketplace",
            "missionStatement": "Our vision is to be earth's most customer-centric company; to build a place where people can come to find and discover anything they might want to buy online."
        },
        "blueOrigin": {
            "founded": 2000,
            "description": "Space travel",
            "missionStatement": "We're committed to building a road to space so our children can build the future."
        }
    }
}
```

Note: We must convert JSON objects before we can use the data. We also must convert JavaScript objects to JSON before we can send it to the server. 

## GraphiQL

[GraphiQL](https://github.com/graphql/graphiql) is an in-browser IDE for writing GraphQL queries. Once we open the interface, we'll see two panels. We write our queries on the left hand side and the results are displayed on the right hand side. 

```
When we configure a GraphQL application, we define our data 
in 'types,' with each type representing a singular resource on 
the server. Graphiql knows this schema and provides us with 
error highlighting and prompts. If we try to query for a 
variable which is not present on the current type, the 
variable will be underlined in red. Hovering over the variable will also display an error message.
```

## Inline Fragments

Setting up inline fragments for harry potter character types:

```js
type Muggle implements Character {
  id: ID!
  name: String!
}

type Wizard implements Character {
  id: ID!
  name: String!
  house: [House]!
}
```

Querying for a character by ID:

```js
query FindCharacter {
  character(id: 117) {
    name
    // this allow us to only get house information if this character is a Wizard
    ... on Wizard {
      house
    }
  }
}
```

## Mutations

Syntax for writing mutations: 

```js
mutation {
    mutationName(key1: "val1", key2: "val2", ...) {
        // These arguments specify the information to be returned from the backend
        key1,
        key2,
        association {
            id,
            name,
            ...
        }
    }
}
```

## GraphQL Types

**Scalar** types are concrete units of data (String, Int, Float, Boolean, ID). 

**Object types** represent a kind of object you can fetch from your service, and what fields it has.

## Express + GraphQL

Install `[express-graphql](https://github.com/graphql/express-graphql)` and `graphql`. 

Simple example of setting up a server using express and `express-graphql`:

```js
const express = require('express');
const expressGraphQL = require('express-graphql');
const { buildSchema } = require('graphql');

// Construct a schema, using GraphQL schema language
const schema = buildSchema(`
  type Query {
    hello: String
  }
`);

// The root provides a resolver function for each API endpoint
const root = {
  hello: () => {
    return 'Hello world!';
  },
};

const app = express();
app.use('/graphql', expressGraphQL({
  schema: schema,
  rootValue: root,
  graphiql: true,
}));

app.listen(5000, () => {
  console.log('Running a GraphQL API server at localhost:5000/graphql');
});
```

## GraphQL Schemas

The schema file tells GraphQL what the application data looks like. including all properties the data has, and how those properties relate to one another. The `GraphQL/type module` defines GraphQL types. The most basic schema componenets are `object types`. Object types represent an object you can fetch from your database and what fields that object has. Here's an example:

```js
// schema.js

const graphql = require("graphql");
// capitalization is important!
const { GraphQLObjectType, GraphQLString, GraphQLInt } = graphql;

// By creating a GraphQLObjectType we are telling GraphQL what a user looks like.
const UserType = new GraphQLObjectType({
  // the name property describes the type we are defining.
  // Since we are defining a UserType the name will be UserType.
  name: "UserType",
  // fields is THE MOST important property - it refers to everything this Type will be able to return to you.
  // Which means all of the data associated with this type in the database.
  // If you don't have a field then you don't have returned data.

  //For our User the fields ar id, name, and favoriteNumber.
  fields: {
    // we have to tell GraphQL what type of data each of these fields
    // returned from the database are.
    id: { type: GraphQLString },
    name: { type: GraphQLString },
    favoriteNumber: { type: GraphQLInt }
  }
});
```