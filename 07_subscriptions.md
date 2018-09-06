[back](README.md)

# Subscriptions

GraphQL supports realtime updating of data, known as _subscriptions_. Changes will be propagated using a _PubSub_ mechanism over WebSockets. Both the GraphQL server and client have to support this feature. The Apollo Client has built-in support (check out the [Subscriptions](https://www.apollographql.com/docs/angular/features/subscriptions.html) chapter of the Apollo Client documentation).

It is possible to extend your Express-based service to support subscriptions. Read the [Apollo Subscriptions documentation](https://www.apollographql.com/docs/graphql-subscriptions/) that contain instructions on how to achieve this.

Another approach would be to use a more powerful implementation like the Apollo Server, that supports GraphQL subscriptions without additional configuration. For more details check out the [Subscriptions](https://www.apollographql.com/docs/apollo-server/features/subscriptions.html) chapter of the Apollo Server documentation.

## Exercise

* Try to setup a server supporting subscriptions.
* Extend your schema with a `Subscription` type.
* Use the subscription feature of the Apollo Client in your Angular application to render data and automatically re-render it when it changes.
