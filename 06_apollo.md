[back](README.md)

# Angular App with the Apollo Client

## Create client

In this step we are going to create a simple Angular application that uses the previously created GraphQL service via the [Apollo Client](https://www.apollographql.com/client). This GraphQL client implementation supports various [JavaScript frameworks](https://github.com/apollographql/apollo-client#learn-how-to-use-apollo-client-with-your-favorite-framework) and provides some additional features like caching.

First, scaffold an Angular project using the Angular CLI:

```
npx -p @angular/cli ng new hello-world
```

Then within the newly created directory, add the Apollo Client's Angular integration:
```
npx -p @angular/cli ng add apollo-angular
npm i typescript@'>=2.7.2 <2.10'
```

This uses Angular Schematics to do all the necessary configurations to your Angular project.


## Configure proxy & backend URL

Since your GraphQL service is running on a different port, we have to [proxy this route](https://github.com/angular/angular-cli/blob/master/docs/documentation/stories/proxy.md) to avoid CORS issues.

Add a `proxy.conf.json` file with the following contents to the project directory:

```
{
  "/graphql": {
    "target": "http://localhost:3000",
    "secure": false
  }
}
```

Add a `proxyConfig` setting to the `serve` target in the `angular.json` file of your project:
```
"serve": {
  "builder": "@angular-devkit/build-angular:dev-server",
  "options": {
    "browserTarget": "hello-world:build",
    "proxyConfig": "proxy.conf.json"
  },
  ...
}
```

Now you can adjust the `uri` variable in the `graphql.module.ts` file, and set it to `/graphql`, which will be proxied due to the setting above to your GraphQL service (on http://localhost:3000/graphql).

Finally start the development server:
```
npm start
```

When now opening the app in the browser you should see a test page: http://localhost:4200/

## Exercise: Query and render data

* Check out the example component in the [Queries](https://www.apollographql.com/docs/angular/basics/queries.html) section of the official Apollo Client documentation.
* Create an Angular component that requests data from your GraphQL service and renders it.

## Exercise: Use AsyncPipe

If no already done, try to rewrite your component to [use Angular's AsyncPipe](https://www.apollographql.com/docs/angular/basics/queries.html#select-pipe) to render the result from the GraphQL query.

## Exercise: Mutation

Add a form and [execute a mutation query](https://www.apollographql.com/docs/angular/basics/mutations.html) to write data from your Angular app.

## Exercise: Query service

Simplify your component by introducing a [query service](https://www.apollographql.com/docs/angular/basics/services.html#Query) to fetch the data.
