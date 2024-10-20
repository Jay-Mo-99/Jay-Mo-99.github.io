---
title: "🧩 Recursive Call"
layout: single
date: 2024-10-20
categories: 🧩 Algorithm 
tags: 
  - Algorithm
excerpt: "Description about the 'Recursive Call'"
author_profile: true
read_time: true
share: true
related: true
toc: true
---

# Recursive Function

- A Recursive Function is a function that calls itself within the function

## Example

```c
void recursive (int n){
	if(n == 0){
		return; //Go back to the place which calls that function 
	}
	printf("Before r %d",n)//This is the print before calling the recursion function, So print "3,2,1"
	recursive(n-1);
	printf("%d", n);// Print statement after calling the recursion function, 
	//In the progress of Step 1,2,3, Function calls recursive(n-1) first, so we can't reach this statement.  
	//However, if recursive(n-1) returns the place called, we can reach the next statement.
	//This statement show us the step of the recursive function

}

int main(){
	recursive(3);
	return 0;
}
```

Step 1. 

- Call the recursive(3) function.
- The recursive(3) function push to the stack memory.
- But parameter 3 is not meet the if condition, so we go to the next statement that calls the recursive (n-1).

```c

void recursive(3){

	recusrsive(2);
}
```

Step 2.

- So we call recursive(2) function, and the recursive(int 2) function push to the stack memory.
- It’s a same way with step 1, so we call the recursive(n-1).

```c

void recursive(2){ 
	recusrsive(1);
}
```

Step 3.

- So we call recursive(1) function, and the recursive(int 1) function push to the stack memory.
- It’s the same way with step 2, so we call the recursive(n-1).

```c
void recursive(1){
	recusrsive(0);
}
```

Step 4 

- So we call recursive(0) function
- The parameter 0 meets the condition of the if statement,
- The if statement has a return, So the recursive(0) pops from the stack memory.
- It means the recursive(0) has disappeared, So we have to go back to the recursive(1) that place calls the recursive(0).

```c

void recursive(0){
	if(n == 0){
		return ;
	}
}
```

Step 5.

- We go back to the recursive(1) which calls the recursive(0)
- The next statement is the print function that shows the parameter n, the number 1.
- After the printf function, the recursive(1) pops from the stack memory.  the recursive(1) function is done.
- Go back to the recursive(2) that place calls the recursive(1)

```c
void recursive(1){
	~~recusrsive(0);//done~~
	printf("%d",n); //We are in the recursive(1) which calls the recursive(0), so the n is 1 
```

Step 6.

- We go back to the recursive(2) which calls the recursive(1)
- The next statement is the print function that shows the parameter n, the number 2.
- After the printf function, the recursive(2) pops from the stack memory.  the recursive(2) function is done.
- Go back to the recursive(3) that place calls the recursive(2)

```c
void recursive(2){
	~~recusrsive(1);//done~~
	printf("%d",n); //We are in the recursive(2) which calls the recursive(1), so the n is 2 

}
```

Step 7.

- We go back to the recursive(3) which calls the recursive(2)
- The next statement is the print function that shows the parameter n, the number 3.
- After the printf function, the recursive(3) pops from the stack memory.  the recursive(3) function is done.
- Go back to the main function that place calls the recursive(3)

```c
void recursive(2){
	~~recusrsive(3);//done~~
	printf("%d",n); //We are in the recursive(3) which calls the recursive(2), so the n is 3 

}

```

Step 8.

- We go back to the main function which calls the recursive(3)
- The next statement is the return
- After the return, the main function pops from the stack memory. The main function is done.

```c

int main(){
	~~recursive(3)~~;//done
	return 0;
}
```

# Base Case

- If there’s no base case in the recursive function, The recursive function will call itself infinitely, leading to a stack overflow.
- The base case is necessary when using the recursive function.

# Considerations

- If recursion can be replaced with a loop, it is often more memory-efficient to use the loop.
- However, recursion is used in problems such as mathematical computations, and structures like trees and graphs.
