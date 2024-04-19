### prove 1

first we define $Z_{i}$ as the standardized form of $X_{i}$
$$
Z_{i} = \cfrac{X_{i}-\mu}{\sigma}
$$
We have $Z_{i}$ as standard normal and $X_{i}$ are normal. For sample variance, we have
$$
S^{2} = \frac{1}{n-1}\sum_{i=1}^{n}(X_{i}-\bar{X})^{2}
$$
Denote $\bar{Z} = \frac{1}{n}\sum_{i=1}^{n}Z_{i}$, substitute (23) into $X_{i}-\bar{X}$, we have
$$
X_{i}-\bar{X}=\sigma(Z_{i}-\bar{Z})
$$
Then we have 
$$
S^2 = \frac{\sigma^2}{n-1}\sum_{i=1}^{n}(Z_{i}-\bar{Z})^2\\
$$
for  $\sum_{i=1}^{n}(Z_{i}-\bar{Z})^{{2}}$ we have
$$
\sum_{i=1}^{n}(Z_{i}-\bar{Z})^2 = \sum_{i=1}^{n}(Z_{i}^{2}-2Z_{i}\bar{Z}+\bar{Z}^{2})\\
=\sum_{i=1}^{n}Z_{i}^{2}-2\bar{Z}\sum_{i=1}^{n}Z_{i}+n\bar{Z}^{2}\\
$$
note that $\bar{Z}$ can be treated as a constant and $\sum_{i=1}^{n}Z_{i} = n\bar{Z}$ , so we have
$$
=\sum_{i = 1}^{n}Z_{i}^{2}-2n\bar{Z}^{2}+n\bar{Z}^{2}\\
=\sum_{i=1}^{n}Z_{i}^{2}-n\bar{Z}^{2}
$$
Substitute $\sum_{i = 1}^{n}(Z_{i}-\bar{Z})^{{2}}=\sum_{i=1}^{n}Z_{i}^{{2}}-n\bar{Z}^{{2}}$ into original formula, we have
$$
S^{2} = \frac{\sigma^{2}}{n-1}(\sum_{i=1}^{n}Z_{i}^{2}-n\bar{Z}^{2})\\
\frac{(n-1)S^{2}}{\sigma^{2}} = \sum_{i=1}^{n}Z_{i}^{2}-n\bar{Z}^{2}
$$
We know that by definition, $\frac{X_{i}-\mu}{\sigma}\sim N(0,1), \frac{\bar{X}-\mu}{\frac{\sigma}{\sqrt{n}}}\sim N(0,1)$  Hence we have
$$
\frac{(n-1)S^{2}}{\sigma^{2}} = \sum_{i=1}^{n}\frac{(X_{i}-\mu)^{2}}{\sigma^{2}}-n\frac{(\bar{X}-\mu)^{2}}{\sigma^{2}}\\
=\sum_{i=1}^{n}\frac{(X_{i}-\mu)^{2}}{\sigma^{2}}-\frac{(\bar{X}-\mu)^{2}}{\frac{\sigma^{2}}{n}}
$$
let $\sum_{i=1}^{n}\frac{(X_{i}-\mu)^{2}}{\sigma^{2}}$ be $Y_{1}$, $-\frac{(\bar{X}-\mu)^{2}} {\frac{\sigma^{2}}{n}}$ be $Y_{{2}}$​. From the property we know that
$$
Y_{1}+Y_{2} \sim\chi^{2}(n_{1}+n_{2}) =\chi^2(n+(-1))=\chi^{2}(n-1)
$$


 Hence we prove  $\frac{(n-1)S^{2}}{\sigma^{2}}\sim\chi^{{2}}(n-1)$ 