# Correlated-Multi-Asset-Monte-Carlo-(GBM)-Risk-Simulation
In this project, I analyse and quantify the risk of a $10k investment strategy. The algorithm will simulate 10,000 paths of portfolio values for the next 2 trading years (504 days), using geometric brownian motion based off the last 5 years of historical daily closed prices imported from Yahoo finance. The random simulated shocks in the stocks daily closed prices will be correlated using a Cholesky decomposition of the historical correlation matrix between the stocks in the portfolio. Next, calculate key risk metrics from the final 10 000 simulated portfolio values at the end of the 2 trading years such as VaR, CVaR, Sharpe ratio and max drawdown. The risk model's limitations will be validated through distributional inaccuracies (skew, kurtosis) of historical and the simulated daily log returns.

## Geometric Brownian Motion engine (GBM using Ito's Lemma)
The stochastic differential equation used to model time-evolution of a price $S(t)$;  

$$dS(t) = \mu S(t)dt + \sigma S(t)dB(t)$$  
where $\mu$ is the drift, $\sigma$ is the volaility.  
The solution to $S(t)$ can be found by applying Ito's Lemma [1]. Divide through by $S(t)$;  

$$\frac{dS(t)}{S(t)} = \mu dt + \sigma dB(t)$$  
The right hand sides form is similar to the derivative of $log(S(t))$, applying Ito's Lemma to $log(S(t))$; 

$$d(log(S(t))) = (log(S(t)))' \mu S(t)dt + (log(S(t)))'\sigma S(t)dB(t) + \frac{1}{2}(log(S(t)))'' \sigma^{2} S(t)^{2} dt$$  
This gives;  

$$d(log(S(t))) = \mu dt + \sigma dB(t) - \frac{1}{2}\sigma^{2}dt = (\mu - \frac{1}{2}\sigma^{2})dt + \sigma dB(t)$$  
This is an Ito drift-diffusion process which is a standard Brownian motion with a drift term. This formulae is an integral formulae so;  

$$log(\frac{S(t)}{S(0)}) = (\mu - \frac{1}{2}\sigma^{2})dt + \sigma dB(t)$$  
where the log daily return, $R = log(\frac{S(t)}{S(0)})$  
This can also be expressed exponentially;  

$$S(t) = S(0)exp((\mu - \frac{1}{2}\sigma^{2})dt + \sigma dB(t))$$  

## Roadmap Of Project:
### 1. Import closed prices of stocks from Yahoo Finance
### 2. Calculate Correlation and Covariance Matrix For Assets In Portfolio
![image alt](https://github.com/chorleyenzo/Correlated-Multi-Asset-Monte-Carlo-GBM-Risk-Simulation/blob/663cd3c5d9ba3afc71cb56596e2183fa7bf355f9/Heatmap.jpg)
### 3. Set Parameters of Portfolio (Initial value of $10k, Equal asset weighting)
### 4. Define Geometric Brownian Motion Function And Correlate Normal Random Shocks
### 5. Simulate 10,000 Correlated Paths For Each Asset
### 6. Plot Paths Of Each Assets Value Over Next 2 Trading Years
![image alt](https://github.com/chorleyenzo/Correlated-Multi-Asset-Monte-Carlo-GBM-Risk-Simulation/blob/93c322ce129d5974018863e98f0cf72732690af7/Asset_price_paths.jpg)
### 7. Plot Paths Of Overall Portfolio Value Over Next 2 Trading Years
![img alt](https://github.com/chorleyenzo/Correlated-Multi-Asset-Monte-Carlo-GBM-Risk-Simulation/blob/cabf1757173af95249451226e26a73b1cab29710/Portfolio_paths.jpg)
### 8. Calculate Risk Metrics (Sharpe ratio, VaR, CVaR, Max drawdown and Probability of Loss)
### 9. Compare And Plot Histoircal And Simulated Daily Log Returns Distributions
![image alt](https://github.com/chorleyenzo/Correlated-Multi-Asset-Monte-Carlo-GBM-Risk-Simulation/blob/cd377395d33c25b600ef6c719ee6559dbffdf327/Limitations.jpg)
  
  
  
  
    
  
## References 
[1] QuarkGluon Ltd, 2016. Geometric Brownian Motion [Online]. Available from: https://www.quantstart.com/articles/Geometric-Brownian-Motion/ [Accessed 12 August 2026].

[2] Paolucci, R. Simulating Correlated Brownian Motions [Online]. ReadMedium. Available from: https://readmedium.com/simulating-correlated-brownian-motions-2fcdeaa546a0 [Accessed 13 September 2026]


