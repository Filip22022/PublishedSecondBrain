---
title: Anagram
Date created: 2024-02-19 19:51
Aliases:
tags: 
  - Public
---
A word or phrase created with the same set of letters as the original word/phrase by rearranging.

### Checking for Anagrams
- Sorting both strings and checking if the result strings are identical
	- Time: O(n.log(n))
	- Space: O(log(n))
- Mapping each character to a prime number and multiplying mapped numbers. anagrams should have the same multiple.
	- Time: O(n)
	- Space: O(1)
- Counting the frequency of characters in string using a HashMap
	- Time: O(n)
	- Space: O(1)