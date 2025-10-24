# SPY Monte Carlo (1-Year) — Percentile Paths & Return Distribution

**What this repo contains:** a reproducible notebook that pulls the last five years of SPY daily data, estimates drift (μ) and volatility (σ), runs a 1‑year Monte Carlo under GBM (~252 trading days, default 1,000 paths), and produces two visuals ready for LinkedIn:
- Percentile path "fan" (**p5/p25/median/p75/p95** and mean)
- Histogram of simulated one‑year returns with percentile markers

> These visuals are scenario views, not point forecasts.

---

## Run it in the cloud (Colab)
Click to open the notebook in Colab (replace the placeholders with your repo path once you publish):
- **Colab:** https://colab.research.google.com/github/<YOUR_GITHUB_USERNAME>/<YOUR_REPO_NAME>/blob/main/MonteCarlo_SPY.ipynb
- **nbviewer (static render):** https://nbviewer.org/github/<YOUR_GITHUB_USERNAME>/<YOUR_REPO_NAME>/blob/main/MonteCarlo_SPY.ipynb

---

## Quickstart (local)

```bash
python -m venv .venv && source .venv/bin/activate  # on macOS/Linux
# .venv\Scripts\activate                          # on Windows PowerShell

pip install -r requirements.txt
jupyter notebook MonteCarlo_SPY.ipynb
```

> The notebook uses **yfinance** to fetch SPY; it requires an internet connection when you run it the first time.

---

## Method (high‑level)
- **Data:** last 5 years of SPY daily adjusted close (yfinance).
- **Estimation:** log returns ⇒ daily μ, σ; annualize by 252.
- **Model:** Geometric Brownian Motion (GBM):  
  S_{t+Δ} = S_t · exp[(μ − 0.5 σ²)Δ + σ√Δ · ε_t], ε_t ~ 𝒩(0,1)
- **Simulation:** default **N=1,000 paths**, **T=252 trading days**.
- **Outputs:**
  - **Percentile paths:** p5/p25/p50/p75/p95 and mean (saved in `figures/percentile_paths.png`)
  - **Return histogram:** one‑year terminal return distribution with percentile lines (saved in `figures/return_histogram.png`)

---

## Reproducibility
- Fixed random seed for baseline runs (change `SEED` to explore variability).
- Notebook writes figures with timestamps into `figures/` for versioned artifacts.
- Consider pinning package versions in `requirements.txt` for fully repeatable runs.

---

## License
MIT © 2025 Derek Balaian
