---
title: "OAS"
---

## MBS的内嵌期权

当贷款发放之后，借款人存在[[MBS Modelling#早偿情况的分析|提前偿还的权利]]，可以灵活地根据利率水平选择是否提前偿还。

如果利率变低，借款人可以选择再融资，以更低的价格获得同样的贷款。拥有看涨期权 (call option) 意味着可以通过较低的价格来获得标的资产，所以抵押贷款的借款人相当于拥有一个看涨期权；类似地，MBS的投资者则相当于卖出一个看涨期权 (short a call option). 同样，借款人也有选择违约并将抵押物（住房）还给银行的权利，相当于拥有一个看跌期权（房价跌到比贷款的价值还低）；类似地，MBS的投资者则相当于卖出一个看跌期权 (short a put option). 

因此，MBS可以看做**内嵌期权**的固定收益产品，可以用**Option-Adjusted Spread**来衡量期权因素对价格的影响。

## OAS的计算方法

OAS是基于不同状态下的利率$r_{t}$使得MBS预期现金流的现值等于该MBS的市场价格所需收益率价差。可以按以下方法倒解出OAS：

设$r_{t}, t=1, \cdots, T$是利率曲线，给定$r_{j t}, t=1, \cdots, T$是状态 $j=1, \cdots, N$下的利率，每个状态下MBS的现金流可以由$C_{j t}, t=1, \cdots, T$确定，OAS被定义为：
$$
V_{M B S}=\sum_{j=1}^{N} p_{j}\left[\sum_{t=1}^{T} \frac{C_{j t}}{\left(1+r_{j 1}+O A S\right) \times \cdots\left(1+r_{j t}+O A S\right)}\right]
$$
其中 $p_{j}$ 是状态 $j$的概率。

常见的利率模型有以下几种：

**Vasicek Model**
$$
dR_t=a(b-R_t)dt+\sigma dW_t
$$
**CIR Model**
$$
dR_t=a(b-R_t)dt+\sigma \sqrt R_t dW_t
$$
**Hull-White Model**
$$
dR_t=a(b_t-R_t)dt+\sigma dW_t
$$

通过**蒙特卡洛**模拟不同的利率曲线随机变化的情况，可以计算出OAS.


## OAS与Z-Spread

Z-Spread是基于目前的即期利率曲线 (spot curve) 计算出的使现金流的现值等于市场价格的价差。

$$
P=\sum_{t=1}^{T} \frac{C_{t}}{\left(1+r_{t}+Z\right) ^t}
$$

其中$r_t$是目前$t$年期的即期利率。

例如，某三年期债券目前的价格为104.90，coupon rate为5%，每年付息一次。相应的一年、两年和三年期零息国债利率（每半年复利一次）分别为2.5%、2.7%和3%。计算Z-Spread的方法为：

$$
104.9 = \frac{5}{(1+\frac{0.025+Z}{2})^2}+\frac{5}{(1+\frac{0.027+Z}{2})^4}+\frac{105}{(1+\frac{0.03+Z}{2})^6}
$$


Z-Spread和OAS的差值可以衡量投资者由于short an option导致的收益率变化：

$$
Z-Spread = OAS+Option\ Cost
$$

例如，如果现在以下两个MBS的Z-Spread和OAS如下所示：

| | MBS 4.00% | MBS 5.50%|
|---|---|---|
|Zero Volatility Spread |1.22% |2.09%|
|Option-Adjusted Spread |0.49%| 0.19%|

则MBS 4.00%的short option value为0.73%，MBS 5.50%的short option value为1.90%. OAS说明了投资者卖出期权的价值，在这个例子中MBS 5.50%的short option value更高，所以MBS 5.50%的YTM更高。

与静态现金流分析相比，OAS可以更清晰地让投资者理解MBS的模型价格。通过选取不同的利率模型，投资者可以观察不同收益率曲线形状的影响，并对**未来的利率进行了模拟**，研究利率对MBS收益率的影响。但OAS分析受限于利率模型和提前还款模型的选取，不同的模型构建方法会影响OAS的分析结果。

## Reference

Glenn M. Schultz: Investing in Mortgage-Backed and Asset-Backed Securities, Wiley Finance, 2015