---
title: "Simple Linear Regression"
---



# Simple Linear Regression Model

$$E(Y |x) = \beta_0 + \beta_1x$$

$$Y=\beta_0+\beta_1x+\varepsilon,\varepsilon\sim N(0,\sigma^2)$$

## Least-Squares Estimation

We shall minimize $Q$ with respect to $\beta_0$ and $\beta_1$ by taking the partial derivatives and setting them to 0. We have

$$\frac{\partial Q}{\partial \beta_{0}}=-2 \sum_{i=1}^{n}\left(y_{i}-\beta_{0}-\beta_{1} x_{i}\right) =0 $$

$$ \frac{\partial Q}{\partial \beta_{1}}=-2\sum_{i=1}^{n}\left(y_{i}-\beta_{0}-\beta_{1} x_{i}\right) x_{i}=0$$

Normal Equation

$$\begin{aligned}\beta_{0} n+\beta_{1} \sum_{i=1}^{n} x_{i} &=\sum_{i=1}^{n} y_{i} \\\beta_{0} \sum_{i=1}^{n} x_{i}+\beta_{1} \sum_{i=1}^{n} x_{i}^{2} &=\sum_{i=1}^{n} x_{i} y_{i} .\end{aligned}$$



## Assumptions

-   Normality. For $i = 1, . . . , n,$ the conditional distribution of $Y_i$ given the values $x_1, . . . , x_n$ is a normal distribution.

-   Linear Mean. There are parameters $\beta_0$ and $\beta_1$ such that the conditional mean of $Y_i$ given the values $x_1, . . . , x_n$ has the form $\beta_0 + \beta_1x_i$ for $i = 1, . . . , n$.

-   Common Variance. There is a parameter $\sigma^2$ such that the conditional variance of $Y_i$ given the values $x_1, . . . , x_n$ is $\sigma^2$ for $i = 1, . . . , n.$ This assumption is often called **homoscedasticity**. Random variables with different variances are called **heteroscedastic**.
    -   The error term is homoskedastic if the variance of the conditional distribution of $\varepsilon_i$ given $X_i$ is constant for $i = 1,\cdots, n$ and in particular does not depend on $X_i$. Otherwise, the error term is heteroskedastic.
-   Independence. The random variables $Y_1, . . . , Y_n$ are independent given the observed $x_1, . . . , x_n$.
-   Predictor is known.

We can now find the M.L.E.

## M.L.E. of Estimators

$$\hat{\beta}_{1}=\frac{\sum_{i=1}^{n} x_{i} Y_{i}-n \bar{x}_{n} \bar{Y}_{n}}{\sum_{i=1}^{n} x_{i}^{2}-n \bar{x}_{n}^{2}}=\frac{\sum_{i=1}^{n}\left(x_{i}-\bar{x}_{n}\right)\left(Y_{i}-\bar{Y}_{n}\right)}{\sum_{i=1}^{n}\left(x_{i}-\bar{x}_{n}\right)^{2}}$$

$$

\hat{\beta}_{0}=\bar{Y}_{n}-\hat{\beta}_{1} \bar{x}_{n}$$

The M.L.E.’s of the regression coefficients $\beta_0$ and $\beta_1$ are precisely the same as the least-squares estimates.

### The Distribution of the Least-Squares Estimators

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

### The Properties of the Least-Squares Estimators

The **sum of the residuals** in any regression model that contains an intercept  $\beta_0$ is always zero.

The **sum of the observed values** $y_i$ equals the **sum of the fitted values** $\hat y_i$. 

The least-squares regression line always passes through the centroid of the data. 

The **sum of the residuals weighted by the corresponding value of the regressor variable** always equals zero, that is,
$$
\sum_i=1 ^n x_i\left[y_i-(\hat\beta_0+\hat\beta_1x_i)\right]=0
$$

The sum of the residuals weighted by the corresponding fitted value always equals zero, that is, 
$$
\sum_i=1 ^n \hat y_i\left[y_i-(\hat\beta_0+\hat\beta_1x_i)\right]=0
$$


## Prediction

### M.S.E. of Prediction

$$
\begin{aligned}E\left[(\hat{Y}-Y)^{2}\right] &=E\left\{[(\hat{Y}-\mu)-(Y-\mu)]^{2}\right\} \\&=\operatorname{Var}(\hat{Y})+\operatorname{Var}(Y)-2 \operatorname{Cov}(\hat{Y}, Y)\\&=\operatorname{Var}(\hat{Y})+\operatorname{Var}(Y)\\&=\sigma^{2}\left[1+\frac{1}{n}+\frac{(x-\bar{x})^{2}}{s_{x}^{2}}\right]\end{aligned}
$$

The random variables $\hat Y$ and $Y$ are independent, because $\hat Y$ is a function of the first $n$ pairs of observations and $Y$ is an independent observation. Therefore,$\operatorname{Cov}(\hat{Y}, Y)=0$.

Since

$$
\operatorname{Var}(\hat{Y}) = \operatorname{Var}(\hat{\beta_0}+\hat{\beta_1} x) = \operatorname{Var}(\hat\beta_0) + x \operatorname{Var}(\hat\beta_1) + 2x \operatorname{Cov}(\hat\beta_0,\hat\beta_1)
$$

Thus,
$$
E\left[(\hat{Y}-Y)^{2}\right] =\sigma^{2}\left[1+\frac{1}{n}+\frac{(x-\bar{x})^{2}}{s_{x}^{2}}\right]
$$





## Statistical Inference in Simple Linear Regression

### M.L.E. for $\sigma^2$

$$
\hat \sigma^2=\frac{1}{n}\sum_{i=1}^n\left[Y_i-(\hat\beta_0+\hat\beta_1x_i)\right]^2
$$

The distribution of $n\hat\sigma^2/\sigma^2$ is the $\chi^2$ distribution with $n-2$ degrees of freedom.

### Unbiased Estimator of $\sigma^2$

$$ 
\sigma^{\prime}=\left(\frac{S^{2}}{n-2}\right)^{1 / 2}, \text{where}\ \ S^{2}=\sum_{i=1}^{n}\left(Y_{i}-\hat{\beta}_{0}-\hat{\beta}_{1} x_{i}\right)^{2}
$$

Note that it is different from the M.L.E.

### Linear Combination of $\beta_0$ and $\beta_1$

$$
\left[\frac{c_{0}^{2}}{n}+\frac{\left(c_{0} \bar{x}-c_{1}\right)^{2}}{s_{x}^{2}}\right]^{-1 / 2} \frac{c_{0} \hat{\beta}_{0}+c_{1} \hat{\beta}_{1}-\left(c_{0} \beta_{0}+c_{1} \beta_{1}\right)}{\sigma^{\prime}}
$$

has the $t$ distribution with $n-2$ degrees of freedom under the assumptions of simple linear regression.

We can use this random variable to test hypotheses about or to construct confidence intervals.

Plug $\sigma^{\prime}$ into $\operatorname{Var}\left(\hat{\beta}{1}\right)=\frac{\sigma^{2}}{s_{x}^{2}}$ and get the equation.

### Confidence Intervals

The open interval is a coefficient $1-\alpha_0$ confidence interval for $c_0\beta_0+c_1\beta_1$.

$$c_{0} \hat{\beta}_{0}+c_{1} \hat{\beta}_{1} \pm \sigma^{\prime}\left[\frac{c_{0}^{2}}{n}+\frac{\left(c_{0} \bar{x}-c_{1}\right)^{2}}{s_{x}^{2}}\right]^{1 / 2} T_{n-2}^{-1}\left(1-\frac{\alpha_{0}}{2}\right)$$

### Prediction Interval

$$\hat{Y} \pm T_{n-2}^{-1}\left(1-\frac{\alpha_{0}}{2}\right) \sigma^{\prime}\left[1+\frac{1}{n}+\frac{(x-\bar{x})^{2}}{s_{x}^{2}}\right]^{1 / 2}$$

### Coefficient of Determination

SST: Total sum of squares
SSE: Explained sum of squares / Regression sum of squares
SSR: Residual sum of squares
$$
\begin{array}{l}{\mathrm{SST} \equiv \sum_{i=1}^{n}\left(y_{i}-\overline{y}\right)^{2}} \\ {\mathrm{SSE} \equiv \sum_{i=1}^{n}\left(\hat{y}_{i}-\overline{y}\right)^{2}} \\ {\mathrm{SSR} \equiv \sum_{i=1}^{n} \left(y_{i}-\hat{y}_{i}\right)^{2}}\\ \mathrm{SST}=\mathrm{SSE}+\mathrm{SSR}\end{array}
$$


$$R^2=1-\frac{SSE}{SST}=1-\frac{\sum_{i=1}^{n}\left(y_{i}-\hat{y}_{i}\right)^{2}}{\sum\left(y_{i}-\bar{y}_{n}\right)^{2}}$$