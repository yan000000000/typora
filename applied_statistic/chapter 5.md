# Limit theorem

## Markov and Chebyshev Inequalities

### Markov inequality

#### Definition

If a random variable $X$ can only take **nonnegative values**, then
$$
P(X\geq a)\leq\frac{E[X]}{a} \ \ \ \ for \ \ all \ \ a >0
$$

* if a nonnegative r.v. has a small mean, then the probability that it takes a large value must also be small

#### proof

fix a positive number $a$ and consider the r.v. $Y_a$ defined by
$$
Y_a = \begin{cases}0 \ \ \ \ if \ \ X \leq a \\
a \ \ \ \ if \ \ X \geq a \end{cases}
$$
the relation  $Y_a \leq X$ always hold because the value of $Y_a$ is never greater than $X$ and $X$ only take **nonnegative values**, therefore we have  $E[Y_a] \leq E[X]$ , for $E[Y_a]$ , we have 
$$
E[Y_a] = aP(Y_a = a) = aP(X\geq a)
$$
substitute into the original formula, we have
$$
aP(X\geq a) \leq E[X] \\
P(X\geq a)\leq\frac{E[X]}{a}
$$

#### illustration in graph

<img src="assets/image-20240402112454817.png" alt="image-20240402112454817" style="zoom: 33%;" />

from the picture we can see

* part(a): the PDF of a nonnegative r.v. $X$
* Part(b): the PMF of a related r.v. $Y_a$ 

> the process from (a) to (b) is the remapping from r.v. $X$ to the r.v. $Y_a$, comparing the probabilities of these 2 r.v.

* for part(a): the mass can be calculated by
  * for $X\in [0,a], P(X \in [0,a]) = \int_{0}^{a}f_X(x)$ while $X$ can only take nonnegative, the min is 0
  * For $X \in[a,\infty], P(X \in [a,\infty]) = \int_{a}^{\infty}f_X(x)$ 
  
* for part(b): the mass can be notated by
  * for $X\in [0,a],P(Y_a = 0)$​ 
  * for $X\in [a,\infty],P(Y_a = a)$ 
  
* for $E[X]$, we have
  *  $E[X]$ we have  $E[X] = \int_{0}^{\infty}xf_X(x) = \int_{0}^{a}xf_X(x) + \int_{a}^{\infty}xf_X(x)$ while when all the possible outcome respectively become $0$ or $a$ we have $E[X] = E[Y_a]$
  *   $E[Y_a]$ we have $E[Y_a] = 0*P(Y_a = 0)+a*P(Y_a = a) = aP(Y_a = a)$ 
  
  用英文讲的有点复杂，就是从PDF转化成PMF，所有从0到a的值变成了0，所有从a到无穷的值变成了a。而两个区域的概率不变，值变小了，所以最后的 $E[Y_a]\leq E[X]$ 只能在 $X$ 的值为类似 $Y_a$​ 的PMF的情况才能相等吧 

## Chebyshev inequality

### Definition

If $X$ is a r.v. with mean $\mu$ and variance $\sigma^2$, then
$$
P(|X-\mu|\geq c) \leq\frac{\sigma^2}{c^2} \ \ \ \ for \ \ all \ \ c > 0
$$

#### Proof 

Consider the nonnegative r.v. $(X-\mu)^2$ and apply the Markov inequality, we have
$$
P((X-\mu)^2\geq c^2) \leq\frac{E[(X-\mu)^2]}{c^2} = \frac{\sigma^2}{c^2}
$$
while for the term $(X-\mu)^2 \geq c^2$, it is identical to $|X-\mu| \geq c$ . Hence we have proved

#### Alternative form

By letting $c = k\sigma$, where $k$ is positive, we have 
$$
P(|X-\mu|\geq c) = P(|X-\mu|\geq k\sigma) \leq \frac{\sigma^2}{c^2} = \frac{\sigma^2}{k^2\sigma^2} = \frac{1}{k^2}
$$
Hence we have our conclusion

* the probability that a r.v. takes a value more than $k$ standard deviations away from its mean is at most $\frac{1}{k^2}$ 

## Comparison

* The Chebyshev inequality tends to be more powerful than the Markov inequality because the bounds are more accurate, because it also uses information on the variance of $X$

* The mean and the variance of a r.v. are only a rough summary of its properties, we can't expect the bounds to be close approximations of the exact probabilities

## The Weak Law of Large Numbers

### sample mean and true mean

* sample mean $M_n$ is the mean of the sample you choose from the sample space (which could be only a part of them)

* true mean $\mu$ is the mean of the whole sample space

### Weak law of large number

consider a sequence $X_1,X_2,\cdots$ of r.v. with mean $\mu$ and variance $\sigma^2$ , the sample mean is $M_n = \frac{X_1+\cdots+X_n}{n}$ while the true mean is $\mu$ 

we have
$$
E[M_n] = \frac{E[X_1]+\cdots+E[X_n]}{n} = \frac{n\mu}{n} = \mu
$$

$$
var(M_n) = \frac{var(X_1+\cdots+X_n)}{n^2} \\ 
 = \frac{var(X_1)+\cdots+var(X_n)}{n^2}\\
  = \frac{n\sigma^2}{n^2}\\
  =\frac{\sigma^2}{n}
$$

By applying the Chebyshev inequality and we have
$$
P(|M_n - \mu|\geq \epsilon) \leq\frac{\sigma^2}{n\epsilon} \ \ for \ \ any \ \ \epsilon > 0
$$
For any fixed $\epsilon > 0$, the right hand side of this inequality goes to 0 as $n$ increases.

### Rigorous definition

Let $X_1,X_2,\cdots$ be independent identically distributed r.v. with mean $\mu$, then for any $\epsilon > 0$ we have
$$
P(|M_n - \mu|\geq \epsilon) \rightarrow 0, \ \ as \ \ n \rightarrow \infty
$$

### Interpretation

The weak law of large numbers states that for large $n$, the bulk of the distribution of $M_n$ is concentrated near $\mu$

If we consider a positive length interval $[\mu-\epsilon,\mu + \epsilon]$ around $\mu$, then there is high probabilities that $M_n$ will fall in that interval.

As $n\rightarrow \infty$, the probability converge to 1. If $\epsilon$ is really small, we need to wait longer to see that $M_n$ fall in that interval.

## Convergence in probability

### Intro

We can interpret the weak law of large numbers as stating that " $M_n$ converges to $\mu$"

However, since $M_1,M_2,\cdots$ is sequence of r.v., we have to make the definition more precise

### Precise definition

#### Convergence of a deterministic sequence

Let $a_1,a_2,\cdots$ be a sequence of real numbers, and let $a$ be another real number. We say that $a_n$ converges to $a$ or
$$
lim_{n\rightarrow\infty} a_n = a
$$
if for every $\epsilon > 0$ there exists some $n_0$ s.t. $|a_n-a| \leq \epsilon$ for all $n\geq n_0$ 

#### Convergence in Probability

Let $Y_1,Y_2,\cdots$ be a sequence of r.v. variables, and let $a$ be a real number

We say that the sequence $Y_n$ converges to $a$ in probability, if for any $\epsilon > 0$, we have
$$
lim_{n\rightarrow\infty}P(|Y_n-a|\geq\epsilon) = 0
$$

## The central limit theorem

### Intro

In the weak law of large numbers, we have sample mean which is $M_N = \frac{X_1+\cdots+X_n}{n}$ tends to converge to the true mean and it variance tends to 0

Remember we are annoyed by $S_n = X_1+\cdots+X_n = nM_n$ which doesn't converge to any thing when n close to infinite large so we introduce the central limit theorem

It is a process to make it useful through a series of changes to a <font color = '#e65529'>standard normal</font> distribution

### Definition

The CDF of $Z_n = \frac{X_1+\cdots+X_n - n\mu}{\sigma\sqrt{n}}$ converges to standard normal CDF
$$
\Phi(z) = \frac{1}{\sqrt{2\pi}}\int_{-\infty}^{z}e^{-\frac{x^2}{2}}dx
$$
  in the sense that  $\lim_{n\rightarrow\infty}P(Z_n\leq z) = \Phi(z)$​ 

#### Adaptation

$$
E[Z_n] = \frac{E[X_1+\cdots+X_n]-n\mu}{\sigma \sqrt{n}} = 0
$$

$$
var(Z_n) = \frac{var(X_1+\cdots+X_n)}{(\sigma \sqrt{n})^2} = \frac{\sigma^2 n}{\sigma^2 n} = 1
$$

### Generality

The central limit theorem can be adapted widely because it has no requirement on the distribution of the $X_i$ , which could be discrete, continuous or mixed

Q:原文不是很理解 Besides independence , the implicit assumption that the mean and variance are finite, it place no other requirement on the distribution of the $X_i$​ 

### Approximation on CLT

The theorem CLT indicateds that <font color = '#e65529'>the sum of a large number of independent r.v. is approximately normal</font> it allows the calculation by referring to the normal CDF, which is equaivalent to treating $S_n$ as a n.v. with mean $n\mu$ and variance $n \sigma^2$ 

## Strong law of large numbers

### Definition

Let $X_1,X_2,\cdots$ be a sequence of independent identically distributed r.v. with mean $\mu$ , then the sequence of sample means $M_n = \frac{X_1+X_2+\cdots+X_n}{n}$ converges to $\mu$ <font color = '#e65529'>with probability 1</font> in the sense that
$$
P(\lim_{n\rightarrow \infty }\frac{X_1+\cdots+X_n}{n} = \mu) = 1
$$
The strong law of large numbers states that<font color = '#e65529'>all of the probabilities</font> is concentrated on this subset $A$ of the sample space and equally the collection of outcomes that do <font color = '#e65529'>not</font> belong to $A$ has <font color = '#e65529'>probabilities of 0</font> 

### Comparison

#### Weak law

The weak law states that the probability $P(|M_n-\mu|\geq \epsilon)$ of a significant deviation of $M_n$ from  $\mu$ goes to zero as $n\rightarrow \infty$ 

which means that this probabilities can be positive and there may exist once in a while greater than $\mu$ 

#### Strong law 

 $M_n$ converges to $\mu$ with a probability of 1 

