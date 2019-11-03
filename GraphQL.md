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



