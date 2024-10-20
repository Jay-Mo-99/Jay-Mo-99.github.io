---
title: "⚡ Generate Parentheses"
layout: single
date: 2024-10-12
categories: ⚡LeetCode
tags: 
  - Backtracking
  - Dynamic Programming
  - String
excerpt: "Solutions for the 'Generate Parentheses' problem using JavaScript."
author_profile: true
read_time: true
share: true
related: true
toc: true
---

# #22. Generate Parentheses

- **Difficulty**: Medium
- **Number**: 2  
- **Optimization**: Yes
- **Review**: October 20, 2024  
- **Select**: Backtracking, Dynamic Programming, String
- **Solve**: No

# My Solution: Wrong

```jsx

```

- Time:
- Spcae:
- Note:
    - Try to use a loop to create each symbol “(” and “)” and store the symbol to stack objects.
    
    → This approach takes a lot of steps to create all combinations, so we need to use a ***recursion function(Call the function by itself)***
    

# Best Solution

1. Recursion Function 

```jsx
const generateParenthesis = (n) => {
  const res = [];

//Function for backtracking (Recursion Fuction)
  const backTracking = (openB, closeB, currentString) => {
    //If using all parentheses, push to the res stack. 
    if (currentString.length === 2 * n) {
      res.push(currentString);
      return;
    }
    //If the open bracket(l) is less than parameter(n)
    //Add the open bracket to the string(s)
    if (openB < n){
	    backTracking(openB + 1, closeB, currentString + '(');
    }
    //If the close bracket(r) is less than the number of open bracket(l)
    //Add the close bracket to the string(s)  
    if (closeB < openB){ 
	    backTracking(openB, closeB + 1, currentString + ')')};
  };
//Call the initial back tracking 
//First calling of the recurision function 
  backTracking(0, 0, '');
  return res;
};
```

Step 1. 

- Call the brackTracking(0,0,””);

Step2 ~ Step 4

- openB is less than n
- Call the backTracking(1,0,”(”) ~ backTracking(3,0,”(((”)
