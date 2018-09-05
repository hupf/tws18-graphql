[back](README.md)

# Mutations

Apart from the `query` type, a GraphQL service can optionally provide a `mutation` type to allow to modify data. The separation between these two types is pure convention (just like avoiding to modify data in HTTP `GET` requests). Technically any query could be implemented to modify data.

Again, assume having the following schema:

```
type User {
  id: ID!,
  name: String
}

type Query {
  users: [User]
}

type Schema {
  query: Query
}
```

To be able to create new users, we create a mutation endpoint called `createUser` and add the `Mutation` type to the schema:

```
type Mutation {
  createUser(name: String): User
}

type Schema {
  query: Query
  mutation: Mutation
}
```

Then we add another resolver function:

```
const users = [...];
const resolvers = {
  users: () => users,
  createUser: ({ name }) => {
    const user = { id: users[users.length - 1].id + 1, name };
    users.push(user);
    return user;
  }
};
```

Finally let's execute a mutation query to create a new entry:

```
mutation {
  createUser(name: "Jane Doe") {
    name
  }
}
```

## Exercise: Mutation endpoint

* Add a mutation endpoint to your schema
* Implement a resolver function that adds objects to the collection.
* Test it by executing a mutation query

## Input type

Instead of passing single values, you can define an input type:

```
input UserInput {
  name: String
}

type Mutation {
  createUser(user: UserInput): User
}
```

Like this, the resolver will receive an object matching this input type.

_Hint:_ The input type differs probably from the query type. E.g. the `UserInput` in this example does not allow to set an `id`.

## Exercise: Input type

Adjust you mutation endpoint to accept an input type.
