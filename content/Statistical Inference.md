---
title: "Statistical Inference"
---

## Estimation

### Prior and Posterior Distributions

-   Suppose that one has a statistical model with parameter $\theta$. If one treats $\theta$ as random, then the distribution that one assigns to $\theta$ before observing the other random variables of interest is called its prior distribution.
-   Consider a statistical inference problem with parameter $\theta$ and random variables $X_1, . . . , X_n$ to be observed. The conditional distribution of $\theta$ given $X_1, . . . , X_n$ is called the posterior distribution of $\theta$.
-   Suppose that the $n$ random variables $X_1, . . . , X_n$ form a random sample from a distribution for which the p.d.f. or the p.f. is $f (x|\theta)$. Suppose also that the value of the parameter $\theta$ is unknown and the prior p.d.f. or p.f. of $\theta$ is $\xi(\theta)$. Then the posterior p.d.f. or p.f. of $\theta$ is

$$\xi(\theta \mid \boldsymbol{x})=\frac{f\left(x_{1} \mid \theta\right) \cdots f\left(x_{n} \mid \theta\right) \xi(\theta)}{g_{n}(\boldsymbol{x})} \quad \text { for } \theta \in \Omega$$

-   where $g_n$ is the marginal joint p.d.f. or p.f. of $X_1, . . . , X_n$.

$$g_{n}(\boldsymbol{x})=\int_{\Omega} f_{n}(\boldsymbol{x} \mid \theta) \xi(\theta) d \theta$$

### Conjugate Prior Distributions

### Bayes Estimators

-   A Bayes estimator is an estimator that is chosen to minimize the posterior mean of some measure of how far the estimator is from the parameter, such as squared error or absolute error.
-   expected loss：

$$E[L(\theta, a) \mid \boldsymbol{x}]=\int_{\Omega} L(\theta, a) \xi(\theta \mid \boldsymbol{x}) d \theta$$

-   For each possible value $x$ of $X$, let $\delta^\star(\boldsymbol x)$ be a value of a such that $E[L(\theta, a)|x]$ is minimized. Then $\delta^\star$ is called a Bayes estimator of $\theta$.
-   Suppose that the squared error loss function is used and that the posterior mean of $\theta, E(\theta \mid \boldsymbol{X}),$ is finite. Then, a Bayes estimator of $\theta$ is $\delta^{*}(\boldsymbol{X})=E(\theta \mid \boldsymbol{X})$.
-   To apply the theory, it is necessary to specify a particular loss function, such as the squared error or absolute error function, and also a prior distribution for the parameter. Meaningful specifications may exist, in principle, but it may be very difficult and time-consuming to determine them.

### Maximum Likelihood Estimators

-   When the joint p.d.f. $f_n(\boldsymbol{x}|\theta)$ of the observations in a random sample is regarded as a function of $\theta$ for given values of $x_1, . . . , x_n$, it is called the likelihood function.
-   If we plug the observed values of the data into the conditional p.f. or p.d.f. of the data given the parameter, the result is a function of the parameter alone, which is called the likelihood function.
-   Maximum Likelihood Estimator/Estimate. For each possible observed vector $\boldsymbol{x},$ let $\delta(\boldsymbol{x}) \in \Omega$ denote a value of $\theta \in \Omega$ for which the likelihood function $f_{n}(\boldsymbol{x} \mid \theta)$ is a maximum, and let $\hat{\theta}=\delta(\boldsymbol{X})$ be the estimator of $\theta$ defined in this way. The estimator $\hat{\theta}$ is called a maximum likelihood estimator of $\theta .$ After $\boldsymbol{X}=\boldsymbol{x}$ is observed, the value $\delta(\boldsymbol{x})$ is called a maximum likelihood estimate of $\theta$.

#### Limitations of Maximum Likelihood Estimation

Nonexistence of an M.L.E.

$$f(x \mid \theta)=\left\{\begin{array}{ll}\frac{1}{\theta} & \text { for } 0<x<\theta \\0 & \text { otherwise }\end{array}\right.$$

Non-uniqueness of an M.L.E.

$$f_{n}(\boldsymbol{x} \mid \theta)=\left\{\begin{array}{ll}1 & \text { for } \theta \leq x_{i} \leq \theta+1,(i=1, \ldots, n) \\0 & \text { otherwise }\end{array}\right.$$

Thus, it is possible to select as an M.L.E. any value of $\theta$ in the interval

$$ \max \left\{x_{1}, \ldots, x_{n}\right\}-1 \leq \theta \leq \min \left\{x_{1}, \ldots, x_{n}\right\} $$

Sampling from a Mixture of Two Distributions

### Properties of Maximum Likelihood Estimators

-   Invariance: Let $\hat\theta$ be an M.L.E. of $\theta$, and let $g(\theta)$ be a function of $\theta$. Then an M.L.E. of $g(\theta)$ is $g(\hat\theta)$.
-   Consistency: the sequence of M.L.E.’s converges in probability to the unknown value of $\theta$ as $n \rightarrow \infty$.

## Sampling Distributions of Estimators

### Joint Distribution of the Sample Mean and Sample Variance

-   Let $X_{1}, \ldots, X_{n}$ be a random sample from the normal distribution with mean $\mu$ and variance $\sigma^{2}$. Then the sample mean $\hat{\mu}=\bar{X}{n}=\frac{1}{n} \sum{i=1}^{n} X_{i}$ and sample variance $\widehat{\sigma^{2}}=\frac{1}{n} \sum_{i=1}^{n}\left(X_{i}-\bar{X}_{n}\right)^{2}$ are independent random variables. Furthermore, $\hat{\mu}$ has the normal distribution with mean $\mu$ and variance $\sigma^{2} / n,$ and $n \widehat{\sigma}^{2} / \sigma^{2}$ has a chi-square distribution with $n-1$ degrees of freedom.

### Confidence Intervals

-   We can find an interval $(A, B)$ that we think has high probability of containing $θ$. The length of such an interval gives us an idea of how closely we can estimate $θ$.
-   Let $X = (X_1, . . . , X_n)$ be a random sample from a distribution that depends on a parameter (or parameter vector) $\theta$. Let $g(\theta)$ be a real-valued function of $\theta$. Let $A \leq B$ be two statistics that have the property that for all values of $\theta$,

$$Pr(A < g(\theta) < B) ≥ \gamma$$

-   Then the random interval $(A, B)$ is called a coefficient $\gamma$ confidence interval for $g(θ)$.

### Unbiased Estimators

-   Let $\delta$ be an estimator of a function $g$ of a parameter $\theta$. We say that $\delta$ is unbiased if $E_{\theta}[\delta(X)] = g(\theta)$ for all values of $\theta$.
-   The quality of an unbiased estimator must be evaluated in terms of its variance or its M.S.E.
-   Limitations:
    -   Nonexistence of an Unbiased Estimator
        -   suppose that $X_1, . . . , X_n$ form n Bernoulli trials for which the parameter $p$ is unknown. It can be shown that there will be no unbiased estimator of $p^{1/2}$.
    -   Inappropriate Unbiased Estimators
        -   Consider an infinite sequence of Bernoulli trials for which the parameter $p$ is unknown $(0 < p < 1)$, and let $X$ denote the number of failures that occur before the first success is obtained.

## Testing Hypotheses

### Problems of Testing Hypotheses

Concepts:

-   Because of focusing on type I error instead of type II error, we usually regard type I error as having more serious consequences than type II error.
    
-   Hence, in formulating null and alternative hypotheses, we use the more conservative hypothesis as the null hypothesis, and will only reject it when the data provide statistically significant evidence against it.
    
-   Type I & II Error
    
    $$\begin{array}{r|cc} &\text{Actually $H_0$ is True}&\text{Actually $H_1$ is True}\\ \hline\text{Do not reject $H_0$}& \text{Correct} &\text{Type II Error} \\ \text{Reject $H_0$} & \text{Type I Error} &\text{Correct} \\ \end{array}$$
    
-   Size
    
    -   Loosely, the size $\alpha(\delta)$ of a given test $\delta$ is the maximum probability of type I error.
-   Level
    
    -   $\delta$ is a level $\alpha_0$ test if and only if $\alpha(\delta)\leq\alpha_0$.
-   $p$-value
    
    -   A $p$-value is a probability that provides a measure of the evidence against the null hypothesis provided by the sample.
    -   In general, the $p$-value is the smallest level $\alpha_0$ such that we would reject the null hypothesis at level $\alpha_0$ with the observed data.
    -   For each $x$, let $\delta_x$ be the test that rejects $H_0$ if $X\geq x$. Then the $p$-value equals:
    
    $$ \sup _{\theta \in \Omega_{0}} \pi\left(\theta | \delta_{x}\right)=\sup _{\theta \in \Omega_{0}} \operatorname{Pr}(X \geq x | \theta)
    
    $$
    
-   Critical Value
    
    -   The critical values are the boundaries of the acceptance region of the test.
    -   The critical value will be a quantile of a certain distribution.

### The t Test

### Comparing the Means of Two Normal Distributions

### The F Distributions

## Categorical Data and Nonparametric Methods

### Tests of Goodness-of-Fit

### Goodness-of-Fit for Composite Hypotheses

### Contingency Tables

### Tests of Homogeneity

### Simpson’s Paradox

## Four Steps to Hypothesis Testing

### Compute the test statistic

| Situation                                                | Null Hypothesis | Test Statistic                                               | Critical Region     |
| :------------------------------------------------------- | --------------- | ------------------------------------------------------------ | --------------------------------- |
| Mean of a Population (known $\sigma$) | $\mu=\mu_0$ | $U=\frac{\bar x-\mu_0}{\sigma/\sqrt{n}}$ | $\{\lvert U\rvert\geq U_{1-\alpha/2}\}$ |
| Mean of a Population (unknown $\sigma$) |      $\mu=\mu_0$            | $T=\frac{\bar x-\mu_0}{s/\sqrt{n}}$                          | $\{\lvert T\rvert\geq t_{1-\alpha/2}(n-1)\}$ |
| Proportion of a Population | $p= p_0$ | $U=\frac{\hat{p}-p_{0}}{\sqrt{\frac{p_{0}\left(1-p_{0}\right)}{n}}}$ | $\{\lvert U\rvert\geq U_{1-\alpha/2}\}$ |
| Means of Two Populations (known $\sigma$) | $\mu_1=\mu_2$ | $U=\frac{(\bar x-\bar{y})}{\sqrt{\frac{\sigma_{1}^{2}}{m}+\frac{\sigma_{2}^{2}}{n}}}$ |   $\{\lvert U\rvert\geq U_{1-\alpha/2}\}$   |
| Means of Two Populations (unknown $\sigma$ and $\sigma_1=\sigma_2$ ) | $\mu_1=\mu_2$ | $T=\frac{\bar x-\bar y}{s_p\sqrt{\frac{1}{m}+\frac{1}{n}}},\\ s_{p}^{2}=\frac{(m-1) s_{x}^{2}+(n-1) s_{y}^{2}}{m+n-2}$ | $\{\lvert T\rvert\geq t_{1-\alpha/2(m+n-2)}\}$ |
| Means of Two Populations (unknown $\sigma_1,\sigma_2,\sigma_1\neq\sigma_2$ and large sample) | $\mu_1=\mu_2$ | $U=\frac{\bar x-\bar y}{\sqrt{\frac{s_x^2}{m}+\frac{s_y^2}{n}}}$ | $\{\lvert U \rvert\geq U_{1-\alpha/2}\}$ |
| Means of Two Populations (unknown $\sigma_1,\sigma_2,\sigma_1\neq\sigma_2$ and small sample)[Do not need to know] | $\mu_1=\mu_2$ | $T=\frac{\bar x-\bar y}{\sqrt{\frac{s_x^2}{m}+\frac{s_y^2}{n}}}$ | $\{\lvert T\rvert\geq t_{1-\alpha/2}(l-1)\},\\l=\frac{s^{4}}{\frac{s_{x}^{4}}{m^{2}(m-1)}+\frac{s_{y}^{4}}{n^{2}(n-1)}},s_{0}^{2}=\frac{s_{x}^{2}}{m}+\frac{s_{y}^{2}}{n}$ |
| Proportion of Two Populations | $p_1=p_2$ | $U=\frac{\hat{p}_{1}-\hat{p}_{2}}{\sqrt{\hat{p}(1-\hat{p})\left(\frac{1}{n_{1}}+\frac{1}{n_{2}}\right)}}, \hat{p}=\frac{n_{1} \hat{p}_{1}+n_{2} \hat{p}_{2}}{n_{1}+n_{2}}$ | $\{\lvert U\rvert\geq U_{1-\alpha/2}\}$ |
| Matched Pairs | $\delta=\mu_1-\mu_2,\delta=\mu_0$ | $T=\frac{\delta-\mu_0}{s_{\delta}/\sqrt{n}}$ | $\{\lvert T\rvert \geq t_{1-\alpha/2}(n-1)\}$ |
| Variance of Two Populations | $\sigma_1^2=\sigma_2^2$ | $F=\frac{s_x}{s_y}$ | $\left\{F \leq F_{\alpha/2}(m-1, n-1) \text { or } F \geq F_{1-\alpha / 2}(m-1, n-1)\right\}$ |
| Coefficient | $\hat\beta_j=\beta_j^{\star}$ | $T=\frac{\hat\beta_j-\beta_j^{\star}}{SE(\hat \beta_j)}$ | $\{\lvert T\rvert \geq t_{1-\alpha/2}(n-k-1)\}$ |
| Goodness of Fit (known $p_i$) | $P(A_i)=p_i$ | $Q=\sum_{i=1}^{k} \frac{\left(N_{i}-n p_{i}\right)^{2}}{n p_{i}}$ | $\{Q\geq \chi^2_{1-\alpha}(k-1)\}$ |
| Goodness of Fit (unknown $p_i$) | $P(A_i)=p_i$ | $Q=\sum_{i=1}^{k} \frac{\left[N_{i}-n \pi_{i}(\hat{\theta})\right]^{2}}{n \pi_{i}(\hat{\theta})}$ | $\{Q\geq \chi^2_{1-\alpha}(k-s-1)\}$ |
| Independence in Contingency Tables | $p_i, p_j\ independent$ | $Q=\sum_{i=1}^{R} \sum_{j=1}^{c} \frac{\left(N_{i j}-\hat{E}_{i j}\right)^{2}}{\hat{E}_{i j}}$ | $\{Q\geq \chi^2_{1-\alpha}((R-1)(C-1))\}$ |

**Note:** $\bar x,\bar y$ is the sample mean. $s,s_x,s_y$ is the standard deviation of sample. i.e. $s=\sqrt{\frac{\sum\left(X_{i}-\bar{X}\right)^{2}}{n-1}}$. 