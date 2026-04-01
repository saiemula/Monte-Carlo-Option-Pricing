Monte Carlo Option Pricing Simulator

A professional-grade simulator for pricing European options using Monte Carlo methods, benchmarked against the Black–Scholes analytical model. This project demonstrates core concepts from quantitative finance, stochastic processes, and numerical methods in a clear and visual way.

Overview

This project simulates stock price evolution using Geometric Brownian Motion (GBM) and applies Monte Carlo simulation to estimate European option prices.

The workflow is as follows:
Simulate multiple stock price paths under GBM
Compute option payoffs at maturity for each path
Discount the average payoff back to present value
Compare the Monte Carlo estimate with the exact Black–Scholes price

The simulator highlights how numerical methods converge to analytical solutions as the number of simulations increases, illustrating the Law of Large Numbers.

Key Concepts
Geometric Brownian Motion (GBM)

GBM is the standard model for stock price dynamics in continuous time. It assumes:

Log-normal distribution of prices
Constant volatility and drift
Continuous compounding
Monte Carlo Simulation

Monte Carlo methods estimate expected values by averaging results over many random samples. In this context:

Each simulated path represents a possible future market scenario
Option prices are computed as expected discounted payoffs
Black–Scholes Model

The Black–Scholes model provides a closed-form solution for European option pricing under GBM assumptions. It serves as a benchmark to validate the Monte Carlo simulation.

Features
High-performance simulation of stock price paths using vectorised NumPy operations
Monte Carlo pricing for European Call and Put options
Analytical pricing using the Black–Scholes formula
Real-time comparison between numerical and analytical results
Animated visualisation of simulated price paths
Configurable parameters for experimentation and sensitivity analysis
Installation
Clone the repository
git clone https://github.com/saiemula/Monte-Carlo-Option-Pricing.git
cd Monte-Carlo-Option-Pricing
Install dependencies
pip install -r requirements.txt
Usage

Run the main script:

python main.py

The program will:

Generate simulated stock price paths
Animate a subset of paths
Display real-time option pricing comparisons
Mathematical Formulation
Geometric Brownian Motion

𝑆
𝑡
=
𝑆
0
exp
⁡
(
(
𝑟
−
1
2
𝜎
2
)
𝑡
+
𝜎
𝑊
𝑡
)
S
t
	​

=S
0
	​

exp((r−
2
1
	​

σ
2
)t+σW
t
	​

)

Monte Carlo Estimator

European Call:

𝐶
≈
𝑒
−
𝑟
𝑇
⋅
1
𝑁
∑
𝑖
=
1
𝑁
max
⁡
(
𝑆
𝑇
(
𝑖
)
−
𝐾
,
 
0
)
C≈e
−rT
⋅
N
1
	​

∑
i=1
N
	​

max(S
T
(i)
	​

−K, 0)

European Put:

𝑃
≈
𝑒
−
𝑟
𝑇
⋅
1
𝑁
∑
𝑖
=
1
𝑁
max
⁡
(
𝐾
−
𝑆
𝑇
(
𝑖
)
,
 
0
)
P≈e
−rT
⋅
N
1
	​

∑
i=1
N
	​

max(K−S
T
(i)
	​

, 0)

Black-Scholes Formula

European Call:

𝐶
=
𝑆
0
𝑁
(
𝑑
1
)
−
𝐾
𝑒
−
𝑟
𝑇
𝑁
(
𝑑
2
)
C=S
0
	​

N(d
1
	​

)−Ke
−rT
N(d
2
	​

)

European Put:

𝑃
=
𝐾
𝑒
−
𝑟
𝑇
𝑁
(
−
𝑑
2
)
−
𝑆
0
𝑁
(
−
𝑑
1
)
P=Ke
−rT
N(−d
2
	​

)−S
0
	​

N(−d
1
	​

)

Implementation Details
Vectorisation: NumPy is used to efficiently simulate thousands of paths simultaneously
Random Sampling: Standard normal variables are used to model Brownian motion increments
Time Discretisation: GBM is approximated using discrete time steps
Numerical Stability: Log-space transformations reduce floating-point issues
Performance: Simulation scales efficiently with increasing path counts
Possible Extensions
American option pricing (e.g. Longstaff–Schwartz method)
Variance reduction techniques (antithetic variates, control variates)
Greeks estimation (Delta, Gamma, Vega)
GPU acceleration using libraries such as CuPy
Calibration to real market data
Interactive dashboard (e.g. using Plotly or Streamlit)
Dependencies
numpy
pandas
matplotlib
scipy
Author

Sai Emula
https://github.com/saiemula

License

This project is licensed under the MIT License.
