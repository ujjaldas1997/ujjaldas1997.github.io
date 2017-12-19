---
layout: post
title:  "Switching to console"
date:   2017-12-10T23:39:51
desc: "Documentation of how I switched from GUI to console mode"
keywords: "Ubuntu 16.04LTS,blog,console mode,grub,tty"
categories: [Math]
tags: [Combinatories,blog,Inequality, Programming]
icon: fa-math
---

#No of solutions of an inequality

##Statement
Lets the inequality be $$x_1 + x_2 + \dots + x_k \le p$$ subjected to constraints $a_1 \le x_j \le a_2 \forall 1 \le j \le k$

#Pre-requisties
Total number of ways of distributing 'n' identical objects to 'p' persons such that each receives 0, 1 or more than 1 objects is$$\Comb{n+p-1}{p-1}$$
Proof:
$$x_1 + x_2 + \dots + x_p = n$$
where $0 \le x_j \le n \forall 1 \le j \le n$

Now co-efficient of $x^n$ in $\left(x^0 + x^1 + \dots + x^n\right)^p$
$\implies$ co-efficient of $x^n$ in $\left(\frac{1 - x^{n+1}}{1 - x}\right)$
$\implies$ co-efficient of $x^n$ in $\left(1 - x\right)^{-p} = \Comb{p+n-1}{n} = \Comb{n+p-1}{p-1}$

##Let's take an example

**Given 10 dices each having 4 faces are rolled at a time. Find the number of solutions so that the sum of outcomes of dices will be at least equal to 40**

##Solution
The answer of the above problem will be **1** as there is only one combination {4, 4, ... 10 times} exist for all of it to sum up to get 40. And 
also from sum of outcomes 41 onwards, there will be no combinations possible for a four faced dice.

Now how can we solve this problem with **No of solutions of an inequality**

---

####Method - 1
The total number of possible outcomes are $4^{10}$
We have to find the solutions of the inequality $$x_1 + x_2 + \dots + x_10 \ge 40  \forall 1 \le x_j \le 4 \tag{1}$$ where $1 \le j \le 10$

Let's find out the solution for the inequality $$x_1 + x_2 + \dots + x_10 \le 39 \tag{2}$$ and finally subtract this result from $4^{10}$

In (1), $1 \le x_j \le 4$
We can find all the solutions for $x_j \ge 1$ (**case - 1**) and for $x_j \ge 5$(**case - 2**) and finally subtract **case - 1** from **case - 2**

__Case - 1__ -
Let's substitute $x_j^{'} = x_j - 1$ in (2) so that $x_j \ge 1$ will be eventually $x_j^{'} \ge 0$
The equation will be $$x_1^{'} + x_2^{'} + \dots + x_10^{'} \le 29 \forall x_j^{'} \ge 0$$
Rewritting the above equation with modification of variable $$x_1 + x_2 + \dots + x_10 \le 29 \forall x_j \ge 0 \tag{3}$$
To convert inequality (3) to an equation, introduce a new variable 'w'
$$x_1 + x_2 + \dots + x_10 + w = 29 \forall x_j \ge 0 and w \ge 0 \tag{4}$$
Now we can apply the above proved formula to (4)

Total number of solutions = $$\Comb{29+11-1}{11-1} = \Comb{39}{10}

__Case - 2__ -
In the equation (3), let $x_1 \ge 5 and x_j \ge 1 \forall 2 \le j \le 10$
Now substituting $x_1^{'} = x_1 - 5 and x_j^{'} = x_j - 1$ in (2), we get the equation
$$x_1 + x_2 + \dots + x_10 \le 25 \forall x_j \ge 0 \tag{5}$$
To convert (5) to an equation, introducing a new variable 'w'
$$x_1 + x_2 + \dots + x_10 + w = 25 \forall x_j \ge 0 and w \ge 0 \tag{6}$$
Now we can apply formula to (6)

Answer = $$\Comb{25+11-1}{11-1} = \Comb{35}{10}
Similarly for $x_2, x_3 \dots x_10$, we will get the same answer
Therefore we can say
The total number of solutions for atleast one $x_j \ge 5$ will be $$10 \times \Comb{35}{10} = \Comb{10}{1} \times \Comb{35}{10} \tag{7}$$

__Final answer__ -
So far we can answer to the equation (2) based on what we have got -
Total number of solutions of equation (2) is $$\Comb{39}{10} - \Comb{10}{1} \times \Comb{35}{10} \tag{8}$$
**OOPS** This does not seem to be ~~$4^{10} - 1$~~(based on what we have predicted). So what went wrong?
We have subtracted those cases where at least 2 variables exceed 4 simultaneously. In case 2, we have calculated the number of solutions for at 
least one $x_j \ge 5$. This also includes the solutions for at least two $x_j \ge 5$, and that is what we have subtracted additionally. So we need 
to add them back to the answer. _How many times will we add them?_ Well, As we should calculate exactly one $x_j \ge 5$, and we have two numbers of
 $x_j$ so to select only one $x_j$, we have two choices($\Comb{2}{1}$). Look at (8), there we had subtracted two $x_j$. But we were supposed to 
subtract only once. That is why we need to add them back to (8) once.

Similar to the above methods (7) we have done here, we can find that the total number of solutions for atleast two $x_j \ge 5$ will be 
$$\Comb{10}{2} \times \Comb{31}{10} \tag{9}$$

That's why Total number of solutions of equation (2) _(so far)_ is 
$$\Comb{39}{10} - \Comb{10}{1} \times \Comb{35}{10} + \Comb{10}{2} \times \Comb{31}{10} \tag{10}$$

Now we are supposed to find how many times we had subtracted or added atleast three $x_j$ from (8). By calculating at least one $x_j$ we had
 subtracted $\Comb{3}{1}$ times in (10). And by calculating at least two $x_j$ we had added $\Comb{3}{2}$ times in (10). So we have 
 $-\Comb{3}{1}+\Comb{3}{2} = 0$ times subtracted at least three $x_j$. But we were supposed to subtract at least three $x_j$ only once. So we will 
 subtract them in (10).
 
 Similar to the above methods (7) we have done here, we can find that the total number of solutions for atleast three $x_j \ge 5$ will be 
$$\Comb{10}{3} \times \Comb{27}{10} \tag{11}$$

That's why Total number of solutions of equation (2) _(so far)_ is 
$$\Comb{39}{10} - \Comb{10}{1} \times \Comb{35}{10} + \Comb{10}{2} \times \Comb{31}{10} - \Comb{10}{3} \times \Comb{27}{10} \tag{12}$$

This leads to **Inclusion-Exclusion Principle**, and desired solution to (2) will be
$$\Comb{39}{10} - \Comb{10}{1} \times \Comb{35}{10} + \Comb{10}{2} \times \Comb{31}{10} - \Comb{10}{3} \times \Comb{27}{10} + \Comb{10}{4} \times \Comb{23}{10} - \Comb{10}{5} \times \Comb{19}{10} + \Comb{10}{6} \times \Comb{15}{10} - \Comb{10}{7} \times \Comb{11}{10} = 1048575 = 4^{10} - 1 \tag{12}$$

**Now coming to the original equation (1)**
The total number of solution of equation (1) is $4^{10} - \left(4^{10} - 1\right) = 1$

---

####Method - 2
However there is also an easier method.
Let $y_j = 5 - x_j for 1 \le j \le 10$. Then each $y_i$ is a positive integer satisfying $1 \le y_i \le 4$(as minimum value of $x_j = 1$ and
 maximum value of $x_j = 4$)
We can construct an equation from (2) as $$50 - y_1 - y_2 - \dots - y_10 \le 39 for y_j \ge 1$$
$$\implies y_1 + y_2 + \dots + y_10 \ge 11 for y_j \ge 1$$
$$\implies y_1 + y_2 + \dots + y_10 \ge 1 for y_j \ge 0 \tag{13}$$

To find solution for (13), let's find solution for $$y_1 + y_2 + \dots + y_10 \le 0 for y_j \ge 0 \tag{14}$$ and subtract (13) from $4^{10}$

The total number of solutions for (14) is $\Comb{0+11-1}{11-1} = 1$

So the total number of solutions for (13) is $4^{10} - 1$
**Now coming to the original equation (1)**
The total number of solution of equation (1) is $4^{10} - \left(4^{10} - 1\right) = 1$

---

