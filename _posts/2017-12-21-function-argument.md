---
layout: post
title:  "Storing function arguments"
date:   2017-12-10T23:39:51
desc: "Sequence of function arguments stored in stack"
keywords: "Programming,blog,C/C++,Function,Arguments"
categories: [Programming]
tags: [Programming,blog,C/C++,Function]
icon: fa-programming
---

# How function arguments are stored in stack in C/C++ programming
Let's declare a function -  
```
// Function Definition
int function(int a, int b){
	// Do some stuff
	return 0;
}

//Function call
int main(){
	function(2, 4);
	return 0;
}
```
In the above code, when `main` function calls `function()`, the arguments are stored from last to first.  
Here in this case, `4` is stored in stack first, and then `2`.  
![Stack](https://raw.githubusercontent.com/ujjaldas1997/Data_images/master/blogs/stack.jpg)  
And when the execution transfer it's control to `function()`, the arguments are retrieved from stack from first to last order(and obviously).  
In the above case, at first `a` is assigned from `top` of the stack, then `top` element is poped and finally `b` is assigned.  

# Does this really work in the above described way?
Let's check with the following code  
```
1  #include<iostream>
2  using namespace std;
3  int fun1(){
4      cout << "Inside fun1\n";
5      return 0;
6  }
7  int fun2(){
8      cout << "Inside fun2\n";
9      return 1;
10 }
11 void fun(int n, int m){
12     return;
13 }
14 int main(){
15     fun(fun1(), fun2());		// Calling function
16     return 0;
17 }
```
In line no#15, `fun()` function is called inside `main()` function. From the above described way, `fun2()` will be executed first and `1` will be
pushed in the stack. Then finally `fun1()` will be executed and `2` will be stored in stack.  
Let's execute this code, and notice the behaviour.  
```
Inside fun2
Inside fun1
```

This proves that function arguments are stored in last to first order inside stack when called.

---
