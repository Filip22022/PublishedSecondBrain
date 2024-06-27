---
title: Truthy and Falsy Values
Date created: 2024-06-13 14:46
Aliases: truthy, fasly
tags: 
  - Public
---

In JavaScript values can be grouped by what Boolean value they will be interpreted as into *truthy values* and *falsy values*

All values are truthy except `false`.`0`,`-0`,`0n`,`""`,`null`,`undefined`,`NaN`,`document.all`

All truthy values will be coerced to `true` when encountered in boolean context. They will execute if blocks and return true with logical operators.