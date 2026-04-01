**Monte Carlo Option Pricing Simulator
**
A professional-grade simulator for pricing European options using Monte Carlo methods, benchmarked against the Black–Scholes analytical model. This project demonstrates core concepts from quantitative finance, stochastic processes, and numerical methods in a clear and visual way.

**Overview**
This project simulates stock price evolution using Geometric Brownian Motion (GBM) and applies Monte Carlo simulation to estimate European option prices.


**The workflow is as follows:**
Simulate multiple stock price paths under GBM
Compute option payoffs at maturity for each path
Discount the average payoff back to present value
Compare the Monte Carlo estimate with the exact Black–Scholes price

The simulator highlights how numerical methods converge to analytical solutions as the number of simulations increases, illustrating the Law of Large Numbers.

**Key Concepts**
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

**Features**
High-performance simulation of stock price paths using vectorised NumPy operations
Monte Carlo pricing for European Call and Put options
Analytical pricing using the Black–Scholes formula
Real-time comparison between numerical and analytical results
Animated visualisation of simulated price paths
Configurable parameters for experimentation and sensitivity analysis

**Installation**
Clone the repository
git clone https://github.com/saiemula/Monte-Carlo-Option-Pricing.git
cd Monte-Carlo-Option-Pricing

**Install dependencies**
pip install -r requirements.txt

**Usage**
Run the main script:
python main.py

The program will:
Generate simulated stock price paths
Animate a subset of paths
Display real-time option pricing comparisons



S_t = S_0 * exp((r - 0.5*sigma^2)t + sigma*W_t)

C ≈ e^(-rT) * (1/N) * Σ max(S_T(i) - K, 0)

P ≈ e^(-rT) * (1/N) * Σ max(K - S_T(i), 0)

C = S0 N(d1) - K e^(-rT) N(d2)

P = K e^(-rT) N(-d2) - S0 N(-d1)
