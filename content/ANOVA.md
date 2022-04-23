---
Area: Statistics
Source: Book
Status: Todo
Type: Notes
---


## ANOVA

ANOVA permits comparisons of multiple populations and even subgroups.

### One-way ANOVA

The design matrix has a special form:

$$\mathbf{X}=\left[\begin{array}{cccc}1 & 0 & 0 & 0 \\& \vdots & & \\1 & 0 & 0 & 0 \\0 & 1 & 0 & 0 \\& \vdots & & \\0 & 1 & 0 & 0 \\0 & 0 & 1 & 0 \\& \vdots & & \\0 & 0 & 1 & 0 \\0 & 0 & 0 & 1 \\& \vdots & & \\0 & 0 & 0 & 1\end{array}\right]$$

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
