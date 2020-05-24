---
author: "Saad Aouad"
date: 2017-11-18
linktitle: Comparison with the equality (==) and strict equality (===) operator in Javascript
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: Comparison with the equality (==) and strict equality (===) operator in Javascript

weight: 10
---

If the values being compared are not of the same type, the equality operator will perform a type conversion, and then evaluate the values. however, the strict equality operator will compare both the data type and values as-is, without converting one type to the other. Example: 

```
1 == "1" // returns true, because Javascript performs type conversion from string to number.
1 === "1" // returns false, because the types are different and type conversion is not performed.
```
