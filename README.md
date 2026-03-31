# ML-Driven Portfolio Optimisation for UK Equities

![Python](https://img.shields.io/badge/Python-3.8%2B-blue) ![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange) ![License](https://img.shields.io/badge/License-MIT-green)

## Overview

An end-to-end machine learning and quantitative finance pipeline applied to **UK retail sector equities** (SBRY.L, TSCO.L, MKS.L, KGF.L, NXT.L, OCDO.L) benchmarked against the **FTSE 100 (^FTSE)**. The project combines unsupervised ML (K-Means clustering) with classical portfolio theory (Mean-Variance Optimisation via PyPortfolioOpt) and Monte Carlo simulation (10,000 portfolios) to construct and evaluate optimal portfolios.

The repo contains two notebooks:
- **ML-Driven Portfolio Optimisation for UK Equitie (1).ipynb** — Main portfolio construction pipeline
- - **regression.ipynb** — ML-based stock price prediction using Random Forest, Ridge Regression & XGBoost
 
  - ---

  ## Notebook 1: ML Portfolio Optimisation

  ### Assets
  | Ticker | Company |
  |--------|---------|
  | SBRY.L | Sainsbury's |
  | TSCO.L | Tesco |
  | MKS.L | Marks & Spencer |
  | KGF.L | Kingfisher |
  | NXT.L | Next |
  | OCDO.L | Ocado |
  | ^FTSE | FTSE 100 (benchmark) |

  Data sourced via `yfinance` (Nov 2024 – Nov 2025).

  ### Pipeline

  **1. K-Means Clustering (Asset Segmentation)**
  Assets are scaled with `StandardScaler` and clustered (k=3) in risk-return space using `sklearn.cluster.KMeans`. Cluster 2 (SBRY, TSCO, NXT) emerged as the high-return, moderate-volatility group.

  **2. Monte Carlo Simulation (10,000 portfolios)**
  Random weight combinations across assets are simulated. For each portfolio, expected return, annualised volatility, and Sharpe ratio are computed using the covariance matrix and a 4.19% risk-free rate (FRED data).

  **3. Portfolio Clustering (Risk-Return-Sharpe Space)**
  The 10,000 Monte Carlo portfolios are themselves clustered (k=3) to identify distinct risk/return regimes, with Cluster 2 achieving the highest average Sharpe ratio (0.946).

  **4. Mean-Variance Optimisation (PyPortfolioOpt)**
  `EfficientFrontier` from `pypfopt` is used to compute:
  - **Maximum Sharpe Ratio (MSR)** portfolio: ~50.2% return, 22.5% volatility
  - - **Minimum Variance** portfolio
   
    - **Best Sharpe Portfolio (Monte Carlo):**
    - - Return: 54.9% | Volatility: 25.8% | Sharpe: 1.97
      - - Weights: SBRY 50.5%, NXT 97.2%, TSCO 8.3% (with short positions)
       
        - ---

        ## Notebook 2: ML Stock Price Prediction (`regression.ipynb`)

        Predicts next-day closing prices for **TSCO.L** (Tesco) and **NXT.L** (Next) using engineered features and multiple ML models.

        ### Feature Engineering
        - Returns at horizons: 1, 3, 21, 63 days
        - - Moving averages (SMA): 5, 10, 20, 50 days
          - - EMAs: 12, 26, 50 periods
            - - MACD and MACD signal line
              - - RSI (14-period)
                - - Rolling volatility, skewness, kurtosis (20-day)
                 
                  - ### Models (via sklearn Pipeline with PCA + SelectKBest)
                  - - **Random Forest** (hypertuned via RandomizedSearchCV)
                  - **Ridge Regression**
                  - - **XGBoost**
                   
                    - ### Backtesting
                    - Each model's predictions generate buy/sell signals. Strategy returns are computed and evaluated via Sharpe ratio, final equity, and max drawdown.
                   
                    - ---

                    ## Technologies Used

                    | Tool | Purpose |
                    |------|---------|
                    | Python 3.8+ | Core language |
                    | yfinance | UK equity & FTSE data |
                    | NumPy / Pandas | Data manipulation |
                    | Scikit-learn | KMeans, Ridge, RandomForest, Pipeline, PCA |
                    | XGBoost | Gradient boosting regressor |
                    | PyPortfolioOpt | Efficient frontier & MSR optimisation |
                    | Matplotlib / Seaborn | Visualisations |
                    | Google Colab | Execution environment |

                    ## Getting Started

                    ```bash
                    git clone https://github.com/srhimal149/srhimal149-srhimal149-ML_Driven_Portfolio.git
                    cd srhimal149-srhimal149-ML_Driven_Portfolio
                    pip install yfinance numpy pandas scikit-learn xgboost pyportfolioopt matplotlib seaborn pykalman
                    jupyter notebook
                    ```

                    ## Author

                    **Md Saifur Rahman Himal**
                    MSc FinTech (Distinction Candidate) | Quantitative Finance & ML
                    [LinkedIn](https://www.linkedin.com/in/md-saifur-rahman-himal-70a0941ba) | [GitHub](https://github.com/srhimal149)

                    ## License

                    MIT License
