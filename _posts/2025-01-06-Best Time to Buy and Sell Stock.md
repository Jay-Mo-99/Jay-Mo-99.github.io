---
title: "⚡Best Time to Buy and Sell Stock"
layout: single
date: 2025-01-06
categories: ⚡LeetCode
tags: 
  - Array
  - Python
excerpt: "Solutions for the 'Best Time to Buy and Sell Stock' problem using Python and array."
author_profile: true
read_time: true
share: true
related: true
toc: true
---
# #121. Best Time to Buy and Sell Stock

- **Difficulty**: Easy
- **Company**: LeetCode75
- **Optimization**:  Yes
- **Review**: January 6, 2025
- **Select**: Array, Dynamic Programming
- **Solved**: Yes
- **Tried**:1

# My Answer

```python
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """

        min_val = prices[0]
        answer = 0

        for n in range(len(prices)):
            min_val= min(min_val,prices[n])
            answer = max(prices[n]-min_val,answer)

        return answer
```

- Description:
    - Using a loop to iterate through each element of the `prices` list.
    - Update `min_val` by comparing the current `prices[n]` and the existing `min_val`.
    - Update the `answer` by comparing the current profit( `prices[n]-min_val`) and each `answer`.
- Time: O(N)
    - for-loop: Depends on the length of the `prices` list, resulting in linear time complexity → O(n)
- Space: O(1)
    - `min_val,` `answer:` Variables occupy constant space because they do not grow with the input size. →O(1)
    - Constant space uses a fixed amount of memory regardless of the input size or any case.

# Reflection

- [x]  Exploring various solutions and clearly communicating them
- [x]  Stating the runtime and space complexity (the pros and cons) of each solution)
- [x]  Translating ideas into code
- [ ]  Debugging your code

# Best Answer

## 1. **Kadane's Algorithm**

```python
class Solution:
    def maxProfit(self, prices):

        buy = prices[0] #Initialize buy to prices[0]
        profit = 0      #Initialize profit 
        for i in range(1, len(prices)): #Loop from prices[1] to prices[len(prices)-1]
		        #If prices[i] is less than buy, Assign buy to prices[i]
            if prices[i] < buy:
                buy = prices[i]
            #If prices[i]-mim value(buy) is more than profit, Assign profit to that value
            elif prices[i] - buy > profit:
                profit = prices[i] - buy
        #Return the profit after loop 
        return profit
```

- Time: $O(n)$
- Space: $O(1)$
- Why is this solution faster than my solution?
    
    The difference lies in the use of `if-elif` conditions vs `min()` `max()` functions:
    
    - if-elif condition:
        - Only update the variables when the specific condition is true.
        - This avoids necessary operations in other cases.
    - min() max():
        - These functions are evaluated in all cases, regardless of whether the value needs to be updated.
        - This adds overhead due to the function calls and additional logic inside `min()` and `max()`.
