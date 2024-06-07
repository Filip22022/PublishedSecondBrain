---
title: Tree
Date created: 2024-06-05 09:39
Aliases:
tags: 
  - Public
---

A tree, in terms of [[Data Structures]], is a non-linear data structure consisting of nodes and links, where one node can be linked to many other nodes. 
A visual representation of a tree looks like an upside down tree.![[Tree 2024-06-06 11.10.45.excalidraw]]

## Structure
- Root - top node of a tree, which never has any links connecting **to** it
- Parent - any node that has a reference to another node
- Child - any node that is referenced by a parent node
- Link/Edge - reference that a parent node has to it's child node
- Sibling - a group of nodes that are children of the same node
- Internal node - any node that has a child node
- Leaf - a node that does not have a child

## Tree Facts
- If the three has *n* nodes -> it has *n-1* edges
- Trees are a *recursive* data structure - it's composed of *subtrees* (part's of the original tree that could be removed to form their own tree)

## Types of Trees
Two most important properties concerning the type of a tree are *depth* of a node and it's *height*

Depth is the number of links that it takes to reach that node from the root, or in other words a measure of how far is the node from the root

Height is the **maximum** number of edges from the node to it's leaves, or in other words the distance ot its furthest leaf

### Balance
A tree is considered *balanced* if any two sibling subtrees (subtrees where root nodes are siblings in the original tree) do not differ in height by more than one. If two sibling subtrees differ significantly in height, the tree is *unbalanced*

The balance is important when talking about tree operations and traversal.

