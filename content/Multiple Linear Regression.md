---
Area: Statistics
Source: Book
Status: Todo
Type: Notes
---


# Multiple Linear Regression

Design Matrix $\mathbf{X}$

$$\mathbf{X}=\left[\begin{array}{ccc}x_{10} & \cdots & x_{1 p-1} \\x_{20} & \cdots & x_{2 p-1} \\\vdots & \ddots & \vdots \\x_{n0} & \cdots & x_{n p-1}\end{array}\right]$$

We shall also let $\mathbf{y}$ be the vector of observed values of $Y_1,...,Y_n$, $\boldsymbol{\beta}$ be the vector of parameters.

$$\mathbf{y}=\left[\begin{array}{c}y_{1} \\ \vdots \\y_{n}\end{array}\right]$$

$$\boldsymbol{\beta}=\left[\begin{array}{c}\beta_{1} \\ \vdots \\\beta_{p-1}\end{array}\right]$$

$$ \mathbf{Y}_{n \times 1}=\mathbf{X}_{n \times p} \boldsymbol{\beta}_{p \times 1}+\boldsymbol\varepsilon_{n \times 1}$$

## M.L.E of Estimators

$$

\widehat{\boldsymbol{\beta}}=\left(\mathbf{X}^{\prime} \mathbf{X}\right)^{-1} \mathbf{X}^{\prime} \mathbf{Y}
$$







## Mean Vector and Covariance Matrix

The coordinates $Y_1, . . . , Y_n$ of $\mathbf{Y}$ are independent.

$$\mathbf{Y}=\left[\begin{array}{c}Y_{1} \\ \vdots \\Y_{n}\end{array}\right]$$


$$

\varepsilon_{i} \sim N\left(0, \sigma_{i}^{2}\right),
\quad E(\varepsilon)=\mathbf{0}
$$

$$
E(\mathbf{Y}) = \mathbf{X} \boldsymbol{\beta}
$$

$$
\quad \operatorname{Cov}(\mathbf{Y})=\operatorname{Cov}(\varepsilon)=\sigma^{2} \mathbf{I}
$$


$$
\begin{aligned}
\operatorname{Cov}(\hat{\boldsymbol{\beta}}) &=\left(\mathbf{X}^{\prime} \mathbf{X}\right)^{-1} \mathbf{X}^{\prime} \operatorname{Cov}(\boldsymbol{Y}) \mathbf{X}\left(\mathbf{X}^{\prime} \mathbf{X}\right)^{-1} \\
&=\left(\mathbf{X}^{\prime} \mathbf{Z}\right)^{-1} \mathbf{Z}^{\prime}\left(\sigma^{2} \boldsymbol{I}\right) \mathbf{X}\left(\mathbf{Z}^{\prime} \mathbf{Z}\right)^{-1} \\
&=\sigma^{2}\left(\mathbf{Z}^{\prime} \mathbf{Z}\right)^{-1}
\end{aligned}
$$

## The Joint Distribution of the Estimators

Let 

$$
\left( \mathbf{X}^{\prime} \mathbf{X}\right)^{-1}_{p\times p}=\left[\begin{array}{ccc}\xi_{00} & \cdots & \xi_{0 p-1} \\\xi_{1 0} & \cdots & \xi_{1 p-1} \\\vdots & \ddots & \vdots \\\xi_{p-1 0} & \cdots & \xi_{p-1 p-1}\end{array}\right]

$$

$$
E(\widehat{\boldsymbol{\beta}})=\left(\mathbf{X}^{\prime} \mathbf{X}\right)^{-1} \mathbf{X}^{\prime} E(\mathbf{Y})=\left(\mathbf{X}^{\prime} \mathbf{X}\right)^{-1} \mathbf{X}^{\prime} \mathbf{X} \boldsymbol{\beta}=\boldsymbol{\beta}
$$

$$

\operatorname{Var}(\widehat{\boldsymbol{\beta}})=\sigma^{2}\left(\mathbf{X}^{\prime} \mathbf{X}\right)^{-1}=\sigma^{2}\left(\xi_{i j}\right)_{i, j=0, \cdots, k}
$$

$$
\boldsymbol{\beta}\sim N_{r}\left(\boldsymbol{\beta},\sigma^{2}\left(\mathbf{X}^{\prime} \mathbf{X}\right)^{-1}\right)
$$



$$
{{\sigma}^{\prime}}^{2}=\frac{\widehat{\varepsilon}^{\prime} \widehat{\varepsilon}}{n-p},\quad \frac{(n-p){{\sigma}^{\prime}}^{2}}{\sigma^2}\sim\chi^2(n-p) 
$$

$$ \frac{\hat\beta_j-\beta_j^{\star}}{\sqrt{\xi_{jj}}{{\sigma}^{\prime}}^{2}}\sim t(n-p)
$$



## Prediction

$$
\widehat{\mathbf{Y}}=\mathbf{x}^{\prime}\left(\mathbf{X}^{\prime} \mathbf{X}\right)^{-1} \mathbf{X}^{\prime} \mathbf{Y}
$$

$$
\operatorname{Var}(\hat{\mathbf{Y}})=\mathbf{x}^{\prime}\left(\mathbf{X}^{\prime}\mathbf{X}\right)^{-1}\mathbf{x}\sigma^2
$$

$$
\frac{Y-\hat{Y}}{\sigma^{\prime}\left[1+\mathbf{x}^{\prime}\left(\mathbf{X}^{\prime}\mathbf{X}\right)^{-1}\mathbf{x}\right]^{1 / 2}}\sim t(n-p)
$$



## Tests of Joint Hypotheses

Test for an overall significant relationship between the response variable and all of the explanatory variables.

### F Test

$$F=\frac{1}{2}\left(\frac{t_{1}^{2}+t_{2}^{2}-2 \hat{\rho}_{t_{1}, t_{2}} t_{1} t_{2}}{1-\hat{\rho}_{t_{1}, t_{2}}^{2}}\right)$$

The homoskedasticity-only F-statistic

$$F =\frac{(SSR_{restricted} - SSR_{unrestricted})/q}{SSR_{unrestricted}/(n - k_{unrestricted} - 1)}$$

$$F =\frac{(R_{unrestricted}^2 - R_{restricted}^2)/q}{(1 - R_{unrestricted}^2)(n -k_{unrestricted} - 1)} $$

## Multiple R Squared

In general, $R^2$ never decreases when a regressor is added to the model, regardless of the value of the contribution of that variable. Therefore, it is difficult to judge whether an increase in $R^2$ is really telling us anything important.

$$R^{2}=1-\frac{\sum_{i=1}^{n}\left(y_{i}-\hat{y}_{i}\right)^{2}}{\sum_{i=1}^{n}\left(y_{i}-\bar{y}\right)^{2}}$$

$$R^2_{adj}=1-\frac{\hat\sigma^2}{\text {SST}/n-1}=1-\frac{(1-R^2)(n-1)}{n-p}$$

## Hidden Extrapolation

Data extrapolating beyond the region containing the original observations. 

In multiple regression it is easy to inadvertently extrapolate, since the levels of the regressors jointly define the region containing the data.

Hat Matrix:
$$
\mathbf{H}=\mathbf{X}\left(\mathbf{X}\right)^{-1} \mathbf{X}^{\prime}
$$

If $h_{ii}>h{max}$, then points are extrapolation points.

## Multicollinearity

$$
VIF_j=\frac{1}{1-R_j^2}
$$
where $R_j^2$ is the coefficient of multiple determination obtained from regressing $x_j$ on the other regressor variables. 

Clearly, if $x_j$ is nearly linearly dependent on some of the other regressors, then $R_j^2$ will be near unity and $VIF_j$ will be large. 

VIFs larger than 10 imply serious problems with multicollinearity. 

