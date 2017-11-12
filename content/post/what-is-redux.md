<!-----
author: "Saad Aouad"
date: 2017-11-05
linktitle: What is Redux
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: What is Redux
description: Redux is a JavaScript library that aims to simplify how we manage stateful data.
weight: 10
---


[Redux](https://github.com/reactjs/redux/) is a JavaScript library that aims to simplify how we manage stateful data. Redux keeps all the data in a single JS object called `store`. A single function, the `reducer`, is responsible for making modifications to the `store`. We trigger the reducer by `dispatching` an `action` - a JS object that describes how our data should change. The `reducer` function receives the `action` as an argument and makes changes accordingly. Other parts of the code (usually React Components) can subscribe to data in the `store`. When data changes, Redux notifies subscribers of the change.
-->