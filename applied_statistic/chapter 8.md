# Classical Statistical Inference

## Comparison

### Before

On Bayesian inference, we have following features.

*  Unknown <font color = '#e65529'>parameters</font> are modeled as random variables
*  Work within a single, fully-specified probabilistic <font color = '#e65529'>model</font> <font color = '#3e9e02'>说实话还不是很明白这里</font>

*  Compute posterior distribution by application of Bayes' rule

### This chapter

* View the unknown parameter $\theta$ as a <font color = '#e65529'>deterministic</font> (not random) but unknown quantity.
* The observation $X$ is random and its distribution depends on the value of $\theta$ 
  *  $p_{X}(x;\theta)$ if $X$ is discrete
  *  $f_{X}(x;\theta)$ if $X$ is continuous

> [!note] 
>
> 这里两者的区别在于贝叶斯统计推断把未知参数(parameter)看成是<font color = '#e65529'>随机变量</font>，利用贝叶斯公式进行统计推断。 而经典统计推断则认为未知参数 $\theta$ 是<font color = '#e65529'>确定的</font>， 但取值未知，观测 $X$ 是随机的

At the same time, we also have other features

* Deal <font color = '#e65529'>simultaneously</font> with multiple candidate models, one model for each possible value of $\theta$ 

* A "good" hypothesis testing or estimation procedure will be one that possesses certain desirable properties under <font color = '#e65529'>every</font> candidate model(for every possible value of $\theta$ )

### Notation

Indicating the dependence of probabilities and expected values on $\theta$ , we denote 

* $E_{\theta}[h(X)]$ of the expected value of a random variable $h(X)$ as <font color = '#e65529'>a function of $\theta$​</font> 
* $P_{\theta}(A)$ to denote the probability of an event $A$

> [!note]
>
> 这里的 $\theta$ 只是表示期望和概率与 $\theta$ 有关系，而不是随机变量

## Classical Parameter Estimation

### Definition

* Given observations $X = (X_{1}, X_{2},\cdots,X_{n})$ an <font color = '#e65529'>estimator</font> is a random variable of the form $\hat{\Theta} = g(X)$ for some function $g$ 

*  $\hat{\Theta}$ depends on the distribution of $\theta$ as well. 

* We use the term <font color = '#e65529'>estimate</font> to refer to an actual realized value of $\hat{\Theta}$ 
* When we are interested in the role of <font color = '#e65529'>the number of observations $n$</font>, we use the notation $\hat{\Theta}_{n}$ for an estimator. Or in another understanding, we can view $\hat{\Theta}_{n}$ as a <font color = '#e65529'>sequence</font> of estimators. 

> [!note]
>
> 这里的n实时对应样本量，而当样本量变多或变少时，这个estimator也会发生变化，所以说像一个序列，由这个n来决定第n项的值

* Because $\hat{\Theta}_{n}$ is also a r.v., so we have its mean and variance respectively. They are denoted as $E_{\theta}[\hat{\Theta}_{n}]$ and $var_{\theta}[\hat{\Theta}_{n}]$. (Sometime the small $\theta$ can be ommited when the context is clear)

### Clarify

* <font color = '#e65529'>Estimator:</font> $\hat{\Theta}_{n}$ a function of $n$ observations for an $(X_{1},X_{2},\cdots,X_{n})$ whose distribution depends on $\theta$

* <font color = '#e65529'>Estimation error:</font> $\tilde{\Theta}_{n} = \hat{\Theta}_{n} - \theta$ (this is a r.v. as well)

* <font color = '#e65529'>Bias of the estimator(偏差):</font>$b_{\theta}(\hat{\Theta}_{n}) = E_{\theta}[\hat{\Theta}_{n}-\theta] = E_{\theta}[\hat{\Theta}_{n}]-\theta$ (the mean of a constant is the constant itself)

### Property

#### Bias

*  $\hat{\Theta}_{n}$ is <font color = '#e65529'>unbiased</font> if $b_{\theta}(\hat{\Theta}_n) = 0$ 
*  $\hat{\Theta}_{n}$ is <font color = '#e65529'>asymptotically unbiased</font> if $\lim_{n\rightarrow \infty} E_{\theta}[\hat{\Theta}_{n}] = 0$ which means $\hat{\Theta}_{n}$ become desirable when the number $n$ of observations increase and when $n$​ is large enough

#### Consistent


*  $\hat{\Theta}_{n}$ is <font color = '#e65529'>consistent</font> if the sequence $\hat{\Theta}_{n}$ converges to the true value $\theta$ , in probability, for every possible value of $\theta$ 

Recall that we have

*  $X_{n}$ converges to $a$ <font color = '#e65529'>in probability</font> if $\forall \epsilon > 0, P(|X_{n} - a| \geq \epsilon)\rightarrow 0$, as $n\rightarrow \infty$ 
*  $X_{n}$ converges to $a$ <font color = '#e65529'>with probability 1</font> (or almost surely) if $p(\lim_{x\rightarrow \infty}X_{n} = a) = 1$ 

#### Mean squared error

From the formula $E[X^2] = (E[X])^{2}+var(X)$, and $X = \tilde{\Theta}_n - \theta$ , we have
$$
E_{\theta}[\tilde{\Theta}_{n}^2] = b_{\theta}^{2}[\hat{\Theta}_{n}]+var_{\theta}[\hat{\Theta}_{n}]
$$
This formula inform that there can be a <font color = '#e65529'>tradeoff</font> between the two terms on the right-hand side. By fixing $E_{\theta}[\tilde{\Theta}_{n}^{2}]$, A reduction in the variance is accompanied by an increase in the bias.

### Maximum Likelihood Estimation(最大似然估计)

Let the vector of <font color = '#e65529'>observations</font> $X = (X_{1},\cdots,X_{n})$ be described by a <font color = '#e65529'>joint PMF</font> $p_{X}(x;\theta)$ . Note that, $p_{X}(x;\theta)$ is PMF for $X$ only,  recall that $\theta$ here is only a constant and $p_{X}(x;\theta)$ depend on $\theta$ 

Suppose we observe a particular value $x = (x_{1},\cdots,x_{n})$ of $X$. A <font color = '#e65529'>Maximum likelihood Estimation</font> is a value of the parameter $\theta$ that maximizes the numerical function $p_{X}(x_{1},\cdots, x_{n};\theta)$ over all $\theta$ 
$$
\hat{\theta}_{n} = argmax \ p_{X}(x_{1},\cdots,x_{n};\theta) \ \ \ \ or \\
\hat{\theta}_{n} = argmax \ f_{X}(x_{1},\cdots,x_{n};\theta)\\
$$
Generally, the observations $X_{i}$ are assumed to be <font color = '#e65529'>independent</font>, then we have
$$
p_{X}(x_{1},\cdots,x_{n};\theta) = \Pi_{i = 1}^{n}p_{X_{i}}(x_{i};\theta)
$$

> [!caution]
>
> $p_{X}(x;\theta)$ is <font color = '#e65529'>not</font> the probability that the unknown parameter is equal to $\theta$
>
> It <font color = '#e65529'>is</font> the probability that the observed value $x$ can arise when the parameter is equal to $\theta$ <font color = '#3e9e02'>这里还不是很明白</font>

To be convenient in calculation, we often use logarithm to calculate, called the <font color = '#e65529'>log-likelihood function</font>
$$
log \ p_{X}(x_{1},\cdots, x_{n};\theta) = \sum_{i=1}^{n}log \ p_{Xi}(x_{i};\theta)
$$

### Summary

总结最大似然估计方法找estimate/estimator

1. 首先我们列出我们的likelihood function
2. 两边取对数来方便计算，通常为ln
3. 最后求导令导数为0来求 $\theta$ 最大值

### 例题

Customers arrive to a facility, with the its customer arriving at time $Y_{i}$.

We assume that the ith interarrival time is $X_{i}= Y_{i}-Y_{i-1}$ is exponentially distributed with parameter $\theta$ ( $Y_{0}=0$)

Assume that $X_{1},\cdots,X_{n}$ are independent

We wish to <font color = '#e65529'>estimate the value of $\theta$</font> (interpreted as the arrival rate), <font color = '#e65529'>on the basis of the observations</font> $X_{1},\cdots,X_{n}$ ​

------

Solution:

1. First we list the likelihood function, <font color = '#e65529'>notice that we set the $\theta$ as the parameter in the function instead of the variable</font>.(Hence here we replace $\lambda$ with $\theta$ 

   The corresponding likelihood function is
   $$
   f_{X}(x;\theta) = \Pi_{i=1}^{n}f_{X_{i}}(x_{i};\theta) = \Pi_{i=1}^n \theta e^{-\theta x_{i}}
   $$

   > [!note]
   >
   > recall that the $f_{X}(x;\theta)$ is a joint PDF related to the value of $\theta$. Given that they are independent, so that we can multiply them all together. 

2. We take log on both sides
   $$
   ln \ f_{X}(x;\theta) = ln \ \Pi_{i = 0}^{n}\theta e^{-\theta x_{i}}\\
   = \Pi_{i = 0}^{n}ln(\theta e^{-\theta x_{i}})\\
   =nlog\theta - \theta \sum_{i=1}^{n}x_{i}\\
   =nlog\theta - \theta y_{n}
   $$
   here we have $y_{n} = \sum_{i=1}^{n}x_{i}$ 

   <font color = '#3e9e02'>不懂那个n怎么来的</font>

3. We take derivative and set it to 0. <font color = '#e65529'>Here we take derivative with respect to the parameter</font>
   $$
   \frac{d}{d\theta} \ nlog\theta - \theta y_{n} = 0\\
   \frac{n}{\theta} - y_{n} = 0
   $$
   Hence we derive $\hat{\theta} = \frac{n}{y_{n}}$ (<font color = '#e65529'>estimate</font>)

   and $\hat{\Theta} = (\frac{\sum_{i=1}^{n}x_{i}}{n})^{-1}$ 
