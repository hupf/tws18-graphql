[back](README.md)

# Schema types

Learn more about the different types of the GraphQL schema language:
* [Scalar types](https://graphql.github.io/learn/schema/#scalar-types) (`Int`, `Float`, `String`, `Boolean` and `ID`)
* [Object types](https://graphql.github.io/learn/schema/#object-types-and-fields) and [interfaces](https://graphql.github.io/learn/schema/#interfaces)
* [Enumeration types](https://graphql.github.io/learn/schema/#enumeration-types)
* [Lists and Non-Null](https://graphql.github.io/learn/schema/#lists-and-non-null)
* [Union types](https://graphql.github.io/learn/schema/#union-types)

## Exercise: Object type

* Add an object type with fields of various types to your schema.
* Create a resolver function for it that returns a dummy object.
* Then [query the object](https://graphql.github.io/learn/queries/#fields) with (some) fields.

The response should contain a single object with the desired fields.

## Exercise: List type

* Define a list type of the previously defined object in your schema.
* Adjust the resolver function to return a list of dummy objects.
* Then query the list (apart from the adjusted list name, the query should look like before).

The response should contain an array of objects.
