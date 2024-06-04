---
title: Linked List
Date created: 2024-06-03 21:28
Aliases:
tags: 
  - Public
---

Linked Lists is a collection of elements, which are not stored in a sequential blocks of memory, instead having each element contain a pointer to the next one. It is linear in structure, meaning that any element only links to one next element and one previous element.

By using pointers in this way insertion and deletion operations on a linked list are O(1) time complexity by removing the need to rearrange whole memory blocks like arrays do.
On the other hand accessing a node needs to traverse the list from the start and is O(n)

## Types of Linked Lists
### Singly Linked
Each node pointing to the next one, while the last node points to `null`

### Doubly Linked List
Each node contains two pointers: one for the next node and one for the previous node.
Both the `previous` of the first node and the `next` of the last node point to `null` 

### Circular Linked List
A linked list where last node's `next` pointer points back to the first node.
In a doubly linked variant the `previous` pointer of the first node links to the last node

## Time Complexity
| Operation | Big-O |
| --------- | ----- |
| Access    | O(n)  |
| Search    | O(n)  |
| Insert    | O(1)* |
| Remove    | O(1)* |
\*Assumes you have traversed to the insertion position

## Common Problems

### Common Tasks on a Linked List
- Counting the number of nodes
- Reversing in-place
- Finding the middle node using fast/slow pointers
- Merging two linked lists
### Corner Cases
- Empty list - head being `null`
- single node
- two nodes
- cycles in the list (ask beforehand on an interview)

## Techniques

### Sentinel/dummy node
Adding empty nodes to the beginning and/or end of a linked list can simplify the steps needed for insertion and deletion by treating all real nodes as middle nodes, and eliminating the need for conditional checks for operating on first/last node 

### Two pointers
Various traversal problems can be solved using the a two pointer approach
- Getting the k-th from last node - two pointers where one is k nodes ahead. When the first one reaches the end the second points to k-th from last
- Detecting cycles - Two pointers where one is twice as fast as the other, if they meet that means a cycle
- Getting the middle node - Two pointers where one is twice as fast as the other, when the first one reaches the end the second one is at the middle

### Using space
Many linked list problems can be easily solved by creating a new linked list and adding nodes to the new list. It takes up extra space and can be disallowed during an interview, but it's still a valid strategy to mention
