---
title: Array
Tags: Public
Aliases:
Date created: 2024-02-11 15:20
---
## Description

Values of the same type at continuous memory location

In some languages (python) it has dynamic size, in others (Java) it has fixed size

### Common terms
**subarray** - a continuous fragment of array
**subsequence** - sequence derived by deleting some elements without changing the order

### Time complexity
| Operation             | Big-O     | Note                                                                                                 |     |
| --------------------- | --------- | ---------------------------------------------------------------------------------------------------- | --- |
| Access                | O(1)      |                                                                                                      |     |
| Search                | O(n)      |                                                                                                      |     |
| Search (sorted array) | O(log(n)) |                                                                                                      |     |
| Insert                | O(n)      | Insertion would require shifting all the subsequent elements to the right by one and that takes O(n) |     |
| Insert (at the end)   | O(1)      | Special case of insertion where no other element needs to be shifted                                 |     |
| Remove                | O(n)      | Removal would require shifting all the subsequent elements to the left by one and that takes O(n)    |     |
| Remove (at the end)   | O(1)      | Special case of removal where no other element needs to be shifted                                   |     |
### Things to look out for
- index going out of bounds
- clarifying if there are duplicate values in array
- slicing and concatenating typically take O(n) time

### Corner cases
- Empty sequence
- Sequence with 1 or 2 elements
- Sequence with repeated elements
- Duplicated values in the sequence


>[!important] Strings are arrays of characters, so most of this applies to strings


## Array techniques
[[Sliding Window]]
[[Two pointers]]
[[Traversing from the Right]]
[[Sorting an Array]]
[[Precomputation]]
[[Index as hash key]]
## Array questions
[[Two Sum]]
[[Best Time to Buy and Sell Stock (coding question)]]
[[Product of Array Except Self]]
[[Maximum Subarray]]
[[Contains Duplicate]]
[[Maximum Product Subarray]]
[[Search in Rotated Sorted Array]]
[[3Sum]]
[[Container With Most Water]]
[[Sliding Window Maximum]]