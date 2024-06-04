---
title: Binary Search
Date created: 2024-05-29 16:18
Aliases:
tags: 
  - Public
---

Binary search is an [[Algorithms|algorithm]] for finding an item in a *sorted* list. 

## Complexity
Time complexity of Binary Search is O(log(n))

## Mechanism
Binary search divides the list in two and checks to which half does the searched item belong by comparing it with the divider, and repeats the process until it finds the searched item.

```
Set Left=0 and Right=n-1
While Left!=Right
	Set middle = ceiling of (Left+Right)/2
	if Array[middle] > Target:
		Set Right = m-1
	else Array[middle] <= Target:
		set Left = m
L==R -> Array[Left] == Target
```