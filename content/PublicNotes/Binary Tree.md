---
title: Binary Tree
Date created: 2024-06-06 12:58
Aliases:
tags: 
  - Public
---

A Binary Tree is a [[Tree]] [[Data Structures|Data Structure]] with a set of specific rules that make them more useful.


## Binary Tree Rules

### What Makes it Binary
The term *Binary* in the name means composed of two things. That doesn't mean that the tree itself can only have two nodes, but that each parent node can only ever have two possible child nodes. In other words each root node points to two subtrees the *left subtree* and the *right subtree*, and because the binary tree is a recursive data structure the rule also applies to the subtrees.

## Binary Search Tree
A binary tree's nodes must be sorted in a specific way to be a binary *search* tree.
==Each node to the left of the root node must be smaller than the root node itself, while all the nodes to the right must be greater than the root node==
That rule is naturally also applied recursively to each of the subtrees, meaning the tree is always sorted in a specific way.

