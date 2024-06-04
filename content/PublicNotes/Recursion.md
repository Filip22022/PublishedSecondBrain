---
title: Recursion
Date created: 2024-05-28 18:35
Aliases:
tags: 
  - Public
---

Recursion is a method of solving computational problems by dividing the original problem and computing the results of the subproblems first. It's used in many algorithms like [[Binary Search]], [[Merge Sort]], [[Tree Traversal]] and more.

Recursive functions consist of two parts: 
1. Base cases defining when the recursion stops
2. Breaking down the problem into parts and recursive invocation of itself


> [!NOTE] Example
> A well known example of recursion is the Fibonacci sequence:
> 	- base cases: fib(0) = 0, fib(1) = 1
> 	- recurrence relation: fib(i) = fib(i-1)+fib(i-2)
> 	
> in code representation:
> ```python
> def fib(n):  
>	if n <= 1:  
>		return n  
>	return fib(n - 1) + fib(n - 2)
>```


## Notes
- Recursion uses a stack
	- Pay attention to not cause stack overflow
	- Will never be O(1) space unless the used language has tail-call optimisation

## Techniques

### Memoization
If computing the result for already computed previous results, storing those results in memory greatly improves the efficiency of recursion and reduces the time complexity

## Corner Cases
- n=1
- n=0