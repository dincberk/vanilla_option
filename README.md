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

Output should look like this:

 	Correlation 	Volatility1 	Volatility2 	LastClosing1 	LastClosing2 	MutualVola_K 	T_Value_days 	PUT_STRIKE_VALUES 	CALL_STRIKE_VALUES
APR21 	0.677856 	0.259609 	0.271095 	45.100000 	49.250033 	0.213251 	16.00 	8.220879 	19.234085
MAY21 	0.706182 	0.218630 	0.441002 	48.976839 	46.499968 	0.325740 	46.00 	9.081494 	41.915896
JUN21 	0.647510 	0.222807 	0.441082 	55.500000 	49.137000 	0.341946 	77.00 	5.835439 	52.974153
JUL21 	0.556955 	0.178447 	0.278419 	59.709000 	51.891000 	0.232418 	107.00 	1.758322 	57.038448
AUG21 	0.643783 	0.183350 	0.292293 	58.622000 	48.713000 	0.223717 	138.00 	0.768617 	57.352664
SEP21 	0.687100 	0.166914 	0.241521 	61.729000 	56.506000 	0.175483 	169.00 	0.195550 	60.765794
OCT21 	0.787724 	0.164586 	0.208815 	59.006000 	60.296000 	0.128636 	199.00 	0.015144 	58.400957
NOV21 	0.796106 	0.161744 	0.180549 	61.220000 	68.868000 	0.110735 	230.00 	0.001638 	60.874422
DEC21 	0.784759 	0.164429 	0.182414 	61.002000 	68.268000 	0.115045 	260.00 	0.000879 	60.830241
JAN22 	0.690532 	0.175235 	0.164306 	55.466000 	70.385000 	0.133940 	291.00 	0.002018 	55.380772
FEB22 	0.468607 	0.155164 	0.164306 	53.841000 	70.385000 	0.164859 	322.00 	0.004817 	53.803052
MAR22 	0.514113 	0.185240 	0.198280 	50.206000 	59.785000 	0.189374 	350.00 	0.004587 	50.191510
--MEAN 	0.663435 	0.186346 	0.255340 	55.864820 	58.332000 	0.196262 	183.75 	0.241133 	55.253893
