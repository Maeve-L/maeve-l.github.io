---
Area: Statistics
Source: Book
Status: Todo
Type: Notes
---

## 1 线性时间序列模型

### 1.1 平稳性

**时间序列**：设有随机变量序列 $\{ x_t, t=\dots, -2, -1, 0, 1, 2, \dots \}$， 称其为一个时间序列。

**自协方差函数**： 时间序列$\{ X_t \}$中两个随机变量的协方差 $\text{Cov}(X_s, X_t)$叫做自协方差。 如果$\text{Cov}(X_s, X_t) = \gamma_{|t-s|}$仅依赖于t-s， 则称
$$
\gamma_k = \text{Cov}(X_{t-k}, X_t), k=0,1,2,\dots
$$
为时间序列$\{X_t \}$的自协方差函数。

**弱平稳序列**(宽平稳序列，weakly stationary time series): 如果时间序列$\{ X_t \}$存在有限的二阶矩且满足：

 (1) $EX_t = \mu$与$t$无关；

 (2) $\text{Var}(X_t) = \gamma_0$与$t$无关;

 (3) $\gamma_k = \text{Cov}(X_{t-k}, X_t), k=1,2,\dots$与$t$无关，

则称$\{ X_t \}$为弱平稳序列。

适当条件下可以用时间序列的样本估计自协方差函数， 这是用一条轨道的信息推断所有实验结果$\Omega$， 估计公式为
$$
\hat\gamma_k = \frac{1}{T} \sum_{t=k+1}^T (x_{t-k} - \bar x)(x_t - \bar x), k=0,1,\dots, T-1
$$
称$\hat\gamma_k$为样本自协方差。 注意这里用了$1/T$而不是$1/(T-k)$，用$1/(T-k)$在获得无偏性的同时会造成一些理论上的困难。



### 1.2 相关系数和自相关函数

#### 1.2.1 相关系数

两个随机变量X和Y的相关系数定义为
$$
\rho(X,Y) = \rho_{xy} = \frac{\text{Cov}(X,Y)}{\sqrt{\text{Var}(X) \text{Var}(Y)}} = \frac{E[(X-\mu_x)(Y-\mu_y)]}{\sqrt{E(X-\mu_x)^2 E(Y-\mu_y)^2}}
$$


如果有$(X,Y)$的独立同分布样本$(x_t, y_t)， t=1,2,\dots,T$， 可估计相关系数为
$$
\hat\rho_{xy} = \frac{\sum_{t=1}^T (x_t - \bar x)(y_t - \bar y)} {\sqrt{\sum_{t=1}^T (x_t - \bar x)^2 \sum_{t=1}^T (y_t - \bar y)^2}}
$$
#### 1.2.2 自相关函数

设$\{X_t \}$为弱平稳序列， $\{ \gamma_k \}$为自协方差函数。 则
$$
\rho(X_{t-k}, X_t)  = \frac{\text{Cov}(X_{t-k}, X_t)}{\sqrt{\text{Var}(X_{t-k})\text{Var}(X_{t})}} = \frac{\gamma_k}{\sqrt{\gamma_0 \gamma_0}} = \frac{\gamma_k}{\gamma_0}, \ k=0,1,\dots, \ \forall t
$$
记$\rho_k = \gamma_k / \gamma_0$，这是$X_{t-k}$与$X_t$的相关系数且与$t$无关， 称$\{ \rho_k, k=0,1,\dots \}$为时间序列$\{ X_t \}$的自相关函数 （Autocorrelation function, ACF）。

适当条件下$\rho_k$可以从时间序列样本估计为
$$
\hat\rho_k = \frac{\hat\gamma_k}{\hat\gamma_0},\  k=0,1,\dots
$$
称$\hat\rho_k, k=1,2,\dots$为样本自相关函数。

#### 1.2.3 用单个自相关系数作白噪声检验

如果$\{ X_ t \}$是独立同分布白噪声， 则$\rho_k(k\geq 1)$近似$\text{N}(0, 1/T)$。 若$H_0$是序列为白噪声， 取统计量
$$
t = \sqrt{T} \hat\rho_k
$$

如果$|t| > \text{qnorm}(1-\alpha/2)$， 则拒绝白噪声零假设。 实际中常取$\alpha=0.05, \text{qnorm}(1-\alpha/2) \approx 2$， 当$\hat\rho_1$超出$\pm 2 /\sqrt{T}$则拒绝$H_0$

#### 1.2.4 Ljung-Box白噪声检验

为了检验时间序列样本是否来自白噪声序列， 可以检验$\rho_k=0, k=1,2,\dots$的零假设。 前面检验单个$\rho_k$的做法如果针对多个进行检验就有多重检验的第一类错误增大的问题。

Ljung和Box对此检验方法进行了改进。 统计量改为
$$
Q(m) = T(T+2) \sum_{j=1}^m \frac{\hat\rho_j^2}{T-j}
$$
在独立同分布白噪声假设下仍近似服从$\chi^2(m)$分布。 当
$$
Q(m) > \text{qchisq}(1-\alpha, m)
$$
时拒绝$H_0$， 否定白噪声假设。这个检验称为Ljung-Box白噪声检验。 如果检验的序列是线性时间序列估计的残差序列， 则卡方自由度应改为$m$减去估计的系数个数。

Ljung-Box检验受到$m$取值的影响， 建议采用$m \approx \ln T$，且序列为季度、月度这样的周期序列时， $m$应取为周期的整数倍。

### 1.3 白噪声和线性时间序列

设$\{ X_t \}$是独立同分布的二阶矩有限的随机变量， 称$\{ X_t \}$为独立同分布白噪声(white noise)。 最常用的白噪声一般假设均值为零。 如果$\{ X_t \}$独立同$\text{N}(0, \sigma^2)$分布， 称$\{ X_t \}$为高斯(Gaussian)白噪声或正态白噪声。

## 2 自回归模型

### 2.1 AR(1)模型的性质

AR(1)：
$$
\begin{align}
X_t = \phi_0 + \phi_1 X_{t-1} + \varepsilon_t
\end{align}
$$

AR(1)模型要求$|\phi_1|<1$，$\{ X_t \}$有弱平稳解的充分必要条件。

必要性证明： 如果模型有弱平稳解$X_t$， 因为要求$\varepsilon_t$与$X_{t-1}, X_{t-2}, \dots$独立， 在模型两边求方差得
$$
\begin{aligned} & \text{Var}(X_t) = \text{Var}(\phi_0 + \phi_1 X_{t-1} + \varepsilon_t) = \phi_1^2 \text{Var}(X_{t-1}) + \sigma^2, \\ & \sigma_X^2 = \phi_1^2 \sigma_X^2 + \sigma^2, \\ & \sigma_X^2 = \frac{\sigma^2}{1 - \phi_1^2} \end{aligned}
$$
因为$\sigma_X^2>0$,所以$1-\phi_1^2>0,|\phi_1|<1$。

上述证明过程也证明了
$$
\mu=EX_t = \frac{\phi_0}{1 - \phi_1}, \quad \sigma_X = \text{Var}(X_t) = \frac{\sigma^2}{1 - \phi_1^2} .
$$

### 2.2 AR(1)模型的自相关函数

AR(1)模型的平稳解满足$\epsilon_t$与$X_{t-1}, X_{t-2}, \dots$独立。 
$$
\begin{align} \gamma_0 =& \sigma_X^2 = \frac{\sigma^2}{1 - \phi_1^2} = \phi_1 \gamma_1 + \sigma^2 \\ \gamma_j =& \phi_1 \gamma_{j-1}, \ j=1,2,\dots \end{align}
$$

于是ACF为
$$
\rho_j = \frac{\gamma_j}{\gamma_0} = \phi_1^j, \ j=1,2,\dots
$$

当$0<\phi_1 < 1$时， ACF为正的单调下降序列， 以负指数速度（几何级数）下降。 当$-1 < \phi_1 < 0$时， ACF为负正交替的序列， 绝对值以负指数速度下降。

### 2.3 AR(2)模型的性质

AR(2)模型为
$$
\begin{align}
X_t = \phi_0 + \phi_1 X_{t-1} + \phi_2 X_{t-2} + \varepsilon_t
\end{align}
$$

其中$\{\varepsilon_t \}$为独立同分布的零均值白噪声,$ \varepsilon_t$与$X_{t-1}, X_{t-2}, \dots$独立。 系数满足特征方程的根都在单位圆外。 特征方程为

$$
\begin{align}
1 - \phi_1 z - \phi_2 z^2 = 0
\tag{4.5}
\end{align}
$$

这个模型有因果线性时间序列形式的弱平稳解。 对(4.4)两边取期望得$\mu=EX_t$的方程
$$
\mu = \phi_0 + \phi_1 \mu + \phi_2 \mu
$$
所以
$$
\mu = \frac{\phi_0}{1 - \phi_1 - \phi_2}
$$

$X_t$减去$\mu$， 方程变成
$$
\begin{align}
X_t - \mu = \phi_1 (X_{t-1}-\mu) + \phi_2 (X_{t-2}-\mu) + \varepsilon_t

\end{align}
$$
两边乘以$X_{t-j}-\mu$， 并利用$\varepsilon_t$与$X_{t-1}, X_{t-2}, \dots$独立的性质，可得
$$
\gamma_j = \phi_1 \gamma_{j-1} + \phi_2 \gamma_{j-2}, \ j=1, 2, \dots
$$

两边除以$\gamma_0$得
$$
\begin{align}
\rho_j = \phi_1 \rho_{j-1} + \phi_2 \rho_{j-2}, \ j=1,2,\dots

\end{align}
$$
这种形式的递推称为齐次线性差分方程。 可以用滞后算子写成
$$
\begin{align}
(1 - \phi_1 B - \phi_2 B^2) \rho_j = 0, \ j=1,2,\dots

\end{align}
$$

特征多项式$1 - \phi_1 z - \phi_2 z^2=0$的根的判别式为 $\Delta = \phi_1^2 + 4 \phi_2$， 当$\phi_2 \geq -4 \phi_1^2$时为实根， 当$\phi_2 < -4 \phi_1^2$时为复根。 两个特征根都在单位圆外的充分必要条件是
$$
|\phi_1| < 2, \ |\phi_2| < 1,
\ \phi_2 < 1 \pm \phi_1
$$

有两个实根时，两个根为
$$
z_1, z_2 = \frac{\phi_1 \pm \sqrt{\phi_1^2 + 4\phi_2}}{-2\phi_2}
$$

这两个根的绝对值都大于1。 如果两个根都是正的，则$\rho_j$为正，呈现出负指数速度单调衰减。 如果两个根正负不同，则绝对值仍以负指数速度衰减但是不单调， 当负根绝对值更小时会正负交替衰减。

有共轭复根时，两个根为
$$
z_1, z_2 = \frac{\phi_1}{-2\phi_2} \pm i \frac{\sqrt{|\phi_1^2 + 4\phi_2}|}{-2\phi_2}
$$

复根的模为
$$
|z_i| = \frac{1}{\sqrt{-\phi_2}}
$$
辐角为
$$
\omega = \cos^{-1} \frac{\phi_1}{2\sqrt{-\phi_2}}
$$
反过来有
$$
\phi_2 = -\frac{1}{|z_1|^2},
\ \phi_2 = \frac{2}{|z_1|} \cos\omega
$$
$\omega$这个辐角对应的周期为
$$
P = \frac{2\pi}{\omega} = \frac{2\pi}{\cos^{-1} \frac{\phi_1}{2\sqrt{-\phi_2}}}
$$
这样的AR(2)模型会体现出随机地平均以周期P的波动； $\rho_j$序列呈现出以周期P震荡的幅度负指数衰减的变化。

### 2.4 AR(p)模型的性质

对于一般的AR(p)模型， 其ACF的性质以及序列的随机周期， 也由其特征根决定。 ACF可以是单调衰减、震荡衰减、正负交替衰减、呈周期震荡衰减。 在有复特征根根或者有接近-1的特征根时时间序列呈现出一定的随机周期变化。

由平稳性得
$$
\mu = \frac{\phi_0}{1 - \phi_1 - \dots - \phi_p}
$$
自相关函数(ACF)满足如下的递推（差分方程）
$$
(1 - \phi_1 B - \dots - \phi_p B^p) \rho_j = 0, \ j=1,2,\dots
$$
AR(p)模型的平稳解是线性时间序列。

### 2.5 偏自相关函数

实际数据用AR模型建模时，阶数p是未知的， 确定p的问题称为定阶。 一般常用偏自相关函数和AIC准则。

$\phi_{nn}$实际是$X_t$与$X_{t-n}$在扣除$X_{t-2}, \dots, X_{t-n+1}$的影响后的偏相关系数。
$$
\begin{array}{l}{\phi_{11}=\rho_{1}} \\ {\phi_{22}=\left(\rho_{2}-\rho_{1}^{2}\right) /\left(1-\rho_{1}^{2}\right)} \\ {\phi_{ss}=\frac{\rho_{s}-\sum_{j=1}^{s-1} \phi_{s-1, j} \rho_{s-j}}{1-\sum_{j=1}^{s-1} \phi_{s-1, j} \rho_{j}}, \quad s=3,4,5, \ldots}\\\phi_{s j}=\phi_{s-1, j}-\phi_{s s} \phi_{s-1, s-j}, j=1,2,3, \ldots, s-1\end{array}
$$
AR(p)序列的样本偏自相关函数$\hat\phi_{kk}$满足如下性质：

- $T\to\infty$时$\hat\phi_{pp} \to \phi_p \neq 0$。
- 对$k>p, \hat\phi_{kk} \to 0(T\to\infty)$。
- 对$k>p,\hat\phi_{kk}$渐近方差为$\frac{1}{T}$。


### 2.6 信息准则

AIC准则（Akaike’s Information Criterion）：
$$
\text{AIC} = -\frac{2}{T}\ln(\text{似然函数值}) + \frac{2}{T} (\text{参数个数})
$$

其中似然函数值是在参数最大似然估计处的似然函数值。 当模型为高斯AR(p)，AIC公式为
$$
\text{AIC}(k) = \ln \tilde\sigma_k^2 + \frac{2k}{T}
$$

其中$k$是模型的阶， $\tilde\sigma_k^2$是阶为$k$的条件下$\varepsilon_t$的方差的最大似然估计。 $\ln \tilde\sigma_k^2$代表了模型对数据的拟合优劣， 此值越大拟合越差；$ \frac{2k}{T}$是对模型复杂程度的惩罚，此值越大，模型越复杂，稳定性越差，对未来的情况的适应性也越差。 

另一个常用的信息准则是BIC准则(Bayesian Information Criterion)， 高斯AR模型为：
$$
\text{BIC}(k) = \ln \tilde\sigma_k^2 + \frac{k \ln T}{T}
$$
BIC倾向于取比AIC更低阶的模型。

大样本时BIC比AIC更准确些。小样本时AIC比BIC更准确些。


### 2.7 AR模型参数估计方法

AR模型有多种估计方法， 比如，用普通线性回归的最小二乘法估计， 假设正态分布用最大似然估计， Yule-Walker递推计算， Burg递推计算，等等。

OLS估计的问题：

- 误差序列相关问题、一致性问题
- OLS无偏性的前提是：线性模型、随机抽样、非完全共线性、外生性
- 时间序列数据不满足随机抽样
  - 误差自相关
  - 外生性出问题：不能满足无偏性

- 比较宽的假设：满足一致性
  - 线性模型弱相关并满足外生、非完全共线性

### 2.8 AR模型检验

拟合AR模型后， 如果模型是能够准确表示数据的规律的， 则拟合的残差应该近似为白噪声， 应该能通过白噪声检验。 因为残差是从模型估计计算得到的， 自由度有损失。


### 2.9 AR模型拟合优度指标

类似于线性回归模型的拟合优度判断， 在线性时间序列建模中，也可以定义如下的拟合优度R^2统计量

比如，拟合了AR(p)模型后，可以计算$R^2$为
$$
R^2 = 1 - \frac{\sum_{t=p+1}^T e_t^2}{\sum_{t=p+1}^T (x_t - \bar x)^2}
$$
其中$\bar x = \frac{1}{T-p} \sum_{t=p+1}^T x_t$。$0 \leq R^2 \leq 1$。

$R^2$越大， 说明模型对数据拟合越好，残差越小。

调整的$R^2$指标(adjusted $R^2$)，定义为
$$
R_{\text{Adj}}^2 = 1 - \frac{\hat\sigma^2}{\hat\sigma_x^2}
$$
其中$\hat\sigma^2$是新息方差$\sigma^2$的估计，$\hat\sigma_x^2$是$X_t$的样本方差。

### 2.10 用估计的AR模型进行预测

#### 2.10.1 超前一步预测

对$\ell=1$，因为
$$
X_{h+1} = \phi_0 + \phi_1 X_{h} + \dots + \phi_p X_{h+1-p} + \varepsilon_{h+1}
$$

以及$E(\varepsilon_{h+1}|X_1, \dots, X_h)=0$，有
$$
\hat x_h(1) = E(X_{h+1} | X_1,\dots, X_h)
= \phi_0 + \phi_1 X_{h} + \dots + \phi_p X_{h+1-p}
$$

一步预测误差为
$$
e_h(1) = x_{h+1} - \hat x_h(1) = \varepsilon_{h+1},
\ \text{Var}(e_h(1)) = \sigma^2
$$

可见模型中的新息方差$\sigma^2$也是超前一步预测的均方误差。

如果$\varepsilon_t$服从正态分布，则$X_{h+1}$的超前一步预测的95%预测区间为$\hat x_h(1) \pm 1.96 \sigma$。

对于时间序列数据， 真实的系数$\phi_i$是未知的， 只能得到估计量$\hat\phi_i$， 当T充分大时可以在预测公式中用$\hat\phi_i$代替$\phi_i$进行预测。这样得到的预测区间是不够准确的。

#### 2.10.2 超前二步预测

预测误差为

$$
e_h(2) = x_{h+2} - \hat x_h(2) = \phi_1 e_h(1) + \varepsilon_{h+2}
$$

预测均方误差为
$$
E[e_h(2)]^2  = \text{Var}(e_h(2)) = \sigma^2(1 + \phi_1^2)
$$
这里用到了$\varepsilon_{h+2}$与$e_h(1) = x_{h+1} - \hat x_h(1)$独立。 显然超前两步预测均方误差大于等于超前一步均方误差， 这对一般情况都是合理的， 预测得越远， 我们现有知识的作用就越小。

#### 2.10.3 超前多步预测

对平稳AR(p)模型， 当超前步数$\ell\to+\infty$时， $\hat x_h(\ell) \to \mu$。 这种性质称为均值回转(mean reversion)。

对AR(1)模型的零均值平稳解$\{ x_t \}$， 可以看出
$$
\hat x_h(\ell) = \phi_1^\ell x_h
$$
这也是与极限0之间的差距， 而$|\phi_1|^\ell$则代表了趋向于极限的速度， 当$|\phi_1|^\ell=\frac12$时趋向于极限0就可以认为极限过程已经到了一半， 这个$\ell=\ln(0.5)/\ln|\phi_1|$称为均值回转的半衰期。 半衰期越短， 多步预报的作用越差。

#### 2.10.4 样本外预测误差

滚动样本外预测

- 没有明显系统偏差
- 用观察值对预测值做回归，$H_0:\alpha=0,\beta=1$
- F检验

Granger-Newbold检验

构造$x_t$和$z_t$序列，使得$x_t=e_{1t}+e_{2t}$和$z_t=e_{1t}-e_{2t}$，得到相关系数为$r_{xz}$

构造统计量：
$$
t=\frac{r_{xz}}{\sqrt{(1-r_{xz}^2)(H-1)}}
$$
$H$是保留期内的观测值。

如果统计量不显著，就可以得出两个模型的预测效果无差异。

## 3 移动平均模型

### 3.1 移动平均模型的概念

移动平均模型是具有q步外不相关性质的平稳列的模型； 对于高阶的AR模型， 有些可以用低阶的MA模型更好地描述。 一般的AR模型也可以用高阶MA模型近似。

一般地，若$\{ \varepsilon_t \}$是零均值独立同分布白噪声，方差为$\sigma^2$，$|\theta_1| < 1$， 令
$$
X_t = \theta_0 + \varepsilon_t + \theta_1 \varepsilon_{t-1}
$$
易见$\{ X_t \}$为线性时间序列形式的弱平稳列， 称为MA(1)序列。

类似地，MA(2)序列的模型为
$$
X_t = \theta_0 + \varepsilon_t + \theta_1 \varepsilon_{t-1} + \theta_2 \varepsilon_{t-2}
$$

MA(q)序列的模型为
$$
X_t = \theta_0 + \varepsilon_t + \theta_1 \varepsilon_{t-1} + \dots + \theta_2 \varepsilon_{t-q}
$$

此模型也有特征多项式
$$
1 + \theta_1 z + \dots + \theta_q z^q
$$

特征方程的根称为特征根，特征根都在单位圆外的条件称为MA模型的可逆条件。

### 3.2 移动平均模型的性质

#### 3.2.1 平稳性与自相关函数性质

以MA(1)为例。$X_t = \theta_0 + \varepsilon_t + \theta_1 \varepsilon_{t-1}$， 其中$\{ \varepsilon_t \}$是零均值独立同分布白噪声，$\theta_0, \theta_1$是任意实数，平稳性不需要特征根的条件。

易见
$$
E X_t = \theta_0, \ \forall t ,
\quad
\text{Var}(X_t) = \sigma^2(1 + \theta_1^2)
$$
$$
\gamma_k = \begin{cases}
\sigma^2(1 + \theta_1^2), & k=0 \\
\sigma^2 \theta_1, & k=1, \\
0, & k>1
\end{cases}
$$

相应地，MA(1)的自相关函数为
$$
\rho_k = \begin{cases}
1, & k=0 \\
\frac{\theta_1}{1 + \theta_1^2}, & k=1, \\
0, & k>1
\end{cases}
$$
这就验证了MA(1)序列是弱平稳列。 MA(1)的自相关函数在k>1后为零的性质叫做MA序列的自相关函数截尾性。

对于MA(q)序列
$$
X_t = \theta_0 + \varepsilon_t + \theta_1 \varepsilon_{t-1} + \dots + \theta_q \varepsilon_{t-q}
$$

易见
$$
EX_t = \theta_0, 
\quad
\text{Var}(X_t) = \sigma^2(1 + \theta_1^2 + \dots + \theta_q^2)
$$
其自相关函数$\rho_k$也满足q后截尾性， 即$\rho_{k}=0, \forall k > q$。如果$\theta_q \neq 0$，则$\rho_q \neq 0$。

自相关系数：
$$
\rho_{j}=\left\{\begin{array}{ll}{\frac{\theta_{j}+\sum_{i=1}^{q-j} \theta_{i} \theta_{i+j}}{1+\theta_{1}^{2}+\cdots+\theta_{q}^{2}},} & {j=1,2, \cdots, q} \\ {0,} & {j>q} \\ {\rho_{-j},} & {j<0}\end{array}\right.
$$


#### 3.2.2 可逆性

对MA(1)模型， 当$|\theta_1|<1$时， 根据本章开始的推导可得
$$
\varepsilon_t = -\phi_0 + X_t + \sum_{j=1}^\infty (-\theta_1)^j X_{t-j}
$$

其中的级数是可以在a.s.意义和均方意义下收敛的。 这表明新息$\varepsilon_t$可以用当前的观测$X_t$以及历史观测$X_{t-j}, j=1,2,\dots$的线性组合表示， 而且历史观测$X_{t-j}$所在时刻离$t$时刻越远， 其作用越小。这种性质叫做模型的可逆性。 MA模型的平稳性不需要可逆性条件， 但是从理论讨论的角度，可逆的线性时间序列更合理：$\{ X_t, X_{t-1}, \dots \}$与$\{\varepsilon_t, \varepsilon_{t-1}, \dots \}$可以互相线性表示， 对任意$t \in \mathbb Z$成立。

### 3.3 移动平均模型定阶

MA(q)序列的理论自相关函数$\rho_k$在q后截尾，$\rho_q\neq 0, \rho_k=0, k>q$。

在$\{ X_t \}$为独立同分布白噪声列的条件下， $k>0$的$\hat\rho_k$渐近$\text{N}(0, \frac{1}{T})$分布，所以查看ACF图，最后一个显著不等于零的$\hat\rho_k$的位置可以暂定为MA模型的阶。

也可以用AIC定阶：
$$
\text{AIC}(k)
=\ln \hat\sigma_k^2 + \frac{2k}{T}
$$
其中$\hat\sigma_k^2$是用MA(k)建模时新息方差的最大似然估计。

### 3.4 移动平均模型的估计

MA模型参数的估计方法有：

矩估计法

逆相关函数法，将MA模型转换为长阶自回归模型，用估计自回归模型的方法估计，能保证可逆性；

新息估计法；

条件最大似然估计法；

精确最大似然估计法。

条件最大似然估计法和完全最大似然估计法都假定$\{\varepsilon_t \}$为高斯白噪声， 计算似然函数。在条件最大似然估计法中， 近似假定$\varepsilon_t=0, t \leq 0$， 这样就可以得到
$$
\varepsilon_1 = x_1 - \theta_0, \varepsilon_{2} = x_2 - \theta_0 - \theta_1 \varepsilon_1
$$

等递推表示， 将其代入$\varepsilon_t, t=1,2,\dots,T$的独立联合正态分布密度中就得到了条件似然函数， 求其关于$\sigma^2$和$\theta_0, \theta_1, \dots, \theta_q$的最大值点。

在精确最大似然估计中，将$\varepsilon_t, t=1-q, 2-q, \dots, -1, 0$也作为未知参数， 与其它模型参数一起估计。


### 3.5 移动平均模型的预测

因为MA(q)序列在间隔超过q步以后就独立， 所以超前多步预测， 只能预测到q步， 从q+1步开始就只能用均值$\mu$预测了。

以MA(1)为例，
$$
X_t = \theta_0 + \varepsilon_t + \theta_1 \varepsilon_{t-1}
$$
超前一步：
$$
\hat x_h(1) = E(X_{h+1}|x_1, \dots, x_h)
= \theta_0 + \theta_1 \varepsilon_{h}
$$


超前两步:
$$
\hat x_h(2) = E(\theta_0 + \varepsilon_{h+2} + \theta_1 \varepsilon_{h+1} | x_1, \dots, x_h) = \theta_0
$$


### 3.6 AR和MA的小结

对MA(q)模型，ACF对定阶有意义，因为其q后截尾；

对AR(p)模型，PACF对定阶有意义，因为其p后截尾；

MA模型的序列不管系数如何总是平稳的， 实际上还是因果线性时间序列， 当特征根都在单位圆外时是可逆的；

AR模型只有当特征根都在单位圆外时才有$\epsilon_t $与$X_{t-1}, X_{t-2}, \dots$独立的弱平稳解；

对AR和MA序列，超前多步预测趋于序列的均值， 预测均方误差趋于序列的方差。



## 4 ARMA模型

### 4.1 ARMA(1,1)

$$
(1 - \phi_1 B) X_t = \phi_0 + (1 + \theta_1 B) \varepsilon_t
$$

形式地，
$$
\begin{aligned} \frac{1}{1 - \phi_1 z} =& \sum_{j=0}^\infty \phi_1^j z^j, \\ \frac{1}{1 - \phi_1 B} =& \sum_{j=0}^\infty \phi_1^j B^j, \\ \frac{1 + \theta_1 z}{1 - \phi_1 z} =& 1 + (\phi_1 + \theta_1) \sum_{j=1}^\infty \phi_1^{j-1} z^j, \\ \frac{1 + \theta_1 B}{1 - \phi_1 B} =& 1 + (\phi_1 + \theta_1) \sum_{j=1}^\infty \phi_1^{j-1} B^j, \end{aligned}
$$
于是
$$
\begin{align} X_t =& \frac{1}{1 - \phi_1 B} \left\{ \phi_0  + (1 + \theta_1 B) \varepsilon_t \right\} \nonumber\\ =& \frac{\phi_0}{1 - \phi_1} + \frac{1 + \theta_1 B}{1 - \phi_1 B}\varepsilon_t \nonumber\\ =& \frac{\phi_0}{1 - \phi_1} + \varepsilon_t  + (\phi_1 + \theta_1) \sum_{j=1}^\infty \phi_1^{j-1} \varepsilon_{t-j}\end{align}
$$
这是因果型线性时间序列，是弱平稳的，满足上述ARMA(1,1)模型方程。
$$
\begin{aligned} E X_t =&  \frac{\phi_0}{1 - \phi_1}, \\ \text{Var}(X_t) =& \sigma^2\left( 1 + (\phi_1+\theta_1)^2 \sum_{j=1}^\infty (\phi_1^2)^{j-1} \right) = \sigma^2 \frac{1 + \theta_1^2 + 2\phi_1 \theta_1}{1 - \phi_1^2} \end{aligned}
$$


由方差的表达式可知$|\phi_1|<1$是平稳性的必要条件。

ARMA(1,1)的自相关函数为
$$
\rho_k = \begin{cases} \dfrac{(\phi_1 + \theta_1)(1 + \phi_1 \theta_1)}{1 + 2\phi_1 \theta_1 + \theta_1^2}, & k=1 \\ \phi_1 \rho_{k-1} = \phi_1^{k-1} \rho_1, & k \geq 2 \end{cases}
$$


所以ARMA(1,1)的ACF与AR(1)的ACF很相似， 但是从$k=2$处才开始负指数衰减。 与AR类似， 自相关函数不能有限步截尾。

ARMA(1,1)的偏自相关函数与MA(1)的偏自相关函数类似， 但负指数衰减从$k=2$开始， 也不能在有限步截尾。

总之， ARMA(1,1)的平稳性条件与AR(1)相同， 自相关函数与偏自相关函数均不能有限步截尾 (设$\phi_1\neq 0, \theta_1 \neq 0$)。

### 4.2 一般ARMA模型

一般ARMA模型为
$$
X_t = \phi_0 + \phi_1 X_{t-1} + \dots + \phi_p X_{t-p} + \varepsilon_t + \theta_1 \varepsilon_{t-1} + \dots + \theta_q \varepsilon_{t-q}
$$

平稳解的均值为：
$$
EX_t = \frac{\phi_0}{1 - \phi_1 - \dots - \phi_p}
$$

### 4.3 ARMA模型的三种表示
设ARMA(p,q)模型的系数满足平稳性条件与可逆性条件。

第一种表示：
$$
(1 - \phi_1 B - \dots - \phi_p B^p) X_t
= \phi_0 + (1 + \theta_1 B + \dots + \theta_q B^q) \varepsilon_t
$$

#### 4.3.1 ARMA模型的MA表示

用滞后算子的性质， 令$P(z) = 1 - \sum_{j=1}^p \phi_p z^j, Q(z) = 1 + \sum_{j=1}^q \theta_q z^j$， 则
$$
\Psi(z) = \frac{Q(z)}{P(z)} = \sum_{j=0}^\infty \psi_j z^j
$$
其中$\{ \psi_j \}$绝对可和（实际上，$j\to\infty$时$c_j$以负指数速度衰减）。 所以
$$
X_t = \mu + \Psi(B) \varepsilon_t
= \mu + \sum_{j=0}^\infty \psi_j \varepsilon_{t-j}, \ t \in \mathbb Z
$$
这称为ARMA模型的MA表示或者Wold表示。

### 4.3.2 ARMA模型的AR表示

## 5 单位根过程

### 5.1 随机游动

考虑$\{ p_t \}$的模型
$$
\begin{align}
p_t = p_{t-1} + \varepsilon_t,
\ t=1,2,\dots
\end{align}
$$
其中$\{ \varepsilon_t \}$是零均值独立同分布白噪声列。称$\{ p_t \}$是一个随机游动(random walk)。

设$p_0=0$，单位根过程$\{p_t\}$有如下特点：

- $p_t$期望值等于0；
- $p_t$方差等于$\sigma^2 t$，随$t$线性增长，趋于无穷；
- 历史的扰动（新息）的影响不衰减；
- 预测只能用最后一个观测值作为预测， 预测均方误差趋于无穷。
- 样本ACF表现为基本不衰减，近似等于1。

### 5.2 带漂移的随机游动

模型可以推广为
$$
p_t = \mu + p_{t-1} + \varepsilon_t,
\ t=1,2,\dots
$$

其中$\{ \varepsilon_t \}$仍为零均值独立同分布白噪声列。 常数$\mu$并不代表均值， 而是对数价格$p_t$的增长速度，称为模型的漂移(drift)。 设初始价格为$p_0$，则
$$
\begin{aligned}
p_1 =& p_0 + \mu +  \varepsilon_1 \\
p_2 =& p_0 + 2\mu + \varepsilon_1 + \varepsilon_2 \\
& \cdots\cdots \\
p_t =& p_0 + t\mu + \varepsilon_1 + \dots + \varepsilon_t
\end{aligned}
$$

于是
$$
E(p_t | p_0) = p_0 + \mu t,
\quad
\text{Var}(p_t | p_0) = \sigma^2 t
$$
所以带漂移的随机游动与不带漂移的随机游动相比，其条件方差不变， 但是条件均值多了一个随t线性增长（若$\mu>0$）的$\mu t$项。

### 5.3 固定趋势模型

设$\{ X_t \}$为弱平稳时间序列 令
$$
Y_t = a + b t + X_t
$$
则
$$
EY_t = (a + \mu_x) + bt， \text{Var}(Y_t) = \text{Var}(X_t) = \sigma_x^2
$$
均值非常数所以$\{ Y_t \}$非平稳。 但是， 减去一个固定趋势$a + bt$后$\{ Y_t \}$就变成了平稳列， 这样的$\{ Y_t \}$与随机游动或者带漂移的随机游动有着本质的区别。

随机游动$p_t = p_{t+1} + \varepsilon_t$与固定趋势加扰动$Y_t = a + bt + X_t$都能呈现出缓慢的趋势变化。区别在于：

- 随机游动的方差是线性增长的， 固定趋势的观测值方差不变；
- 随机游动的扰动的影响是永久的， 固定趋势的扰动的影响仅在一个时刻（如果扰动$X_t$是白噪声） 或者很短时间（如果是扰动$X_t$是线性时间序列）；
- 随机游动的趋势没有固定方向， 固定趋势的变化形状是固定的；
- 固定趋势模型$Y_t$减去一个固定的回归函数$Y = a + bt$就可以变成平稳列， 随机游动减去任意的非随机函数都不能变平稳， 可以用差分运算变成平稳。
- 在AR和ARMA模型中， 常数项$\phi_0$与平稳均值有关。 但是在带漂移的随机游动模型中， 常数项$\mu$是每一步的平均增量，是固定线性趋势的斜率。 所以时间序列模型中的常数项可能会依模型的不同而具有迥然不同的含义。

### 5.4 ARIMA模型

将带漂移的随机游动模型中的白噪声替换成一个ARMA平稳列， 其主要的性质仍能保留。即
$$
Y_t = Y_{t-1} + \mu + X_t
$$
其中$\{ X_t \}$是零均值平稳可逆ARMA(p,q)平稳列。 这时有
$$
Y_t = Y_0 + \mu t + \sum_{j=1}^t X_j
$$

于是
$$
E(Y_t|Y_0) = Y_0 + \mu t,
\quad
\text{Var}(Y_t | Y_0)
= \text{随}t\text{增大而趋于}\infty
$$

称$\{ Y_t \}$服从ARIMA(p,1,q)模型， 是非平稳的。$ \{Y_t\}$不能通过减去任何的非随机趋势变成平稳。 但是， 差分运算
$$
\Delta Y_t = (1-B)Y_t = Y_t - Y_{t-1} = \mu + X_t
$$
将ARIMA(p,1,q)序列$\{Y_t\}$转化成平稳可逆的ARMA(p,q)序列。


如果$Y_t$本身已经是弱平稳列， 则不应对$Y_t$进行差分。 如果$Y_t$是非随机的线性趋势加平稳列， 虽然差分能将其变成平稳列， 但是也不应该使用差分来做而是应该用回归来做， 用差分来做会在ARMA模型的MA部分引入不必要的单位根。

### 5.5 单位根检验

单位根非平稳列是金融中最常用的非平稳模型， 单位根非平稳列不能使用平稳列的模型来建模。 所以， 要建模的序列应该进行“单位根检验”。

对不带漂移的单位根过程， 考虑如下的基础模型：
$$
\begin{align}
p_t = \phi_1 p_{t-1} + \varepsilon_t

\end{align}
$$
其中$\{\varepsilon_t\}$是零均值独立同分布白噪声列。$ |\phi_1| \leq 1$。 考虑如下零假设与对立假设：
$$
H_0: \phi_1 = 1
\longleftrightarrow
H_a: \phi_1 < 1
$$

这样的检验问题称为单位根检验问题。 基础模型也可以是带有常数项的：
$$
\begin{align}
p_t = \phi_0 + \phi_1 p_{t-1} + \varepsilon_t

\end{align}
$$

对模型作最小二乘估计
$$
\hat\phi_1 = \frac{\sum_{t=1}^T p_{t-1}p_t}{\sum_{t=1}^T p_t^2},
\quad
\hat\sigma^2 = \frac{1}{T-1} \sum_{t=1}^T (p_t - \hat\phi_1 p_{t-1})^2
$$

其中$p_0=0, T$为样本量。取检验统计量
$$
\text{DF} = \frac{\hat\phi_1 - 1}{\text{SE}(\hat\phi_1)}
= \frac{\sum_{t=1}^T p_{t-1} e_t}{\hat\sigma \sqrt{\sum_{t=1}^T p_{t-1}^2}}
$$

当$T$充分大时在$H_0$下有渐近分布， 当DF统计量足够小的时候拒绝$H_0$。 p值一般通过随机模拟计算。 这个检验称为Dicky-Fuller检验。

在使用作为基础模型时， 如果实际上$\phi_0=0$， 则DF统计量也有非标准的渐近分布， 可以用随机模拟方法计算p值。 如果实际上$\phi_0\neq 0$， 则DF统计量渐近正态分布，但是需要很大的样本量。

许多经济和金融序列并不能仅用随机游动来描述， 可能需要用ARIMA。 因为ARMA模型可以看成长阶自回归， 所以检验是否ARIMA模型， 可以用$q=0$的ARIMA作为基础模型。 对序列$\{ x_t \}$为了检验其是否有单位根， 考虑如下的基础模型：
$$
\begin{align}
X_t = c_t + \beta X_{t-1} + \sum_{j=1}^{p-1} \phi_j \Delta X_{t-j} + e_t

\end{align}
$$
当$\beta=1$时， 就是$\Delta X_t的AR(p-1)$模型； 当$\beta<1$时， 是$X_t$的$AR(p)$模型。$ c_t$是非随机的趋势部分， 可以取0，或常数，或$a + bt$这样的非随机线性趋势。 检验假设
$$
H_0: \beta = 1
\longleftrightarrow
H_a: \beta < 1
$$

如果拒绝$H_0$， 就说明没有单位根。 使用统计量
$$
\text{ADF} = \frac{\hat\beta - 1}{\text{SE}(\hat\beta)}
$$
当ADF统计量足够小的时候拒绝$H_0$。

基础模型也可以改写成
$$
\Delta X_t = c_t + \beta_c X_{t-1} + \sum_{j=1}^{p-1} \phi_j \Delta X_{t-j} + e_t
$$

其中$\beta_c = \beta-1$， 检验
$$
H_0: \beta_c = 0
\longleftrightarrow
H_a: \beta_c < 0
$$
这个检验称为ADF检验(Augmented Dicky-Fuller Test)。

注意，单位根DF检验和ADF检验都是在拒绝$H_0$（显著）时否认有单位根， 不显著时承认有单位根。

ADF检验倾向于把平稳过程检验为单位根过程的原因在于检验的设定：

- 一般的检验都是在有比较强的证据情况下，才拒绝$H_0$,即拒绝$H_0$难，不拒绝容易
- 这样规律在ADF检验中，$H_0$是单位根过程。所以倾向单位根
- 但另一方面，这个偏差（偏向单位根）问题的后果不严重,预测的精度可能更好

关于ADF检验的效率，其它几个特点：

- ADF检验的效率更依赖于数据的时间跨度，而不是观测值的个数。当然观察个数越多效率还是越高。这一点与波动率的估计类似
- 如果数据产生的本来过程没有常数项和趋势项等，加入它们到ADF检验中，会降低效率，即倾向判断为单位根
- 如果数据产生的本来过程有常数项和趋势项等，在ADF检验中没有加入，在大样本情况下，检验无效

### 5.5 区分和选择单位根模型

对有结构变化数据的单位根检验

- 比如数据在某一时间前后有跳跃，那么在做回归分析时，显然有时间趋势，这一点与带漂移的单位根相似
- 显然有非常高的自相关性，即小的观测值接着小的观测值，大的观测值接着大的观测值。自相关性=1就是单位根
- 因此，有结构变化数据会经常被检验为单位根，即使它本来是有结构变化的平稳过程。因此，要首先检查是否有结构变化。如果有：
  - 分阶段检验
  - 或者在检验回归模型中，加入结构变化虚拟变量

数据看，很难区分接近非平稳的平稳过程与非平稳过程。也很难区分确定性趋势与带漂移的单位根。

- 所以，要用经济学直观，经济学传统。传统的宏观经济学中Business Cycle认为宏观变量（比如GDP等）是确定性增长及周期合成，但Nelson and Plosser（1982）认为主要的宏观变量是带漂移的单位根过程

滞后项：

- 每个模型中选取适当的滞后差分项，以使模型的残差项是一个白噪声（主要保证不存在自相关）；可以用回归系数的t-值判定
  - 这里之所以可以用t检验，因为在用时间系列数据时，如果一个模型中解释变量有平稳的，也有非平稳的，那么平稳解释变量的系数估计是一致的，并且可以用t检验。
- 还可以用AIC/BIC选择

趋势项：

- 首先看数据图，判断是否应该有趋势项。很多情况下，数据有明显特征
- Sims, Stock, and Watson (1990)的另一个结论：如果一个时间系列数据的产生过程本来有确定性项（常数项/时间项），而检验模型正确地包含了这些项，那么可以对所有系数用通常的t检验和F检验。这是由于这时的收敛速度等于收敛最慢的那个参数的收敛速度

### 5.6 对时间序列取对数

- 表示增长率；均值和残差是积的关系
- 如果均值与波动的关系（而不是时间与波动的关系，尽管经常是均值与时间同步）成正比；再看是确定性趋势还是带漂移的随机趋势（看去均值后的波动与时间的关系），可以用ADF检验

## 6 季节模型

### 6.1 季节同比

- 对季节性增长率问题，一种简单的办法是用同比
  - 中国的CPI有同步和环比，环比CPI有季节性问题，而同比CPI有翘尾问题
  - “翘尾”因素，(carryover effects)，也称滞后影响，是计算同比价格指数中独有的、上年商品价格上涨对下一年价格指数的影响部分。
    - 如某一商品1995年前6个月价格均为每公斤0.5元，7月份上涨到1元，一直到1996年12月份均保持同一价格，虽然1996年价格保持稳定，但计算出来的1996年前6个月的同比价格指数却为200%，表明价格上涨一倍，这就是这一商品价格指数中的“翘尾”因素，是上年7月份价格上涨对下一年上半年价格指数的滞后影响。
  - 同比的问题是，基准点是去年同期，不能准确地反映最近的变化。因此基于同步数据的模型，可能不是最好的。

### 6.2 季节哑变量

确定性季节趋势

- 多由节（假）日安排影响，我们通过有效工作日或控制季节虚拟变量处理：
  - 加入一个工作日变量：28天等等
  - 加入四个季节虚拟变量：控制哑变量系数和为1

### 6.3 乘性季节模型

$$
(1-B)(1 - B^s) x_t = (1 - \theta B)(1 - \Theta B^s) \varepsilon_t
$$



### 6.4 X11分解

$$
y_{t}=T_{t}+C_{t}+S_{t}+u_{t}
$$



## 7 资产波动率模型特征

### 7.1 波动率的特征

波动率(volatility)指的是资产价格的波动强弱程度， 类似于概率论中随机变量标准差的概念。 波动率不能直接观测， 可以从资产收益率中看出波动率的一些特征。

- 存在波动率聚集(volatility clustering)
- 波动率随时间连续变化，一般不出现波动率的跳跃式变动
- 波动率一般在固定的范围内变化，意味着动态的波动率是平稳的
- 在资产价格大幅上扬和大幅下跌两种情形下， 波动率的反映不同， 大幅下跌时波动率一般也更大， 这种现象称为杠杆效应（leverage effect）

这些性质对波动率模型的提出、改进有重要意义， 许多新的波动率模型都是诊断原有模型不能反映上面的某型特征而提出的。 例如， EGARCH模型和TGARCH模型可以反映出波动率在价格上扬和下跌时的不对称性。

不同的波动率计算方法使用不同的数据源。例如， 对IBM股票有如下三种数据源：

- 每个交易日的日收益率；
- 伴随IBM股票的期权数据
- 盘中交易和报价的分笔数据；

分别可以计算如下三种不同的波动率：

- 作为日收益率的条件标准差（或条件方差），建模计算。
- 隐含波动率：根据期权的理论公式如BS公式， 从股票价格和期权价格数据反解出模型中的波动率， 这样的得到的波动率称为隐含波动率。 隐含波动率倾向于比用日收益率建模得到的波动率数值要大。 CBOE的VIX指数就是隐含波动率。
- 实际波动率：利用一天内所有的收益率数据， 如每5分钟的收益率，估计一天收益率的条件标准差。

类似于利率， 度量波动率的时间区间一般也取为一年， 波动率一般是年化波动率。 如果有了日收益率（条件标准差）， 可以将其乘以$\sqrt{252}$转换成年化的波动率。

估计将来回报的波动率：

- 两步法
  - 先估计历史上的波动率（第一步），再用一个时间系列模型预测波动率（第二步）。
  - 历史数据样本标准差就是第一步，ARMA模型经常被用在第二步。业界经常用一个最简单的ARMA模型作为第二步：单位根过程
  - 这类方法的优点是：简单、直观
  - 这类方法的缺点是：没有逻辑一致的理论基础：不能保证用来估计波动率的模型与用来预测波动率的模型来自同一个大模型
- 一步法：用一个模型直接估计历史上的波动率和预测将来的波动率
  - 直接用一个模型模拟有观测值的回报过程本身，这个模型中回报的条件标准差是一个时变的。我们可以用这个模型计算、预测波动率
  - 优点: 有严密的理论基础
  - 缺点: 不够稳健，估计困难、不够稳健、适应性不强

### 7.2 波动率模型的结构

本章的问题就是对$\hat\sigma_t$建模， 这种模型叫做条件异方差模型。 条件异方差模型分为两类：

- 用确定函数来刻画$\hat\sigma_t$的变化，ARCH和GARCH模型属于这一类；
- 用随机方程描述$\hat\sigma_t$的变化，随机波动率(RV)模型属于这一类。

### 7.3 波动率模型的建立

对资产收益率序列建立波动率模型需要如下四个步骤：

1. 通过检验序列的自相关性建立均值的方程， 必要时还可以引入适当的解释变量；
2. 对均值方程的残差作白噪声检验， 通过后，对残差检验ARCH效应；
3. 如果ARCH效应检验结果显著， 则指定一个波动率模型， 对均值方程和波动率方程进行联合估计；
4. 对得到的模型进行验证， 需要时做改进。

关于均值方程， 资产收益率一般没有自相关（注意，这并不是独立）或者仅有弱的自相关。 如果样本均值显著不等于零， 需要从数据中减去样本均值， 这称为**中心化**。 对某些日收益率或更高频的序列可能需要建立简单的AR模型。 某些情况下可以加入额外的解释变量或者与日期有关的解释变量， 比如反映周末的哑变量， 反映一月份的哑变量，等等。

### 7.4 ARCH效应的检验

为了检验ARCH效应， 先建立均值模型，拟合$\mu_t$，计算残差$a_t = r_t - \mu_t$。 用残差序列的平方$\{ a_t^2 \}$作ARCH效应检验。

有两种检验方法。 

一种是对$\{ a_t^2 \}$作Ljung-Box白噪声检验， 检验不显著时没有ARCH效应， 检验显著时有ARCH效应。

另一种检验方法是Engle提出的。 考虑如下的最小二乘问题：
$$
a_t^2 = \alpha_0 + \alpha_1 a_{t-1}^2 + \dots + \alpha_m a_{t-m}^2 + e_t, \ t=m+1, \dots, T
$$
其中$T$为样本量，$m$是适当的AR阶数，$e_t$为回归残差。 零假设为
$$
H_0: \ \alpha_1 = \dots = \alpha_m = 0
$$
拒绝$H_0$时有ARCH效应。 这称为Engle的拉格朗日乘子法检验。

## 8 ARCH模型

### 8.1 ARCH模型公式

基本思想是：

资产收益率的扰动序列$a_t = r_t - E(r_t | F_{t-1})$是前后不相关的， 但是前后不独立。

$a_t$的不独立性， 描述为$\text{Var}(r_t | F_{t-1}) = \text{Var}(a_t | F_{t-1})$ 可以用$a_t^2$的滞后值的线性组合表示。

具体地， ARCH(m)模型为
$$
\begin{align}
\begin{aligned}
a_t =& \sigma_t \varepsilon_t \\
\sigma_t^2 =& \alpha_0 + \alpha_1 a_{t-1}^2 + \dots + \alpha_m a_{t-m}^2
\end{aligned}
\tag{17.1}
\end{align}
$$

其中$\{ \varepsilon_t \}$是零均值单位方差的独立同分布白噪声， $\alpha_0>0， \alpha_j \geq 0, j=1,2,\dots,m$， 另外$\{ \alpha_j \}$还需要满足一些条件使得$\text{Var}(a_t)$有限， 类似于AR(p)序列的平稳性的特征根条件。


### 8.2 ARCH模型的性质

以最简单的ARCH(1)为例讨论模型的性质。 模型为
$$
a_t = \sigma_t \varepsilon_t,
\ \sigma_t^2 = \alpha_0 + \alpha_1 a_{t-1}^2
$$
其中$\alpha_0>0, 0 < \alpha_1 < 1$。

#### 8.2.1 无条件期望和方差

考虑$a_t$的无条件期望和方差。
$$
\begin{align}
E(a_t)
=& E[ E(a_t | F_{t-1})] \\
=& E[ E(\sigma_t \varepsilon_t | F_{t-1})]
= E[ \sigma_t E( \varepsilon_t | F_{t-1})] = 0
\end{align}
$$
即无条件期望为零。
$$
\begin{align}
\text{Var}(a_t)
=& E(a_t^2)
= E[ E(a_t^2 | F_{t-1})] \\
=& E[ E(\sigma_t^2 \varepsilon_t^2 | F_{t-1})]
= E[ \sigma_t^2 E(\varepsilon_t^2 | F_{t-1})]
= E(\sigma_t^2) \\
=& \alpha_0 + \alpha_1 E(a_{t-1}^2)
\end{align}
$$
因为$a_t$是平稳列， 所以$\text{Var}(a_t)$为常数， 所以
$$
\text{Var}(a_t)
= E(a_t^2)
= \frac{\alpha_0}{1 - \alpha_1}
$$
这要求$0 < \alpha_1 < 1$。

高阶的ARCH模型：
$$
E \sigma_t^2=\frac{\alpha_0}{1-\sum_{i=1}^m\alpha_i}
$$
平稳条件是：
$$
\sum_{i=1}^m\alpha_i<1
$$


#### 8.2.2 高阶矩

有些应用需要利用$a_t$的高阶矩， 例如， 为了研究$a_t$是否厚尾分布， 需要计算峰度， 峰度依赖于四阶矩。

高阶矩的存在要求(17.1)中的$\varepsilon_t$与$\{ \alpha_j \}$满足一定的约束性条件。 若(17.1)中的$\varepsilon_t$服从标准正态分布， 则其有任意阶矩， 这时条件四阶矩
$$
\begin{align}
E(a_t^4 | F_{t-1})
=& E(\sigma_t^4 \varepsilon_t^4 | F_{t-1})
= \sigma_t^4 E(\varepsilon_t^4 | F_{t-1})\\
=& 3 \sigma_t^4
= 3(\alpha_0 + \alpha_1 a_{t-1}^2)^2
\end{align}
$$
从而无条件的四阶矩为
$$
E(a_t^4)
= E[ E(a_t^4|F_{t-1})]
= 3 E [ (\alpha_0 + \alpha_1 a_{t-1}^2)^2 ]
= 3 \left[ \alpha_0^2 + 2\alpha_0 \alpha_1 E(a_{t-1}^2) + \alpha_1^2 E(a_{t-1}^4) \right]
$$
如果$\{ a_t \}$为四阶矩有限的严平稳时间序列， 则$Ea_t^4 = Ea_{t-1}^4$，于是
$$
(1 - 3 \alpha_1^2) Ea_t^4
= 3\left( \alpha_0 + 2\alpha_0 \alpha_1 \frac{\alpha_0}{1 - \alpha_1} \right)
$$
这要求$1 - 3\alpha_1^2>0$，即$0<\alpha_1 < \frac{\sqrt{3}}{3}$。 这时
$$
Ea_t^4 = \frac{3\alpha_0^2(1+\alpha_1)}{(1-\alpha_1)(1-3\alpha_1^2)}
$$

由此可以计算$a_t$的峰度为
$$
\frac{Ea_t^4}{[\text{Var}(a_t^2)]^2}
= 3 \frac{1-\alpha_1^2}{1 - 3\alpha_1^2} > 3
$$
$a_t$的超额峰度为
$$
\frac{Ea_t^4}{[\text{Var}(a_t^2)]^2} - 3
= \frac{6\alpha_1^2}{1 - 3\alpha_1^2} > 0
$$
这说明$\{a_t \}$序列是厚尾（重尾）分布， 其样本比均值和方差相同的正态序列有更多的离群值（outliers）。 这与实证分析中对资产收益率的分布观察结果一致。


### 8.3 ARCH模型的优缺点

优点：

- 可以产生波动率聚集
- 扰动$a_t$具有厚尾分布。

缺点：

- 因为假定$a_{t-j}$通过$a_{t-j}^2$影响波动率$\sigma_t$， 所以正的扰动和负的扰动对波动率影响相同， 但是实际的资产收益率中正负扰动对波动率影响不同， 较大的负扰动比正扰动引起的波动更大。
- ARCH模型对模型参数有较严格的约束条件， 即使是ARCH(1)， 为了能计算峰度，也需要$\alpha_1 \in (0, \frac{\sqrt{3}}{3})$， 高阶的ARCH(m)的约束条件更为复杂。 这对带高斯新息的ARCH模型通过超额峰度表达厚尾性是一个限制。
- 只能描述条件方差的变化， 但是不能解释变化的原因。
- 由模型做的波动率预测会偏高。

### 8.4 ARCH模型的建模步骤

#### 8.4.1 定阶

在ARCH效应检验显著后， 可以通过考察$\{ a_t^2 \}$序列的PACF来对ARCH模型定阶。 下面解释理由。

首先， 模型为
$$
\sigma_t^2 = \alpha_0 + \alpha_1 a_{t-1}^2 + \dots + \alpha_m a_{t-m}^2
$$
因为$E(a_t^2 | F_{t-1}) = \sigma_t^2$， 所以认为近似有
$$
a_t^2 \approx \alpha_0 + \alpha_1 a_{t-1}^2 + \dots + \alpha_m a_{t-m}^2
$$
这样可以用$\{ a_t^2 \}$序列的PACF的截尾性来估计ARCH阶m。


#### 8.4.2 模型估计

## 9 GARCH模型

### 9.1 模型方程

如果$a_t$满足
$$
\begin{align}
a_t = \sigma_t \varepsilon_t,
\quad
\sigma_t^2 = \alpha_0 + \sum_{i=1}^m \alpha_i a_{t-i}^2 + \sum_{j=1}^s \beta_j \sigma_{t-j}^2

\end{align}
$$
其中$\{ \varepsilon_t \}$为零均值单位方差的独立同分布白噪声列， $\alpha_0>0, \alpha_i \geq 0, \beta_j \geq 0, 0 < \sum_{i=1}^m \alpha_i + \sum_{j=1}^s \beta_j < 1$， 这最后一个条件用来保证满足模型的$a_t$的无条件方差有限且不变， 而条件方差$\sigma_t^2$可以随时间t而变。


### 9.2 GARCH模型的性质

下面以最简单的GARCH(1,1)为例研究GARCH模型的性质。 令$F_{t-1}$表示截止到$t-1$时刻的$a_{t-i}$和$\sigma_{t-j}$所包含的信息。 模型为
$$
\begin{align}
a_t =& \sigma_t \varepsilon_t,
\varepsilon_t \text{ i.i.d. WN} (0,1)\\
\sigma_t^2 =& \alpha_0 + \alpha_1 a_{t-1}^2 + \beta_1 \sigma_{t-1}^2
\end{align}
$$
为了计算无条件均值$Ea_t$，先计算条件期望
$$
E(a_t | F_{t-1})
= E(\sigma_t \varepsilon_t | F_{t-1})
= \sigma_t E(\varepsilon_t | F_{t-1})
= 0
$$
这里用了$\sigma_t \in F_{t-1}$而$\varepsilon_t$与$F_{t-1}$独立。 于是
$$
E a_t = E[ E(a_t | F_{t-1})] = 0
$$
即GARCH模型的新息$a_t$的无条件期望为零。

来计算$a_t$的无条件方差。 设模型的$\{ a_t \}$序列存在严平稳解，则
$$
\begin{aligned}
\text{Var}(a_t)
=& E(a_t^2)
= E[ E(a_t^2 | F_{t-1})]
= E[ E(\sigma_t^2 \varepsilon_t^2 | F_{t-1})]\\
=& E[\sigma_t^2 E(\varepsilon_t^2 | F_{t-1})]
= E[\sigma_t^2 E(\varepsilon_t^2)] \\
=& E[\sigma_t^2] 
= E[\alpha_0 + \alpha_1 a_{t-1}^2 + \beta_1 \sigma_{t-1}^2] \\
=& \alpha_0 + \alpha_1 E(a_{t-1}^2) + \beta_1 E[E(a_{t-1}^2|F_{t-2})]\\
=& \alpha_0 + (\alpha_1 + \beta_1) E(a_{t-1}^2)
\end{aligned}
$$
令$E a_t^2 = E a_{t-1}^2$， 解得
$$
\text{Var}(a_t) = E a_t^2
= \frac{\alpha_0}{1 - \alpha_1 - \beta_1} .
$$
GARCH(1,1)模型的性质：

第一，像ARCH模型一样，$a_t$存在波动率聚集， 一个较大的$a_{t-1}$或$\sigma_{t-1}$使得1步以后的条件方差变大， 从而倾向于出现较大的对数收益率。

- $\alpha$捕捉之前的冲击的影响，$\beta$捕捉之前的波动率的影响。大的$\beta$说明冲击对波动率的影响需要一段时间才能消失，所以GARCH项更加持久。大的$\alpha$说明波动率对之前的市场波动更密集，所以波动率更尖锐。在金融实证中，一般的$β_1$大于0.7， $α_1$在0.2左右。

第二，当$\varepsilon_t$为标准正态分布时， 在如下条件下$a_t$有无条件四阶矩：
$$
1 - 2 \alpha_1^2 - (\alpha_1 + \beta_1)^2 > 0
$$
这时超额峰度为
$$
\frac{E a_t^4}{(Ea_t^2)^2} - 3
= \frac{2\left[1 - (\alpha_1 + \beta_1)^2 + \alpha_1^2 \right]}
{1 - (\alpha_1 + \beta_1)^2 - 2\alpha_1^2}
> 0
$$

即$a_t$分布厚尾。

第三，GARCH模型给出了一个比较简单的波动率模型。

问题：纯统计模型，没有解释、预测力度不够好、对称、对参数要求比较严格

### 9.3 估计

MLE估计中$a_0$不知道，有三种解决方法：

- 估计$a_0$
- 用$a_0^2$的长期均值，$E a_0^2=\frac{\alpha_0}{1-\alpha_1}$
- 条件MLE：样本比较大时没有什么误差

需要初始波动率，也有三种方案：

- 样本方差
- 波动率的长期均值
- 待估计系数

均值部分可以是任何符合经济学原理的模型，比如想要估计股票回报的特质风险，均值部分就是市场模型，甚至再加上市场回报的滞后。

- 波动率部分，一般来说，很少有超过GARCH(2, 2)的。
- 还有一种导致不收敛的原因是离群值的存在。（偏度和峰度非常大）
  - 去掉：这样的激烈波动是否还会重演
  - 如果不能去掉，解决方法：
    - 改变参数估计的初始值
    - 改变最大化似然函数的数值方法
    - 改变模型，用简单些的模型
- 有明显的峰度：选择学生t分布



### 9.4 预测

可以用类似ARMA预测的方法预测波动率。 仍以GARCH(1,1)为例， 基于截止到h时刻的观测作超前一步预测：
$$
\sigma_{h+1}^2 = \alpha_0 + \alpha_1 a_{h}^2 + \beta_1 \sigma_{h}^2 \in F_{h}
$$
所以
$$
\begin{align}
\sigma_h^2(1) = E(\sigma_{h+1}^2 | F_{h})
= \sigma_{h+1}^2 = \alpha_0 + \alpha_1 a_{h}^2 + \beta_1 \sigma_{h}^2 .

\end{align}
$$
对$\sigma_{h+2}^2$，利用$a_t^2 = \sigma_t^2 \varepsilon_t^2$，有
$$
\begin{aligned}
\sigma_{h+2}^2 =& \alpha_0 + \alpha_1 a_{h+1}^2 + \beta_1 \sigma_{h+1}^2  \\
=& \alpha_0 + \alpha_1 \sigma_{h+1}^2 \varepsilon_{h+1}^2 + \beta_1 \sigma_{h+1}^2 \\
=& \alpha_0 + (\alpha_1 \varepsilon_{h+1}^2 + \beta_1) \sigma_{h+1}^2
\end{aligned}
$$
于是
$$
\sigma_h^2(2)
= E(\sigma_{h+2}^2 | F_{h})
= \alpha_0 + E(\alpha_1 \varepsilon_{h+1}^2 + \beta_1 | F_h) \sigma_{h+1}^2
= \alpha_0 + (\alpha_1 + \beta_1) \sigma_h^2(1)
$$
类似地，对$\ell \geq 2$有
$$
\sigma_{h+\ell}^2
= \alpha_0 + \alpha_1 \varepsilon_{h+\ell-1}^2 \sigma_{h+\ell-1}^2 + \beta_1 \sigma_{h+\ell-1}^2
= \alpha_0 + (\alpha_1 \varepsilon_{h+\ell-1}^2 + \beta_1) \sigma_{h+\ell-1}^2
$$
于是
$$
\begin{align}
\sigma_h^2(\ell)
=& E\left\{ \sigma_{h+\ell}^2 | F_h \right\} 
= \alpha_0 
+ E\left\{ (\alpha_1 \varepsilon_{h+\ell-1}^2 + \beta_1) \sigma_{h+\ell-1}^2 | F_h \right\} \\
=& \alpha_0 
+ E\left\{ E\left[ 
(\alpha_1 \varepsilon_{h+\ell-1}^2 + \beta_1) \sigma_{h+\ell-1}^2 | F_{h+\ell-2} 
\right] | F_h  \right\} \\
=& \alpha_0 
+ E\left\{ \sigma_{h+\ell-1}^2 E\left[ 
\alpha_1 \varepsilon_{h+\ell-1}^2 + \beta_1 | F_{h+\ell-2} \right]
| F_h \right\} 
\quad(\text{注意}\sigma_{h+\ell-1}^2 \in F_{h+\ell-2}) \\
=& \alpha_0 
+ \left\{ \sigma_{h+\ell-1}^2 (\alpha_1 + \beta_1) | F_h \right\}  \\
=& \alpha_0 + (\alpha_1 + \beta_1) \sigma_h^2(\ell-1)

\end{align}
$$
预测公式与自回归系数为$(\alpha_1 + \beta_1)$的ARMA(1,1)的超前预测公式相同。

从$\ell=1$迭代计算得
$$
\sigma_h^2(\ell)
= \frac{\alpha_0[1 - (\alpha_1 + \beta_1)^{\ell-1}]}{1 - (\alpha_1 + \beta_1)}
+ (\alpha_1 + \beta_1)^{(\ell-1)} \sigma_h^2(1)
$$

只要$\alpha_1 + \beta_1 < 1$就有
$$
\sigma_h^2(\ell)
\to
\frac{\alpha_0}{1 - \alpha_1 - \beta_1} 
= \text{Var}(a_t)
$$
即超前多步条件方差预测趋于$a_t$的无条件方差。

GARCH模型有和ARCH模型类似的弱点。 在高频数据研究发现及时使用t分布， 分布厚尾性也不足； 对于收益率的正负不对称性无法反映。



### 9.5 在险价值

在险价值(Value-at-risk, VaR)是，如果一个资产在一定时期内（h天），损失大于等于V的概率小于a，那么我们说这个资产的对应h和a的VaR等于V。

计算单个资产的VaR

计算一个投资组合的VaR

- 直接考察这个组合的回报数据
  - 优点：简单
  - 缺点：
    - 有时没有足够的数据
    - 投资组合的结构一般会变化，导致历史回报数据不能很好反应将来
- 考察组合内的每个资产的风险，根据当前的组合结构加总
  - 问题在于需要估计资产之间的相关性
  - 多元GARCH模型是解决这个相关性问题的一个有效模型



### 9.6 改进的GARCH模型

### 9.6.1 EGARCH

EGARCH(m,s)模型可以用滞后算子的形式写成
$$
\begin{align} a_t = \sigma_t \varepsilon_t, \quad \ln\sigma_t^2 = \alpha_0 + \frac{1 + \beta_2B + \dots \beta_s B^{s-1}}{1 - \alpha_1 B - \dots - \alpha_m B^m} g(\varepsilon_{t-1}),\quad   g(\varepsilon_t) = \theta\varepsilon_t + \gamma\left[ |\varepsilon_t| - E|\varepsilon_t| \right] \end{align}
$$

$\alpha_0$为常数， 其中B是滞后算子， 多项式$1 + \beta_2 z + \dots + \beta_s z^{s-1}$和$ 1 - \alpha_1 z - \dots - \alpha_m z^m$的根都在单位圆外且两个多项式没有公因子。

EGARCH(m,s)模型的另一种形式是
$$
\begin{align}
\ln\sigma_t^2
= \alpha_0 
+ \sum_{i=1}^m \alpha_i
\frac{|a_{t-i}| + \gamma_i a_{t-i}}{\sigma_{t-i}}
+ \sum_{j=1}^s \beta_j \ln\sigma_{t-j}^2

\end{align}
$$
这时， 正的扰动$a_{t-i}$对于对数波动率$\ln\sigma_{t}^2$的贡献为 $\alpha_i (1 + \gamma_i) |\varepsilon_{t-i}|$， 而负的对数波动率的影响为$ \alpha_i (1 - \gamma_i) |\varepsilon_{t-i}|$， 其中$\varepsilon_{t-i} = a_{t-i}/\sigma_{t-i}$， 其正负号由扰动$a_{t-i}$的正负号决定。 参数$\gamma_i$代表了扰动的正负号的不同影响， 称为杠杆效应， 一般期望$\gamma_i$是负数， 这样负扰动时影响更大（若$\alpha_i \geq 0$）。

解决GARCH的问题：

- 过去扰动对将来波动率的影响是对称的，但实际上大跌比大涨带来更大的市场波动
  - 心理因素
  - 杠杆效应
- 参数约束给模型估计带来困难

缺点：

- 参数估计更困难：尽管少了非负约束，但是存在浮点溢出问题
- 关键在于是否有非对称性

### 9.6.2 IGARCH

- 金融时间序列数据中，波动率一般存在较强的持续性，$\alpha+\beta$接近1
- 波动率几乎是一个单位根过程

IGARCH(1,1)：
$$
\sigma_t^2=\alpha_0+\beta_1\sigma_{t-1}^2+(1-\beta_1)\varepsilon_{t-1}^2,0<\beta_1<1
$$
尽管波动率过程非平稳，但依然可以用MLE方法进行一致估计

问题：波动率长期均值不存在，不太适合预测较为长期的波动率

### 9.7 实现波动率

用历史数据计算标准差作为波动率

优点：简单、符合直觉

缺点：

- 隐含假设为结构变化，即在一个月之内的方差相同，而在月末相邻两天（分别属于两个月）却不一样。这个假设没有理论基础。
- 对月度方差，一般只有 21/22 个数据，这样的样本量对方差估计来说偏少
- 如果要计算周度、日度回报的方差，问题更大
  - 样本量问题改进方法之一：用高频数据，比如日内intraday每一分钟的数据。
  - 但有两个问题：
    - 微观结构误差
    - 非交易时段的波动率估计问题：由于回报是一段时期内，用日度回报计算问题不大，时间全覆盖
  - 样本量问题改进方法之二：用运动窗口，即计算t日的波动率，用从t-m日到t日的日度回报观测值
    - 一个大问题是'ghosting': 某一个观测值（比较大的波动）对接下来的m天的波动率估计有影响，但突然在m+1天时没有影响

#### 9.7.1 EWMA

$$
\begin{align}\frac{x_{t-1}+\lambda x_{t-2}+\lambda^{2} x_{t-3}+\ldots+\lambda^{n-1} x_{t-n}}{1+\lambda+\lambda^{2}+\ldots+\lambda^{n-1}}
\\
\hat{\sigma}_{t}^{2}=(1-\lambda) \sum_{i=1}^{\infty} \lambda^{i-1} r_{t-i}^{2}
\end{align}
$$

- $\lambda=1$且$n$有限时，就是通常的样本方差
- $\lambda$越大，最近的波动在波动率的估计中越不重要
- IGARCH(1,1)的$\alpha_0=0$时，就是EWMA模型
- 但参数的选取不一样：IGARCH中$\beta$是用历史数据估计的，EWMA中是使用者主观选取的
  - 金融市场上，0.75-0.98；短期用小的$\lambda$，长期用大的$\lambda$
- 多长数据来计算EWMA？
  - 目前业界经常用过去n天的日度回报数据计算波动率（调整时间）用来作为将来n天回报的波动率的预测。比如为一个20天到期的期权定价预测20天股票回报的波动率，就用过去20天的日度回报计算样本标准差，再乘上$\sqrt{20}$
  - 但如果n比较小，比如10天，那也会用稍微多些的样本，比如20天
  - 预测长期波动率而要用长期数据时，有一个问题是过去某个市场有激烈波动的特别时点是否应该加入？这个问题与前面讨论GARCH模型的样本选择一样，完全主观
  - 一定用日度数据？对比较长期的波动率预测，周度甚至月度数据也经常用
  - 在VaR的计算上，用GARCH计算的VaR会比正态假定的VaR更大。GARCH和等权方差在VaR计算上捕捉肥尾现象比EWMA更好。


## 10 向量自回归模型
多个资产收益率的联合模型中最常用的是向量自回归 (Vector Autoregression, VAR)模型。 称k元时间序列$\boldsymbol r_t$服从一个一阶向量自回归模型， 即VAR(1)，若有
$$
\begin{align}
\boldsymbol r_t
= \boldsymbol\phi_0 + \boldsymbol\Phi \boldsymbol r_{t-1}
+ \boldsymbol a_t

\end{align}
$$
其中$\boldsymbol\phi_0$是$k$维常数向量， $\boldsymbol\Phi$是$k$阶常数方阵，$ \{\boldsymbol a_t\}$是序列不相关的弱平稳列， $E\boldsymbol a_t $= $\boldsymbol 0, \text{Var}(\boldsymbol a_t) = \boldsymbol\Sigma>0$(对称正定矩阵)。

文献中经常假定$\{ \boldsymbol a_t \}$服从多元正态分布$ N_k(\boldsymbol 0, \boldsymbol\Sigma)$， 则这时$\boldsymbol a_t$是独立同分布随机向量序列。

记$\boldsymbol a_t = (a_{1t}, \dots, a_{kt})^T， \boldsymbol\phi_0 = (\phi_{10}, \dots, \phi_{k0})^T, \boldsymbol\Phi=(\phi_{ij})_{k\times k}$。

### 10.1 定阶

估计VAR(p)和VAR(p-1)，看第$p$阶滞后项的系数是否显著
$$
\begin{aligned}
M(p) =& - (T - k -p -\frac32) \ln \frac{|\hat{\boldsymbol\Sigma}_p|}{|\hat{\boldsymbol\Sigma}_{p-1}|}
\end{aligned}
$$
卡方分布，自由度为$p^2$

### 10.2 模型结构和格兰杰因果性

格兰杰检验：

首先在没有$x$的历史值的时候，确定模型大小：
$$
\begin{array}{c}{y_{t}=a_{10}+\sum_{i=1}^{m} a_{1 i} y_{t-i}+\varepsilon_{t}} \\ {\operatorname{FPE}(m)=\frac{T+m+1}{T-m+1} \frac{\operatorname{ESS}(m)}{T}}\end{array}
$$
选择阶数：
$$
\begin{array}{c}{y_{t}=a_{20}+\sum_{i=1}^{m} a_{2 i} y_{t-i}+\sum_{j=1}^{k} b_{2 j} x_{t-j}+\varepsilon_{t}} \\ {\operatorname{FPE}(m, k)=\frac{T+m+k+1}{T-m-k+1} \frac{\operatorname{ESS}(m, k)}{T}}\end{array}
$$
构造F统计量
$$
F=\frac{\left(\mathrm{ESS}_{1}-\mathrm{ESS}_{2}\right) / k}{\mathrm{ESS}_{2} /[T-(k+m+1)]}
$$
如果统计量大于临界值，拒绝原假设：系数为零。有格兰杰效应。

### 10.3 脉冲反应

用待定系数法：

- 给定VAR：$(I-a_1 L-a_2 L^2-\dots a_p L^p) y_t=a_0+ε_t$
- 假设我们有对应的VMA：$y_t=μ+(I+β_1 L+β_2 L^2+⋯)\varepsilon_t$
- 把VMA中的$y$代入到VAR中，有$(I-a_1 L-a_2 L^2-⋯a_p L^p) (I+β_1 L+β_2 L^2+⋯) =I$
- 那么方程左边$L$的系数为0，$L^2$的系数为0……
- $β_i$可求。

### 10.4 方差分解


$$
\begin{aligned} \mathbf{A}=\mathbf{L D L}^{\mathrm{T}} &=\left(\begin{array}{ccc}{1} & {0} & {0} \\ {L_{21}} & {1} & {0} \\ {L_{31}} & {L_{32}} & {1}\end{array}\right)\left(\begin{array}{ccc}{D_{1}} & {0} & {0} \\ {0} & {D_{2}} & {0} \\ {0} & {0} & {D_{3}}\end{array}\right)\left(\begin{array}{ccc}{1} & {L_{21}} & {L_{31}} \\ {0} & {1} & {L_{32}} \\ {0} & {0} & {1}\end{array}\right) \\ &=\left(\begin{array}{ccc}{D_{1}} & {L_{21}^{2} D_{1}+D_{2}} \\ {L_{31} D_{1}} & {L_{31} L_{21} D_{1}+L_{32} D_{2}} & {L_{31}^{2} D_{1}+L_{32}^{2} D_{2}+D_{3}}\end{array}\right) \end{aligned}
$$

