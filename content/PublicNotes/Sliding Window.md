---
title: Sliding Window
tags: Public
Aliases:
Date created: 2024-02-12 21:34
---

Sliding window is a technique used to reduce the time complexity of algorithms by eliminating the need to repeatedly loop through a structure.

## Static Sliding Window
The static sliding window algorithm uses a window of fixed size that moves through the structure.

### Algorithm
1. Determine window size
2. Initialization and initial calculations
3. Repeat
	1. Slide the window
	2. Update state, evaluate window
4. Return result

### Complexity
Time complexity is usually linear or close to linear - O(n)
Space complexity is O(1) because the amount of things stored in memory is constant, regardless of input size.

### Example
finding the maximum subarray sum

	public static int maxSubarraySum(int[] numbers, int subLength)
	int maxSum = Interger.MIN_VALUE;
	int windowSum = 0;
	
	// initial window calculation
	for (int i = 0; i<k ; i++) {
		windowSum += numbers[i]
	}
	
	//sliding and evaluation
	for (int i = subLength; i < numbers.length; i++) {
		windowSum += numbers[i] - numbers[i-k]
		maxSum = Math.max(maxSum, windowSum)
	}
	
	return maxSum

## Dynamic Sliding Window
In this version of the Sliding Window Algorithm, the window is determined by start and end pointers, and the size of the window is changing according to the needs

### Algorithm
1. Initialization
2. Move the end of the window, making it bigger 
	1. Evaluate window
	2. if appropriate move the start of the window, making it smaller

## Useful in
- [[Longest Substring Without Repeating Characters]]
- [[Minimum Size Subarray Sum]]
- [[Minimum Window Substring]]