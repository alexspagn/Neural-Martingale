# Enhancing Time-Series Models with Neural Martingales

**Authors**: Alessio Spagnoletti, Giulia Livieri, Anastasis Kratsios, Luca Galimberti

This repository contains the codes for the implementations and numerical experimentations of the project: *"Enhancing Time-Series Models with Neural Martingales"*.

## Introduction
In the field of financial modeling, it is common for financial institutions, such as banks, to develop a range of internally approved models to analyze and predict market behavior. These models are typically formulated as Stochastic Differential Equations (SDEs), which describe the dynamics of financial quantities over time. In this work, we consider a simplified scenario where a bank has an approved model $$X_t^{\star}$$ represented by a Geometric Brownian Motion (GBM) since closed-form option pricing is available. We emphasize that our theory holds for most SDE models used in classical quantitative finance.

The GBM is a stochastic process that satisfies the following conditions:

$$
\begin{cases}
    dX_t^{\star} = \mu^{\star}X_s^{\star}\,ds +\sigma^{\star}X_s^{\star}\,dW_s \\
    X_0^{\star} = x
\end{cases}
$$

Here, $$X_t^{\star}$$ represents the financial quantity of interest at time $$t$$, $$x$$ is an initial condition, $$\mu^{\star}$$ and $$\sigma^{\star}$$ are respectively a constant representing the drift and a \(d\)-dimensional row vector representing the volatility. $$W_{\cdot}$$ is a $$d$$-dimensional Brownian motion. Without loss of generality, we will consider the $$d=1$$ case. While all our analysis can be easily adapted to a general $$d$$ case, we will conduct experiments only in $$1$$-d.

The solution of such SDE (that satisfies the condition of existence and uniqueness) is:

$$
X_t^{\star} = x\exp\left(\left( \mu^{\star} - \frac{(\sigma^{\star})^2}{2} \right)t + \sigma^{\star}W_t \right)
$$

The main objective of this work is to calibrate these models using real market data derived from historical time series and option prices. Traditional calibration methods often rely on optimization techniques, which may suffer from high computational costs and limited flexibility [Fukasawa et al., 2011; Bayer et al., 2015; Bennedsen et al., 2015]. To overcome these limitations, recent efforts explored the use of Neural Networks (NNs) as models to learn how to price options [Horvath et al., 2019]. Following this trend, we propose to leverage the power of deep learning universal approximation results [Shen et al., 2022], and the effectiveness of approximating complex operators between abstract spaces [Galimberti et al., 2023] to define a new framework for calibrating SDE-based models.

Our approach involves developing a deep learning-based mapping function that takes historical time series as input and outputs a martingale. This martingale represents the correction term that needs to be applied to the model $$X_{\cdot}^{\star}$$ in order to align it with the observed market data. By incorporating this correction, we can improve the model's ability to capture the dynamics of the underlying asset. Furthermore, the calibrated model can be used for predicting future values of the underlying asset and computing option prices more accurately.

## Usage
This repository contains the Python codes and datasets used in the paper.

## Codes Description

1. **`Neural_Martingale.ipynb`**: This code contains all the functions needed to implement the model described in the paper.

2. **`Adjust.ipynb`**: This code was used in order to produce the CSV files from a single `.mat` file with options and underlying data collected each Wednesday from the S&P index between 1996 and 2014. The `.csv` files contain, for each row, the data of a single time series containing the information depending on which `.csv` file we are looking at. Here are their descriptions:

## Datasets

1. **`Maturity_adj.csv`**: The time to maturity.
2. **`Price_adj.csv`**: The option price.
3. **`Security_adj.csv`**: The underlying price.
4. **`Strike_adj.csv`**: The strike price at which the underlying transaction settles if the option is exercised.

## References

- **Fukasawa, M. (2011)**: Asymptotic Analysis for Stochastic Volatility Models.
- **Bayer, C., Friz, P., & Gatheral, J. (2015)**: Pricing under Rough Volatility.
- **Bennedsen, M., Lunde, A., & Pakkanen, M. S. (2015)**: Hybrid Scheme for Rough Volatility.
- **Horvath, B., Muguruza, A., & Tomas, M. (2019)**: Deep Learning Volatility.
- **Shen, Z., Yang, H., & Zhang, S. (2022)**: Deep Network Approximation.
- **Galimberti, L., Kratsios, A., & Livieri, G. (2023)**: Designing Universal Causal Deep Learning Models.
