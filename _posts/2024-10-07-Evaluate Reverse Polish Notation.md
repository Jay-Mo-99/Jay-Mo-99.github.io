---
title: "⚡Evaluate Reverse Polish Notation"
layout: single
date: 2024-10-09
categories: ⚡LeetCode
tags: 
  - Array
  - Math
  - JavaScript
excerpt: "Solutions for the 'Evaluate Reverse Polish Notation' problem using JavaScript and stacks."
author_profile: true
read_time: true
share: true
related: true
toc: true
---
# #20. Valid Parentheses

- **Difficulty**: Medium  
- **Number**: 1  
- **Optimization**: Yes  
- **Review**: October 9, 2024  
- **Select**: Array, Math, Stack  
- **Solve**: Yes  

# #150. Evaluate Reverse Polish Notation

# My Answer

```cpp
/**
 * @param {string[]} tokens
 * @return {number}
 */
var evalRPN = function(tokens) {
    const nStack = [];//Assign the Stack for number
        let answer =0; //Variable for store the answer of calculation
    //If the element of the tokens are operator, push the oStack, if not push the nStack
    for(e of tokens){
        let top = 0;
        let preTop = 0;
        if(e === "+"){
            top = nStack.pop();
            preTop = nStack.pop();
            answer = parseInt(preTop) + parseInt(top);
            nStack.push(answer);

        }else if(e === "-"){
            top = nStack.pop();
            preTop = nStack.pop();
            answer = preTop - top;
            nStack.push(answer);

        }else if(e === "*"){
            top = nStack.pop();
            preTop = nStack.pop();
            answer = preTop * top;
            nStack.push(answer);

        }else if(e === "/"){
            top = nStack.pop();
            preTop = nStack.pop();
            answer = Math.trunc(preTop/top);
            nStack.push(answer);

        }else{
            nStack.push(e) 
        }

    }
    return parseInt(nStack[nStack.length-1]);

};
```

- Time: O(n): It depends of the number of tokens’ elements(n)
- Space: O(n): The nStack’s capacity depends on the number of the elements in token
- Note
    - The “+” operator also can be used for string connection.
    - In JavaScript, Confirm the type(number of strings) of the values when using the“+” operator.
    - The other operators (”-”,”*”,”/”) change the value to the number automatically.

# Reflection

- [x]  Exploring various solutions and clearly communicating them
- [x]  Stating the runtime and space complexity (the pros and cons) of each solution)
- [ ]  Translating ideas into code
- [ ]  Debugging your code

# Best Answer

## 1. Using Stack Array

```jsx
function evalRPN(tokens) {
  let stack = []; //Assign the array for stack
  //Assign the object which has key and the value is the function for each operator
  let ops = {
    '+': (a, b) => a + b,
    '-': (a, b) => a - b,
    '*': (a, b) => a * b,
    //If the a/b >0, Round Down. If not, Round up 
    '/': (a, b) => a / b >= 0 ? Math.floor(a / b) : Math.ceil(a / b),
  };
  for (let t of tokens) {
  //If ops object contains the t, that is true 
    if (ops[t]) {
      let top = stack.pop();//Top element is deleted and store the value to top
      let second = stack.pop();//Top element is deleted and store the value to second
      stack.push(ops[t](second, top));
    } else {
    //If ops object didn't contain the t, that is the number. 
    //Turn the value of t to Number 
      stack.push(Number(t));
    }
  }
  return stack.pop();
};

```

- Time: O(n). It depends on the number of elements in the tokens
- Space: O(n). The stack array capacity depends on the number of elements in tokens.

## 2. Instead of function, bitwise operation

```jsx
const evalRPN = function ( tokens ) {
  const stack = [];
  
  //Approach each element of tokens object
  tokens.forEach(( token ) => {
	  //If the token is in the regular expression, 
	  //Create the [y,x] object that contains the value of top and second value of stack
    if ( /^[+\-*/]$/.test( token ) ) {
      const [y, x] = [stack.pop(), stack.pop()];
      //Push the value of evaulate function
      stack.push( evaluate( x, y, token ) );
    } else {
      stack.push( +token );  // Number(token) //unary plus operator
    }
  });
 
  // The last evaluated expression is the answer
  return stack.pop();
};

const evaluate = ( x, y, op ) => {
  switch ( op ) {
    case '+': return x + y;
    case '-': return x - y;
    case '*': return x * y;
    case '/': return x / y | 0;  //bitwise operator, Math.trunc()
  }
};
```

- Time: O(n). It depends on the number of elements in the tokens
- Space: O(n). The stack array capacity depends on the number of elements in tokens.

# Note

- Optimize the algorithm to minimize dependence on n. → Aim to reduce the dependence on n
- Try to minimize the use of extra variables or arrays
- If performance is a priority over readability
    - Use `“x/y|0”` instead of `Math.trunc()` → More Faster
    - Use `+”string”` instead of `Number(string)`
