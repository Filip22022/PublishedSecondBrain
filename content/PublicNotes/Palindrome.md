---
title: Palindrome
Date created: 2024-02-19 19:51
Aliases:
tags: 
  - Public
---

Sequence of characters that reads the same forward as backwards

### Checking for Palindromes
- reversing the string and checking equality with original string
- Creating two pointers at the ends of the string, and moving them until they meet - the characters at pointers should be equal

If checking for a number of palindromes, it's usually checked with two pointers from the middle. There's need to consider two cases, including the middle character and excluding it, because the palindrome can have odd or even number of characters.