---
title: String
Tags: 
  - Public
Aliases:
Date created: 2024-02-19 18:38
---

## Description
A sequence of characters. Very similar to an [[Array]].

### Time Complexity
|Operation|Big-O|
|---|---|
|Access|O(1)|
|Search|O(n)|
|Insert|O(n)|
|Remove|O(n)|

|Operation|Big-O|Note|
|---|---|---|
|Find substring|O(n.m)|This is the most naive case. There are more efficient algorithms for string searching such as the [KMP algorithm](https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm)|
|Concatenating strings|O(n + m)||
|Slice|O(m)||
|Split (by token)|O(n + m)||
|Strip (remove leading and trailing whitespaces)|O(n)|

### Related Algorithms

- KMP (Knuth-Morris-Pratt) - efficient searching of substrings
- Rabin Kar - Searching of substrings with rolling hash

### Common Data Structures

[[Trie |Trie/Prefix Tree]]
[[Suffix Tree]]

### Things to Look out for
Input character set and case sensitivity. Usually lowercase Latin characters a-z

#### Corner Cases
- Empty string
- String with 1 or 2 characters
- repeated characters
- only distinct characters

## String Techniques

### Counting Characters

The most common way of counting characters in a string is using a hash table/map.
The space complexity is usually O(1) (26 for Latin characters)


### Anagram
[[Anagram]]

### Palindrome
[[Palindrome]]


## String Questions
- [[Valid Anagram]]
- [[Valid Palindrome]]
- [[Longest Substring Without Repeating Characters]]

- [[Longest Repeating Character Replacement]]
- [[Find All Anagrams in a String]]
- [[Minimum Window Substring]]
- [[Group Anagrams]]
- [[Longest Palindromic Substring]]