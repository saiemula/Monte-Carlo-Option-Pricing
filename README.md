# Monte Carlo Option Pricing Simulator

A professional-grade simulator for pricing European options using Monte Carlo methods, benchmarked against the Black–Scholes analytical model. This project demonstrates core concepts from quantitative finance, stochastic processes, and numerical methods in a clear and visual way.

---

## Overview

This project simulates stock price evolution using Geometric Brownian Motion (GBM) and applies Monte Carlo simulation to estimate European option prices.

The workflow is as follows:

1. Simulate multiple stock price paths under GBM
2. Compute option payoffs at maturity for each path
3. Discount the average payoff back to present value
4. Compare the Monte Carlo estimate with the exact Black–Scholes price

The simulator highlights how numerical methods converge to analytical solutions as the number of simulations increases, illustrating the **Law of Large Numbers**.

---

## Key Concepts

### Geometric Brownian Motion (GBM)

GBM is the standard model for stock price dynamics in continuous time. It assumes:

- Log-normal distribution of prices
- Constant volatility and drift
- Continuous compounding

### Monte Carlo Simulation

Monte Carlo methods estimate expected values by averaging results over many random samples. In this context:

- Each simulated path represents a possible future market scenario
- Option prices are computed as expected discounted payoffs

### Black–Scholes Model

The Black–Scholes model provides a closed-form solution for European option pricing under GBM assumptions. It serves as a benchmark to validate the Monte Carlo simulation.

---

## Features

- High-performance simulation of stock price paths using vectorised NumPy operations
- Monte Carlo pricing for European Call and Put options
- Analytical pricing using the Black–Scholes formula
- Real-time comparison between numerical and analytical results
- Animated visualisation of simulated price paths
- Configurable parameters for experimentation and sensitivity analysis

---

## Installation

**Clone the repository**

```bash
git clone https://github.com/saiemula/Monte-Carlo-Option-Pricing.git
cd Monte-Carlo-Option-Pricing
```

**Install dependencies**

```bash
pip install -r requirements.txt
```

---

## Usage

Run the main script:

```bash
python main.py
```

The program will:

1. Generate simulated stock price paths
2. Animate a subset of paths
3. Display real-time option pricing comparisons

---

## Mathematical Formulation

### Geometric Brownian Motion

$$S_t = S_0 \exp\left(\left(r - \frac{1}{2}\sigma^2\right)t + \sigma W_t\right)$$

### Monte Carlo Estimator

European Call:

$$C \approx e^{-rT} \cdot \frac{1}{N} \sum_{i=1}^{N} \max\left(S_T^{(i)} - K,\ 0\right)$$

European Put:

$$P \approx e^{-rT} \cdot \frac{1}{N} \sum_{i=1}^{N} \max\left(K - S_T^{(i)},\ 0\right)$$

### Black–Scholes Formula

European Call:

$$C = S_0 N(d_1) - K e^{-rT} N(d_2)$$

European Put:

$$P = K e^{-rT} N(-d_2) - S_0 N(-d_1)$$

### Definitions

$$d_1 = \frac{\ln(S_0 / K) + \left(r + \frac{1}{2}\sigma^2\right)T}{\sigma\sqrt{T}}$$

$$d_2 = d_1 - \sigma\sqrt{T}$$


---

## Implementation Details

- **Vectorisation:** NumPy is used to efficiently simulate thousands of paths simultaneously
- **Random Sampling:** Standard normal variables are used to model Brownian motion increments
- **Time Discretisation:** GBM is approximated using discrete time steps
- **Numerical Stability:** Log-space transformations reduce floating-point issues
- **Performance:** Simulation scales efficiently with increasing path counts

---

## Possible Extensions

- American option pricing (e.g. Longstaff–Schwartz method)
- Variance reduction techniques (antithetic variates, control variates)
- Greeks estimation (Delta, Gamma, Vega)
- GPU acceleration using libraries such as CuPy
- Calibration to real market data
- Interactive dashboard (e.g. using Plotly or Streamlit)

---

## Dependencies

- `numpy`
- `pandas`
- `matplotlib`
- `scipy`

---

## Author

**Sai Emula**
[github.com/saiemula](https://github.com/saiemula)

---

## License

This project is licensed under the [MIT License](LICENSE).




Input: T-day return window (N_assets × T)
         │
┌────────▼────────────────────────────────────┐
│              ENCODER                         │
│   Conv1D layers → FC layers                  │
│   Output: μ(z), σ(z)  ← learned mean/var    │
└────────┬────────────────────────────────────┘
         │ Reparameterisation: z = μ + σ·ε
┌────────▼────────────────────────────────────┐
│           LATENT SPACE  z ∈ ℝᵈ              │
│   d = 8–16 dimensions                        │
│   Structured, continuous, interpolatable     │
└────────┬────────────────────────────────────┘
         │
┌────────▼────────────────────────────────────┐
│              DECODER                         │
│   FC layers → Conv1DTranspose layers         │
│   Output: Reconstructed return window         │
└─────────────────────────────────────────────┘

Loss = Reconstruction Loss (MSE) + KL Divergence
     = E[||x - x̂||²] + KL[q(z|x) || p(z)]
