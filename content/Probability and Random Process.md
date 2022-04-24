---
title: "Probability and Random Process"
---


## Counting

### Sampling Table

The sampling table gives the number of possible samples of size $k$ out of a population of size $n$, under various assumptions about how the sample is collected

$$ \begin{array}{r|cc} & \textbf{Order Matters} & \textbf{Not Matter} \\ \hline \textbf{With Replacement} & \displaystyle n^k & \displaystyle{n+k-1 \choose k} \\ \textbf{Without Replacement} & \displaystyle\frac{n!}{(n - k)!} & \displaystyle{n \choose k} \end{array}$$

-   Experiments/Outcomes - An experiment generates an outcome from a pre-determined list. For example, a dice roll generates outcomes in the set $\{1, 2, 3, 4, 5, 6\}$
-   Sample Space - The sample space, denoted $\Omega$, is the set of possible outcomes. Note that the probability of this event is 1, since something in the sample space will always occur.
-   Event - An event is a subset of the sample space, or a collection of possible outcomes of an experiment. We say that the event has occurred if any of the outcomes in the event have happened.

## Conditional

### Law of Total Probability (LOTP)

Let ${ B}_1, { B}_2, { B}_3, ... { B}_n$ be a _partition_ of the sample space (i.e., they are disjoint and their union is the entire sample space).

$$ \begin{aligned} P({ A}) &= P({ A} | { B}_1)P({ B}_1) + P({ A} | { B}_2)P({ B}_2) + \dots + P({ A} | { B}_n)P({ B}_n)\\ P({ A}) &= P({ A} \cap { B}_1)+ P({ A} \cap { B}_2)+ \dots + P({ A} \cap { B}_n) \end{aligned} $$

$$ \begin{aligned} P({ A}| { C}) &= P({ A} | { B}_1, { C})P({ B}_1 | { C}) + \dots + P({ A} | { B}_n, { C})P({ B}_n | { C})\\ P({ A}| { C}) &= P({ A} \cap { B}_1 | { C})+ P({ A} \cap { B}_2 | { C})+ \dots + P({ A} \cap { B}_n | { C})\end{aligned} $$

Special case of LOTP with ${ B}$ and ${ B^c}$ as partition:

$$ \begin{aligned} P({ A}) &= P({ A} | { B})P({ B}) + P({ A} | { B^c})P({ B^c}) \\ P({ A}) &= P({ A} \cap { B})+ P({ A} \cap { B^c}) \\ \end{aligned} $$

### Bayes' Rule

$$ P({ A}|{ B}) = \frac{P({ B}|{ A})P({ A})}{P({ B})}, P({ A}|{ B}, { C}) = \frac{P({ B}|{ A}, { C})P({ A} | { C})}{P({ B} | { C})} $$

We can also write

$$ P(A|B,C) = \frac{P(A,B,C)}{P(B,C)} = \frac{P(B,C|A)P(A)}{P(B,C)} $$

**Odds Form of Bayes' Rule**

$$ \frac{P({ A}| { B})}{P({ A^c}| { B})} = \frac{P({ B}|{ A})}{P({ B}| { A^c})}\frac{P({ A})}{P({ A^c})}$$

The _posterior odds_ of $A$ are the _likelihood ratio_ times the _prior odds_.

## Expected Value and Variance

Expected Value

$$E(X) = \sum\limits_{i}x_iP(X=x_i)$$

For any r.v.s $X$ and $Y$, and constants $a,b,c,$

$$E(aX + bY + c) = aE(X) + bE(Y) + c$$

Same distribution implies same mean - If $X$ and $Y$ have the same distribution, then $E(X)=E(Y)$ and, more generally,

$$E(g(X)) = E(g(Y))$$

Conditional Expected Value is defined like expectation, only conditioned on any event $A$.

$$ E(X | A) = \sum\limits_{x}xP(X=x | A)$$

Variance and Standard Deviation

$${Var}(X) = E \left(X - E(X)\right)^2 = E(X^2) - (E(X))^2$$

## Continuous RVs

### Continuous Random Variables (CRVs)

A continuous random variable can take on any possible value within a certain interval (for example, [0, 1]), whereas a discrete random variable can only take on variables in a list of countable values.

The probability that a continuous random variable takes on any specific value is 0.

$$F'(x) = f(x)$$

$$E(X) = \int^\infty_{-\infty}xf(x)dx $$

### LOTUS

-   The expected value of $X$ is defined this way:

$$E(X) = \sum_x xP(X=x) \textnormal{ (for discrete $X$)}$$

$$E(X) = \int^\infty_{-\infty}xf(x)dx \textnormal{ (for continuous $X$)}$$

-   The Law of the Unconscious Statistician (LOTUS) states that you can find the expected value of a function of a random variable, $g(X)$, in a similar way, by replacing the $x$ in front of the PMF/PDF by $g(x)$ but still working with the PMF/PDF of $X$:

$$ E(g(X)) = \sum_x g(x)P(X=x) \textnormal{ (for discrete $X$)} $$

$$E(g(X)) = \int^\infty_{-\infty}g(x)f(x)dx \textnormal{ (for continuous $X$)}$$

-   _What's a function of a random variable? A function of a random variable is also a random variable. For example, if $X$ is the number of bikes you see in an hour, then $g(X) = 2X$ is the number of bike wheels you see in that hour and $h(X) = {X \choose 2} = \frac{X(X-1)}{2}$ is the number of pairs of bikes such that you see both of those bikes in that hour._

### Universality of Uniform (UoU)

When you plug any CRV into its own CDF, you get a Uniform(0,1) random variable. When you plug a Uniform(0,1) r.v.~into an inverse CDF, you get an r.v.~with that CDF. For example, let's say that a random variable $X$ has CDF

$$F(x) = 1 - e^{-x}, \textrm{ for $x>0$} $$

By UoU, if we plug $X$ into this function then we get a uniformly distributed random variable.

$$F(X) = 1 - e^{-X} \sim \textrm{Unif}(0,1)$$

Similarly, if $U \sim \textrm{Unif}(0,1)$ then $F^{-1}(U)$ has CDF $F$. The key point is that for any continuous random variable, we can transform it into a Uniform random variable and back by using its CDF.

## Moments

Moments describe the shape of a distribution.

Let $X$ have mean $\mu$ and standard deviation $\sigma$, and $Z=(X-\mu)/\sigma$ be the _standardized_ version of $X$. The $k$th moment of $X$ is $\mu_k = E(X^k)$ and the $k$th standardized moment of $X$ is $m_k =E (Z^k)$.

The mean, variance, skewness, and kurtosis are important summaries of the shape of a distribution.

### Moment Generating Functions

For any random variable $X$, the function

$$ M_X(t) = E(e^{tX}) $$

is the **moment generating function (MGF)** of $X$, if it exists for all $t$ in some open interval containing $0$.

MGF of linear functions: If we have $Y = aX + b$, then

$$M_Y(t) = E(e^{t(aX + b)}) = e^{bt}E(e^{(at)X}) = e^{bt}M_X(at)$$

Uniqueness: If it exists, the MGF uniquely determines the distribution. This means that for any two random variables $X$ and $Y$, they are distributed the same (their PMFs/PDFs are equal) if and only if their MGFs are equal.

Summing Independent RVs by Multiplying MGFs: If $X$ and $Y$ are independent, then

$$M_{X+Y}(t) = E(e^{t(X + Y)}) = E(e^{tX})E(e^{tY}) = M_X(t) \cdot M_Y(t) $$

The MGF of the sum of two random variables is the product of the MGFs of those two random variables.

## Joint PDFs and CDFs

### Joint Distributions

The joint CDF of $X$ and $Y$

$$F(x,y)=P(X \leq x, Y \leq y) $$

In the discrete case, $X$ and $Y$ have a **joint PMF**

$$p_{X,Y}(x,y) = P(X=x,Y=y)$$

In the continuous case, they have a **joint PDF**

$$f_{X,Y}(x,y) = \frac{\partial^2}{\partial x \partial y} F_{X,Y}(x,y).$$

The joint PMF/PDF must be nonnegative and sum/integrate to 1.

### Conditional Distributions

Conditioning and Bayes' rule for discrete r.v.s

$$ P(Y=y|X=x) = \frac{P(X=x, Y=y)}{P(X=x)} = \frac{P(X=x|Y=y)P(Y=y)}{P(X=x)}$$

Conditioning and Bayes' rule for continuous r.v.s

$$f_{Y|X}(y|x) = \frac{f_{X,Y}(x, y)}{f_X(x)} = \frac{f_{X|Y}(x|y)f_Y(y)}{f_X(x)}$$

Hybrid Bayes' rule

$$f_X(x|A) = \frac{P(A | X = x)f_X(x)}{P(A)}$$

### Marginal Distributions

To find the distribution of one (or more) random variables from a joint PMF/PDF, sum/integrate over the unwanted random variables.

Marginal PMF from joint PMF

$$P(X = x) = \sum_y P(X=x, Y=y)$$

Marginal PDF from joint PDF

$$f_X(x) = \int_{-\infty}^\infty f_{X, Y}(x, y) dy$$