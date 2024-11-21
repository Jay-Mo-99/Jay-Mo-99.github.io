---
title: "⚡Lucky Numbers in a Matrix"
layout: single
date: 2024-11-20
categories: ⚡LeetCode
tags: 
  - Array
  - Matrix
  - JavaScript
excerpt: "Solutions for the 'Lucky Numbers in a Matrix' problem using JavaScript."
author_profile: true
read_time: true
share: true
related: true
toc: true
---

# #1380. Lucky Numbers in a Matrix

- **Difficulty**: Easy
- **Company**: Cisco
- **Optimization**: Yes
- **Review**: November 20, 2024
- **Select**: Array, Matrix
- **Solve**: No

# Understanding the Problem

- A **lucky number** is an element of the matrix such that it is the minimum element in its row and maximum in its column

```jsx
3,7,8
9,11,13
**15**,16,17 //Minimum of the row[15,16,17]
//Maximum of the column [3,9,15]

1,10,4,2
9,3,8,7
15,16,17,**12** //Minimum of the row[15,16,17,12]
//Maximum of the column [2,7,12]

3,6
7,1
5,2
**4**,8
```

- m == mat.length == the number of row
- n == mat[i].length == the number of column

# My Answer: Wrong

```jsx
let matrix = [[3,7,8],[9,11,13],[15,16,17]]
var luckyNumbers = function(matrix) {
    const minRow = [];
    //console.log(matrix.length) //행의 갯수
    for(let i =0;i<matrix.length;i++){
     minRow.push(Math.min(...matrix[i])) //행 내부에서 가장 작은 수 
     //console.log(matrix[i].length)//열의 갯수
    }
    const answer = Math.max(...minRow);
    return [answer];

};
```

- Time: O(n)
- Space: O(n)
- Reason of Wrong:
    - I have to follow a criteria about row and column at the same time
        - minRow stack can catch the min value of each row
        - However, max num of minRow stack not always the max number of each “Column”

# Reflection

- [x]  Exploring various solutions and clearly communicating them
- [ ]  Stating the runtime and space complexity (the pros and cons) of each solution)
- [ ]  Translating ideas into code
- [ ]  Debugging your code

# Best Answer

```jsx
/**
 * @param {number[][]} matrix
 * @return {number[]}
 */
var luckyNumbers = function(matrix) {
     // Loop through each row of the matrix
    for(let i =0;i<matrix.length;i++){
        let row = matrix[i]//Current row
        let minRow = Math.min(...row)// Find the minimum value in the current row
        let index = row.indexOf(minRow); //Get the column index of the minimum value
        //matrix every can chech the all element is accepted the all criteria
        //every can check all element is satisfied the all critera at the same time
        if(matrix.every(elem=> elem[index]<=minRow)){
        // Example: In [[3, 6], [7, 1], [5, 2], [4, 8]], "3" is minRow in row 0 (index 0),
        //In this case, every method check elem[0] <= 3,(3<=3,7<=3,5<=3,4<=3) → Condition fails
            return [minRow]
        } 
    }
    return [];

};
```

- Time: O(n)
- Space: O(n)

# Note

- Don’t create unnecessary object such as minStack.
- Try to utilize the Index and value when we approach that case  → Reduce the num of the variables
- Using the every method and some method whether to find the all elements are matched or unmatched the conditions
