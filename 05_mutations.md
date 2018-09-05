[back](README.md)

# Mutations

Apart from the `query` type, a GraphQL service can optionally provide a `mutation` type to allow to modify data. The separation between these two types is pure convention (just like avoiding to modify data in `GET` requests). Technically any query could be implemented to modify data.

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

Finally let's execute a mutation query, creation a new entry:

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

## Exercise: Input object type

Adjust the mutation endpoint to accept a input object type.
