## 1. Basic concepts

### random variable

#### Definition

when dealing with these numberical values, it is useful to assign probabilities to them, this is done through the notion of a random variable

#### Main concepts

* starting with a probabilistic model of an experiment
* a random variable is a real-valued function of the outcome of the experiment
* a function of a random variable defines another random variable

#### personal understanding

* Random variable is actually a function, so you can rewrite it into $f(x)$ to understand

#### example

* **Evenness Indicator**: $X$ could be defined to indicate whether the outcome is even or odd.

$\begin{cases}1, i \ is \ even\\ 0, i \ is \ odd \end{cases}$

So for a roll of 2, $X(2)=1$, and for a roll of 3, $X(3)=0$

* **Greater Than Four Indicator**: X*X* might indicate whether the roll is greater than 4.

$\begin{cases}1, i > 4\\ 0, i \leq 4 \end{cases}$

* **Modulo Mapping**: $X$ could map the outcome of the die to its remainder when divided by 3 (mod 3). $X(i)=i \ mod \ 3$

  This would give $X(1)=1$, $X(2)=2$, $X(3)=0$, etc.

* **Squared Outcome**: $X$ might be the square of the outcome. $X(i)=i^2$ Which would yield $X(1)=1$$, $$X(2)=4$, $X(3)=9$, etc.

* **Prime Number Indicator**: $X$ could indicate whether the outcome is a prime number.

$\begin{cases}1, i \ is \ prime\\ 0, otherwise \end{cases}$

### Discrete random variable

#### Definition

A random variable is called discrete if its range is either finite or countably infinite

#### e.g.

a random variable of the sum of 2 rolls of a die

Or

$sign(a) = \begin{cases}1, a > 0 \\ 0, a = 0 \\ -1, a < 0  \end{cases}$​

#### concepts

* A discrete random variable is a real-valued(range $\in R$) function of the outcome of a discrete experiment
* A discrete random variable has an associated probability mass function(PMF) which gives the probability of each numerical value that the random variable can take
* A function of a discrete random variable defines another discrete random variable, whose PMF can be obtained from the PMF of the original random variable（类似复合函数，可以从原函数PMF得到衍生函数的PMF，后面再看看怎么解释，

### Continuous random variable

Later on next chapter

## 2. Probability mass function

### Probability mass function

#### Definition

For a discrete random variable $X$, the probability mass function(PMF) of $X$ captures the probabilities of the values that it can take

#### Notation

if $x$ is any possible value of $X$, the probability mass of $x$ , denoted $p_X(x)$, is the probability of the event $\{X = x\}$ consisting of all outcomes that give rise to a value of $X$ equal to x:
$$
p_X(x) = P(\{X = x\})
$$

* Upper case characters to denote random variables, $X,Y,Z$ 
* Lower case characters to denote real numbers, $ x,y,z$
* we will write $P(X = x)$ in place of notation $P(\{X = x\})$ ,and similarly $P(X\in S)$ 

####  e.g.

Two independent tosses of a fair coin

 $X$ is the number of heads obtained

The PMF of $X$ is
$$
p_X(x) = \begin{cases}\frac{1}{4}, \ if \ x = 0 \ or \ x = 2 \\ \frac{1}{2}, \ if \ x = 1 \\ 0 \ \ otherwise \end{cases}
$$

> remember the otherwise, that's the point

#### the adaption of basic law

##### Additivity and normalization axioms

* follow from the additivity and normalization axioms

$$
\sum_{x:all\ possible \ values \ of X}^{} p_X(x) = 1
$$

The events ${X = x}$ are disjoint, and they form a partition of the sample space

* for any set $S$ of real numbers

$$
P(X\in S) = \sum_{x\in S}^{}p_X(x)
$$

* for each possible value $x$ of $X$
  * collect all the possible outcomes that give rise to the event $\{X = x\}$ 
  * add their probabilities to obtain $pX(x)$ 

### Important specific distribution

#### Binomial random variable

##### Definition

The bernoulli random variable takes the two values 1 and 0

##### PMF

$$
p_X(x) = \begin{cases}p \ \ if \ x = 1 \\ 1-p \ \ if \ x = 0 \end{cases}
$$

##### for k times

sometimes we refer binomial random variable $X$ as $X~Bio(n,p)$ which $n$ refer to the repeat time of the experiment and $p$​ refer to the probability

for $k = 0,1,\cdots,n$
$$
p_X(k) = P(X = k) = (_k^n)p^k(1-p)^{n-k}
$$

##### normalization

$$
\sum_{k = 0}^{n}(_k^n)p^k(1-p)^{n-k} = 1
$$

##### graph

<img src="assets/Binomial_Distribution.svg.png" alt="Binomial_Distribution.svg" style="zoom: 15%;" />

#### Geometric random variable

##### intro scenario

Independently and repeatedly toss a biased coin with probability of head $p$, where $0<p<1$

The $k$ is the number $X$ of tosses needed for a head to come up for the first time

##### PMF

$$
p_X(k) = (1-p)^{k-1}p
$$

 $k - 1$ tails followed by a head

##### normalization

$$
\sum_{k = 1}^{\infty}p_X(k) = \sum_{k = 1}^{\infty}(1-p)^{k-1}p = p\sum_{k = 0}^{\infty}(1-p)^k = p\frac{1}{1-(1-p)} = 1
$$

While $p\sum_{k = 0}^{\infty}(1-p)^k$ are using summation of geometric progression(等比数列求和) and limit

##### graph

<img src="assets/Geometric_pmf.svg.png" alt="Geometric_pmf.svg" style="zoom:25%;" />

#### Poisson random variable

##### Definition

A poisson random variable takes nonnegative integer values

##### PMF

$$
p_X(k) = e^{-\lambda}\frac{\lambda^k}{k!}, \ \ \ k = 0, 1, 2,\cdots 
$$

##### Normalization condition

$$
\sum_{k = 0}^{\infty}e^{-\lambda}\frac{\lambda^k}{k!} = e^{-\lambda}(1+\lambda+\frac{\lambda^2}{2!}+\cdots) = e^{-\lambda}e^{\lambda} = 1 
$$

##### feature

* poisson random variable can be viewed as a binomial random variable with very small $p$ and very large $n$ 
* precisely Poisson PMF with parameter $\lambda$ is a good approximation for a binomial PMF with parameters $n$ and $p$ where $ \lambda = np$, $n$ is large and $p$ is small

##### graph

<img src="assets/Poisson-distribution-graph.webp" alt="Poisson-distribution-graph" style="zoom:25%;" />

* for $\lambda \leq 1$, it is monotonically decreasing
* for $\lambda > 1$ first increases and then decrease

## 3. Functions of random variable

### Functions of random variable

In general, if $Y = g(X)$ is a function of a random variable $X$, then $Y$ is also a random variable

The PMF $p_Y$ of $Y = g(X)$ can be calculated as
$$
p_Y(y) = \sum_{x:g(x) = y}^{}p_X(x)
$$

## 4. Expectation,mean,and variance

### Expectation

#### Intro scenario

Sometimes we are desired to summarize the values and probabilities by one number

#### Definition

The expectation of $X$ is a weighted average of the possible values of $X$ (Weight:probabilities)

In math, formally, we denote as
$$
E[X] = \sum_{}^{}xp_X(x)
$$

#### Mean of $aX+b$

let $Y$ be a linear function of $X$, we have $Y = aX+b$

The mean of $Y$
$$
E[Y] = E[aX+B] = \sum_{x}^{}(aX+b)p_X(x) = a\sum_{x}^{}x \ p_X(x)+\sum_{x}^{}b \ p_X(x) = aE[x] + b
$$
using the definition of expectation and the normalization condition

#### Expectation for g(X)

there is a simple way of computing $E[g(X)]$

Let $X$ be a random variable with PMF $p_X(x)$ and let $g(X)$ be a real-valued function of $X$, the expected value of the random variable $Y = g(X) is$
$$
E[g(X)] = \sum_{x}^{}g(x)p_X(x)
$$

##### proof

Using the formula $p_Y(y) = \sum_{x|g(x) = y}p_X(x)$​ 
$$
E[g(X)] = E[Y] = \sum_{y}^{}yp_Y(y) \\
= \sum_{y}^{}y \ \sum_{x|g(x) = y}^{}p_X(x) \\
= \sum_{y}^{}\sum_{x|g(x) = y}^{}y \ p_X(x) \\
= \sum_{y}^{}\sum_{x|g(x) = y}^{}g(x)p_X(x) \\
=\sum_{x|g(x) = y}^{}g(x)p_X(x)
$$


### Variance

#### notice

the $k$th moment of $E[x]$ is $E[x^k]$, so when $k = 1$, or just say the first moment is just the mean. I think the moment here is the to the $k$th power of the variable.

#### Definition

Variance of $X$, denoted by var$(X)$ is
$$
var(X) = E[(X - E[X])^2]
$$
which is the second moment of $X - E[x]$, therefore the variance is always non-negative
$$
var(X) \geq 0
$$


#### Question

**why did the researcher define the var as the second moment?**

if we define the var as the first moment, we have
$$
E[X - E[X]] = E[X]-E[E[X]] = E[X] - E[X] = 0
$$
while $E[E[X]]$ is a constant $E[X]$​ 

#### variance of $aX+b$​

let $Y$ be a linear function of $X$, we have $Y = aX + b$, using the [formula (99)](# expectation for g(x))

The variance of $Y$​​ is 
$$
var(Y) = var(aX+b) = a^2var(X)
$$


##### proof

$$
var(Y) = E[(Y-E[Y])^2] \\
= E[(ax+b-E[ax+b])^2] \\
=\sum_{x}^{}(ax+b-E[ax+b])^2p_X(x) \\
=\sum_{x}^{}(ax+b-aE[x]-b)^2p_X(x) \\
=a^2\sum_{x}^{}(x-E[x])^2p_X(x) \\
=a^2var(x)
$$

#### Variance as moments

$$
var(X) = E[X^2]-(E[X])^2
$$

##### proof

$$
var(X) = E[(X-E[X])^2]\\
=E[X^2-2XE[X]+E[X]^2] \\
=E[X^2]-E[2XE[X]] +E[E[X]^2]\\
=E[X^2]-2E[X]E[X]+(E[X])^2 \\
=E[X^2]-(E[X])^2
$$



### Standard deviation

#### Definition

Standard deviation of $X$, denoted by $\sigma_X$ is
$$
\sigma_X = \sqrt{var(X)}
$$

## 5. Joint PMFs of multiple random variables

### Joint PMFs

#### Intro Scenario

Probabilistic models often involve several random variables of interest

e.g. In a networking context, the workloads of several gateways may be of interest

#### Definition

Consider two discrete random variables $X$ and $Y$ associated with the same experiment

The joint PMF of $X$ and $Y$ is denoted by $P_{{X,Y}}$.

If $(x,y)$ is a pair of values that $(X,Y)$ can take, then the probability mass of $(x,y)$ is the probability of the event

$\{X=x,Y=y\}$, which is
$$
P_{X,Y}(x,y) = P(X = x, Y = y)
$$

* The joint PMF determines the probability of any event that can be specified in terms of random variables $X$ and $Y$ 

* The joint PMF $p_{{X,Y}}$ is arranged in a two-dimensional table

  ![image105607568030551416785](assets/image105607568030551416785.png)

#### formula

  The respective PMFs of $X$ and $Y$ is 
$$
  p_X(x) = \sum_{y}^{}p_{X,Y}(x,y), \ \ \ \ p_Y(y) = \sum_{x}^{}p_{X,Y}(x,y)
$$

meaning to get $P_X(x)$ we have to go through all the value of y, similar for $p_Y(y)$ 

*  $p_X,p_Y$ are called the **marginal PMFs**

##### verification

$$
p_X(x)= P(X = x)\\
=\sum_{y}^{}P(X=x,Y=y)\\
=\sum_{y}^{}p_{X,Y}(x,y)
$$

#### graphical meaning

The marginal PMF of $X$ or $Y$ at a given value is obtained by adding the table entries along a corresponding column or row, respectively

### Functions of multiple random variable

#### New random variable

One can generate new random variables by applying functions on several random variables

1. Consider $Z = g(X, Y)$
2. Its PMF can be calculated from the joint PMF $P_{X,Y}$ according to $P_Z(z) = \sum_{x,y|g(x,y )= z}^{}p_{X,Y}(x,y)$

#### Expect value rule

$$
E[g(X,Y)] = \sum_{x,y}^{}g(x,y)P_{X,Y}(x,y)
$$

##### Linear case

For special case, if g is linear and of the form of $aX + bY + c$ , we have
$$
E[aX+bY+c] = aE[X]+bE[Y]+c
$$
"linearity of expectation"--regardless of dependence of $X$ and $Y$

### More than two random variable

We can also consider 3 or more random variable

#### Joint PMF of 3 variable

The joint PMF of three random variables $X,Y,Z$
$$
p_{X,Y,Z}(x,y,z) = P(X = x,Y=y,Z=z)
$$

#### Marginal PMF

$$
p_{X,Y}(x,y) = \sum_{z}^{}p_{X,Y,Z}(x,y,z)
$$

others are the same

#### Expected value rule

$$
E[g(X,Y,Z)] = \sum_{x,y,z}^{}g(x,y,z)p_{X,Y,Z}(x,y,z)
$$

Same with 2 random variable, if $g$ is linear and of form $g(X,Y,Z) = aX + bY + cZ + d$, then we have
$$
E[aX+bY+cZ+d] = aE[X]+bE[Y]+cE[Z]+d
$$


#### Generalization

For any random variables $X_1,X_2,\cdots,X_n$ and any scalars $a_1,a_2,\cdots,a_n$, wehave 
$$
E[a_1X_1+a_2X_2+\cdots+a_nX_n] = a_1E[X_1]+a_2E[X_2]+\cdots + a_nE[x_n]
$$



## 6. Conditioning

### review

* Conditional probability captures the event which has occurred in a probabilistic model
* Conditional probability are like ordinary probabilities(satisfy the three axioms)
* it refer to a new universe: an event A which is known to have occurred



### Conditioning a random variable on an event

The conditional PMF of a random variable $X$ conditioned on a particular event $A$ with $P(A)> 0$ is defined by
$$
p_{X|A}(x) = p(X = x|A) \\
= \frac{P(\{X = x\}\cap A)}{P(A)}
$$

#### proof of available

* Consider the events $\{X=x\}\cap A$
  * they are disjoint for different values of $x$
  * their union is $A$​ , thus we have $P(A) = \sum_{x}^{}P(\{X = x\}\cap A)$​
* Combining the formula 33, we have $\sum_{x}^{}p_{X|A}(x) = 1$ 
* so $p_{X|A}$ is a legitimate PMF

#### reflect

为什么所有随机变量取值与事件A的交集的所有并集是A, 即 $\sum_{x}^{}\{X = x\}\cap A = A$

首先我没有搞明白样本空间的含义，简单来说是指所有可能出现的值，其次是随机变量，我一开始的理解是函数黑盒子，但是我漏掉了一点是，“所有的可能值”，

随机变量 $X$ 是一个映射，它将样本空间中的每个可能结果映射到一个实数。这个映射定义了随机变量的全部可能值，这些值构成了随机变量的值域。所以才一定要说otherwise

### Conditioning one random varaible on another

Let $X$ and $Y$ be two random variables associated with the same experiment, the experimental value $Y = y(p_Y(y) > 0)$ provides partial knowledge about the value of $X$

#### Definition

The knowledge is captured by the conditional PMF $p_{X|Y}$ of $X$ given $Y$
$$
p_{X|Y}(x|y) = P(X = x|Y = y)
$$


by the definition of conditional probabilities, we have
$$
p_{X|Y}(x|y) = \frac{P(X=x,Y = y)}{P(Y = y)} = \frac{p_{X,Y}(x,y)}{p_Y(y)}
$$
where $p_{X,Y}(x,y)$ is the joint PMF of $x$ and $y$, and $p_{Y}(y)$ is the marginal PMF of $y$ 

*  when we calculate $p_{X,Y}(x,y)$ , we fix some $y$, see $y$ as constant with $p_Y(y)>0$ (this is important because it shows that it can provide some knowledge), see the whole thing is the function of $x$ 
* This funcction is a valid PMF for $X$:
  * each possible $x$ is nonnegative
  * these value add to 1
  * has the same shape as $p_{X,Y}(x,y)$
  *  $\sum_{x}^{}p_{X|Y}(x|y) = 1 $

#### calculation technique

##### for joint PMF

* it is convenient to calculate the joint PMF by the conditional PMF

$$
p_{X,Y}(x,y) = p_Y(y)p_{X|Y}(x|y)
$$

or its counter part
$$
p_{X,Y}(x,y) = p_X(x)p_{Y|X}(y|x)
$$

##### for marginal PMF

the conditional PMF can also be used to calculate the marginal PMFs
$$
p_X(x) = \sum_{y}^{}p_{X,Y}(x,y) = \sum_{y}^{}p_Y(y)p_{X|Y}(x|y)
$$
this method provides a divide and conquer method for calculating marginal PMFs

### Conditional expectation

#### Conditional expectation for one r.v. on event A

The conditional expectation of $X$ given an event $A$ with $P(A)> 0$, is defined by
$$
E[X|A] = \sum_{x}^{} xp_{X|A}(x|A)
$$
For a function $g(X)$, it is given by
$$
E[g(X)|A] = \sum_{x}^{}g(x)p_{X|A}(x|A)
$$

#### Conditional expectation for one r.v. on another r.v.

The conditional expectation of $X$ given a value $y$ of $Y$ is defined by
$$
E[X|Y = y] = \sum_{x}^{}xp_{X|Y}(x|y)
$$
The **total expectation theorem**
$$
E[X] = \sum_{x}^{}p_Y(y)E[X|Y = y]
$$
Hint: can be proved using formula 39

#### total expectation theorem for one r.v. on event A

Let $A_1,\cdots,A_n$ be disjoint events that form a partition of the sample space, and assume that $P(A_i)> 0$ for all $i$ Then, we have
$$
E[X] = \sum_{i = 1}^{n}p(A_i)E[X|A_i]
$$

##### proof

$$
E[X] = \sum_{x}^{}xp_X(x) \\
= \sum_{x}^{}x\sum_{i = 1}^{n }p(A_i)p_{X|A_i}(x|A_i)\\
= \sum_{i = 1}^{n}p(A_i)\sum_{x}^{}xp_{X|A_i}(x|A_i)\\
 = \sum_{i = 1}^{n}p(A_i)E[X|A_i]
$$

### Mean and Variance of the Geometric r.v.

 $X$ is a geometric r.v. with PMF,
$$
p_x(k) =(1-p)^{k-1}p  \ \ \ k = 1,2,\cdots
$$

#### mean

$$
E[x] = \sum_{k = 1}^{\infty}k(1-p)^{k-1}p
$$

#### variance

$$
var(x) = \sum_{k = 1}^{\infty}(k - E[X])^2(1-p)^{k-1}p
$$

#### calculation of $E[X]$

It is tedious to calculate them one by one, so we apply the total expectation theorem

##### Proof

we consider the first situation with random variable $Y$. The probabilities of first try is successful is $p$ and the probabilities of first try failed is $(1-p)$, which include $Y_1 = \{X = 1\} $ with $P_1 = p$ and $Y_2 = \{X > 1\}$​ with $P_2 = 1-p$  

According to total expectation theorem, we have 
$$
E[X] = \sum_{x}^{}p_Y(y)E[X|Y = y]
$$
therefore we have 
$$
E[X] = p_Y(y_1)E[X = 1|Y = 1] + p_Y(y_2)E[X > 1|Y = 2]
$$
so our goal is to compute $E[X > 1|Y = 2]$

###### Method 1

$$
E[X>1|Y = 2] = \sum_{x = 2}^{\infty}xp_{X|Y}(x)\\
=\sum_{x= 2}^{\infty}x(1-p)^{x-2}p\\
=\sum_{x = 1}^{\infty}(x+1)(1-p)^{x - 1}p\\
=E[X+1]\\
=E[X]+1
$$

###### method 2

For r.v. $X$, we have $X = 1, 2,\cdots,\infty$, we let r.v. $Y = 2,3,\cdots,\infty $​ 

then we have $E[Y] = E[X+1] = E[X]+ 1$ 

##### back to our proof

Substitute $E[X>1|Y = 2] = E[X]+ 1$ to the formula(51), we have 
$$
E[X] = p_Y(y_1)E[X = 1|Y = 1] + p_Y(y_2)E[X > 1|Y = 2] \\
= p * 1 + (1-p)(E[X]+1)\\
=p+E[X]+1-pE[X]-p
$$
Finally, we have
$$
E[X] = \frac{1}{p} 
$$

##### for $E[X^2]$​

Similarly, we have 
$$
E[X^2|X = 1] = 1 \\
$$

$$
E[X^2|X > 1] = E[(1+X)^2]\\
= 1+2E[X]+E[X^2]
$$

so
$$
E[X^2] = p + (1-p)(1+2E[X]+E[X^2])\\
=p+1+2E[X]+E[X^2]-p-2pE[X]-pE[X^2]\\
$$
so 
$$
E[X^2] = \frac{2}{p^2}-\frac{1}{p}
$$

#### calculation for $var(X)$

from the above calculation, we can conclude that
$$
var(X) = E[X^2] - (E[X])^2\\
=\frac{2}{p^2} - \frac{1}{p} - \frac{1}{p^2}\\
=\frac{1}{p^2}-\frac{1}{p}
$$

## 7. Independence

### Review

#### Definition

Knowing the occurrence of the conditioning event tells us nothing about the value of the random variable
$$
P(A\cap B) = P(A)\cdot P(B)
$$

### Independence of r.v. from an event

#### Definition

Formally, the r.v. $X$ is independent of the event $A$ if
$$
P(X=x  \ and \ A) = P(X =x)P(A) = p_X(x)P(A)
$$
for any choice of $x$

or equivalently, requiring that the events $\{X =x\}$ and $A$ are independent, for any choice $x$

#### Formula

consider $P(A) > 0$, by the definition of the conditional PMF we have
$$
p_{X|A} = \frac{P(X = x \ and \ A)}{P(A)}
$$
given that we have $X$ is independent of the event $A$, we have
$$
P(X = x \ and \ A) = P(X = x)\cap P(A)
$$
substitute it into the original formula, we have
$$
p_{X|A} = \frac{P(X = x)P(A)}{P(A)} = P(X = x) = p_X(x)
$$

###  Independence of r.v. from another r.v.

#### Definition

Similar to the independence of r.v. from an event, we have 2 r.v. $X$ and $Y$ are independent if
$$
p_{X,Y}(x,y) = p_X(x)\cdot p_Y(y) \ \ for \ \ all \ x,y
$$
or in other word, it requires that the 2 events $\{X=x\}$ and $\{Y=y\}$ is independent for every $x$ and $y$​

#### Formula

By the formula (65), we have 
$$
p_{X|Y}(x|y) = p_X(x)
$$

##### Proof

$$
p_{X|Y}(x|y) = \frac{p_{X,Y}(x,y)}{p_Y(y)}\\
=\frac{p_X(x)p_Y(y)}{p_Y(y)}\\
=p_X(x)
$$

### Conditionally independent

#### Definition

 $X$ and $Y$ are conditionally independent if given a positive probability event $A$ 
$$
P(X=x,Y=y|A) =P(X = x|A)P(Y=y|A)
$$
or in another notation
$$
p_{X,Y|A}(x,y) = p_{X|A}(x)p_{Y|A}(y)
$$
or equivalently
$$
p_{X|Y,A}(x,y) = p_{X|A}(x)
$$
for all $x,y$ such that $p_{y|A}(y) > 0$​

#### notice

notice that conditional independence may not imply unconditional independence

### Mean of independent

#### formula

If $X$ and $Y$ are independent r.v. then
$$
E[XY] = E[X]\cdot E[Y]
$$

#### proof

$$
E[XY] = E[X]\cdot E[Y]\\
=\sum_{x}^{}\sum_{y}^{}xy\cdot p_{X,Y}(x,y)\\
=\sum_{x}^{}\sum_{y}^{}xy\cdot p_X(x)p_Y(y)\\
=\sum_{x}^{}xp_X(x)\sum_{y}^{}yp_Y(y)\\
=E[X]\cdot E[Y]
$$

#### more

By similar calculation, if $X$ and $Y$ are independent, then so are $g(X)$ and $h(Y)$ for any functions $g$ and $h$
$$
E[g(X)h(Y)]=E[g(X)]E[h(Y)]
$$

### Variance of independent

#### Definition

Consider $Z = X + Y$, where $X$ and $Y$ are independent, we have
$$
var(Z) = var(X)+ var(Y)
$$

#### proof

$$
var(Z) = E[(Z - E[Z])^2]\\
= E[(X+Y-E[X+Y])^2]\\
= E[(X+Y-E[X]-E[Y])^2]\\
= E[(X-E[X]+Y-E[Y])^2]\\
= E[((X-E[X])+(Y-E[Y]))^2]\\
= E[(X-E[X])^2+(Y-E[Y])^2+2(X-E[X])(Y-E[Y])]\\
= E[(X-E[X])^2]+E[(Y-E[Y])^2]+E[2(X-E[X])(Y-E[Y])]\\
$$

Given that $X$ and $Y$ are independent, from formula (71), and consider $E[X]$ and $E[Y]$ is a constant,
$$
2E[(X-E[X])(Y-E[Y])] = 2E[X-E[X]]E[Y-E[Y]]\\
$$
for $E[X - E[X]]$ , we have
$$
E[X -E[X]] = E[X] - E[E[X]]\\
=E[X ] - E[X]\\
= 0
$$
Therefore
$$
2E[(X-E[X])(Y-E[Y])] = 0
$$
back to formula(75), we have
$$
E[(X-E[X])^2]+E[(Y-E[Y])^2]+E[2(X-E[X])(Y-E[Y])]\\
=E[(X-E[X])^2]+E[(Y-E[Y])^2]\\
=var(X)+var(Y)
$$

### Extension

All previous results have natural extensions to more than 2 r.v.

* Definition

$$
p_{X,Y,Z}(x,y,z) = p_X(x)p_Y(y)p_Z(z)
$$

* variance

$$
var(X_1+X_2+\cdots+X_n) = var(X_1)+var(X_2)+ \cdots + var(X_n)
$$

### variance of binomial

Let $X = X_1 + X_2 + \cdots +X_n$ be a binomial r.v.

for $X_i$, where $i = 1, 2,\cdots,\infty$, we have $var(X_i) = E[X^2] - (E[X])^2 = p-p^2 = p(1-p)$

By the variance extension, we have
$$
var(X) = \sum_{i = 1}^{n}var(X_i) = np(1-p)
$$

###  Mean and variance of the sample mean

Model $X_1,X_2,\cdots,X_n$ as independent bernoulli random variables

we denote mean as $p$ and variance as $p(1-p)$ 

the sample mean can be represent as
$$
S_n = \frac{X_1+X_2+\cdots+X_n}{n}
$$

#### mean

$$
E[S_n] = \sum_{i = 1}^{n}\frac{1}{n}E[X_i] = \frac{1}{n}\sum_{i = 1}^{n}p = p
$$

#### variance

$$
var(S_n) = \sum_{i = 1}^{n}\frac{1}{n^2}var(X_i) = \frac{p(1-p)}{n}
$$




## Reflection

### 对随机变量的新理解

<img src="assets/IMG_8E85016A11AD-1.jpeg" alt="IMG_8E85016A11AD-1" style="zoom:25%;" />

类似这幅图，我们的随机变量通过映射从事件本身变成了一个个事件 $\{X = a\}$ 和 $\{X = b\}$ ，最后这些事件的并集组成了样本空间。当然，这其中映射的过程，从事件到数字这个过程本身是没有体现的，在这种图上表示出来的只有最后的数字表示。那么不同的随机变量意味着什么，不同的随机变量意味着不同的画圆方式。而不同随机变量的交集组成了joint PMF，之后再看看有无新东西

fdfsddfsklfdsjflsdjfdsljflsdjfkldsjflkdsjflsdjfadj













