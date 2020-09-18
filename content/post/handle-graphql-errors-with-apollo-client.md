---
author: "Saad Aouad"
date: 2019-08-04
linktitle: Handle GraphQL errors with Apollo Client
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: Handle GraphQL errors with Apollo Client

weight: 10
---

In any application it's important to handle and inspect erros since this helps a lot to debug and check what happened exactly in your application. Today we will see how to handle GraphQL errors with Apollo Client.

When using Apollo Link, the ability to handle network errors is way more powerful. The best way to do this is to use the `apollo-link-error` to catch and handle server, network and GraphQL errors. Here is a custom logic to do in your Apollo Provider file when a GraphQL or network error happens:

```
// ApolloProvider.js
import {ApolloLink} from 'apollo-link';
import { onError } from "apollo-link-error";
import {createHttpLink} from 'apollo-link-http';
import {InMemoryCache} from 'apollo-cache-inmemory';

// networkError: This refer any error during the link execution or server response
// graphQLErrors: Is an array of errors from the GraphQL endpoint
const errorLink = onError(({networkError, graphQLErrors}) => {
    if (graphQLErrors) {
        graphQLErrors.map(({message, locations, path}) =>
            console.log(`[GraphQL error]: Message: ${message}, Location: ${locations}, Path: ${path}`);
        );
    }

    if (networkError)
        console.log(`[Network error]: ${networkError}`);
    });

    const httpLink = createHttpLink({
        uri: YOUR_GRAPHQL_ENDPOINT,
    });

    const link = ApolloLink.from([errorLink, httpLink]);

    client = new ApolloClient({
        cache: new InMemoryCache(),
        link,
    })
});
```

By the way if you are enthusiastic to know how you can handle GraphQL errors from server side as well, here is a good reference for it https://blog.apollographql.com/full-stack-error-handling-with-graphql-apollo-5c12da407210