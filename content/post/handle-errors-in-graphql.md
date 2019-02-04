---
author: "Saad Aouad"
date: 2019-02-04
linktitle: Handle and inspect errors in GraphQL network stack
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: Handle and inspect errors in GraphQL network stack

weight: 10
---

In any application it's important to handle and inspect erros from server and client sides, since this can help a lot to debug and check what happened exactly on your app. Today we will see how we can handle errors in GraphQL especially from client side using <a href="https://www.apollographql.com/docs/react/" target="_blank">react apollo</a>.

When using Apollo Link, the best way to handle errors is to use `apollo-link-error` to handle Graphql, network and server errors:

```
import {ApolloLink} from 'apollo-link';
import { onError } from "apollo-link-error";
import {createHttpLink} from 'apollo-link-http';
import {InMemoryCache} from 'apollo-cache-inmemory';

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
```

- `graphQLErrors`: Is an array of errors from the GraphQL endpoint
- `networkError`: This refer any error during the link execution or server response

And finally if you are enthusiastic to know how you can handle GraphQL errors from server side as well, here is a good reference https://blog.apollographql.com/full-stack-error-handling-with-graphql-apollo-5c12da407210