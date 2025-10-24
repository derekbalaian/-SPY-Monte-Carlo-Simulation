# SPY Monte Carlo — 1‑Year Percentile Paths & Return Distribution

This repository contains a **reproducible Jupyter notebook** (`$SPY Monte Carlo Price Simulation.ipynb`) that:
- pulls the last **5 years** of **SPY** daily prices via **yfinance**,
- computes daily log returns and annualizes **drift (μ)** and **volatility (σ)**,
- simulates **1 year (252 trading days)** of prices under **Geometric Brownian Motion (GBM)** with **~1,000 paths**, 
- and produces two key visuals:
  1) **Percentile paths** (p5/p25/median/p75/p95) plus mean, and  
  2) **Histogram of simulated one‑year returns** with percentile markers.

---

## Open the notebook in Colab
- **Colab:** `https://colab.research.google.com/github/derekbalaian/-SPY-Monte-Carlo-Simulation/blob/main/%24SPY%20Monte%20Carlo%20Price%20Simulation-3.ipynb`

---

## Quickstart (local)

```bash
python -m venv .venv && source .venv/bin/activate  # macOS/Linux
# .venv\Scripts\activate                         # Windows PowerShell

pip install -r requirements.txt
jupyter notebook "$SPY Monte Carlo Price Simulation.ipynb-3"
```

### Method (high‑level)
- **Data:** 5y daily adjusted close from yfinance (`auto_adjust=True`).
- **Estimation:** daily log returns ⇒ annualized μ, σ (×252).
- **Model:** GBM  
  \( S_{t+\Delta} = S_t \cdot \exp\left[(\mu - 0.5\sigma^2)\Delta + \sigma\sqrt{\Delta}\,\varepsilon_t\right],\; \varepsilon_t \sim \mathcal N(0,1) \).
- **Simulation:** default **N = 1000** paths, **T = 252** steps (1y).

### Outputs
- **Percentile lines:** p5 / p25 / p50 / p75 / p95 (+ mean).  
- **One‑year return distribution:** histogram + percentile reference lines.

### Reproducibility notes
- Set a fixed random seed for consistent runs if needed (e.g., `np.random.seed(42)`).
- Package versions are pinned in `requirements.txt` for consistent environments.

---

## License
MIT © 2025 Derek Balaian
