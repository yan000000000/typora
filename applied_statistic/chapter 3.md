# General random variable

## Continuous random variables and pdfs

### feature of continuous r.v.

* with a continuous range of possible values
* Finer-grained than discrete r.v.
* able to exploit powerful tools from calculus

### Definition

A random r.v. $X$ is called continuous if there is a function $f_X \geq 0$ , called the probability density function of $X$, or PDF, s.t.
$$
P(X \in B) = \int_{B}^{}f_X(x)dx
$$
for every subset $B \subseteq \R$ (we assume the integral is well-defined)

* compare to the discrete case, we replace summation by integral

> it is called density because PDF can be interpret as probability per unit area.
>
> PDF is only the function and the curve but the area represent the probabilities mass.
>
> By the way, area time density equal to mass, in this way you can know why they named it like this 细品

### Extension 

#### PDF and area

when $B = [a,b]$ we have
$$
P(a \leq X \leq b) = \int_{a}^{b}f_X(x)dx
$$
which is the **area under the graph of PDF** 

> PDF is only the curve line, while area stand for the probabilities

#### Total probabilities

the entire area under the graph is equal to 1
$$
\int_{-\infty}^{\infty}f_X(x)dx = P(-\infty \leq X \leq \infty) = 1
$$

#### Probabilities of point

$$
P(a\leq X \leq a) = \int_{a}^{a}f_X(x)dx = 0 
$$

so we have  $P(a \leq X \leq b) = P(a < X \leq b)= P(a \leq X < b)=P(a < X < b)$

#### Interpretation of PDF

 $f_X(x)$​ can be interpret as **probability mass per unit length**
$$
P([x,x+\delta]) = \int_{x}^{x+\delta}f_X(t)dt \approx f_X(x)\cdot \delta
$$
<img src="assets/IMG_1820.jpg" alt="IMG_1820" style="zoom:33%;" />

#### Large value

e.g. consider a r.v. $X$ with PDF
$$
f_X(x) = \begin{cases}\frac{1}{2\sqrt{x}} \ \ \ \ if \ \ 0 < x \leq 1  \\ 0 \ \ \ \ otherwise\end{cases}
$$
by integrating $\frac{1}{2\sqrt{x}}$ we can know this PDF satisfy total probabilities theorem, but consider the case when we have
$$
lim_{x\rightarrow 0^+}f_X(x) = lim_{x\rightarrow 0^+}\frac{1}{2\sqrt{x}} = \infty
$$
Therefore we come to the conclusion that a PDF can take arbitrarily large values

### Expectation

#### Definition

The expectation of a continuous r.v. $X$ is defined by 
$$
E[X] = \int_{-\infty}^{\infty}xf_X(x)dx
$$
the expectation can be interpret as the anticipated average value of $X$ in a large number of independdent repetitions of the experiment

### Functions of r.v.

For any real-valued function $g$, $Y = g(X)$ is also a r.v.

The expectation of $g(X)$ is 
$$
E[g(X)] = \sum_{-\infty}^{\infty}g(x)f_X(x)dx
$$

### Moments and variance

The $n^{th}$ moment of $X$ is defined by $E[X^n]$

the variance of $X$ is defined by
$$
var[X] = E[(X - E[X])^2]\\
= \int_{-\infty}^{\infty}(x-E[X])^2f_X(x)dx\\
= E[X^2] - 2E[X]^2+E[X]^2 \\
= E[X^2] - (E[X])^2
$$
If $Y = aX+b$, then
$$
E[Y] = E[aX+b] = aE[X]+b \\
var[Y] = var[aX+b] = a^2var[X]
$$

### Exponential

An exponential r.v. has PDF
$$
f_X(x) = \begin{cases}\lambda e^{-\lambda x} \ \ \ \ if  \ \ x \geq 0 \\
0 \ \ \ \ otherwise\end {cases}
$$
while $\lambda $ is positive and $f_X(0) = \lambda$

![IMG_9742F9447A24-1](assets/IMG_9742F9447A24-1.jpeg)

#### Verification of total probability theorem

$$
\int_{0}^{\infty}\lambda e^{-\lambda x} dx = -e^{-\lambda x}|_0^\infty = 1
$$

#### Tail of exponential

$$
P(X \geq a) = \int_{a}^{\infty} f_X(x)dx = \int_{a}^{\infty}\lambda e^{-\lambda x}dx = -e^{-\lambda x}|_a^\infty = e^{-\lambda a}
$$

#### Mean 

$$
E[X] = \frac{1}{n}
$$

##### proof

$$
E[X] = \int_{0}^{\infty}xf_X(x) dx \\= \int_{0}^{\infty}x\cdot \lambda e^{-\lambda x}dx \\ 
= -xe^{-\lambda x}|_0^\infty - \int_{0}^{\infty}-e^{-\lambda x}dx\\
=0 - \int_{0}^{\infty}e^{-\lambda x}dx \\
= -\frac{e^{-\lambda x}}{\lambda}|_0^\infty\\
= \frac{1}{\lambda}
$$

##### $E[X^2]$ 

$$
E[X^2] = \int_{0}^{\infty}x^2\lambda e^{-\lambda x}dx \\ 
 = -x^2e^{-\lambda x} |_0^\infty - \int_{0}^{\infty}-2xe^{-\lambda x}dx\\
 = 0+\int_{0}^{\infty}2xe^{-\lambda x}dx\\
 = \frac{2}{\lambda}E[X]\\
 =\frac{2}{\lambda^2}
$$

#### variance

$$
var[X] = E[X^2] - (E[X])^2 \\
 = \frac{2}{\lambda^2} - \frac{1}{\lambda^2}\\
 = \frac{1}{\lambda^2}
$$

## Cumulative Distribution Function

### Definition

The cumulative distribution function or CDF of a r.v. $X$ is
$$
F_X(x) = P(X \leq x)\\
= \begin{cases}\sum_{k\leq x}^{}p_X(k) \ \ \ \ discrete \\
\int_{-\infty}^{x}p_X(y)dy \ \ \ \ continuous\end{cases}
$$
The CDF $F_X(x)$ accumulates probabilities up to the value $x$

#### graph

* graph for discrete case

<img src="assets/IMG_6508DDDAE1CA-1.jpeg" alt="IMG_6508DDDAE1CA-1" style="zoom: 33%;" />

* graph for continuous case

<img src="assets/IMG_979F692275C0-1.jpeg" alt="IMG_979F692275C0-1" style="zoom:33%;" />

### Property

*  $F_X$ is monotonically increasing: if $x \leq y$, then $F_X(x)\leq F_X(y)$

* $lim_{x\rightarrow -\infty}F_X(x) = 0$  $lim_{x\rightarrow\infty}F_X(x) = 1$
* If $X$ is discrete, $F_X$ is piecewise constant
* If $X$ is continuous, $F_X$ is continuous and

$$
F_X(x) = \int_{-\infty}^{\infty}f_X(t)dt, \ \ \ \ f_X(x) = \frac{dF_X(x)}{dx}
$$

> CDF and PDF is the same relation of integral and differentiation

### E.g.

#### maximum of several r.v.

Take a test 3 times with score in {1,2,3,...,10}. The final score is the maximum of the scores which is $ X = max(X_1,X_2,X_3)$ 

Each $X_i$ takes values {1,2,3,...,10} equally likely and different $X_i$ are independent

##### CDF

the CDF of the final score $X$ is
$$
F_X(k) = P(X \leq k)\\
= P(X_1 \leq k)P(X_2 \leq k)P(X_3 \leq k)\\
=( \frac{k}{10})^3
$$

##### PMF

the PMF of the final score $X$​ is
$$
P_X(k) = F_X(k) - F_X(k-1) = (\frac{k}{10})^3 - (\frac{k-1}{10})^3
$$

#### Geometric and exponential

* CDF for geometric r.v.

$$
F_{geo}(n) = \sum_{k = 1}^{n}p(1-p)^{k-1} = p\frac{1-(1-p)^n}{1-(1-p)} = 1-(1-p)^n \ \ \ \ for \ \ n = 1,2,\cdots
$$

* CDF for exponential r.v.
  * while $x\geq 0$​
  
  $$
  F_{exp}(n) = \int_{0}^{x}\lambda e^{-\lambda t}dt = -e^{-\lambda t}|_0^x = 1 - e^{-\lambda t}
  $$
  
  
  
  * while $x\leq 0$​
  
  $$
  F_{exp}(n) = P(X \leq 0) = 0
  $$
  
  

From observation, we see that if $e^{-\lambda x} = 1-p$ , then $F_{exp}(n\delta) = F_{geo}(n)$

<img src="assets/IMG_F0EB6F284CE9-1.jpeg" alt="IMG_F0EB6F284CE9-1" style="zoom:33%;" />

## Normal random variable 正态分布

### Definition

A continuous random variable $X$ is normal, or Gaussian, if it has a PDF
$$
f_X(x) = \frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}}
$$
for some $\sigma > 0$

#### Verification of total probabilities

$$
\int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x -\mu)^2}{2\sigma^2}}dx = 1
$$

### Graph

<img src="assets/螢幕截圖 2024-04-06 上午10.50.04.png" alt="螢幕截圖 2024-04-06 上午10.50.04" style="zoom: 33%;" />

This is the graph of a normal PDF and CDF with $\mu = 1$ and $\sigma^2 = 1$ where $\mu$ stands for the mean and $\sigma^2$ stands for the variance. 

### Feature

* The normal PDF is symmetric around its mean $\mu$​ 
* as $x$ get further from $\mu$​ , the value decrease rapidly
*  $E[X] = \mu$ and $var(X) = \sigma^2$

### Mean and variance

Since the graph is symmetric around mean $\mu$ so the mean $E[X] = \mu$ 

for variance $var(X)$ we have $var(X) = \sigma^2$ 

#### proof

$$
var(X) = \int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi}\sigma}(x-\mu)^2e^{-\frac{(x-\mu)^2}{2\sigma^2}}dx\\
take \ \ y = \frac{x-\mu}{\sigma}, \ \ dx = \sigma  \ dy\\
=\int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi}\sigma}\sigma^2y^2e^{-\frac{y^2}{2}}\sigma  \ dy \\
= \frac{\sigma^2}{\sqrt{2\pi}}\int_{-\infty}^{\infty}y^2e^{-\frac{y^2}{2}}dy\\
=\frac{\sigma^2}{\sqrt{2\pi}}(y(-e^{-\frac{y^2}{2}})|_{-\infty}^{\infty} - (\int_{-\infty}^{\infty}-e^{-\frac{y^2}{2}})dy) \ \ integration \ \ by \ \ part\ \ taking \ \ u = y \ \ v = -e^{-\frac{y^2}{2}}\\
= \frac{\sigma^2}{\sqrt{2\pi}}\int_{-\infty}^{\infty}e^{-\frac{y^2}{2}}dy\\
=\sigma^2
$$

**having question with the last step and the first step why the variance should be calculated like that**

第一步中我们从方差的定义我们可以知道 $var(X) = E[(X-\mu)^2]$ ,则定义中的式子则是表示概率， $(X-\mu)^2$ 的部分则相当于 $x$ 

关于最后一步 $\int_{-\infty}^{\infty}e{-\frac{y^2}{2}}dy$ 的证明好像要用到二重积分，先暂且放一放

### Standard normal

#### Definition

The normal r.v. with 0 mean and unit variance (which is 1) is a standard normal. Its CDF is denoted by
$$
\phi(y) = P(Y \leq y) = \frac{1}{\sqrt{2\pi}}\int_{-\infty}^{y}e^{-\frac{t^2}{2}}dt
$$
by symmetry, it holds
$$
\phi(y) = 1 -\phi(-y)
$$

#### graph

<img src="assets/image-20240406135637569.png" alt="image-20240406135637569" style="zoom:33%;" />

#### Tabel of $\phi(x)$ for positive $x$

<img src="assets/螢幕截圖 2024-04-06 下午1.58.33.png" alt="螢幕截圖 2024-04-06 下午1.58.33" style="zoom:33%;" />

Remember: row first then column

#### transform into standard normal

Let $X$ be a normal r.v. with mean $\mu$ and variance $\sigma^2$ . Then we have
$$
Y = \frac{X - \mu}{\sigma}
$$
is also a normal which we can prove by
$$
E[Y] = E[\frac{X-\mu}{\sigma}] = \frac{E[X]-\mu}{\sigma} = 0 \\
var(Y) = var(\frac{X-\mu}{\sigma}) = \frac{var(X)}{\sigma^2} = 1
$$

> This fact allow us to calculate any normal r.v. by redefining the r.v. $X$ in terms of $Y$, then we can use the standard normal table

