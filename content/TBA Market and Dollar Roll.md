---
Area: Finance
Source: Paper
Status: Done
Type: Notes
---



本文综述了Song and Zhu两位教授发表于RFS的文章“Mortgage Dollar Roll”，并辅以其他文献整理总结 Agency MBS、TBA 市场及 Dollar Roll 的融资机制。

## 机构 MBS (Agency MBS)

Agency MBS 是指由 Ginnie Mae (GNMA)、Fannie Mae (FNMA) 和 Freddie Mac (FHLM) 担保的抵押贷款支持证券 (MBS)，是美国固定收益市场的主要组成部分。其重要性主要体现在以下特点：

- **规模大**：根据 SIFMA 的数据，截至 2017 年第二季度，机构抵押贷款支持证券（MBS）的流通量约为 9.2 万亿美元，仅次于美国国债市场的流通量 14.0 万亿美元。
- **货币政策传导作用**：美联储自 2009 年以来进行了多轮量化宽松（QE），累计面值为 1.74 万亿美元。
- **住房抵押贷款作用**：RMBS 满足了居民的购房需要，而机构 MBS 市场对抵押贷款市场的健康发展至关重要。

## TBA市场 (To-be-announced market, TBA market)

TBA 合约本质上是MBS的远期买卖合约。在 TBA 交易中，买卖双方只约定六个参数：发行人 (Agency)、到期日 (Maturity)、票息 (Coupon)、面值 (Par Amount)、价格 (Price)、结算日 (Settlement Date)。与其他远期合约不同，TBA 合约每月只有一个结算日，由 SIFMA 设定。

TBA 交易的独特之处在于，在结算日交付的交易双方并未在交易日指定具体的需要买卖的 MBS CUSIP，而是仅指定几个关键的 MBS 特征。这种交易设计显著增加了可交付 MBS 的数量并提高了市场流动性。 

TBA 市场可以为抵押贷款发起人提供风险对冲和融资作用。贷款机构通常会给予优质申请人30天到90天的利率锁定期，允许申请人在锁定期内决定是否按照特定的固定利率借入款项，这实质上相当于给予贷款申请人一个30天到90天的“固定利率期权”。贷款发起人将面临市场利率变动所引发的利率风险。通过TBA市场，抵押贷款发起人可以在发放贷款之前就锁定MBS的转售价格，比较直接地实现了对贷款利率风险的对冲目的。因此，即使是小规模贷款机构也可以发放贷款，使购房者获得更低廉的利率。

## 美元滚动交易 (Dollar Roll)

美元滚动交易由两笔 TBA 交易组成。卖家 (roll seller, MBS持有者，即融入资金方）出售一张MBS，承诺在近月 (front month) 交付这张券给对方，同时承诺在远月 (future month) 再把同类同面值的券买回来。这两个 MBS 不需要完全相同，只要它们具有相同的 TBA 特征即可。 


美元滚动交易的“下跌” (dollar roll drop) 是近月和远月 TBA 合约之间的价差，一般来说是正的，原因有二。 

- 由于没有规定两次交易时交付的券是一致的，所以在逆向选择的前提下，卖家在远月会收到较差的券，所以 MBS 的价值也较低。
- 其次，卖家在近月卖出了这张 MBS 后，也放弃了这期间的本金和利息收入，所以会存在dollar roll drop.

这两个特征将 dollar roll 与 MBS 回购交易区分开来。在 MBS 回购交易中，融出资金方必须归还相同的 MBS pool，并且原始所有者在回购期间会收取本金和利息。

## 美元滚动交易的特殊性 (Dollar Roll Specialness)

如果通过 dollar roll 融资时的隐含融资利率低于现行利率（例如 MBS 回购利率），就称这个 dollar roll 为“特殊 (on special)”。可以通过计算回购利率与隐含融资利率之间的差值衡量一个 dollar roll 的“特殊”程度 (specialness).

- 因为不指定两次交易时需要同样的个券，所以当资金融入方回购 MBS 时，融出资金方可以选更便宜的券交付，通常更便宜的券对应更高的“提前偿付风险”。正的 specialness 是对卖方承担再交付风险的补偿。
    
- 持有稀缺的 MBS 可以在回购市场和证券借贷市场中融到更多的钱。如果不进入回购市场而是进行 dollar roll，卖方不仅放弃了利息和本金支付，而且放弃了与更便宜的融资利率和贷款费用。因此，dollar roll中的均衡隐含融资利率必然下降，从而导致更高的specialness. 特定类别 MBS 的稀缺性可能受到交易商和贷款发行人的做空和对冲以及新发行的 MBS 数量的推动。



### Dollar Roll Specialness 的决定因素

#### 再交付风险和逆向选择

相对于回购融资，dollar roll 的一个关键特征是融出资金方（借出现金并接收 MBS）可以选择在滚动合约的远月交付基本相似但不同的 MBS. 所以由于逆向选择，buyer 会选择交付一个最差的 MBS. 因为 Agency MBS 不存在违约风险，所以更差的券一般意味着更大的提前偿还风险。所以可交付的 MBS 范围内，**提前偿还风险的分散度 (dispersion) 越大，specialness 越高。**


除了类似于回购市场中供应量对融资利率的影响机制，dollar roll还有一个特殊之处：由于逆向选择的存在，市场参与人对于交付最差证券的行为具有充分的理性预期，**MBS 的流动将缩小到最便宜可交付券 (CTD, Cheapest-to-deliver)**。这进一步导致了可流动的 MBS 供应量的减少。**即使 MBS 总供应不变，更高的逆向选择可以缩小 MBS 的有效供应，使其 specialness 增加**。这种逆向选择和供应之间的内生反馈是 dollar roll 独有的。

随着可交付 MBS 的分散度变大，卖家因为会想到买家一定会交付回更差的 MBS，所以一开始就不愿意在 dollar roll 中交易高质量的 MBS。所以高质量的 MBS 将在指定池市场 (specified pool market) 交易。因此，**提前偿还风险的分散度 (dispersion) 越大，specified pool market 交易应该越活跃**。 所以 **specialness 和 specified pool market 的交易量正相关**。

#### MBS 所有权的交换 (Ownership Exchange)

**杠杆率的影响：**

- 基于 Dollar roll 的融资可以被看做表外业务，而通过回购融资更可能被看做表内业务。所以使用 dollar roll 融资（相对于回购）可以更节约表空间。所以 **specialness 与金融机构的杠杆负相关**。
  
**提前偿付风险的转移：**

- 在融资期间，dollar roll 中MBS的利息和本金偿还均直接给到资金融出方，而回购中，抵押品的一切利息和本金收益均由资金融入方获得。因此，买方承担提前还款风险。如果持有的是 premium MBS，提前还款会造成损失，如果持有的是 discount MBS，提前还款会带来收益。所以如果提前还款风险比预期更高，则买方如果收到了 premium MBS，则期待更高的融资利率；如果收到了 discount MBS，则会期待更低的融资利率。**Specialness 正向（负向）依赖于premium（discount）MBS 抵押品在融资期间的提前还款速度**。


### Dollar Roll Specialness 与 MBS 回报之间的关系

**Dollar roll specialness 与预期 MBS 回报呈负相关。**

MBS 回报率越高，dollar roll 相对于 MBS 回购放弃掉的回报率就越大，市场参与者会更青睐回购，回购利率上升，specialness 下降。Specialness 较高的 MBS 为其持有者在融资市场上提供了“便利收益 (convenience yield)”，所以这些持有者愿意接受较低的预期回报。


## 实证研究

### 再交付风险

作者建立了如下的模型进行面板数据回归：

$$
Specialness_{i t}=\sum_{t} \alpha_{t} D_{t}+\sum_{i} \gamma_{i} D_{i}+\beta Disp_{it}^{CPR}+\varepsilon_{i t}
$$


$Specialness_{it}$: dollar roll specialness, dollar roll financing rates 和一个月的 MBS 回购利率的差值。

$D_{t}, D_{i}$分别是息票利率和时间的哑变量。

$Disp_{it}^{CPR}$: 用提前偿还率的分散度作为 value dispersion 的代理变量。剔除至少具有以下特征之一的 MBS CUSIP：剩余本金余额低于 150,000 美元，再融资份额大于 75%，平均 LTV 比率高于 85%，平均 FICO 分数低于 680。这些特征使提前还款的可能性降低，因此不太可能成为 CTD. 基于可能交易的 MBS 的 SMM数据，根据SMM计算CPR，再计算CPR的范围，即相同息票$i$和时间$t$下，各个CUSIP的CPR从高到低排序，计算最高CPR与最低CPR的差。

结论是$Disp_{it}^{CPR}$增加 1个标准差，dollar roll specialness 将提高约 41 个bp. 

另一种衡量 value dispersion 的方法是利用 specified pool 数据，计算$Payup_{it}$和$Trade^{SP}$. Specified pool 指定了可交割的 MBS，不存在再交付风险，因此对寻求融资优质MBS的市场参与者更具吸引力。因此$Payup_{it}$定义为 SP 和 TBA 的价格差异，也是 value dispersion 的代表。计算方法为相同息票$i$和时间$t$下按交易量加权平均的 SP 和 TBA 的价格差。$Trade^{SP}$是相同息票$i$和时间$t$下 SP 的交易量。回归后结论都是和 specialness 呈正相关。

$$
Specialness_{i t}=\sum_{t} \alpha_{t} D_{t}+\sum_{i} \gamma_{i} D_{i}+\beta Payup_{it}+\varepsilon_{i t}
$$

$$
Specialness_{i t}=\sum_{t} \alpha_{t} D_{t}+\sum_{i} \gamma_{i} D_{i}+\beta Trade_{it}^{SP}+\varepsilon_{i t}
$$





### 所有权交换

作者建立了以下模型研究杠杆率对 specialness 的影响：

$$
Specialness_{it}=\sum_{i} \gamma_{i} D_{i}+\beta Leverage_{t-1}+\varepsilon_{i t}
$$

$Leveraget_{t-1}$: 上一期 primary dealer 的 asset/equity ratio 的平方和，用以衡量是否有出表的需求，越大说明资产比例越高，越不需要出表。

结论是$Leverage$增加 1个标准差，dollar roll specialness 将降低约 11 个bp. 

作者定义$CPR^{Signed,Change}$为：如果是 premium MBS则是$\Delta CPR$，如果是 discount MBS则是$-\Delta CPR$，以便进行回归分析。作者建立下面的模型来观察提前偿还风险的变化（超出预期）是否会对买家对 MBS 的优劣产生影响进而对 specialness 有影响。

$$
Specialness_{it}=\sum_{i} \gamma_{i} D_{i}+\beta CPR^{Signed,Change}+\varepsilon_{i t}
$$

结论是$CPR^{Signed,Change}$增加 1个标准差，dollar roll specialness 将降低约 21 个bp. 


### Dollar Roll Specialness 和 MBS 回报率

作者建立了如下的模型进行面板数据回归：

$$
OAS_{i t}=\sum_{t} \alpha_{t} D_{t}+\sum_{i} \gamma_{i} D_{i}+\beta Specialness_{i t}+\varepsilon_{i t}
$$

$$
Ret_{i t}=\sum_{t} \alpha_{t} D_{t}+\sum_{i} \gamma_{i} D_{i}+\beta Specialness_{i t}+\varepsilon_{i t}
$$

其中 [[OAS]] 是基于利率 $r_{t}$ 上使得 MBS 预期现金流的现值等于该 MBS 的市场价格所需收益率价差。可以按以下方法倒解出 OAS：

设$r_{t}, t=1, \cdots, T$是利率曲线，给定$r_{j t}, t=1, \cdots, T$是状态 $j=1, \cdots, N$下的利率，每个状态下 MBS 的现金流可以$C_{j t}, t=1, \cdots, T$确定，OAS被定义为：
$$
V_{M B S}=\sum_{j=1}^{N} p_{j}\left[\sum_{t=1}^{T} \frac{C_{j t}}{\left(1+r_{j 1}+O A S\right) \times \cdots\left(1+r_{j t}+O A S\right)}\right]
$$
其中 $p_{j}$ 是状态 $j$的概率。

Ret是FNMA 30YR TBA 合约的月度回报率。可以避免使用OAS带来的内生性问题。

**结论是 dollar roll specialness 和 MBS 回报率负相关。**




## 美联储在量化宽松期间使用 dollar roll


美联储在金融危机之中采用了量化宽松政策，大量购买了 Agency MBS 和 Treasury，以达成维持就业水平与稳定物价的双重目标。**这将推升近月合约的价格，造成 drop 数值高于合理值，借压低长期利率，支持抵押贷款市场，让资金状况更为宽松。**

金融机构因此担忧大量的 MBS 购买是否会造成 MBS 的市场扭曲，新发行 MBS 的速度是否能美联储购买的速度。


美联储可以通过 dollar roll 把交割日移到下个月, 等于推迟了 MBS 交割。为了研究美联储的 dollar roll sale 是否意在对市场 specialness 的关注，是否减轻了 MBS 市场的资金扭曲，作者比较了 specialness 在美联储 dollar roll sale 之后的变化。

$$
\Delta Specialness_{it}=\sum_{t}\alpha_t D_t+ \beta_1 d^{Roll}_{it}+ \epsilon_{it}
$$

$d_{Roll}$是哑变量，判断美联储是否实行了 dollar roll sales. 

$\beta_1$的估计结果为负值，意味着在美联储 dollar roll sales后，specialness 会下降。

## 结论

Dollar roll 可以看做以 MBS 为抵押品的融资，但在以下方面又与 MBS 回购不同。
  
- 再交付风险：资金融出者可以选择在贷款到期时归还不同的 MBS 抵押品。

- 所有权交换：MBS 的所有权在融资期间有所转移。
  
因此造成了通过 dollar roll 融资的成本比回购更低，也即 dollar roll specialness.

美联储可以通过 dollar roll sale 推迟交割，缓解由量化宽松购买 MBS 造成的供应短缺。


## Reference

Song, Z., & Zhu, H. (2019). Mortgage Dollar Roll. _The Review of Financial Studies_, _32_(8), 2955–2996. [https://doi.org/10.1093/rfs/hhy117](https://doi.org/10.1093/rfs/hhy117)

[美元滚动策略即dollar roll是什么，能直白的解释下吗？ - 知乎](https://www.zhihu.com/question/67960832/answer/2331550109)


[李力，雕刻现金流：从证券化到项目融资，中信出版集团股份有限公司，2017](https://weread.qq.com/web/reader/78c32f805e10dc78c9981c5kc81322c012c81e728d9d180)

[林华，中国资产证券化产品投资手册，中信出版集团股份有限公司，2017](https://weread.qq.com/web/reader/cab3224071ae93c6cabb193kc81322c012c81e728d9d180)

