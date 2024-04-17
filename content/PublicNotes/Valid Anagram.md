---
title: Valid Anagram
Tags: Public
Aliases:
Date created: 2024-02-19 19:52
---

# Valid Anagram

## Description
### Question

Given two strings `s` and `t`, return `true` _if_ `t` _is an anagram of_ `s`_, and_ `false` _otherwise_.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

### Examples
**Example 1:**

**Input:** s = "anagram", t = "nagaram"
**Output:** true

**Example 2:**

**Input:** s = "rat", t = "car"
**Output:** false



## Clarification
paraphrase: Check if string t consists of exactly the same set of letters as string s

- Are letters uppercase and lowercase
- do I count whitespaces

## Solving

### Thoughts
- As per [[Anagram]] there are three main ways to check anagrams
- Different from [[Ransom Note (coding question)]] all characters from original string have to be used

### Approach 1 - counting in HashMap

```
class Solution {
    public boolean isAnagram(String s, String t) {
        HashMap<Character, Integer> letters = new HashMap<Character, Integer>();

        for (char c: s.toCharArray()) {
            Integer count = letters.get(c);
            if (count == null) {
                letters.put(c,1);
            } else {
                letters.put(c, count+1);
            }
        }

        for (char c: t.toCharArray()) {
            Integer count = letters.get(c);
            if (count == null || count == 0) {
                return false;
            } else if (count == 1) {
                letters.remove(c);
            } else {
                letters.put(c, count-1); 
            }
        }
        
        if (letters.isEmpty()) {
            return true;
        } else {
            return false;
        }
    }
}
```

Time Complexity: O(n)
Space Complexity: O(1)

A relatively slower solution, but with good O complexity

### Approach 2 - sort and compare

```
class Solution {
    public boolean isAnagram(String s, String t) {
        char[] t1 = t.toCharArray();
        char[] s1 = s.toCharArray();

        Arrays.sort(s1);
        Arrays.sort(t1);

        String s2 = new String(s1);
        String t2 = new String(t1);

        return s2.equals(t2);
    }
}
```

Time Complexity: O(n (log n))
Space Complexity: O(n)

Faster in given testcases, but with more complexity

### Approach 3 - counting in integers

```
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;

        int[] map = new int[26];
        for (char ch : s.toCharArray()) {
            map[ch - 'a']++;
        }

        for (char ch : t.toCharArray()) {
            if (map[ch - 'a'] > 0) {
                map[ch - 'a']--;
            } else return false;
        }
        return true;
    }
}
```

Time Complexity: O(n)
Space Complexity: O(1)

An optimized approach, using integers instead of chars and an simplified array instead of map by converting the characters to their position in the alphabet.
Limits the number of loops by using the conclusion, that for strings of the same length, either all characters will be used or some of them will not be in original string.