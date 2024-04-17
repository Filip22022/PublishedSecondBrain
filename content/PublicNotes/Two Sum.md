---
title: Two Sum
Tags: Public
Aliases:
Date created: 2024-02-14 18:18
---

# Two Sum
Coding Interview Question

## Description

### Question
Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

**Follow-up:** Can you come up with an algorithm that is less than `O(n^2)` time complexity?

### Examples
1. **Input:** nums = [2,7,11,15], target = 9
	**Output:** [0,1]
	**Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].

2. 
	**Input:** nums = [3,2,4], target = 6
	**Output:** [1,2]

3. 
	**Input:** nums = [3,3], target = 6
	**Output:** [0,1]

## Clarification

- Is the input array sorted (examples suggest it isn't)
- Duplicate values in input array are allowed (also from examples)

## Solving

### Approach 1 - Brute Force
Nested loop through the array checking for the target sum, excluding situation of accessing the same position.

Complexity: O(n^2)

#### Code
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int n = nums.length;
        
        for (int i = 0; i < n - 1; i++) {
            for (int j = i + 1; j < n; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[]{i, j};
                }
            }
        }
        return new int[]{}; // No solution found
    }
}
```

### Approach 2


Sorting the array with quicksort (java .sort), then using the [[Two pointers]] technique to check for the sum
If can't overwrite input array, requires allocation of a new array

Complexity O(n * log(n)) - O(n^2) quicksort complexity, finding the sum O(n) 

After finding the correct indices in the sorted array, looping over the original array to restore the indices, maybe would be faster to create a hash map first anyway

#### Code
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] sortedNums = Arrays.copyOf(nums, nums.length);
        Arrays.sort(sortedNums);
        int start = 0;
        int end = sortedNums.length - 1;
        int[] result = new int[2];
        int len = nums.length;


        while (start < end) {

            int sum = sortedNums[start] + sortedNums[end];

            if ( sum < target ) {
                start++;
            } else if (sum > target) {
                end--;
            } else {
                break;
            } 
        }

        for (int i=0; i<len; i++) {
            if (nums[i] == sortedNums[start]) {
                result[0] = i;
                break;
            }
        }
        for (int i = len-1; i >= 0; i--) {
            if (nums[i] == sortedNums[end]) {
                result[1] = i;
                break;
            }
        }
        return result;
    }
}
```

### Approach 3 - Best
Using [[Hash Table]] 

#### Two Pass Hash Table

1. Creating the hash table containing the indices of original array as values and the original values as keys for lookup
2. For each number in the array check if it's complement exists as a key in hash map, and return its index (map value)
3. Remember to check if they have the same index

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> numMap = new HashMap<>();
        int n = nums.length;

        // Build the hash table
        for (int i = 0; i < n; i++) {
            numMap.put(nums[i], i);
        }

        // Find the complement
        for (int i = 0; i < n; i++) {
            int complement = target - nums[i];
            if (numMap.containsKey(complement) && numMap.get(complement) != i) {
                return new int[]{i, numMap.get(complement)};
            }
        }

        return new int[]{}; // No solution found
    }
}
```

#### One Pass Hash Table
Optimization of the hash table approach

- Instead of initializing the whole hash table, initialize the elements as you iterate through original array
- the first of the solution pair will be initialized into hash table, and the second will find it as it's complement
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> numMap = new HashMap<>();
        int n = nums.length;

        for (int i = 0; i < n; i++) {
            int complement = target - nums[i];
            if (numMap.containsKey(complement)) {
                return new int[]{numMap.get(complement), i};
            }
            numMap.put(nums[i], i);
        }

        return new int[]{}; // No solution found
    }
}
```


### Trade-off
The second method is faster, but requires more space due to the allocation of a sorted array
