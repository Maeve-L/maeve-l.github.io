---
Area: Finance
Source: Book
Status: Done
Type: Notes
---


## 久期和凸性的定义

[[Rates#久期和修正久期]]

[[Rates#凸性]]


## 有效久期 (Effective Duration)

根据之前提到的[[OAS]]定义，有效久期的计算方法如下：

- 根据市场价格P计算OAS.
- 将收益率曲线平行向上移动$\Delta y$，再加上用市场价格计算出的 OAS重新定价$P^{+}$.
- 将收益率曲线平行向下移动$\Delta y$，再加上用市场价格计算出的 OAS重新定价$P^{-}$.


有效久期为：

$$
D=\frac{P^{-}-P^{+}}{2P\Delta y} \times 100
$$


### 有效久期没有考虑的风险因素

#### 国债曲线的变化

在使用上述公式用有效久期预测价格变化时，我们认为整条利率曲线是**平行移动**的，并用10年期国债利率的变化代表整条利率曲线的变化。如果国债曲线的形状变得更陡峭或者更平缓，继续使用久期与利率变化的乘积来预测价格变化就会不够准确。

#### 当前票息价差 (Current Coupon Spread)

Current Coupon指的是目前市场价格恰好为面值 (par value) 的MBS的coupon（考虑了servicing fee之后），一般由线性插值得出，可以看做是par value MBS pass-through的yield. 大多数新发起的抵押贷款都以接近面值的票面利率证券化，因此current coupon yield可以被认为是新贷款的二级市场利率 (mortgage rate)。

Current Coupon Spread是指current coupon和treasury rate之间的差值，相当于par value MBS pass-through的treasury OAS，也相当于mortgage rate和treasury rate之间的差值。

有效久期的计算假设current coupon spread和国债利率之间是线性关系。但实际并非如此。如果current coupon spread增加，则说明相对于国债利率，贷款利率更高了，借款人的再融资动机减弱，所以提前还款的风险降低，久期增加，价格有可能上升。Current coupon spread的partial duration也因此是负的。利率曲线的形状、波动率、提前还款风险都会影响current coupon spread.


#### 凸性或不对称价格变动

由于 MBS 存在[[MBS Modelling#早偿情况的分析|提前偿还风险]]，所以利率下降时，再融资比例可能上升，借款人会选择提前偿还手中的贷款。因此对投资者来讲，**这相当于原本很长的久期突然变小了**。所以利率下降时，MBS的久期也有可能变小，其凸性是负的。这意味着，在其他条件相同的情况下，使用有效久期预测价格，将在利率下降时高估价格，而在利率上升时低估价格。

投资于RMBS的机构持有者一般会在多RMBS的同时空国债作为对冲。由于MBS的负凸性性质，**利率上行，MBS久期增加，持有者就要卖空更多的国债以对冲久期，国债利率继续上行**。反之亦然。因此，MBS的负凸性可能是市场利率大幅变动的一个原因。



#### 利率波动率

利率的波动率可能会随着期限变化而改变，也有可能存在波动率聚集的现象。但使用有效久期预测价格时，认为利率曲线是平行移动的，没有考虑波动率的情况，可能会造成对价格的高估或低估。

## 实际久期 (Empirical Duration)

实际久期是指从市场数据中用回归分析的方式来估计久期。

理论上有
$$
\frac{\Delta B}{B}=-D\Delta y
$$

所以用$\frac{\Delta B}{B}$作为因变量，国债利率的变化作为自变量，采用过去一段时间的数据进行回归，回归的斜率估计量$\beta$就是实际久期。

## 有效久期和实际久期之间的关系

如果其他的风险因素和国债利率变化之间存在相关性，则有效久期和实际久期之间就会有所不同。由线性回归的估计量性质，忽略价格变化的高阶项，有：

$$
D_{\text{Empirical Estimate}} = D_{\text{Current Effective}}+\mu+D_{s} \rho_{\Delta s \Delta y} \frac{\sigma_{\Delta s}}{\sigma_{\Delta y}}+D_{v} \rho_{\Delta v \Delta y} \frac{\sigma_{\Delta v}}{\sigma_{\Delta y}}+\ldots+\varepsilon
$$

其中$\mu$是当前有效久期和实际久期之差的平均值；$\rho_{\Delta s \Delta y}$是相关系数；$\sigma_{\Delta s}$是标准差。

如果风险因素的变化（如每日OAS）和国债收益率变化之间呈负相关，那么**实际久期将短于有效久期**。

## 另一种实际久期的计算

实际久期计算中的一个隐含假设是**国债收益率变化会立刻影响到同一天的MBS价格**。然而，流动性不够活跃的MBS不一定满足这个假设。例如，高溢价MBS的流通量很小，大部分交易都在SP进行，而不是TBA市场。因此，高溢价TBA的价格变化通常会滞后于国债收益率的变化，如果用同一天的价格变化进行回归，会导致对实际久期的估计偏低。

为了解决这个问题，可以选用一段时间的MBS价格对国债收益率进行回归 ($ln\ P =\alpha + \beta y+\varepsilon, \frac{dP/dy}{P} =−Duration = \beta$)，斜率就是实际久期的估计量。它描述了**一段时间内**MBS价格和国债收益率水平之间的关系，因此这样计算出的久期可能不利于对冲每天的收益率曲线波动。

## 久期和对冲

有效久期可以对冲收益率曲线平行移动时发生的价格变化。使用有效久期意味着认为其他风险因素不变。

实际久期假设过去的国债收益率变化与其他风险因素变化之间的关系将继续存在且相同。因此，如果风险因素和国债收益率之间的相关性发生了改变，使用实际久期可能会出现错误。







## 参考文献


Hayre, L. (Ed.). (2001). _Salomon Smith Barney guide to mortgage-backed and asset-backed securities_. John Wiley.

[RMBS随谈录4：RMBS对冲—美国固收市场大幅变动时的尾大摇身现象](https://mp.weixin.qq.com/s/QPGKf8RZiQNxkkNQoj3Rlg)

[Managing Against MBS Indexes: A Duration Perspective](https://www.msci.com/www/blog-posts/managing-against-mbs-indexes-a/02667007821)

[Measuring MBS curve risk with Implied Mortgage Rate Sensitivity (“IMS”) approach](https://research-doc.credit-suisse.com/docView?language=ENG&format=PDF&source_id=csplusresearchcp&document_id=1041260871&serialid=0MH9veO3E0x5Z%2B76qli7rYOAyJDVt7fLdbi2VSkop%2FA%3D&cspId=null)

[Can MBS Duration Turn Negative?](https://www.msci.com/www/blog-posts/can-mbs-duration-turn-negative/02108224451)