## Basic concepts

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

## Probability mass function

### Probability mass function

#### Definition

For a discrete random variable $X$, the probability mass function(PMF) of $X$ captures the probabilities of the values that it can take

#### Notation

if $x$ is any possible value of $X$, the probability mass of $x$ , denoted $p_X(x)$, is the probability of the event $\{X = x\}$ consisting of all outcomes that 