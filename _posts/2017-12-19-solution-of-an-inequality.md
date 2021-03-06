---
layout: post
title:  "Inequality"
date:   2017-12-19T23:39:51
desc: "Number of solutions of inequality given constraints"
keywords: "Combinatories,blog,Math,Inequality,Coding"
categories: [Math]
tags: [Combinatories,blog,Inequality,Programming]
icon: fa-math
---

# No of solutions of an inequality  

## Statement
Lets the inequality be $$x_1 + x_2 + \dots + x_k \le p$$ subjected to constraints $a_1 \le x_j \le a_2 \, for \, 1 \le j \le k$

# Pre-requisties
Total number of ways of distributing 'n' identical objects to 'p' persons such that each receives 0, 1 or more than 1 objects is $$\binom{n+p-1}{p-1}$$  
Proof:    
$$x_1 + x_2 + \dots + x_p = n$$
where $0 \le x_j \le n \, for \, 1 \le j \le n$

Now co-efficient of $x^n$ in $\left(x^0 + x^1 + \dots + x^n\right)^p$  
$\implies$ co-efficient of $x^n$ in $\left(\frac{1 - x^{n+1}}{1 - x}\right)$  
$\implies$ co-efficient of $x^n$ in $\left(1 - x\right)^{-p} = \binom{p+n-1}{n} = \binom{n+p-1}{p-1}$  

## Let's take an example

**Given 10 dices each having 4 faces are rolled at a time. Find the number of solutions so that the sum of outcomes of dices will be at least equal to 40**

## Solution
The answer of the above problem will be **1** as there is only one combination {4, 4, ... 10 times} exist for all of it to sum up to get 40. And 
also from sum of outcomes 41 onwards, there will be no combinations possible for a four faced dice.

Now how can we solve this problem with **No of solutions of an inequality**

---

#### Method - 1
The total number of possible outcomes are $4^{10}$
We have to find the solutions of the inequality $$x_1 + x_2 + \dots + x_{10} \ge 40  \, for \, 1 \le x_j \le 4 \tag{1}$$ where $1 \le j \le 10$

Let's find out the solution for the inequality $$x_1 + x_2 + \dots + x_{10} \le 39 \tag{2}$$ and finally subtract this result from $4^{10}$

In (1), $1 \le x_j \le 4$  
We can find all the solutions for $x_j \ge 1$ (**case - 1**) and for $x_j \ge 5$(**case - 2**) and finally subtract **case - 1** from **case - 2**

__Case - 1__ -  
Let's substitute $x_j^{'} = x_j - 1$ in (2) so that $x_j \ge 1$ will be eventually $x_j^{'} \ge 0$  
The equation will be  $$x_1^{'} + x_2^{'} + \dots + x_{10}^{'} \le 29 \, for \, x_j^{'} \ge 0$$  
Rewritting the above equation with modification of variable $$x_1 + x_2 + \dots + x_{10} \le 29 \, for \, x_j \ge 0 \tag{3}$$
To convert inequality (3) to an equation, introduce a new variable 'w'
$$x_1 + x_2 + \dots + x_{10} + w = 29 \, for \, x_j \ge 0 \, and \, w \ge 0 \tag{4}$$
Now we can apply the above proved formula to (4)

Total number of solutions = $$\binom{29+11-1}{11-1} = \binom{39}{10}$$

__Case - 2__ -  
In the equation (3), let $x_1 \ge 5 \, and \, x_j \ge 1 \, for \, 2 \le j \le 10$  
Now substituting $x_1^{'} = x_1 - 5 \, and \, x_j^{'} = x_j - 1$ in (2), we get the equation
$$x_1 + x_2 + \dots + x_{10} \le 25 \, for \, x_j \ge 0 \tag{5}$$
To convert (5) to an equation, introducing a new variable 'w'  
$$x_1 + x_2 + \dots + x_{10} + w = 25 \, for \, x_j \ge 0 \, and \, w \ge 0 \tag{6}$$
Now we can apply formula to (6)  

Answer = $$\binom{25+11-1}{11-1} = \binom{35}{10}$$  
Similarly for $x_2, x_3 \dots x_{10}$, we will get the same answer  
Therefore we can say -  
The total number of solutions for atleast one $x_j \ge 5$ will be $$10 \times \binom{35}{10} = \binom{10}{1} \times \binom{35}{10} \tag{7}$$

__Final answer__ -  
So far we can answer to the equation (2) based on what we have got -  
Total number of solutions of equation (2) is $$\binom{39}{10} - \binom{10}{1} \times \binom{35}{10} \tag{8}$$  
**OOPS** This does not seem to be $4^{10} - 1$ (based on what we have predicted). So what went wrong?  
We have subtracted those cases where at least 2 variables exceed 4 simultaneously. In case 2, we have calculated the number of solutions for at 
least one $x_j \ge 5$. This also includes the solutions for at least two $x_j \ge 5$, and that is what we have subtracted additionally. So we need 
to add them back to the answer. _How many times will we add them?_  Well, As we should calculate exactly one $x_j \ge 5$, and we have two numbers of
 $x_j$ so to select only one $x_j$, we have two choices i.e. $\binom{2}{1}$ . Look at (8), there we had subtracted two $x_j$. But we were supposed to 
subtract only once. That is why we need to add them back to (8) once.  

Similar to the above methods (7) we have done here, we can find that the total number of solutions for at least two $x_j \ge 5$ will be 
$$\binom{10}{2} \times \binom{31}{10} \tag{9}$$

That's why Total number of solutions of equation (2) _(so far)_ is 
$$\binom{39}{10} - \binom{10}{1} \times \binom{35}{10} + \binom{10}{2} \times \binom{31}{10} \tag{10}$$

Now we are supposed to find how many times we had subtracted or added at least three $x_j$ from (8). By calculating at least one $x_j$ we had
 subtracted $\binom{3}{1}$ times in (10). And by calculating at least two $x_j$ we had added $\binom{3}{2}$ times in (10). So we have 
 $-\binom{3}{1}+\binom{3}{2} = 0$ times subtracted at least three $x_j$. But we were supposed to subtract at least three $x_j$ only once. So we will 
 subtract them in (10).  
 
 Similar to the above methods (7) we have done here, we can find that the total number of solutions for at least three $x_j \ge 5$ will be 
$$\binom{10}{3} \times \binom{27}{10} \tag{11}$$

That's why Total number of solutions of equation (2) _(so far)_ is 
$$\binom{39}{10} - \binom{10}{1} \times \binom{35}{10} + \binom{10}{2} \times \binom{31}{10} - \binom{10}{3} \times \binom{27}{10} \tag{12}$$

This leads to **Inclusion-Exclusion Principle**, and desired solution to (2) will be
$$\binom{39}{10} - \binom{10}{1} \times \binom{35}{10} + \binom{10}{2} \times \binom{31}{10} - \binom{10}{3} \times \binom{27}{10} + \binom{10}{4} \times \binom{23}{10} - \binom{10}{5} \times \binom{19}{10} + \binom{10}{6} \times \binom{15}{10} - \binom{10}{7} \times \binom{11}{10} = 1048575 = 4^{10} - 1 \tag{12}$$

**Now coming to the original equation (1)**  
The total number of solution of equation (1) is $4^{10} - \left(4^{10} - 1\right) = 1$  

---

#### Method - 2
However there is also an easier method.  
Let $y_j = 5 - x_j \, for \, 1 \le j \le 10$. Then each $y_i$ is a positive integer satisfying $1 \le y_i \le 4$(as minimum value of $x_j = 1$ and
 maximum value of $x_j = 4$)  
We can construct an equation from (2) as  $$50 - y_1 - y_2 - \dots - y_{10} \le 39 \, for \, y_j \ge 1 \\ \implies y_1 + y_2 + \dots + y_{10} \ge 11 \, for \, y_j \ge 1 \\ \implies y_1 + y_2 + \dots + y_{10} \ge 1 \, for \, y_j \ge 0 \tag{13}$$

To find solution for (13), let's find solution for $$y_1 + y_2 + \dots + y_{10} \le 0 \, for \, y_j \ge 0 \tag{14}$$ and subtract (13) from $4^{10}$

The total number of solutions for (14) is $\binom{0+11-1}{11-1} = 1$

So the total number of solutions for (13) is $4^{10} - 1$  
**Now coming to the original equation (1)**  
The total number of solution of equation (1) is $4^{10} - \left(4^{10} - 1\right) = 1$

---

# Programming
Now let's write code in c++ about what we have done so far  -  
```
#include<bits/stdc++.h>
using namespace std;
double combination(int n, int m){
    /*
    * This is a function that returns combination
    * of two integer numbers
    */
	if((m > n) or (n < 0) or (m < 0))
		return 0;
	else if(n == m or m == 0)
		return 1;
	double temp = 1;
	for(int i = 1; i <= m; ++i){
		temp = (temp * n) / i;
		--n;
	}
	return temp;
}
double process(int result, int n, int N){
	// Calculate for value atmost result - 1
	// and finally subtract from the total
	// sample space
	result = result - 1;
	double prob = combination(result, N);
	double to_exclude = 0;
	int cnt = 1;
	bool add = true;
	while(result >= N){
        result -= n;
        // Inclusion exclusion property
        if(add)
            to_exclude += combination(N, cnt) * combination(result, N);
        else
            to_exclude -= combination(N, cnt) * combination(result, N);
        add = !add;
        ++cnt;
	}
	prob = 1 - ((prob - to_exclude) / pow(n , N));
	// Ignore all the impossible cases
	if(prob > 1)
        return 0;
	return prob;
}
int main(){
	int T;
	cin >> T;           // Test cases
	for(int i = 1; i <= T; ++i){
		int result, n, N;
		cin >> result >> n >> N;        // Input given
        double prob = process(result, n, N);
		cout << "Rolling a dice having " << n << " faces " << N << " times, the probability that getting sum of outcomes atleast "
		<< result << " is " << prob << endl;
	}
	return 0;
}
```
#### Input
The first line consists of T test cases. The following T lines consists of 3 integers
- sum of outcomes to be atleast a number
- Number of faces of a dice
- Total number of dices  

Now input given to be  
```
4
2 2 2
20 6 10
2 8 1
40 8 5
```
The output will be  
```
Rolling a dice having 2 faces 2 times, the probability that getting sum of outcomes atleast 2 is 1
Rolling a dice having 6 faces 10 times, the probability that getting sum of outcomes atleast 20 is 0.99852
Rolling a dice having 8 faces 1 times, the probability that getting sum of outcomes atleast 2 is 0.875
Rolling a dice having 8 faces 5 times, the probability that getting sum of outcomes atleast 40 is 3.05176e-05
```

---
