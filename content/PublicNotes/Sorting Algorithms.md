---
title: Sorting Algorithms
Date created: 2024-05-29 16:17
Aliases:
tags: 
  - Public
---

Sorting algorithms are one of the most commonly used. It's unlikely you will need to implement any of them from scratch, but knowledge on how they work and how long they take can be useful.


### Space and Time Complexity

|Algorithm|Time|Space|
|---|---|---|
|Bubble sort|O(n2)|O(1)|
|Insertion sort|O(n2)|O(1)|
|Selection sort|O(n2)|O(1)|
|Quicksort|O(nlog(n))|O(log(n))|
|Mergesort|O(nlog(n))|O(n)|
|Heapsort|O(nlog(n))|O(1)|
|Counting sort|O(n + k)|O(k)|
|Radix sort|O(nk)|O(n + k)|

### Classification of Sorting Algorithms

Different kinds of sorting algorithms can be classified by few key factors

#### Space Complexity
When it comes to memory usage sorting algorithms can be *in-place*, meaning that they operate on the input data directly, or *out-of-place* which act on a copy of the data

#### Stability
A stable algorithm is one that preserves the relative order of equal elements, while an unstable one does not guarantee in what order equal elements will appear in the sorted set.

#### Internal vs. External
Internal sorting happens in the ram memory, when all the data can be kept there. External sorting on the other hand is when data is stored somewhere during the sorting.

It's important when sorting large datasets that wouldn't fit in the ram memory
#### Recursion
Recursive algorithm use a divide and conquer approach by calling the sort function on parts of themselves while non-recursive one work iteratively.

#### Comparison
Any algorithm that compares two items is a *comparison sort*, while ones that don't use any comparators (<,<=, etc.) are non-comparison sorts

