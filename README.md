# ML-Driven Portfolio Optimisation for UK Equities

![Python](https://img.shields.io/badge/Python-3.8%2B-blue) ![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange) ![License](https://img.shields.io/badge/License-MIT-green)

## Overview

An end-to-end machine learning and quantitative finance pipeline for optimising a portfolio of UK equities. The project combines unsupervised learning with classical portfolio theory to construct efficient, data-driven portfolios and rigorously assess their risk.

## Key Features

- **K-Means Clustering** for intelligent asset segmentation based on return/risk profiles
- **Mean-Variance Optimisation (MVO)** for constructing the optimal portfolio weights
- **Monte Carlo VaR** with 10,000 simulations for robust risk estimation
- **Backtesting vs FTSE 100** benchmark with full Sharpe ratio analysis
- **Regression Analysis** for factor exposure and alpha/beta decomposition

## Project Structure

```
├── ML-Driven Portfolio Optimisation for UK Equitie (1).ipynb   # Main pipeline notebook
├── regression.ipynb                                              # Factor regression analysis
└── README.md
```

## Methodology

### 1. Asset Segmentation (K-Means Clustering)
UK equities are grouped into clusters based on historical return distributions and volatility profiles, enabling diversified selection across distinct risk/return segments.

### 2. Portfolio Optimisation (Mean-Variance)
Using the Markowitz framework, optimal asset weights are computed to maximise the Sharpe ratio and trace the efficient frontier.

### 3. Risk Assessment (Monte Carlo VaR)
10,000 simulated portfolio return paths are generated to compute Value-at-Risk (VaR) and Conditional Value-at-Risk (CVaR) at standard confidence levels (95% and 99%).

### 4. Backtesting
The optimised portfolio is backtested against the FTSE 100 index, evaluating performance via cumulative returns, drawdown analysis, and Sharpe ratio comparison.

## Technologies Used

| Tool | Purpose |
|------|---------|
| Python 3.8+ | Core language |
| NumPy / Pandas | Data manipulation |
| Scikit-learn | K-Means clustering |
| SciPy | Optimisation routines |
| Matplotlib / Seaborn | Visualisation |
| yfinance | UK equity data retrieval |

## Results Summary

- Achieved a higher Sharpe ratio compared to the FTSE 100 benchmark over the backtested period
- Monte Carlo VaR at 99% confidence provided a conservative risk bound for portfolio sizing
- K-Means clustering identified 4 distinct equity clusters, improving diversification

## Getting Started

```bash
# Clone the repository
git clone https://github.com/srhimal149/srhimal149-srhimal149-ML_Driven_Portfolio.git
cd srhimal149-srhimal149-ML_Driven_Portfolio

# Install dependencies
pip install numpy pandas scikit-learn scipy matplotlib seaborn yfinance jupyter

# Launch Jupyter
jupyter notebook
```

## Author

**Md Saifur Rahman Himal**
MSc FinTech (Distinction Candidate) | Quantitative Finance & ML
[LinkedIn](https://www.linkedin.com/in/md-saifur-rahman-himal-70a0941ba) | [GitHub](https://github.com/srhimal149)

## License

MIT License — feel free to use and adapt with attribution.
