---
title: Queue
Date created: 2024-06-04 09:40
Aliases:
tags: 
  - Public
---

Queue is an abstract data type following the First In First Out behaviour, where all element additions happen at the end (enqueue operation) and all element removals happen at the front of the queue (dequeue operation). It's a linear data structure and can be implemented using an [[Array]] or a [[Linked List]] 

## Time Complexity
|Operation|Big-O|
|---|---|
|Enqueue/Offer|O(1)|
|Dequeue/Poll|O(1)|
|Front|O(1)|
|Back|O(1)|
|isEmpty|O(1)|
## Common Problems

### Using Arrays
In languages without built-in queue structure (JS, python), you can arrays or lists, but such implementation will have O(n) operations because of needing to shift an array.

### Corner Cases
- empty queue
- one item
- two items