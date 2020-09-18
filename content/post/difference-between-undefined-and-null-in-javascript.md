---
author: "Saad Aouad"
date: 2017-12-12
linktitle: Difference between undefined and null in Javascript
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: Difference between undefined and null in Javascript

weight: 10
---

- In Javascript `undefined` means a variable that has been declared but doesn't have a value assigned, example:

```
var myVar; // gives undefined
typeof myVar; // gives undefined
```

- `null` is a primitive assigned value. it can be null, empty or non-existent value, example:

```
var myVar = null; // gives null
typeof myVar; // gives object
```