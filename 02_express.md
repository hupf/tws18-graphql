[back](README.md)

# Serve over HTTP

Instead of launching the script with Node.js, we are going to serve the schema over HTTP.

Install the Express web framework for Node.js and its GraphQL middleware:

```
npm i express express-graphql
```

Remove the `query` variable definition and the `graphql(schema, query, resolvers)...` utility function call from `index.js`. Instead, register the GraphQL middleware (initialized with your schema) and the HTTP server:

```
const express = require('express');
const graphqlHttp = require('express-graphql');

const PORT = process.env.PORT || 3000;
const server = express();

server.use('/graphql', graphqlHttp({
  schema,
  graphiql: true,
  rootValue: resolvers
}));

server.listen(PORT, () => {
  console.log(`Listening on http://localhost:${PORT}`);
});
```

The `graphiql: true` option will enable the [GraphiQL](https://github.com/graphql/graphiql) in-browser IDE for exploring GraphQL.

Now start the server by launching the script:

```
node index.js
```

And visit http://localhost:3000/graphql in your web browser, this should display the GraphiQL interface.

_Hint:_ On the top right of the screen is a "Docs" link which allows you to browse the schema definition.

_Hint:_ From now on, remember to restart the server when making any changes on the file.

## Exercises

* Execute the previous query from the GraphiQL interface.
* Execute a query using CURL in the terminal or `fetch()` in the browser (see [GraphQL Clients](https://graphql.github.io/graphql-js/graphql-clients/))
