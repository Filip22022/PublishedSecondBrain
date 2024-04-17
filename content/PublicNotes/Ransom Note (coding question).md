---
title: Ransom Note
Tags: Public
Aliases:
Date created: 2024-02-18 11:44
---

## Description
### Question
Given two strings `ransomNote` and `magazine`, return `true` _if_ `ransomNote` _can be constructed by using the letters from_ `magazine` _and_ `false` _otherwise_.

Each letter in `magazine` can only be used once in `ransomNote`.

### Examples
**Example 1:**

**Input:** ransomNote = "a", magazine = "b"
**Output:** false

**Example 2:**

**Input:** ransomNote = "aa", magazine = "ab"
**Output:** false

**Example 3:**

**Input:** ransomNote = "aa", magazine = "aab"
**Output:** true

## Clarification
paraphrase: Determine if string ransomNote can be created using characters from Magazine, using each only once

- Are letters uppercase and lowercase

## Solving

### Approach 1 - Checking All Letters
with optimization beats 50%

Time Complexity: O(nk)
Space Complexity: O(1)

```
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        int start = 'a';
        int end = 'z';
        int countNote = 0;
        int countMagazine = 0;
        for (int i = start; i <= end; i++) {
            for (char c: ransomNote.toCharArray()) {
                int code = c;
                if (code == i) {
                    countNote += 1;
                }
            }
            if (countNote == 0) {
                continue;
            }

            for (char c: magazine.toCharArray()) {
                int code = c;
                if (code == i) {
                    countMagazine += 1;
                }
                if (countMagazine >= countNote) {
                    break;
                }
            }
            if (countNote > countMagazine) {
                return false;
            }
            countNote = 0;
            countMagazine = 0;
        }
        return true;
    }
}
```

### Approach 2 - Hash Map Letters
Runs in similar time on leetcode question but has less time complexity


Time Complexity: O(n)
Space Complexity: O(k)


```
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        HashMap<Character, Integer> letters = new HashMap<Character, Integer>();

        for (char c: magazine.toCharArray()) {
            Integer value = letters.get(c);
            if (value == null) {
                letters.put(c, 1);
            } else {
                letters.put(c, value+1);
            }
        }

        for (char c: ransomNote.toCharArray()) {
            Integer available = letters.get(c);
            if (available == null || available == 0) {
                return false;
            }
             
            letters.put(c, available-1);
        }

        return true;
    }
}
```