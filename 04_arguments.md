[back](README.md)

# Query arguments

As a prepration (if not already done), add an `id` field of type `ID` to your list objects from the previous chapter.

In GraphQL, every field and nested object can get its own set of arguments. To use arguments, you have to:

* Define the accepted arguments in the schema.
* Extend the resolver function to receive an object containing the endpoint's arguments.

Let's say we have the following schema:

```
type User {
  id: ID!,
  name: String
}

type Query {
  users: [User]
}
```

To be able to filter by `id`, add another query definition allowing an argument:

```
user(id: ID!): User
```

Extend the resolver to filter the array by the given `id` argument:

```
const users = [...];
const resolvers = {
  users: () => users,
  user: (args) => users.find(u => u.id == args.id)
};
```

Now query an object with a certain `id` by [passing arguments to the object field](https://graphql.github.io/learn/queries/#arguments).

See also: [Passing Arguments](https://graphql.github.io/graphql-js/passing-arguments/)

## Exercise: Filter argument

* Extend your schema to accept an argument that filters the list of objects.
* Pass an argument in the query.
* See what happens if you don't pass an argument in the query (see [Non-Null](https://graphql.github.io/learn/schema/#lists-and-non-null))

## Exercise: Option argument

Add a field that returns its value depending on a unit argument (e.g. a price in CHF or USD).
