# Further topic on r.v.

## Covariance and Correlation

### Intro

the measurement of the strength and direction of the relation between 2 r.v.

### Covariance

#### Definition

The covariance of 2 r.v. $X$ and $Y$ are defined as
$$
cov(X,Y) = E[(X-E[X])(Y-E[Y])]
$$
or alternatively
$$
cov(X,Y) = E[XY] - E[X]E[Y]
$$

##### proof

$$
cov(X,Y) = E[XY - XE[Y] - YE[X]+E[X]E[Y]] \\
=E[XY] - E[XE[Y]]-E[YE[X]]+E[E[X]E[Y]] \\
$$

in this step, we can view $E[X]$ in the $E[YE[X]]$ as a pre-calculated constant, same with $Y$ . So we can take it out of the me
$$
 = E[XY] - E[Y]E[X] - E[X]E[Y]+E[X]E[Y]\\
 = E[XY] - E[X]E[Y]
$$
**the proof need verified**

#### Properties

* independent r.v. are uncorrelated, so we have

$$
cov(X,Y) = E[XY] - E[X]E[Y] = 0
$$

* notice that vice versa(which is $cov(X,Y)$ mean 2 two r.v. is independent) is not correct

* For any r.v. $X,Y,Z$ and any scalars $a$ and $b$ 

$$
cov(X,X) = var(X)
$$

$$
cov(X,aY+b) = a\cdot cov(X,Y)
$$

$$
cov(X,Y+Z) = cov(X,Y) + cov(X,Z)
$$

### Correlation coefficient

#### Definition

For any r.v. $X,Y$ with nonzero variances, the correlation coefficient $\rho(X,Y)$ of them is defined as
$$
\rho(X,Y) = \frac{cov(X,Y)}{\sqrt{var(X)var(Y)}}
$$


it is easily verified that we have $-1\leq\rho(X<Y)\leq 1$​

* it may be viewed as the normalized version of covariance $cov(X,Y)$ 
  * because it may not be affected by the change of the value change of $X,Y$ 

#### Properties

*  $\rho(X,Y) = 1 $ if there exist a positive number $c$ s.t.

$$
X - E[X] = c(Y-E[Y])
$$

*  $\rho(X,Y) = -1 $ if there exist a negative number $c$ s.t.

$$
X - E[X] = c(Y-E[Y])
$$

* If $\rho(X,Y) > 0$, then the values of $X-E[X]$ and $Y - E[Y]$​ "tend" to have the same sign
* If $\rho(X,Y) < 0$, then the values of $X-E[X]$ and $Y - E[Y]$ "tend" to have the opposite sign

### Variance of summations

#### Intro

In general, we have $var(X_1+X_2)\neq var(X_1)+var(X_2)$ , here we have a more precise statement
$$
var(X_1+X_2) = var(X_1)+var(X_2)+2cov(X_1,X_2)
$$
* If 2 r.v. are independent, we have $cov(X_1,X_2) = 0$ so the phrase $var(X_1+X_2) = var(X_1)+var(X_2)$ also stands 

For a general case, let $X_1,X_2,\cdots,X_n$ be r.v. with finite variance, then we have
$$
var(\sum_{i}^{}X_i) = \sum_{i}^{}var(X_i)+\sum_{i\neq j}^{}cov(X_i,X_j)
$$

## Conditional Expectation and variance revisited

