---
title: Best Time to Buy and Sell Stock (coding question)
Tags: Public
Aliases:
Date created: 2024-02-15 20:30
---

## Description

### Question
You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.

You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

Return _the maximum profit you can achieve from this transaction_. If you cannot achieve any profit, return `0`.

### Examples
#### **Example 1:**

**Input:** prices = [7,1,5,3,6,4]
**Output:** 5
**Explanation:** Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.

#### **Example 2:**

**Input:** prices = [7,6,4,3,1]
**Output:** 0
**Explanation:** In this case, no transactions are done and the max profit = 0.

## Clarification
paraphrase: I'm given an array of stock prices on each day, and have to find the period over which I would get the biggest profit.

- Are the prices integers or float values?
- 

## Solving
### Thoughts
- it's possible to find the biggest number to the right of each entry, and then choose lowest
- iterate creating the array of lowest right first, and then checking the difference would be O(n) time and O(n) space complexity
- To return 0 if there's no profit, result variable should be updated it only if the result is positive

### Approach 1 - Brute Force
For each number, iterate through the rest of the array and save the values if the profit is greater than currentBest
time - O(n^2), space O(1)
```
class Solution {
    public int maxProfit(int[] prices) {
        int len = prices.length;
        int maxProfit = 0;

        for (int i=0; i<len; i++) {
            for (int j=i+1; j<len; j++) {
                int profit = prices[j] - prices[i];
                if (profit > maxProfit) {
                    maxProfit = profit;
                }
            }
        }
        return maxProfit;
    }
}
```

### Approach 2 - Precomputation
Create an array of biggest values to the right of current value, by iterating from the left and saving the biggest value - O(n)
Then check the difference at each point to the biggest to right value and save the best result

Time complexity: O(n)
Space complexity: O(n)
```
class Solution {
    public int maxProfit(int[] prices) {
        int len = prices.length;
        int maxProfit = 0;

        int[] biggestLater = new int[len];
        int highestPrice = -1;
        for (int i=len-1; i>=0; i--) {
            if (prices[i] > highestPrice) {
                highestPrice = prices[i];
            }
            biggestLater[i] = highestPrice;
        }

        for (int i=0; i<len; i++) {
            int profit = biggestLater[i] - prices[i];
            if (profit > maxProfit) {
                maxProfit = profit;
            }
        }
        return maxProfit;
    }
}
```


### Approach 3 - Copied
If we iterate from the left, and check for the lowest value and biggest profit simultaneously we can solve the problem in one loop. The important fact is that any higher price coming later will not give us a bigger profit, as we could use the earlier price

Time complexity: O(n) 
Space complexity: O(1)
```
class Solution {
    public int maxProfit(int[] prices) {
        int minValue = Integer.MAX_VALUE;
        int maxProfit = 0;
        int profitToday = 0;
        
        for(int i = 0; i < prices.length; i++){
            if(prices[i] < minValue){
                minValue = prices[i];
            }
            pist = prices[i] - lsf;
            if(maxProfit < profitToday){
                maxProfit = profitToday;
            }
        }
        return maxProfit;
    }
}
```

### Trade-off
The third approach is a logical optimization of the brute force approach, and as such is the best option.