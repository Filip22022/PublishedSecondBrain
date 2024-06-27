---
title: JS && Operator
Date created: 2024-06-13 14:51
Aliases:
tags: 
  - Public
---

In JavaScript the logical AND operator `&&` returns the second operand if the first operand is [[Truthy and Falsy Values|truthy]] 

```js
true && "dog"
// returns "dog"

[] && "dog"
// returns "dog"

```

If the first object is [[Truthy and Falsy Values|falsy]], it returns that object

```js
false && "dog");
// returns false

0 && "dog");
// returns 0

```