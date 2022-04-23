## Hazard Function
$$
\lambda(t)=\lim _{h \rightarrow 0^{+}} \frac{P(t \leq T<t+h \mid T \geq t)}{h}

$$

$$
\lambda(t)=\frac{f(t)}{S(t)}=-\frac{d}{dt}\text{log}(S(t))
$$

$f(t)$ is the pdf of $T$, $F(t)$ is the cdf of $T$. $S(t)=1-F(t)$ is the survival function.

## Kaplan-Meier Estimator

$$
\hat\lambda_j=\frac{d_j}{n_j}
$$

$$
\hat S(t)=\prod_{t_j\leq t}(1-\hat \lambda_j)=\prod_{t_j\leq t}\frac{n_j-d_j}{n_j}
$$

$$
n_{j+1}=n_j-d_j-c_j
$$

## Log-Rank Test

## Cox Proportional Hazard Model
$$
\lambda_i(t)=\lambda_0(t)\text{exp}(x_i^T\beta)
$$
[MBS早偿率的生存分析建模](MBS%20Modelling.md#生存分析建模)

### Testing
Wald
$$
\hat\beta\sim N(\beta,(X^TWX)^{-1})
$$

Likelihood Ratio

## Reference

[生存分析科普](https://zhuanlan.zhihu.com/c_1189624821506506752)
[Cox Regression Model vs Logistics Regression Model](http://courses.washington.edu/b513/Spring%202010/Discussion/Discussion10.pdf)



