# Limit theorem

## Markov and Chebyshev Inequalities

### Markov inequality

#### Definition

If a random variable $X$ can only take <font color = '#e65529'>nonnegative values</font>, then
$$
P(X\geq a)\leq\frac{E[X]}{a} \ \ \ \ for \ \ all \ \ a >0
$$

* if a nonnegative r.v. has a small mean, then the probability that it takes a large value must also be small

#### proof

fix a <font color = '#e65529'>positive</font> number $a$ and consider the r.v. $Y_a$ defined by
$$
Y_a = \begin{cases}0 \ \ \ \ if \ \ X \leq a \\
a \ \ \ \ if \ \ X \geq a \end{cases}
$$
the relation  $Y_a \leq X$ always hold because the value of $Y_a$ is never greater than $X$ and $X$ only take <font color = '#e65529'>nonnegative values</font>, therefore we have  $E[Y_a] \leq E[X]$ , for $E[Y_a]$ , we have 
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

> the process from (a) to (b) is the <font color = '#e65529'>remapping</font> from r.v. $X$ to the r.v. $Y_a$, comparing the probabilities of these 2 r.v.

* for part(a): the mass can be calculated by
  * for $X\in [0,a], P(X \in [0,a]) = \int_{0}^{a}f_X(x)$ while $X$ can only take nonnegative, the min is 0
  * For $X \in[a,\infty], P(X \in [a,\infty]) = \int_{a}^{\infty}f_X(x)$ 
  
* for part(b): the mass can be notated by
  * for $X\in [0,a],P(Y_a = 0)$​ 
  * for $X\in [a,\infty],P(Y_a = a)$ 
  
* for $E[X]$, we have
  *  $E[X]$ we have  $E[X] = \int_{0}^{\infty}xf_X(x) = \int_{0}^{a}xf_X(x) + \int_{a}^{\infty}xf_X(x)$ while when all the possible outcome respectively become $0$ or $a$ we have $E[X] = E[Y_a]$
  *   $E[Y_a]$ we have $E[Y_a] = 0*P(Y_a = 0)+a*P(Y_a = a) = aP(Y_a = a)$​ 
  
  
  
  <font color = '#3e9e02'>用英文讲的有点复杂，就是从PDF转化成PMF，所有从0到a的值变成了0，所有从a到无穷的值变成了a。而两个区域的概率不变，值变小了，所以最后的 $E[Y_a]\leq E[X]$ 只能在 $X$ 的值为类似 $Y_a$ 的PMF的情况才能相等</font>

## Chebyshev inequality

### Definition

If $X$ is a r.v. with mean $\mu$ and variance $\sigma^2$, then
$$
P(|X-\mu|\geq c) \leq\frac{\sigma^2}{c^2} \ \ \ \ for \ \ all \ \ c > 0
$$

> [!note]
>
> we <font color = '#e65529'>does not</font> require $X$ to be nonnegative here for the absolute value

#### Proof 

Consider the nonnegative r.v. $(X-\mu)^2$ and apply the Markov inequality, we have
$$
P((X-\mu)^2\geq c^2) \leq\frac{E[(X-\mu)^2]}{c^2} = \frac{\sigma^2}{c^2}
$$
while for the term $(X-\mu)^2 \geq c^2$, it is identical to $|X-\mu| \geq c$​​ . 

$E[(X- \mu)^2]$ is the definition for variance

Hence we have proved

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

* <font color = '#e65529'>sample mean $M_n$</font> is the mean of the sample you choose from the sample space (which could be only a part of them)

* <font color = '#e65529'>true mean $\mu$</font> is the mean of the whole sample space

### Weak law of large number

consider a sequence $X_1,X_2,\cdots$ of r.v. with **mean $\mu$** and **variance $\sigma^2$** , the sample mean is $M_n = \frac{X_1+\cdots+X_n}{n}$ while the true mean is $\mu$, we have

$$
E[M_n] = \frac{E[X_1]+\cdots+E[X_n]}{n} = \frac{n\mu}{n} = \mu
$$

$$
var(M_n) = \frac{var(X_1+\cdots+X_n)}{n^2} \\ 
 = \frac{var(X_1)+\cdots+var(X_n)}{n^2}\\
  = \frac{n\sigma^2}{n^2}\\
  =\frac{\sigma^2}{n}
$$

By applying the <font color = '#e65529'>Chebyshev inequality</font> and substituting $X = M_{n}$, $\sigma^{2} = var(M_{n}) = \frac{\sigma^2}{n}$ into the formula we have
$$
P(|M_n - \mu|\geq \epsilon) \leq\frac{\sigma^2}{n\epsilon^{2}} \ \ for \ \ any \ \ \epsilon > 0
$$
For any fixed $\epsilon > 0$, the right hand side of this inequality goes to 0 as $n$ increases.

### Rigorous definition

Let $X_1,X_2,\cdots$ be <font color = '#e65529'>independent identically distributed</font> r.v. with mean $\mu$, then for any $\epsilon > 0$ we have
$$
P(|M_n - \mu|\geq \epsilon) \rightarrow 0, \ \ as \ \ n \rightarrow \infty
$$

### Interpretation

The weak law of large numbers states that for large $n$, the <font color = '#e65529'>main part</font> of the distribution of $M_n$ is <font color = '#e65529'>concentrated</font> near $\mu$

If we consider a positive length interval $[\mu-\epsilon,\mu + \epsilon]$ around $\mu$, then there is <font color = '#e65529'>high probabilities</font> that $M_n$ will fall in that interval.

As $n\rightarrow \infty$, the probability <font color = '#e65529'>converge to 1</font>. If $\epsilon$ is really small, we need to wait longer to see that $M_n$ fall in that interval.

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

The central limit theorem can be adapted widely because it has <font color = '#e65529'>no requirement</font> on the distribution of the $X_i$ , which could be discrete, continuous or mixed

It only requires the distribution of $X_{i}$ to be <font color = '#e65529'>independence</font>, and both <font color = '#e65529'>mean and variance are finite</font>, instead of the detailed probabilistic model

### Approximation on CLT

The theorem CLT indicateds that <font color = '#e65529'>the sum of a large number of independent r.v. is approximately normal</font> it allows the calculation by referring to the normal CDF, which is equaivalent to treating $S_n$ as a n.v. with mean $n\mu$ and variance $n \sigma^2$​ 

#### methodology

Let $S_{n} = X_{1}+\cdots+X_{n}$, where the $X_{i}$ are <font color = '#e65529'>i.i.d</font> r.v. with mean $\mu$ and variance $\sigma^{2}$. If $n$ is large, the probability $P(S_{n} \leq c)$ can be approximated by treating $S_{n}$ as if it were normal, according to the following procedure

1. Calculate the mean $n\mu$ and variance $n\sigma^2$ 
2. By transforming $S_{n}$ into <font color = '#e65529'>standard normal</font>, we have

$$
P(S_{n} \leq c) = P(\frac{S_{n}-n\mu}{\sigma\sqrt{n}} \leq \frac{c-n\mu}{\sigma \sqrt{n}}) 
$$

3. In the case where $c$ is given in the problem, we can calculate the value of the term, let's say $z$, where $z = \frac{c-n\mu}{\sigma\sqrt{n}}$ 
4. By <font color = '#e65529'>checking the table</font> of standard normal, we can find out the probability where $P(\frac{S_{n}-n\mu}{\sigma \sqrt{n}} < z)$ which hold the same result as $P(S_{n} \leq c)$ 

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

which means that this probabilities <font color = '#e65529'>can be positive</font> and there may <font color = '#e65529'>exist once</font> in a while greater than $\mu$ 

#### Strong law 

 $M_n$ converges to $\mu$ with a probability of 1, this implies that for any given $\epsilon > 0$, the probability that the difference $|M_{n}-\mu|$ will exceed $\epsilon$ an <font color = '#e65529'>infinite</font> number of times is equal to 0

#### e.g.

Consider an event $A$ defined in terms of some probabilistic experiment. Consider a sequence of independent repetitions of the same experiment. Let $M_{n}$ be the fraction of the first $n$ repetitions in which $A$ occurs.

**The strong law of large numbers:** $M_{n}$ converges to $\mu$, with probability $1$ 
$$
P(\lim_{n\rightarrow \infty}M_{n} = \mu) = 1
$$
**The weak law of large numbers:**  $M_{n}$ converges to $P(A)$ in probability
$$
\forall \epsilon > 0, P(|M_{n}-\mu|\geq \epsilon)\rightarrow 0, as \ n \rightarrow \infty
$$

### Convergence with probability 1

To demonstrate the difference between the strong law and weak law, the example above give a hint about the new convergence concept <font color = '#e65529'>convergence with probability 1</font> and <font color = '#e65529'>convergence in probability</font>. We will talk a little more here

#### Definition1

Let $Y_{1}, Y_{2},\cdots$ be a sequence of r.v.(not necessarily independent). Let $c$ be a real number. We say that <font color = '#e65529'>$Y_{n}$ converges to $c$ with probability 1</font> (or almost surely) if
$$
P(\lim_{n\rightarrow \infty}Y_{n} = c) = 1
$$
All of the probability is <font color = '#e65529'>concentrated</font> on those sequences that converge to $c$, this <font color = '#e65529'>does not</font> mean that other sequences are impossible, only that their total probability is zero

#### Definition2(from gpt)

A sequence of r.v. $X_{n}$ <font color = '#e65529'>converges in probability</font> to $X$ if for every $\epsilon > 0$, the probability that $X_{n}$ deviates from $X$ by more than $\epsilon$ goes to zero as n increase:
$$
\lim_{n\rightarrow \infty}P(|X_{n} - X| > \epsilon) = 0
$$

#### Difference

Convergence with probability 1 implies convergence in probability, but the <font color = '#e65529'>converse is not necessarily true</font>.

Convergence with probability 1 is <font color = '#e65529'>stronger and more strict</font> than converge in probability
