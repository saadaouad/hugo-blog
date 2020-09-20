---
author: "Saad Aouad"
date: 2017-12-05
linktitle: Return early pattern for functions
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: Return early pattern for functions

weight: 10
---

When a first return statement is reached, the execution of the current function stops and control returns to the calling location. Example:

```
function myFunc() {
    console.log("Salam alaykum");
    return "Wa alaykum salam";
    console.log("Ciao");
}

myFunc();
```

The output "Salam alaykum" to the console, returns "Wa alaykum salam", but "Ciao" is never output, because the function exits at the first return statement.

***Ref*** <a href="https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/return-early-pattern-for-functions" target="_blank" rel="noopener noreferrer">freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/return-early-pattern-for-functions</a>
