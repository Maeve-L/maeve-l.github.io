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

#### Likelihood ratio tests

The likelihood for $n$ observations:

$$L=\prod_{i=1}^{n}\left(\frac{\exp \left(x_{i}^{\prime} \beta\right)}{1+\exp \left(x_{i}^{\prime} \beta\right)}\right)^{\sum_{i=1}^{n} Y_{i}}\left(1-\frac{\exp \left(x_{i}^{\prime} \beta\right)}{1+\exp \left(x_{i}^{\prime} \beta\right)}\right)^{n-\sum_{i=1}^{n} Y_{i}}$$

Likelihood Ratio

$$LR = −2

l(\hat\beta|H_0) − 2l(\hat\beta|H_A)\sim \chi^2_p $$

need to fit two models: the full model and the model under $H_0$. Then $l(\hat\beta|H_0)$ is the log-likelihood from the model under $H_0$, and $l(\hat\beta|H_A)$ is the log-likelihood from the full model.

$$LR=Deviance_A-Deviance_0 $$

#### Wald tests

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