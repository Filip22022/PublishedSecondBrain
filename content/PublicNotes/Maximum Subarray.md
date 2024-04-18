---
title: Maximum Subarray
tags: Public
Aliases:
Date created: 2024-02-18 10:23
---

# Maximum Subarray

## Description

### Question
Given an integer array `nums`, find the subarray with the largest sum, and return _its sum_.

If you have figured out the `O(n)` solution, try coding another solution using the **divide and conquer** approach, which is more subtle.
### Examples
**Example 1:**

**Input:** nums = [-2,1,-3,4,-1,2,1,-5,4]
**Output:** 6
**Explanation:** The subarray [4,-1,2,1] has the largest sum 6.

**Example 2:**

**Input:** nums = [1]
**Output:** 1
**Explanation:** The subarray [1] has the largest sum 1.

**Example 3:**

**Input:** nums = [5,4,-1,7,8]
**Output:** 23
**Explanation:** The subarray [5,4,-1,7,8] has the largest sum 23.

## Clarification
paraphrase: the task is finding the part of an integer array for which the sum is the largest.

## Solving

### Approach 1 - Brute Force
Looping through everything - awful

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int len = nums.length;
        int biggestSum = Integer.MIN_VALUE;
        int currentSum = 0;

        for (int i = 0; i<len; i++) {
            for (int j=i; j<len; j++) {
                currentSum = 0;
                for (int k=i; k<=j; k++) {
                    currentSum += nums[k];
                    if (currentSum > biggestSum) {
                        biggestSum = currentSum;
                    }   
                }
            }
        }
        return biggestSum;
    }
}
```

### Approach 2 - Iterate saving Biggest
Assuming on all negative numbers I should return the negative number closest to zero
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int biggestSum = nums[0];
        int currentSum = 0;

        for (int i: nums) {
            currentSum += i;
            if (currentSum > biggestSum) {
                biggestSum = currentSum;
            } 
            if (currentSum < 0) {
                currentSum = 0;
            }
        }
        return biggestSum;
    }
}
```