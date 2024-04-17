---
title: Valid Palindrome
Tags: Public
Aliases:
Date created: 2024-02-22 10:35
---

# Valid Palindrome

## Description
### Question
A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string `s`, return `true` _if it is a **palindrome**, or_ `false` _otherwise_.

### Examples
**Example 1:**

**Input:** s = "A man, a plan, a canal: Panama"
**Output:** true
**Explanation:** "amanaplanacanalpanama" is a palindrome.

**Example 2:**

**Input:** s = "race a car"
**Output:** false
**Explanation:** "raceacar" is not a palindrome.

**Example 3:**

**Input:** s = " "
**Output:** true
**Explanation:** s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.
## Clarification
paraphrase: Determine if provided string is a palindrome, taking into account only alphanumeric characters

- can the string be empty (yes, per example )
- are there uppercase and lowercase letters, and should they be counted as one letter

## Solving

### Approach 1 - Remove Non-alphanumeric , Two Pointers
```java
class Solution {
    public boolean isPalindrome(String s) {
        char[] alphanumeric = s.toCharArray();
        int count = 0; 

        for (char c: alphanumeric) {
            if (Character.isAlphabetic(c) || Character.isDigit(c)) {
                alphanumeric[count] = Character.toLowerCase(c);
                count++;
            }
        }

        int left = 0;
        int right = count-1;

        while (left < right) {
            if (alphanumeric[left] != alphanumeric[right]) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
}
```

Time Complexity: O(n)
Space Complexity: O(n)

### Approach 2 - Skip Non Alphanumeric, Two Pointers

```java
class Solution {
    public boolean isPalindrome(String s) {
        char[] c = s.toCharArray();
        int left = 0;
        int right = s.length()-1;

        while (left < right) {
            char l = c[left];
            char r = c[right];
            if (!(Character.isAlphabetic(l) || Character.isDigit(l))) {
                left++;
                continue;
            }
            if (!(Character.isAlphabetic(r) || Character.isDigit(r))) {
                right--;
                continue;
            }
            if (Character.toLowerCase(l) != Character.toLowerCase(r)) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
}
```
Time Complexity: O(n)
Space Complexity: O(n)