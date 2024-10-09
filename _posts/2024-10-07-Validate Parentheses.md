---
title: "⚡Valid Parentheses"
layout: single
date: 2024-10-07
categories: LeetCode
tags: 
  - Stack
  - String
  - JavaScript
excerpt: "Solutions for the 'Valid Parentheses' problem using JavaScript and stacks."
author_profile: true
read_time: true
share: true
related: true
toc: true
---
# #20. Valid Parentheses

- **Difficulty**: Easy  
- **Number**: 1  
- **Optimization**: No  
- **Review**: October 7, 2024  
- **Select**: Stack, String  
- **Solve**: No  

# Validate Parentheses

**Easy**

# My Answer: *Wrong*

```jsx
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    //Create the stack from the s
    const stack =[];
    const array =s.split("");//Create the ascending sorted array from s 
    if(array.length===0){
        return false;
    }
    
    for(let i =0;i<array.length ;i++){
        
        if(array[i]==="(" || array[i]==="{" || array[i]==="[" ){
            stack.push(array[i]);//If I encounter a open bracket, push the stack
        }else{
            ////When you encounter a closing bracket, check if the top of the stack was the opening for it.
            if(array[i]===")" && array[i-1]==="("){
                stack.push(array[i]);
            }else if(array[i]==="}" && array[i-1]==="{"){
                 stack.push(array[i]);
            }else if(array[i]==="]" && array[i-1]==="["){
                 stack.push(array[i]);
            }else{
                return false;
            }
            //If yes, pop it from the stack. Otherwise, return false.
        }
    }
    console.log(stack);
    return true;

};
```

- Time:
- Space:
- Reason of wrong answer
    - Could not use the “pop” → The less understanding about stack.
    

# Reflection

- [ ]  Exploring various solutions and clearly communicating them
- [ ]  Stating the runtime and space complexity (the pros and cons) of each solution)
- [ ]  Translating ideas into code
- [ ]  Debugging your code

# Best Answer

## 1. HashMap and Stack

```jsx
var isValid = function(s) {
        const stack = [];
        const mapping = {
            ')': '(',
            '}': '{',
            ']': '['
        };

        for (const c of s) {
        //If the c is the open bracket, such as the value of the mapping, push to the stack
            if (Object.values(mapping).includes(c)) {
                stack.push(c);
                //If not, it is the close bracket.
            } else if (mapping.hasOwnProperty(c)) {
            //If the stack.lengt is empty, return false and
            // close bracket(c) is not matched with mapping's key, return ffalse
            //
                if (!stack.length || mapping[c] !== stack.pop()) {
                    return false;
                }
            }
        }
				//If the stack's element are poped successfully, return true
        return stack.length === 0;    
};
```

- Time: O(n)
    - The `for-of` loop iterates over each character `c` in the string `s`
    - Each `c` constant time opertion such as pop and push the stack are perfomed.
    - Thus overall time complexity is O(n), where n is length of the input string s
- Space: O(n)
    - The `stack` is depends on parameter string `s,` thus `O(n)`
    - The `mapping` object has a fixed size, unrelated to the input parameter, so it is $O(1)$
    - `Object.values(mapping)` retrieves the value of `mapping`, it always fixed and unrelated to the parameter, so $O(1)$
    - Therefore, the overall space complexity is O(n), where n is length of the input string s

## 2. Stack Only

```jsx
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    let stack = []; // create an empty stack to store opening brackets
    for (let c of s) { // loop through each character in the string
        if (c === '(' || c === '{' || c === '[') { // if the character is an opening bracket
            stack.push(c); // push it onto the stack
        } else { // if the character is a closing bracket
            if (!stack.length || // if the stack is empty or 
                (c === ')' && stack[stack.length - 1] !== '(') || // the closing bracket doesn't match the corresponding opening bracket at the top of the stack
                (c === '}' && stack[stack.length - 1] !== '{') ||
                (c === ']' && stack[stack.length - 1] !== '[')) {
                return false; // the string is not valid, so return false
            }
            stack.pop(); // otherwise, pop the opening bracket from the stack
        }
    }
    return !stack.length; // if the stack is empty, all opening brackets have been matched with their corresponding closing brackets,
                          // so the string is valid, otherwise, there are unmatched opening brackets, so return false
};
```

- Time: $O(n)$
    - The `for-of` loop iterates over each character `c` in the string `s`
    - Thus, if~else complexity logic is unrealated with time Big O
- Space: $O(n)$
    - If~else is not unrealated with space Big O.

# Note

- Please try to use key-value object freely
- Recycle the object and variable for the space capacity
