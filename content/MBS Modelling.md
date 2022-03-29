---
Area: Finance
Source: Book
Status: Done
Type: Notes
---


# 抵押贷款支持证券

资产证券化是指将能够产生可预见的稳定现金流的资产，通过一定的结构安排，对资产中风险与收益要素进行分离与重组，进而转换成为在金融市场上可出售、可流通的证券的过程。
 
设法剥离主体带来的不确定性，以“物的信用”替代“主体信用”，以基础资产“自动变现”产生现金流为偿付支持发行标准化债务证券，通过引入第三方机构、架设结构化交易安排来拆解、控制道德风险，就是“资产支持证券”的核心理念。
 
最早出现的资产支持证券是20世纪70年代诞生的以住宅抵押贷款为基础资产的RMBS，之后又陆续诞生了以其他信贷资产为支持的证券。

传统的MBS交易结构中没有分层设计，所发行的证券之间不存在偿付次序、风险等级的区别，这种结构被称为“过手型” (pass-through) 结构。相对而言，将现金流进行分层、增信之后再按先后次序支付给不同等级证券投资人的交易结构叫作“转付型” (pay-through) 结构。

和其他固定收益类产品一样，MBS的价值可以用现金流折现进行评估：

$$
V=\sum_{i=1}^N\frac{CF_i}{(1+d)^i}
$$

其中$d$为折现率 (discount rate). 

折现率和当前抵押贷款挂钩的利率种类的远期利率有关，可以采用随机过程模型对远期利率进行建模。如：
Vasicek Model
$$
dR_t=a(b-R_t)dt+\sigma dW_t
$$
CIR Model
$$
dR_t=a(b-R_t)dt+\sigma \sqrt R_t dW_t
$$
Hull-White Model
$$
dR_t=a(b_t-R_t)dt+\sigma dW_t
$$

但不同的是，由于借款人可以选择提前偿还贷款，所以每一期的现金流是不确定的，会受到利率的影响。即：
$$
CF_i=f(r)
$$

市场利率上升会导致抵押贷款支持证券出现延长风险 (extension risk)。收益率上行时，预期中的提前还款速度放缓，导致抵押贷款支持证券投资者收回本金的时机延后。投资人将因为延后收回本金而错过在收益率较高时进行再投资的机会。如果利率继续上升，低票息抵押贷款支持证券的价格下跌，高票息抵押贷款支持证券的表现要好于低票息抵押贷款支持证券。


市场利率下降将出现抵押贷款者提前清偿的风险 (prepayment risk)，使抵押贷款支持证券投资人被迫降低仓位，存续期限缩短。

因此，在对MBS进行建模时，既要对每一期的折现情况进行建模，也要估计每一期现金流的情况。


## 抵押贷款的现金流
假设某支抵押贷款的年息票利率为$\hat C$，到期日为$N$个月。令：
$$
c=\frac{\hat C}{12}, d=\frac{1}{1+c}
$$
假设名义本金为单位1，每月还款额 (Scheduled monthly payment)为$m$，则应该有
$$
1=\sum_{i=1}^N \frac{m}{(1+c)^i}
$$
解得
$$
m=\frac{c}{1-d^N}
$$

第$j$个月底，设尚未还款的余额为$B_j$，有
$$
\sum_{i=1}^{j}\frac{m}{(1+c)^i}+B=(1+c)^j
$$
得
$$
B_j=\frac{1-d^{N-j}}{1-d^N}
$$
第$j$个月的利息偿还额为
$$
I_j = cB_{j−1}=\frac{c\left(1-d^{N-j+1}\right)}{1-d^{N}}
$$
第$j$个月的本金偿还额为
$$
P_j = m-I_j=m-cB_{j−1}=\frac{cd^{N-j+1}}{1-d^{N}}
$$


## 早偿情况的分析

利率走低时，借款人更倾向于提前还贷，用更低利率的贷款置换现有贷款；利率走高时，借款人则倾向于放慢还贷速度，更多的享受低息好处。

每月早偿率 (single monthly mortality rate, SMM) 衡量了贷款池中在当月提前偿还的比率：

$$
SMM=\frac{Scheduled\ balance − Ending\ balance}{Scheduled\ balance}
$$

条件早偿率 (Conditional Prepayment Rate, CPR) 是SMM的年化结果：
$$
CPR=1-(1-SMM)^{12}
$$

### PSA模型

PSA模型 (Public Securities Association Model) 是估计早偿率的一种经验方法：第一个月的CPR设为0.2%，此后每个月增加0.2%的CPR，直到第30个月后，始终维持CPR为6%不变。150PSA的假设意味着要将PSA模型乘以150%。

该模型的基本假设是，成立时间越久的抵押贷款，提前还贷的可能性越大，越是新贷款，提前还贷的可能性越小；但是，在贷款成立30个月之后，提前还贷比率将稳定在一个恒定的值而不再变化。


### 影响早偿率的因素

#### 主要因素

**借款人再融资的动力 (Incentive to Refinance)**
- 如果市场抵押贷款利率下降，抵押贷款者将有动力提前偿还贷款然后以较低的利率进行再融资，因此提高了早偿率。
- 一般用现行市场利率和抵押贷款者的利率的差值来衡量借款人再融资的动力。

**贷款持有时间 (Age of a Mortgage)**
- 抵押贷款人可能因为工作调动、家庭因素、房屋价格影响而选择置换房屋，为此需要清偿抵押贷款，因此房屋换手情况对早偿率有影响。
- 类似于PSA模型，将房屋换手率和抵押贷款人的贷款持有时间相关联，一般贷款账龄在30个月时CPR将达到顶峰。


**季节因素**
- 不同的月份和季度，还款人提前偿还的概率不同，主要和家庭因素相关（如为孩子上学而搬家），房屋的销售也有季节性。

**贷款人的倦怠 (Borrower Burnout)**
- 虽然一般情况下，利率下降会导致借款人有动力进行再融资，但有些时候会发现，即使利率下降，借款人也没有提前偿还。这可能是因为借款人此前已经提前还款过了，或者是这个池中的借款人对利率不敏感，不会进行再融资。
- Burnout是用来捕捉某个特定的MBS中不同贷款的异质性，关注这个池中借款人之前的提前偿还记录，通过之前的行为来推测之后是否会有提前偿还的动力。
	- 再融资速度：通过借款人从利率下降到进行再融资的反应时间判断这是一个快速还款人还是一个慢速还款人
	- 逆向选择：信用条件较好的借款人会比信用条件更差的还款人更快进行再融资   
$$
\text{burnout} = \text{exp}^{\beta_1\times \text{Loan\ Age}+\beta_2\times \text{Incentive}}
$$
$$
\text{where Incentive = Max[(Note rate − Mtg. rate), Start value]}
$$
- 其中$\beta_1,\beta_2$可以根据经验确定Burnout衡量了某个借款人是否会是快速还款人的先验概率。

#### 其他因素

**房价 (House Price Index, HPI)**
**信用评分 (FICO)**
**债务收入比 (Debt-to-Income Ratio, DTI)**
**贷款价值比 (Loan-to-Value Ratio, LTV)**
**贷款余额**
- 由于再融资存在固定费用，对贷款余额较低的借款人来说，固定费用的占比会上升，所以余额较低的借款人需要更高的市场利率和原贷款利率差值才有提前还款再融资的动机。

**贷款期限**
- 通常，具有更强信用和更大财务灵活性的借款人会选择更短的摊销期限，这意味着 15 年的借款人可能比 30 年的借款人表现出更大的再融资倾向。

**贷款利率类型**
- 与标准固定利率抵押贷款相比，借款人可以选择可调整利率或混合抵押贷款（初始固定利率随后是可调整利率的抵押贷款），以获得较低的相对起始付款。不断浮动的贷款利率可能会激励借款人再融资。


### 生存分析建模

Schwartz和Torous利用1978-1987的美国30年期GNMA MBS数据，建立生存分析(survival analysis)模型，用Cox Proportional-hazards Model来对早偿率进行建模。

设某个抵押贷款从开始到提前偿还的时间为连续随机变量$T$，$t$是其实现。设$\underline{v}=\left(v_{1}, v_{1}, \cdots, v_{s}\right)$为由影响早偿率的各种变量组成的向量，$\underline{\theta}=\left(\theta_{1}, \theta_{2}, \cdots, \theta_{k}\right)$是需要估计的系数值。早偿率函数$\lambda(t ; \underline{v}, \underline{\theta})$可以写为：
$$
\begin{aligned}
\lambda(t ; \underline{v}, \underline{\theta}) &=\lim _{\Delta t \rightarrow 0^{+}} \frac{P(t \leq T<t+\Delta t \mid T \geq t)}{\Delta t} \\
&=\frac{f(t ; \underline{v}, \underline{\theta})}{F(t ; \underline{v}, \underline{\theta})}
\end{aligned}
$$
其中$f(t)$是$T$的概率密度函数，$F(t)$是$T$的分布函数。
$$ 
F(t ; \underline{v}, \underline{\theta})=P(T \geq t \mid \underline{v}, \underline{\theta}) 
$$

$$ 
f(t ; \underline{v}, \underline{\theta})=\lim _{\Delta t \rightarrow 0^{+}} \frac{P(t \leq T<t+\Delta t)}{\Delta t}=-\frac{dF(t)}{dt}
$$

使用Cox Proportional-hazards Model对早偿率进行建模：

$$
\lambda(t ; \underline{v}, \underline{\theta})=\lambda_{0}(t ; \gamma, p) \exp (\underline{\beta} \underline{v})
$$
其中基准风险函数 (base-line hazard function) $\lambda_{0}(t ; \gamma, p)$由对数逻辑斯谛函数(log-logistic hazard function)的形式给出

$$
\lambda_{0}(t ; \gamma, p)=\frac{\gamma p(\gamma t)^{p-1}}{1+(\gamma t)^{p}}
$$
Base-line hazard function衡量的是没有考虑其它解释变量时提前偿还的风险： $\underline{v}=\underline{0}$. Log-logistic hazard function考虑了早偿率和贷款年龄之间的关系。如果$p>1$, 提前偿还的风险从0逐渐上升到最大值：
$$
t^{*}=(p-1)^{1 / p} / \gamma
$$

$\underline{v}$中还包括影响MBS价格的其他因素，包括借款人的还款激励、此前提前还款的情况、季节因素等。


## 违约情况的分析

### 影响违约率的因素

**房价 (House Price Index, HPI)**
**信用评分 (FICO)**
**债务收入比 (Debt-to-Income Ratio, DTI)**
**贷款价值比 (Loan-to-Value Ratio, LTV)**
**贷款金额 (Loan Size) 及其对数**
**贷款种类**
	- 固定利率、浮动利率等
**物业类型**
	- 独栋、3-4人合并住宅等
**占有人类型 (Occupancy Type)**
	- 原所有人占有（owner-occupied）、第二住宅（second home）、非所有人占有（non-owner-occupied）等
**借款目的 (Loan Purpose)**
	- 购买住宅 (Purchase)
	- 再融资 (Refinance)
	- 将住宅再融资以取得现金 (Cashout)

### 对违约过程建模

MBS的违约过程是一个多状态的过程，可以看作一个连续时间的马尔科夫链：
$$
S=\left[\begin{array}{l}
S_{1} \\
S_{2} \\
S_{3} \\
S_{4} \\
S_{5}
\end{array}\right]=\left[\begin{array}{c}
\text { Current } \\
60+\text { Days Delinquent } \\
\text { In Foreclosure } \\
\text { REO } \\
\text { Liquidated }
\end{array}\right]
$$

$$
D(t)=\left[\begin{array}{ccccccc}
-\lambda_{1}(t) & \lambda_{1}(t) & 0 & 0 & \ldots & 0 & 0 \\
0 & \lambda_{2}(t) & -\lambda_{2}(t) & 0 & \cdots & 0 & 0 \\
\vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots \\
0 & 0 & 0 & 0 & \ldots & -\lambda_{n-1}(t) & \lambda_{n-1}(t) \\
0 & 0 & 0 & 0 & \ldots & 0 & 0
\end{array}\right]
$$
其中 $\lambda_{j}(t)$ 是transitions $S_{j} \rightarrow S_{j+1}$过程的风险函数。

因此可以将MBS的违约步骤分拆成几个生存分析过程，然后再对每个过程进行建模。

## 房价指数分析

房屋价格水平会影响早偿率和违约率。如果房价下跌，借款人违约的可能性升高。对HPI/HPA的建模是一个比较复杂的过程，可以考虑将HPI看作一个随机过程：
$$
d HPI =a dt +\sigma_w dz
$$
$\sigma_w$是波动率，$a$是漂移，$z$是布朗运动。

HPA（房价指数增长率）是HPI的年回报率。白噪声+扩散模型可以用来对HPA进行建模：有：
$$
HPA=\frac{d HPI}{dt} = a+\sigma_w w
$$


设$\sigma_d$是HPA扩散的波动率，一阶扩散模型的理论统计量的函数是

$$
\begin{gathered}
\operatorname{stdev}[H P A(t)]=\left[\sigma_{d}^{2} \frac{1-e^{-2 a t}}{2 a}+\sigma_{w}^{2}\right]^{\frac{1}{2}} \\
\operatorname{Corr}[\operatorname{HPA}(T), H P A(t+T)] \underset{T \rightarrow \infty}{\rightarrow e^{-a t} \frac{1}{1+2 a \sigma_{w}^{2} / \sigma_{d}^{2}}}
\end{gathered}
$$


## Reference

[Andrew Lesniewski, Interest Rate and Credit Models: 13. Mortgage Backed Securities](https://mfe.baruch.cuny.edu/wp-content/uploads/2019/12/IRC_Lecture13_2019.pdf)

Schwartz, E. S., and W. N. Torous, 1989, “Prepayment and the Valuation of Mortgage-Backed Securities,” Journal of Finance, 44, 375–392.

Davidson, A., and Levin, A.: Mortgage Valuation Models: Embedded Options, Risk, and Uncertainty, Oxford University Press (2014).

Glenn M. Schultz: Investing in Mortgage-Backed and Asset-Backed Securities, Wiley Finance, 2015

[李力，雕刻现金流：从证券化到项目融资，中信出版集团股份有限公司，2017](https://weread.qq.com/web/reader/78c32f805e10dc78c9981c5kc81322c012c81e728d9d180)

[林华，中国资产证券化产品投资手册，中信出版集团股份有限公司，2017](https://weread.qq.com/web/reader/cab3224071ae93c6cabb193kc81322c012c81e728d9d180)


