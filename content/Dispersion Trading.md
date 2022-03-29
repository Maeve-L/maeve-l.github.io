---
Area: Finance
Source: Website
Status: Todo
Type: Notes
---

## Introduction

- Dispersion trading refers to trades in which one
	- sells index options and buys options on the index components: selling index volatility and buying volatility of the index components
	- buys index options and sells options on the index components: buying index volatility and selling volatility on the index components
- All trades are delta-neutral (hedged with stock)


### Motivation and Opportunities
- toprofit from price differences in volatility marketsusing index options and options on individual stocks
- Market segmentation, temporary shifts in correlations between assets, idiosyncratic news on individual stocks

### Strategies

#### Volatility Swaps
- Correlation trades using volatility swaps aim to capture the correlation premium embedded in the volatility smile of equity indices.
- These trades are particularly popular with hedge funds as they have a reduced cost of carry and are long vega whilst negating the theta bleed of other long vol strategies such as dual digitals or vanilla straddles.
#### Call Options on Spot Dispersion (Palladiums)
- [Palladium Options](Palladium%20Options.md) were introduced to trade correlation where there was not yet a liquid volatility swap market (EM, tech stocks and low volume stocks).
- Their payoff is the average outperformance (upside or downside) of the assets versus the basket average. Simply a call on a basket of options versus a call on the basket.
- Essentially palladiums are the average outperformance of a portfolio of straddles on all of the index components versus a straddle on the index itself. Historically, palladiums perform well in flat to rising markets where idiosyncratic risks provide outperformance versus the index as a whole.
- Palladiums are more suited to the current pricing environment of low volatility as they are relatively high vega similar to outperformance options...


## Reference

[Dispersion Trading](https://www.math.nyu.edu/~avellane/Lecture10Quant.pdf)
[Blog Page | Catley Lakeman Securities](https://www.catleylakeman.co.uk/blogPage.php?blogId=16)
