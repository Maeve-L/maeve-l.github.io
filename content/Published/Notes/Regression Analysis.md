## Linear Statistical Models

### OLS

We shall minimize $Q$ with respect to $\beta_0$ and $\beta_1$ by taking the partial derivatives and setting them to 0. We have

$$\frac{\partial Q}{\partial \beta_{0}}=-2 \sum_{i=1}^{n}\left(y_{i}-\beta_{0}-\beta_{1} x_{i}\right) =0 $$

$$ \frac{\partial Q}{\partial \beta_{1}}=-2\sum_{i=1}^{n}\left(y_{i}-\beta_{0}-\beta_{1} x_{i}\right) x_{i}=0$$

Normal Equation

$$\begin{aligned}\beta_{0} n+\beta_{1} \sum_{i=1}^{n} x_{i} &=\sum_{i=1}^{n} y_{i} \\\beta_{0} \sum_{i=1}^{n} x_{i}+\beta_{1} \sum_{i=1}^{n} x_{i}^{2} &=\sum_{i=1}^{n} x_{i} y_{i} .\end{aligned}$$

### Simple Linear Regression

$$E(Y |x_1, . . . , x_k) = \beta_0 + \beta_1x_1 + . . . + \beta_kx_k. $$

$$Y=\beta_0+\beta_1x+\varepsilon,\varepsilon\sim N(0,\sigma^2)$$

Assumptions:

-   Normality. For $i = 1, . . . , n,$ the conditional distribution of $Y_i$ given the values $x_1, . . . , x_n$ is a normal distribution.

-   Linear Mean. There are parameters $\beta_0$ and $\beta_1$ such that the conditional mean of $Y_i$

given the values $x_1, . . . , x_n$ has the form $\beta_0 + \beta_1x_i$ for $i = 1, . . . , n$.

-   Common Variance. There is a parameter $\sigma^2$ such that the conditional variance of $Y_i$ given the values $x_1, . . . , x_n$ is $\sigma^2$ for $i = 1, . . . , n.$ This assumption is often called **homoscedasticity**. Random variables with different variances are called **heteroscedastic**.
    -   The error term is homoskedastic if the variance of the conditional distribution of $\varepsilon_i$ given $X_i$ is constant for $i = 1,\cdots, n$ and in particular does not depend on $X_i$. Otherwise, the error term is heteroskedastic.
-   Independence. The random variables $Y_1, . . . , Y_n$ are independent given the observed $x_1, . . . , x_n$.
-   Predictor is known.

We can now find the M.L.E.

#### M.L.E. of Estimators

$$\hat{\beta}_{1}=\frac{\sum_{i=1}^{n} x_{i} Y_{i}-n \bar{x}_{n} \bar{Y}_{n}}{\sum_{i=1}^{n} x_{i}^{2}-n \bar{x}_{n}^{2}}=\frac{\sum_{i=1}^{n}\left(x_{i}-\bar{x}_{n}\right)\left(Y_{i}-\bar{Y}_{n}\right)}{\sum_{i=1}^{n}\left(x_{i}-\bar{x}_{n}\right)^{2}}$$

$$

\hat{\beta}_{0}=\bar{Y}_{n}-\hat{\beta}_{1} \bar{x}_{n}$$

Let us introduce the symbol

$$

s_{x}=\left(\sum_{i=1}^{n}\left(x_{i}-\bar{x}\right)^{2}\right)^{1 / 2}$$

Thus

$$
\operatorname{E}[\hat\beta_1]=\beta_1,\operatorname{E}[\hat\beta_0]=\beta_0
$$

$$
\operatorname{Var}\left(\hat{\beta}_{1}\right)=\frac{\sum_{i=1}^{n}\left(x_{i}-\bar{x}\right)^{2} \operatorname{Var}\left(Y_{i}\right)}{s_{x}^{4}}=\frac{\sigma^{2}}{s_{x}^{2}}
$$

$$
  
\begin{aligned} \operatorname{Var}(\hat{\beta_{0}})&=\operatorname{Var}(\bar{Y}-\hat{\beta_{1}} \bar{x})\\&=\operatorname{Var}(\bar{Y})+\bar{x}^{2}-2 \bar{x} \operatorname{Cov}(\bar{Y}, \hat{\beta_{1}})\\&=\frac{\sigma^{2}}{n}+\frac{\sigma^{2}}{s_{x}^{2}} \bar{{x}}^{2}-0 \\&=\left(\frac{1}{n}+\frac{\bar{x}^{2}}{s_{x}^{2}}\right) \sigma^{2} \end{aligned}
$$


$$
\begin{aligned} \operatorname{Cov}(\hat{\beta_{0}},\hat{\beta_{1}})&=\operatorname{Cov}(\bar{Y}-\hat{\beta_{1}} \bar{x},\hat{\beta_{1}})\\&=\operatorname{Cov}(\bar{Y}, \hat{\beta_{1}})-\bar{x} \operatorname{Cov}(\hat{\beta_{1}}, \hat{\beta_{1}})\\&=-\bar{x} \operatorname{Var}(\bar{\beta_{1}}) \\&=-\frac{\bar{x} \sigma^{2}}{s_{x}^{2}}\end{aligned}
$$

So we can calculate the expectations and variances of the linear combinations of $\beta_0$ and $\beta_1$.

#### M.S.E. of Prediction

$$
\begin{aligned}E\left[(\hat{Y}-Y)^{2}\right] &=E\left\{[(\hat{Y}-\mu)-(Y-\mu)]^{2}\right\} \\&=\operatorname{Var}(\hat{Y})+\operatorname{Var}(Y)-2 \operatorname{Cov}(\hat{Y}, Y)\\&=\sigma^{2}\left[1+\frac{1}{n}+\frac{(x-\bar{x})^{2}}{s_{x}^{2}}\right]\end{aligned}
$$

#### M.L.E. for $\sigma^2$

$$
\hat \sigma^2=\frac{1}{n}\sum_{i=1}^n\left[Y_i-(\hat\beta_0+\hat\beta_1x_i)\right]^2
$$

The distribution of $n\hat\sigma^2/\sigma^2$ is the $\chi^2$ distribution with $n-2$ degrees of freedom.

### Statistical Inference in Simple Linear Regression

#### Unbiased Estimator of $\sigma^2$

$$ 
\sigma^{\prime}=\left(\frac{S^{2}}{n-2}\right)^{1 / 2}, \text{where}\ \ S^{2}=\sum_{i=1}^{n}\left(Y_{i}-\hat{\beta}_{0}-\hat{\beta}_{1} x_{i}\right)^{2}
$$

Note that it is different from the M.L.E.

#### Linear Combination of $\beta_0$ and $\beta_1$

$$
\left[\frac{c_{0}^{2}}{n}+\frac{\left(c_{0} \bar{x}-c_{1}\right)^{2}}{s_{x}^{2}}\right]^{-1 / 2} \frac{c_{0} \hat{\beta}_{0}+c_{1} \hat{\beta}_{1}-\left(c_{0} \beta_{0}+c_{1} \beta_{1}\right)}{\sigma^{\prime}}
$$

has the $t$ distribution with $n-2$ degrees of freedom under the assumptions of simple linear regression.

We can use this random variable to test hypotheses about or to construct confidence intervals.

Plug $\sigma^{\prime}$ into $\operatorname{Var}\left(\hat{\beta}{1}\right)=\frac{\sigma^{2}}{s_{x}^{2}}$ and get the equation.

#### Confidence Intervals

The open interval is a coefficient $1-\alpha_0$ confidence interval for $c_0\beta_0+c_1\beta_1$.

$$c_{0} \hat{\beta}_{0}+c_{1} \hat{\beta}_{1} \pm \sigma^{\prime}\left[\frac{c_{0}^{2}}{n}+\frac{\left(c_{0} \bar{x}-c_{1}\right)^{2}}{s_{x}^{2}}\right]^{1 / 2} T_{n-2}^{-1}\left(1-\frac{\alpha_{0}}{2}\right)$$

#### Prediction Interval

$$\hat{Y} \pm T_{n-2}^{-1}\left(1-\frac{\alpha_{0}}{2}\right) \sigma^{\prime}\left[1+\frac{1}{n}+\frac{(x-\bar{x})^{2}}{s_{x}^{2}}\right]^{1 / 2}$$

#### Coefficient of Determination

$$R^2=1-\frac{SSE}{SST}=1-\frac{\sum_{i=1}^{n}\left(y_{i}-\hat{y}_{i}\right)^{2}}{\sum\left(y_{i}-\bar{y}_{n}\right)^{2}}$$

## Multiple Linear Regression

Design Matrix $\mathbf{X}$

$$\mathbf{X}=\left[\begin{array}{ccc}x_{10} & \cdots & x_{1 p-1} \\x_{20} & \cdots & x_{2 p-1} \\\vdots & \ddots & \vdots \\x_{n} 0 & \cdots & x_{n p-1}\end{array}\right]$$

$$ \mathbf{Y}_{n \times 1}=\mathbf{X}_{n \times r} \boldsymbol{\beta}_{(k+1) \times 1}+\varepsilon_{n \times 1}$$

### Mean Vector and Covariance Matrix

$$

\varepsilon_{i} \sim N\left(0, \sigma_{i}^{2}\right), \quad E(\varepsilon)=\mathbf{0}, \quad \operatorname{Cov}(\mathbf{Y})=\operatorname{Cov}(\varepsilon)=\sigma^{2} \mathbf{I}$$

The coordinates $Y_1, . . . , Y_n$ of $\mathbf{Y}$ are independent.

### The Joint Distribution of the Estimators

$$

\widehat{\boldsymbol{\beta}}=\left(\mathbf{X}^{\prime} \mathbf{X}\right)^{-1} \mathbf{X}^{\prime} \mathbf{Y},\quad\widehat{\boldsymbol{\beta}} \sim N_{r}\left(\boldsymbol{\beta}, \sigma^{2}\left(\mathbf{X}^{\prime} \mathbf{X}\right)^{-1}\right)$$

$$

\operatorname{Var}(\widehat{\boldsymbol{\beta}})=\sigma^{2}\left(\mathbf{X}^{\prime} \mathbf{X}\right)^{-1}=\sigma^{2}\left(\xi_{i j}\right)_{i, j=0, \cdots, k}$$

### Testing Hypotheses

$$
{{\sigma}^{\prime}}^{2}=\frac{\widehat{\varepsilon}^{\prime} \widehat{\varepsilon}}{n-k-1},\quad \frac{(n-k-1){{\sigma}^{\prime}}^{2}}{\sigma^2}\sim\chi^2(n-k-1) 
$$

$$ \frac{\hat\beta_j-\beta_j^{\star}}{\sqrt{\xi_{jj}}{{\sigma}^{\prime}}^{2}}\sim t(n-k-1)
$$

### Prediction

$$
\hat{\mathbf{Y}}=\mathbf{x}^{\prime}\left(\mathbf{X}^{\prime} \mathbf{X}\right)^{-1} \mathbf{X}^{\prime} \mathbf{Y}
$$

$$
Var(\hat{\mathbf{Y}})=\mathbf{x}^{\prime}\left(\mathbf{X}^{\prime}\mathbf{X}\right)^{-1}\mathbf{x}\sigma^2
$$

$$
\frac{Y-\hat{Y}}{\sigma^{\prime}\left[1+z^{\prime}\left(Z^{\prime} Z\right)^{-1} z\right]^{1 / 2}}\sim t(n-k-1)
$$

### Multiple R Squared

$$R^{2}=1-\frac{\sum_{i=1}^{n}\left(y_{i}-\hat{y}_{i}\right)^{2}}{\sum_{i=1}^{n}\left(y_{i}-\bar{y}\right)^{2}}$$

$$adj\ R^2=1-\frac{\hat\sigma^2}{\text {SST}/n-1}=1-\frac{(1-R^2)(n-1)}{n-k-1}$$

### Tests of Joint Hypotheses

Test for an overall significant relationship between the response variable and all of the explanatory variables.

#### F Test

$$F=\frac{1}{2}\left(\frac{t_{1}^{2}+t_{2}^{2}-2 \hat{\rho}_{t_{1}, t_{2}} t_{1} t_{2}}{1-\hat{\rho}_{t_{1}, t_{2}}^{2}}\right)$$

The homoskedasticity-only F-statistic

$$F =\frac{(SSR_{restricted} - SSR_{unrestricted})/q}{SSR_{unrestricted}/(n - k_{unrestricted} - 1)}$$

$$F =\frac{(R_{unrestricted}^2 - R_{restricted}^2)/q}{(1 - R_{unrestricted}^2)(n -k_{unrestricted} - 1)} $$

## ANOVA

ANOVA permits comparisons of multiple populations and even subgroups.

### One-way ANOVA

The design matrix has a special form:

$$\boldsymbol{Z}=\left[\begin{array}{cccc}1 & 0 & 0 & 0 \\& \vdots & & \\1 & 0 & 0 & 0 \\0 & 1 & 0 & 0 \\& \vdots & & \\0 & 1 & 0 & 0 \\0 & 0 & 1 & 0 \\& \vdots & & \\0 & 0 & 1 & 0 \\0 & 0 & 0 & 1 \\& \vdots & & \\0 & 0 & 0 & 1\end{array}\right]$$

#### Partitioning a Sum of Squares

$$ S_{\mathrm{Tot}}^{2}=S_{\mathrm{Resid}}^{2}+S_{\mathrm{Betw}}^{2}

$$

$$ S_{\text {Resid }}^{2}=\sum_{i=1}^{p} \sum_{j=1}^{n_{i}}\left(Y_{i j}-\bar{Y}_{i+}\right)^{2}, S_{\text {Betw }}^{2}=\sum_{i=1}^{p} n_{i}\left(\bar{Y}_{i+}-\bar{Y}_{++}\right)^{2} ,S_{\mathrm{Tot}}^{2}=\sum_{i=1}^{p} \sum_{j=1}^{n_{i}}\left(Y_{i j}-\bar{Y}_{++}\right)^{2}$$

-   $\bar Y_{++}$ is the overall average of all n observations.
-   $S_{Resid}^2 /\sigma^2$ has the $\chi^2$ distribution with $n- p$ degrees of freedom and is independent of $S_{Betw}$.

#### Testing Hypotheses

$$U ^2 = \frac{S_{Betw}^ 2 /(p - 1)}{S_{Resid}^2/(n-p)}$$

has the $F$ distribution with $p - 1$ and $n - p$ degrees of freedom.

Important ratio:

$$\frac{\text{Variability AMONG/BETWEEN the means}}{\text{Variability AROUND/WITHIN the distributions}}$$

-   If the variabitlity BETWEEN the means (distance from overall mean) in the numerator is relatively large compared to the variance WITHIN the samples (internal spread) in the denominator, the ratio will be much larger than 1. The samples then most likely do NOT come from a common population; REJECT Null Hypothesis that mean(s) are equal.

### Two-way ANOVA

## Logistic Regression

### Logit Model

_Model_:

$$\pi_i=Pr(Y_i=1|X_i=x_i)=\dfrac{\text{exp}(\beta_0+\beta_1 x_i)}{1+\text{exp}(\beta_0+\beta_1 x_i)}$$

or,

$$\begin{aligned} \text{logit}(\pi_i)&=\text{log}\left(\dfrac{\pi_i}{1-\pi_i}\right)\\ &= \beta_0+\beta_1 x_i\\ &= \beta_0+\beta_1 x_{i1} + \ldots + \beta_k x_{ik}\\ \end{aligned}$$

-   It uses maximum likelihood estimation (MLE) rather than ordinary least squares (OLS) to estimate the parameters, and thus relies on large-sample approximations.

The _maximum likelihood estimator_ (MLE) for $(\beta_0, \beta_1)$ is obtained by finding $(\hat{\beta}_0,\hat{\beta}_1)$ that maximizes:

$$L(\beta_0,\beta_1)=\prod\limits_{i=1}^N \pi_i^{y_i}(1-\pi_i)^{n_i-y_i}=\prod\limits_{i=1}^N \dfrac{\text{exp}\{y_i(\beta_0+\beta_1 x_i)\}}{1+\text{exp}(\beta_0+\beta_1 x_i)}$$

-   $exp(\beta_0)$ = the odds that the characteristic is present in an observation _i_ when _Xi_ = 0, i.e., at baseline.
-   $exp(\beta_1)$ = for every unit increase in _X_, the odds that the characteristic is present is multiplied by $exp(\beta_1)$. This is similar to simple linear regression but instead of additive change it is a multiplicative change in rate. This is an estimated _odds ratio_.

$$\dfrac{\text{exp}(\beta_0+\beta_1(x_{i1}+1))}{\text{exp}(\beta_0+\beta_1 x_{i1})}=\text{exp}(\beta_1)$$

### Probit Model

The _probit_ model

$$\text{probit}(\pi(x))=\beta_0+\beta x$$

uses _normal_ cdf

$$\text{probit}(\pi)=F^{-1}(X \leq x)$$

### Hypothesis Tests

Likelihood ratio tests

The likelihood for $n$ observations:

$$L=\prod_{i=1}^{n}\left(\frac{\exp \left(x_{i}^{\prime} \beta\right)}{1+\exp \left(x_{i}^{\prime} \beta\right)}\right)^{\sum_{i=1}^{n} Y_{i}}\left(1-\frac{\exp \left(x_{i}^{\prime} \beta\right)}{1+\exp \left(x_{i}^{\prime} \beta\right)}\right)^{n-\sum_{i=1}^{n} Y_{i}}$$

Likelihood Ratio

$$LR = −2

l(\hat\beta|H_0) − 2l(\hat\beta|H_A)\sim \chi^2_p $$

need to fit two models: the full model and the model under $H_0$. Then $l(\hat\beta|H_0)$ is the log-likelihood from the model under $H_0$, and $l(\hat\beta|H_A)$ is the log-likelihood from the full model.

$$LR=Deviance_A-Deviance_0 $$

### Wald tests

$$\frac{\hat{\beta}_{j}-\beta_{j 0}}{\hat{s e}(\hat{\beta})} \sim N(0,1)$$

Limitation

### Overdispersion

For the binomial response, if $Y_i \sim Bin(n_i, \pi_i)$, the mean is $\mu_i=n_i\pi_i$ and the variance is $n_i\pi_i(1-\pi_i)$.

-   **_Overdispersion_** means that the data show evidence that the variance of the response is greater than $n_i\pi_i(1-\pi_i)$.
-   Overdispersion can be explained by
    -   variation among the success probabilities
    -   correlation between the binary responses

The most popular method for adjusting for overdispersion comes from the theory of quasi-likelihood.


## Reference

Introduction to Econometrics / James H. Stock & Mark W. Watson C6-C9 esp. multiple t test

Probability and Statistics / Morris H. DeGroot & Mark J. Schervish C7-C11 except C10

[Lesson 7: Further Topics on Logistic Regression](https://online.stat.psu.edu/stat504/node/217/)

[极大似然估计和贝叶斯估计](https://zhuanlan.zhihu.com/p/61593112)

[Probability & Statistics Fundamental](https://nancyyanyu.github.io/posts/c27004a0/)

[Logistic 回归模型的参数估计为什么不能采用最小二乘法？](https://www.zhihu.com/question/23817253)

[在进行 OLS 估计时，为了满足 BLUE 条件，为什么会有 X 取值要在重复抽样时固定的前提？](https://www.zhihu.com/question/25832437)

[](https://www.groups.ma.tum.de/fileadmin/w00ccg/statistics/czado/lec5.pdf)

[](https://courses.washington.edu/b515/l13.pdf)

[逻辑回归是否靠谱，你懂得如何裁判吗？](https://mp.weixin.qq.com/s?subscene=23&__biz=MzAxMDA4NjU3OA==&mid=2652553697&idx=1&sn=09f2a67c9fe3a7081ee8fd76d40150a6&chksm=80bbd03cb7cc592a928c50b7b16518b1837d7a1258fa6d6cad305ff5e09525b98e26b1b147c8&scene=7&key=cc7cc2a0b445493e5a74d4ae079f895dfc0c723c3cff51870eaa2a2a299182d9309998c97eb86ff92300a6f2c05bd4d4f760054842fab5deff7b4ff39f1e151212234c47c80d1d2bf5d2c619ceb025d8a1f838dd7fbcb62c777b6239e637772bdecc698e4c1aadb4a61511031c88bfc27f30af629897d1c218e8cc582ff5a929&ascene=0&uin=MjU1NDk5MDUwOA%3D%3D&devicetype=Windows+10+x64&version=6300002f&lang=zh_CN&exportkey=A5G3CGCLpGJLnOrCZ13ZVHs%3D&pass_ticket=ok4tnaFWS7zPPSCRKPSyUIzrRRcpn0LMaKl%2FkngUWsaWK0ChENo%2FKgwaJH5CCexq&wx_header=0)