---
author: "Saad Aouad"
date: 2020-09-15
linktitle: Difference between var, let and const keywords
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: Difference between var, let and const keywords

weight: 10
---

ES6 introduced two new ways to create variables, `let` and `const`. But before we actually dive into the differences between `var`, `let` and `const`, there is a prerequisite you need to know first. It’s scope (specifically function scope).

#### Scope
Scope defines where variables and functions are accessible inside of your program. In JavaScript, there are two kinds of scope - **global scope**, and **function scope**. According to the official spec,

> “If the variable statement occurs inside a FunctionDeclaration, the variables are defined with function-local scope in that function.”.

That means If you create a variable with `var`, that variable is “scoped” to the function it was created in and is only accessible inside of that function or, any nested functions. 

```
function addSum(num) {
  var sum = 3;

  return sum = sum + num;
}

addSum(2);
console.log(sum); // ❌ Reference Error
```

As you can see we try to access a variable outside of `addSum()` function it was declared. Since `sum` is scoped to `addSum()` function it’s only accessible inside of this function itself or any nested function inside `addSum()`. e.g:


```
function addSum(num) {
  var sum = "3"; 

  function numberSum() {
    return  sum =  parseInt(sum) + num; // ✅
  }

  return numberSum();
}

addSum(2);
console.log(sum); // ❌ Reference Error
```

### var VS let

Now, let’s compare `var` and `let`. The main difference between `var` and `let` is that instead of being function scoped, what that means is that a variable created with the `let` keyword is available inside the “block” that it was created in as well as any nested block. When I say “block”, I mean anything surrounded by a curly brace `{}` like `if` statement or  `for` loop. 

Let’s look to `discountPrices()` function:

```
function discountPrices (prices, discount) {
  var discounted = []

  for (var i = 0; i < prices.length; i++) {
    var discountedPrice = prices[i] * (1 - discount)
    var finalPrice = Math.round(discountedPrice * 100) / 100
    discounted.push(finalPrice)
  }

  console.log(i) // 3
  console.log(discountedPrice) // 150
  console.log(finalPrice) // 150
  return discounted
}
``` 

Remember that we were able to log `i`, `discountedPrice` and `finalPrice` outside of the `for` loop since they were declared with `var` and `var` is function scoped. But now, what happens if we change those `var` declarations to use `let` and try to run it?

```
function discountPrices (prices, discount) {
  let discounted = []

  for (let i = 0; i < prices.length; i++) {
    let discountedPrice = prices[i] * (1 - discount)
    let finalPrice = Math.round(discountedPrice * 100) / 100
    discounted.push(finalPrice)
  }

  console.log(i)
  console.log(discountedPrice)
  console.log(finalPrice)
  return discounted
}

discountPrices([100, 200, 300], .5) // ❌ ReferenceError: i is not defined
```

We get `ReferenceError: i is not defined`. What this tells us is that variables declared with let are block scoped, not function scoped. So trying to access i (or discountedPrice or
finalPrice) outside of the “block” they were declared in is going to give us a reference error as we just barely saw.

```
var VS let

var: function scoped

let: block scoped
```

The next difference has to do with Hoisting. When you try to access a variable using `var` keyword you will get `undefined`:

```
function discountPrices (prices, discount) {
  console.log(discounted) // undefined
  var discounted = []
…
```

And when you try to access a variable using `let` keyword, you’ll get a `ReferenceError`:

```
function discountPrices (prices, discount) {
  console.log(discounted) // ❌ ReferenceError
  let discounted = []
…
```

```
var VS let

var:
  function scoped
  undefined when accessing a variable before it's declared

let:
  block scoped
  ReferenceError when accessing a variable before it's declared
```

### let VS const

Now that you understand the difference between `var` and `let`, `const` is almost exactly the same as `let`. However, the only difference is that once you’ve assigned a value to a variable using `const`, you can’t reassign it to a new value. Example:

```
let name = 'Saad'
const currentPosition = 'Front-End Engineer'

name = 'Saad Aouad' // ✅
currentPosition = 'Software Engineer' // ❌ TypeError: Assignment to constant variable.
```

```
var VS let VS const

var:
  function scoped
  undefined when accessing a variable before it's declared

let:
  block scoped
  ReferenceError when accessing a variable before it's declared

const:
  block scoped
  ReferenceError when accessing a variable before it's declared
  can't be reassigned
```

***Ref*** <a href="https://ui.dev/var-let-const/" target="_blank" rel="noopener noreferrer">ui.dev/var-let-const/</a>
