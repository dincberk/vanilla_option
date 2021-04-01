# EUROPEAN VANILLA OPTION PRICER/PRICING
Notebook code includes a European Vanilla Pricer for the monthly spread option for the given underlyings.

Notebook code has been set in different parts yet at the end vanilla pricer has been set as:

"""
def european_vanilla_option(S, K, T, r, sigma, option = 'call'):
    #S: First price set as spot price.
    #K: Second price set as the strike price.
    #T: Time to maturity.
    #r: interest rate
    #sigma: volatility of underlying asset
    #cdf: cumulative distribution function. A cumulative probability refers to the probability that the value of a random variables falls within aspecified range. Gives the area under the probability density function -from minus infinity to X-. F(x)= P|X<=x| where F(x) lies only within 0 and 1.
    
    d1 = (np.log(S / K) + (r + 0.5 * sigma ** 2) * T) / (sigma * np.sqrt(T))
    d2 = (np.log(S / K) + (r - 0.5 * sigma ** 2) * T) / (sigma * np.sqrt(T))
    
    if option == 'call':
        result = (S * si.norm.cdf(d1, 0.0, 1.0) - K * np.exp(-r * T) * si.norm.cdf(d2, 0.0, 1.0))
    if option == 'put':
        result = (K * np.exp(-r * T) * si.norm.cdf(-d2, 0.0, 1.0) - S * si.norm.cdf(-d1, 0.0, 1.0))
        
    return result
"""

Which is basicly the definion of European type of Vanilla Option Pricing.


For more information you can reach me from dincberk@gmail.com

Output should give front 12 months with PUT & CALL option prices of the each month.


