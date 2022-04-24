---
title: "Options"
---

## Properties of Options

### Factors affecting option prices
![](Pasted%20image%2020220220232341.png)

### Call-Put Parity

Portfolio A : one European call option plus a zero-coupon bond that provides a payoff of $K$ at time $T$ Portfolio B : one European put option plus one share of the stock.

$$c+Ke^{-rT}=p+S_0$$

### American Options

-   It is **never optimal to exercise an American call option** on a non-dividend-paying stock before the expiration date.
-   A call option, when held instead of the stock itself, in effect insures the holder against the stock price falling below the strike price. Once the option has been exercised and the strike price has been exchanged for the stock price, this insurance vanishes.
-   The time value of money. From the perspective of the option holder, the later the strike price is paid out the better.
-   _What if the investor thinks the stock is currently overpriced and is wondering whether to exercise the option and sell the stock? In this case, the investor is better off selling the option than exercising it._

$$C\geq c\geq S_0-Ke^{-rT}>S_0-K$$

-   It can be optimal to exercise an American put option on a non-dividend-paying stock early. Indeed, at any given time during its life, the put option should always be exercised early if it is sufficiently deep in the money.

## Trading Strategies

### Principal-protected notes

-   A 3-year zero-coupon bond with a principal of $1,000
-   A 3-year at-the-money European call option on the stock portfolio.

### Option and Underlying Asset

-   writing a covered call: the portfolio consists of **a long position in a stock** plus **a short position in a European call option.**
-   protective put strategy: the investment strategy involves **buying a European put option** on a stock and **the stock itself.**

### Bull Spreads

-   **buying** a European **call** option on a stock with a certain strike price and **selling** a European **call** option on the same stock **with a higher strike price**. Both options have the same expiration date.
-   The strategy can be described by saying that the investor has a call option with a strike price equal to $K_1$ and has chosen to give up some upside potential by selling a call option with strike price $K_2 (K2 > K1)$.

### Bear Spreads

-   Bear spreads can be created by **buying** a European **put** with one strike price and **selling** a European **put** with another strike price. The strike price of the option purchased is greater than the strike price of the option sold.
-   The investor has bought a put with a certain strike price and chosen to give up some of the profit potential by selling a put with a lower strike price

### Box Spreads

-   A box spread is a combination of a bull call spread with strike prices $K_1$ and $K_2$ and a bear put spread with the same two strike prices.
-   The payoff from a box spread is always $K_2-K_1$. The value of a box spread is therefore always the present value of this payoff or $(K_2-K_1)e^{-rT}$ .

### Butterfly Spreads

-   A butterfly spread involves positions in options with three different strike prices.
-   It can be created by
    -   buying a European call option with a relatively low strike price $K_1$,
    -   buying a European call option with a relatively high strike price $K_3$,
    -   and selling two European call options with a strike price $K_2$ that is halfway between $K_1$ and $K_3$.
-   Generally, $K_2$ is close to the current stock price.

### Calendar Spreads

-   A calendar spread can be created by **selling a European call option with a certain strike price** and **buying a longer-maturity Eurpean call option with the same strike price.**
-   The longer the maturity of an option, the more expensive it usually is.

### Straddle

-   buying a European call and put with the same strike price and expiration date.

### Strips

-   A strip consists of a long position in **one European call and two European puts** with the same strike price and expiration date.
-   In a strip the investor is betting that there will be a big stock price move and considers a decrease in the stock price to be more likely than an increase.

### Straps

-   A strap consists of a long position in **two European calls and one European put** with the same strike price and expiration date.
-   In a strap the investor is also betting that there will be a big stock price move. However, in this case, an increase in the stock price is considered to be more likely than a decrease.

### Strangles

-   In a strangle, an investor **buys a European put and a European call with the same expiration date and different strike prices**.

## Binomial Tree

### Riskless

We imagine a portfolio consisting of a long position in $H$ shares and a short position in one option. At the beginning, the value is

$$HS_0+C_0$$

If there is an up movement in the stock price, the value of the portfolio at the end of the life of the option is

$$HS_u+C_u$$

If there is a down movement in the stock price, the value becomes

$$HS_d+C_d$$

Riskless:

$$HS_u+C_u=HS_d+C_d=e^{r}(HS_0+C_0)$$

Calculate $C_0$.

### Replicate Portfolios

We imagine a portfolio consisting of a long position in $H$ shares and $B$ bonds.

$$HS_u+e^{r}B=C_u,\ HS_d+e^{r}B=C_d$$

$$C_0=HS_0+B$$

### Risk Neutral

The option pricing formula in equation does not involve the probabilities of the stock price moving up or down.

The probabilities of future up or down movements are already incorporated into the stock price: we do not need to take them into account again when valuing the option in terms of the stock price.

A risk-neutral world has two features that simplify the pricing of derivatives:

-   The expected return on a stock (or any other investment) is the risk-free rate.
-   The discount rate used for the expected payoff on an option (or any other instrument) is the risk-free rate.

$$S_0=e^{-r}[qS_u+(1-q)S_d]$$

solve $q$, and plug in:

$$C_0=e^{-r}[qC_u+(1-q)C_d]$$

### Derivation the BSM Formula from a Binomial Tree

**See John Hull OFD C13 Appendix**

## Continuous Time Finance

### Brownian Motion

A continuous stochastic process $W(t), t \geq 0,$ is a Brownian motion if

-   $W(0)=0$
-   The increments of the process $W\left(t_{1}\right)-W(0), W\left(t_{2}\right)-W\left(t_{1}\right), \cdots, W\left(t_{n}\right)-W\left(t_{n-1}\right),$$\forall 0 \leq t_{1} \leq t_{2} \leq \cdots \leq t_{n}$ are independent
-   Each of these increments is normally distributed with distribution $W\left(t_{i+1}\right)-W\left(t_{i}\right) \sim N\left(0, t_{i+1}-t_{i}\right)$

### Ito Formula

$$d f=\left(\frac{\partial f}{\partial t}+\beta(t, X) \frac{\partial f}{\partial x}+\frac{1}{2} \gamma^{2}(t, X) \frac{\partial^{2} f}{\partial x^{2}}\right) d t+\gamma(t, X) \frac{\partial f}{\partial x} d W(t)$$

from Taylor's formula as quadratic variation = $dWdW=dt$

### BSM Formula

Assumptions

1.  The stock price follows $dS_t=\mu S_t dt+\sigma S_t dW_t$ with $\mu$ and $\sigma$ constant.
2.  The short selling of securities with full use of proceeds is permitted.
3.  There are no transaction costs or taxes. All securities are perfectly divisible.
4.  There are no dividends during the life of the derivative.
5.  There are no riskless arbitrage opportunities.
6.  Security trading is continuous.
7.  The risk-free rate of interest is constant and the same for all maturities.

#### Lognormal Property of Stock Prices

Stock Price

$$dS_t=\mu S_t dt+\sigma S_t dW_t$$

Return

$$dR_t=\mu dt+\sigma dW_t$$

#### Reallocate the wealth

A self-financing strategy to reallocate the wealth $X_t$:

-   long or short $\Delta_t$ shares of stocks;
-   borrow or lend the $X_t-\Delta_tS_t$ amount of money

$$\begin{aligned}dX_t&=\Delta_tdS_t+r(X_t-\Delta_tS_t)dt\\&=\Delta_t[\mu S_tdt+\sigma S_tdW_t]+r(X_t-\Delta_tS_t)dt\\&=[rX_t+\Delta_t(\mu-r)S_t]dt+\Delta_t\sigma S_tdW_t\end{aligned}$$

#### Calculate call option's value

Suppose that $c$ is the price of a call option on the stock. The variable $c$ must be some function of $S$ and $t$, i.e. $c(S_t,t)$. Hence, by using Ito formula,

$$\begin{aligned}& d c(t, S_t) \\=& c_{t}(t, S_t) d t+c_{x}(t, S_t) d S_t+\frac{1}{2} c_{x x}(t, S_t) d[S, S](t) \\=&\left[c_{t}(t, S_t)+\mu S(t) c_{x}(t, S_t)+\frac{1}{2} \sigma^{2} S^{2}_t c_{x x}(t, S_t)\right] d t \\&+\sigma S_t c_{x}(t, S_t) d W_t\end{aligned}$$

#### $dX_t=dc(t,S_t)$

We have

$$c_t(t,S_t)+rS_tc_x(t,S_t)+\frac{1}{2}\sigma^2S^2_tc_{xx}(t,S_t)-rc(t,S_t)=0$$

the terminal condition

$$c(T,S_t)=(S_t-K)^{+}$$

#### BSM Formulas

$$\begin{array}{c} c=S_{0} N\left(d_{1}\right)-K e^{-r T} N\left(d_{2}\right) \\ p=K e^{-r T} N\left(-d_{2}\right)-S_{0} N\left(-d_{1}\right) \end{array}$$

$$\begin{array}{l} d_{1}=\frac{\ln \left(S_{0} / K\right)+\left(r+\sigma^{2} / 2\right) T}{\sigma \sqrt{T}} \\ d_{2}=\frac{\ln \left(S_{0} / K\right)+\left(r-\sigma^{2} / 2\right) T}{\sigma \sqrt{T}}=d_{1}-\sigma \sqrt{T} \end{array}$$

The term $N(d_2)$ is the probability that a call option will be exercised in a risk-neutral world.

The expression $S_0N(d_1)e^{rT}$ is the expected stock price at time $T$ in a risk-neutral world when stock prices less than the strike price are counted as zero.

Solve the PDE, or connect between stochastic processes and PDEs with **Feynman-Kac Theorem.**

### Martingale Method

Let

$$d \tilde{W}_{t}=\frac{\mu-r}{\sigma} d t+d W_{t}$$

We have

$$\begin{aligned}d S_{t} &=\mu r S_{t} d t+\sigma S_{t}\left(d W_{t}^{Q}-\frac{\mu-r}{\sigma} d t\right) \\&=r S_{t} d t+\sigma S_{t} d W_{t}^{Q}\end{aligned}$$

Under $Q$, we have the following martingales:

-   the discounted underlying asset price $e^{-rt}S_t$
-   the discounted replicating portfolio value $e^{-rt}X_t$
-   the discounted option price $e^{-rt}V_t$

The Q-martingale property leads to

$$\begin{aligned}c(t,S_t)=V_{t} &=e^{-r(T-t)} E^{Q}\left[\left(S_{T}-K\right) \cdot \mathbf{1}_{\left\{S_{T} \geq K\right\}} \mid \mathcal{F}_{t}\right] \\&=S_{t} Q\left\{x \geq-d_{2}-\sigma \sqrt{T-t}\right\}-K e^{-r(T-t)} Q\left\{x \geq-d_{2}\right\} \\&=S_{t} N\left(d_{1}\right)-K e^{-r(T-t)} N\left(d_{2}\right)\end{aligned}$$

## Greeks

$$\text { Delta: } \Delta=\frac{\partial f}{\partial S} ; \text { Gamma: } \Gamma=\frac{\partial^{2} f}{\partial S^{2}} ; \text { Theta: } \Theta=\frac{\partial f}{\partial t} ; \text { Vega: } v=\frac{\partial f}{\partial \sigma} ; \text { Rho: } \rho=\frac{\partial f}{\partial r}$$

### Naked and covered positions

#### naked position

-   One strategy open to the financial institution is to do nothing.

#### covered position

-   This involves buying 100,000 shares as soon as the option has been sold. If the option is exercised, this strategy works well, but in other circumstances it could lead to a significant loss.

### A stop-loss strategy

-   an institution that has written a call option with strike price $K$ to buy one unit of a stock. The hedging procedure involves buying one unit of the stock as soon as its price rises above $K$ and selling it as soon as its price falls below $K$.

Problem

-   The first is that the cash flows to the hedger occur at different times and must be discounted. The second is that purchases and sales cannot be made at exactly the same price K.

### Delta hedging

-   Delta is defined as the rate of change of the option price with respect to the price of the underlying asset.

$$\Delta(call)=N(d_1),\ \Delta(put)=N(d_1)-1$$

#### Dynamic Aspects of Delta Hedging

-   Derivatives dealers usually rebalance their positions once a day to maintain delta neutrality.

### Theta

-   The theta of a portfolio of options is the rate of change of the value of the portfolio with respect to the passage of time with all else remaining the same.
-   **time decay**
-   As time passes with all else remaining the same, the option tends to become less valuable.
-   When the stock price is very low, theta is close to zero.
-   For an at-the-money call option, theta is large and negative.

### Gamma

The gamma of a portfolio of options on an underlying asset is the rate of change of the portfolio’s delta with respect to the price of the underlying asset.

$$\Delta \Pi=\Theta \Delta t+\frac{1}{2} \Gamma \Delta S^{2}$$

#### Making a Portfolio Gamma Neutral

-   Delta neutrality provides protection against relatively small stock price moves between rebalancing.
-   Gamma neutrality provides protection against larger movements in this stock price between hedge rebalancing.

$$w_{T}=-\Gamma/\Gamma_T$$

### Relationship between Delta, Theta, and Gamma

$$\Theta+rS\Delta+\frac{1}{2}\sigma^2 S^2\Gamma=r\Pi$$

-   theta can to some extent be regarded as a proxy for gamma in a delta-neutral portfolio.

### Vega

-   the rate of change of the value of the portfolio with respect to the volatility of the underlying asset.
-   If a hedger requires a portfolio to be both gamma and vega neutral, **at least two traded derivatives** dependent on the underlying asset must usually be used.
-   When volatilities change, the implied volatilities of short-dated options tend to change by more than the implied volatilities of long-dated options. The vega of a portfolio is therefore often calculated by changing the volatilities of long-dated options by less than that of short-dated options.

### Rho

-   The rho of a portfolio of options is the rate of change of the value of the portfolio with respect to the interest rate.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1c65c777-465e-42c5-9d70-53f782174b16/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1c65c777-465e-42c5-9d70-53f782174b16/Untitled.png)

## Volatility Smile

-   The volatility smile defines the relationship between the implied volatility of an option and its strike price.
-   For equity options, the volatility smile tends to be downward sloping.
    -   This means that **out of-the-money puts** and **in-the-money calls** tend to have high implied volatilities whereas **out-of-the-money calls** and **in-the-money puts** tend to have low implied volatilities.
-   For foreign currency options, the volatility smile is U-shaped.
    -   Both out-of-the-money and in-the-money options have higher implied volatilities than at-the-money options.
-   A refinement of this is to calculate the volatility smile as the relationship between the implied volatility and $K/S_0$ or $K/F_0$, where $F_0$ is the forward price of the asset for a contract maturing at the same time as the options that are considered.
-   Yet another approach to defining the volatility smile is as the relationship between the implied volatility and the delta of the option.

## Exotic Options

### Perpetual American Options

A perpetual derivative has $T=\infty$.

Recall Black-Scholes equation:

$$c_t(t,S_t)+rS_tc_x(t,S_t)+\frac{1}{2}\sigma^2S^2_tc_{xx}(t,S_t)-rc(t,S_t)=0$$

The term $c_t(t,S_t)$ disappears from the equation due to time-homogeneity, and we get an **ODE instead of a PDE.**

### Bermudan Options

Early exercise may be restricted to **certain dates**.

### Gap Options

A gap call option is a European call options that pays off $S_T-K_1$ when $S_T > K_2$.

The difference between a gap call option and a regular call option with a strike price of $K_2$ is that the payoff when $S_T > K_2$ is increased by $K_2-K_1$.

### Forward Start Options

Forward start options are options that will **start at some time in the future**. Sometimes employee stock options can be viewed as forward start options.

### Compound Options

Compound options are options on options. Compound options have two strike prices and two exercise dates.

Consider, for example, a call on a call. On the first exercise date, $T_1$, the holder of the compound option is entitled to pay the first strike price, $K_1$, and receive a call option.

The call option gives the holder the right to buy the underlying asset for the second strike price, $K_2$, on the second exercise date, $T_2$. The compound option will be exercised on the first exercise date only if the value of the option on that date is greater than the first strike price.

### Barrier Options

Barrier options are options where the payoff depends on whether the underlying asset’s price reaches a certain level during a certain period of time.

A **knock-out option** ceases to exist when the underlying asset price reaches a certain barrier; **a knock-in option** comes into existence only when the underlying asset price reaches a barrier.

### Binary Options

Binary options are options with discontinuous payoffs.

A simple example of a binary option is a **cash-or-nothing call**. This pays off nothing if the asset price ends up below the strike price at time $T$ and pays a fixed amount, $Q$, if it ends up above the strike price.

### Lookback Options

The payoffs from lookback options depend on the maximum or minimum asset price reached during the life of the option.

The payoff from a floating lookback call is the amount that the final asset price exceeds the minimum asset price achieved during the life of the option.

The payoff from a floating lookback put is the amount by which the maximum asset price achieved during the life of the option exceeds the final asset price.

### Shout Options

A shout option is a European option where the holder can ‘‘shout’’ to the writer at one time during its life.

At the end of the life of the option, the option holder receives **either the usual payoff from a European option or the intrinsic value at the time of the shout, whichever is greater**.

### Asian Options

Asian options are options where the payoff depends on the **arithmetic average** of the price of the underlying asset during the life of the option.

### Exchange Options

An option to buy yen with Australian dollars is, from the point of view of a US investor, an option to exchange one foreign currency asset for another foreign currency asset.

A stock tender offer is an option to exchange shares in one stock for shares in another stock.

### Options Involving Several Options

Rainbow options. European basket option.

### Volatility Swap

A volatility swap is an agreement to exchange the realized volatility of an asset between time $0$ and time $T$ for a prespecifed fixed volatility.

## Real Options

### Extension of the Risk Neutral Valuation Method

the market price of risk for a variable $\theta$ was defined as

$$\lambda=\frac{\mu-r}{\sigma}$$

where $r$ is the risk-free rate, $\mu$ is the return on a traded security dependent only on $\theta$, and $\sigma$ is its volatility. Suppose that a real asset depends on several variables $\theta_i$. Let $m_i$ and $s_i$ be the expected growth rate and volatility of $\theta_i$

$$d\theta_i/\theta=m_idt+s_idW_t$$

where $W_t$ is a Brownian Motion.

Define $\lambda_i$ as the market price of risk of $\theta_i$. Risk-neutral valuation can be extended to show that any asset dependent on the i can be valued by

-   Reducing the expected growth rate of each $\theta_i$ from $m_i$ to $m_i-\lambda_is_i$ (because $(m_i-r)/s_i=\lambda_i$.)
-   Discounting cash flows at the risk-free rate.

### Estimating the Market Price of Risk

$\rho$: Instantaneous correlation between the percentage changes in the variable and returns on a broad index of stock market prices

$\mu_m$: Expected return on broad index of stock market prices

$\sigma_m$: Volatility of return on the broad index of stock market prices

From a continuous-time version of the capital asset pricing model

$$\mu-r=\frac{\rho\sigma}{\sigma_m}(\mu_m-r)$$

Another expression

$$\mu-r=\lambda\sigma$$

Thus

$$\lambda=\frac{\rho}{\sigma_m}(\mu_m-r)$$

### Examples of Options Embedded in Projects

-   **Abandonment options**: It is an American put option on the project’s value.
-   **Expansion options**: It is an American call option on the value of additional capacity. The strike price of the call option is the cost of creating this additional capacity discounted to the time of option exercise.
-   **Contraction options**: It is an American put option on the value of the lost capacity. The strike price is the present value of the future expenditures saved as seen at the time of exercise of the option.
-   **Options to defer**: This is an American call option on the value of the project.
-   **Options to extend life**: This is a European call option on the asset’s future value.

## Reference

OFD / John Hull

《金融经济学二十五讲》/ 徐高

《金融经济学十讲》/ 史树中

Financial Calculus: An Introduction to Derivative Pricing / Martin Baxter

[布朗运动、伊藤引理、BS公式（前篇）](https://mp.weixin.qq.com/s?__biz=MzIyMDEwNDk1Mg==&mid=2650876491&idx=1&sn=2ccfdfbaf250228974e984c5e7168366&chksm=8c249bdcbb5312ca46b0261df16109ad8e19d559ab919dd95f8097b46b36eaf81e85b4eef76c&scene=126&sessionid=1605256784&key=409586cdc8db5733d89744fef149cbd55e0825fce39bb62d733d518ddf15b3e1ecd31bb2ba4e18d5c4853db53d9fb1cba066bb33110f8740f658772187889b75c666cbb2a0fd6f016e9b0079f7403eadcb884f6a5bd1c6e957edbebba629f17c26a5c2f9489f0820c2cabc44aa656224da99bcf28ba4bf2f4170c17b3f255ca9&ascene=1&uin=MjU1NDk5MDUwOA%3D%3D&devicetype=Windows+10+x64&version=6300002f&lang=zh_CN&exportkey=A0Tn4xOWv3Nl%2BjMxJtPWumI%3D&pass_ticket=ok4tnaFWS7zPPSCRKPSyUIzrRRcpn0LMaKl%2FkngUWsaWK0ChENo%2FKgwaJH5CCexq&wx_header=0)

[布朗运动、伊藤引理、BS公式（后篇）](https://mp.weixin.qq.com/s?__biz=MzIyMDEwNDk1Mg==&mid=2650876561&idx=1&sn=ee4ecb91b0c95e7d539375ef35efdf4a&chksm=8c249b06bb53121043a58a2163779774ef0f054659bee3033ff2cb3b7af7996bd75a3a862e31&scene=126&sessionid=1605256784&key=cc7cc2a0b445493e06dbff52441567153cc0ac0f70486c51768cc951d0871d265c6e19ab75a980bbef7f1864f8f6bd16dcf347cfa2628abb7b13727fcbdf5188cc98f354b29144935c3aecd91ad2f0011ef56f23448f8df115987ca174fac91babc728e21455cb515b27820ee01203a772cb23c4a69a797b16820bb2213c58c5&ascene=1&uin=MjU1NDk5MDUwOA%3D%3D&devicetype=Windows+10+x64&version=6300002f&lang=zh_CN&exportkey=A7l3K9ytHaVtOJYXPnoJ8Sw%3D&pass_ticket=ok4tnaFWS7zPPSCRKPSyUIzrRRcpn0LMaKl%2FkngUWsaWK0ChENo%2FKgwaJH5CCexq&wx_header=0)

[《期权交易随笔》题记](https://mp.weixin.qq.com/s?__biz=MzIyMTE5OTE5Mg==&mid=409677815&idx=2&sn=491afd3a6f32dea8d3282ea1fb5aa02b&chksm=0a5fe1c03d2868d60ed449598bbe5d72e6281f8a038a0e4a52876768d50edc248a8c49210cb1&scene=126&sessionid=1605759166&key=e17ad8edb8d975168ae4132b815fac2689bbcfcb92f93d58076345765d5cd2a91167cdafb664797fcd8a9b664459656a6ac0dde4490e389de04932454612f3f59527447cbbe69dc1483225420a515553eb0e30f7b9fd915c34f1346e29564da1e2ef8a0053d40ee27f65c3c3c790be526070ec2cfbc98e942b7d9fca74a663fd&ascene=1&uin=MjU1NDk5MDUwOA%3D%3D&devicetype=Windows+10+x64&version=6300002f&lang=zh_CN&exportkey=A1eyaqvaIFoWdFTokV4gWNI%3D&pass_ticket=6X9rN0ahWibDlXeT0QKsoq3d9UL3kop49HI7%2F%2Ba%2B30zMh6TprHofEq9FsxXicYqb&wx_header=0)

[BS公式--鞅定价推导法](https://zhuanlan.zhihu.com/p/95538708)

[American Options](https://people.kth.se/~armerin/FinInsMathRwanda/Lecture18.pdf)