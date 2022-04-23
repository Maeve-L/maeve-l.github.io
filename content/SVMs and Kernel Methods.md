Awkward issue with logistic regression is that it fails if the training data are linearly separable. What this means is that, in the feature space, one can separate the two classes by a linear boundary. In cases such as this, maximum likelihood fails and some parameters march off to infinity. 

## Optimal Separating Hyperplane
Finding an **optimal separating hyperplane** was in fact the launching point for SVMs.

We define a two-class linear classifier via a function $f(x)=\beta_0+x^{\prime}\beta$, with the convention that we classify a point $x_0$ as $+1$ if $f(x_0)>0$, and as $-1$ if $f(x_0)<0$(on the fence we flip a coin). Hence the classifier itself is $C(x)=sign[ f(x)]$ .

The decision boundary is the set $\{x|f(x)=0\}$.

The (signed) Euclidean distance from a point $x_0$ to the linear decision boundary defined by $f$ is given by 
$$
\frac{1}{||\beta||_2}f(x_0)
$$

With this in mind, for a separating hyperplane the quantity $\frac{1}{||\beta||_2}y_if(x_i)$is the distance of xi from the decision boundary. 
This leads to an optimization problem for creating the optimal margin classifier:

$$\underset{\beta_{0}, \beta}{\operatorname{maximize}} M, {\operatorname{s.t.}} \frac{1}{\|\beta\|_{2}} y_{i}\left(\beta_{0}+x^{\prime} \beta\right) \geq M, i=1, \ldots, n$$



A rescaling argument reduces this to the simpler form
$$
\begin{aligned}
&\underset{\beta_{0}, \beta}{\operatorname{minimize}}\|\beta\|_{2} \\
&\text { subject to } y_{i}\left(\beta_{0}+x^{\prime} \beta\right) \geq 1, i=1, \ldots, n
\end{aligned}
$$

One noteworthy property of the solution is that
$$
\hat\beta=\sum_{i\in S}\hat\alpha_i x_i
$$
where $S$ is the support set.


## Soft-Margin Classifier

The generalization to a soft margin allows points to violate their margin. Each of the violators has a line segment connecting it to its margin, showing the extent of the violation. The soft-margin classifier solves 

$$
\begin{aligned}
&\underset{\beta_{0}, \beta}{\operatorname{minimize}}\|\beta\|_{2} \\
&\text { subject to } y_{i}\left(\beta_{0}+x^{\prime} \beta\right) \geq 1-\epsilon_i, i=1, \ldots, n\\
&\epsilon_i>0, \sum_{i=1}^N \epsilon_i\leq B, i=1, \ldots, n
\end{aligned}
$$

Here $B$ is the budget for the total amount of overlap.

## SVM Criterion as Loss Plus Penalty

## Kernel Trick

## Reference

Efron, B., & Hastie, T. (2016). _Computer Age Statistical Inference: Algorithms, Evidence, and Data Science_ (1st ed.). Cambridge University Press. [https://doi.org/10.1017/CBO9781316576533](https://doi.org/10.1017/CBO9781316576533)