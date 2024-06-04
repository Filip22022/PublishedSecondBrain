---
title: Stack
Date created: 2024-06-04 09:47
Aliases:
tags: 
  - Public
---

Stack is an abstract data structure similar to [[Queue]], but follows a Last In, First Out principle.
It's operations are inserting on top of the stack (**push**) and removing the most recently added element from the top of the stack (**pop**)
Stacks are important for supporting nested and recursive function calls and depth-first-search.

## Time Complexity
|Operation|Big-O|
|---|---|
|Top/Peek|O(1)|
|Push|O(1)|
|Pop|O(1)|
|isEmpty|O(1)|
|Search|O(n)|

## Corner Cases
- Empty stack
- Stack with one item
- Stack with two items