[back](README.md)

# Setup & first steps

Within a new directory, create a `package.json` file:

```
npm init -y
```

Add GraphQL to the project:

```
npm i graphql
```

Add an `index.js` file with an initial schema definition (a schema defines queries, mutations and subscriptions):

```
`use strict`;

const { graphql, buildSchema } = require('graphql');

const schema = buildSchema(`
  type Query {
    name: String
  }

  type Schema {
    query: Query
  }
`);
```

This allows us to query the schema for `name` and get back a string. GraphQL knows how to return a value for `name` through a _resolver_.

So add a resolver:

```
const resolvers = {
  name: () => 'John Doe'
};
```

And add a query to get the data:

```
const query = `
  query {
    name
  }
`;

graphql(schema, query, resolvers)
  .then(result => console.log(result))
  .then(error => console.error(error));
```
Execute the script in the terminal to study the response:

```
node index.js
```
