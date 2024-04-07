# Enhancing Models through Time Series Observations: The Neural Martingales approach

Authors: Luca Galimberti, Anastasis Kratsios, Giulia Livieri, Alessio Spagnoletti

This repository contains the codes for the implementations and numerical experimentations of the project: "Enhancing Models through Time Series Observations: The Neural
Martingales approach"

## Introduction
In the field of financial modeling, stochastic differential equations (SDEs) are commonly used to analyze and predict market behavior. This paper proposes a novel approach to calibrating SDE-based models using real market data. The proposed method leverages deep learning approximation techniques and the encoding and decoding of data from different spaces to improve the accuracy of financial models. By incorporating historical time series and option prices, a deep learning-based mapping function is developed to generate a martingale that aligns the model with observed market data. The calibrated model can then be used for more accurate prediction of future asset values and option pricing.

The paper considers a scenario where a bank has an approved model represented by a Geometric Brownian Motion (GBM). The authors propose calibrating this model using real market data derived from historical time series and option prices. The approach involves developing a deep learning-based mapping function that generates a martingale, which represents the correction term needed to align the model with observed market data. By incorporating this correction, the model's ability to capture asset dynamics is improved, leading to more accurate predictions and option pricing.

## Usage
This repository contains the python codes and datasets udes in the paper.

## Codes Description

1. `Neural_Martingale.ipynb`: this code contains all the functions needed to implement the model described in the paper

2. `Adjust.ipynb`: this code was used in order to produce the csv files from a single .mat file with options and underlying data collected each Wednesday from S&P between 1996 and 2014. The .csv files contains for each row the data of a single time series containing the information depending on which .csv file we are looking at, here are their descriptions:

## Datasets

1. `Maturity_adj.csv`: The time to maturity
2. `Price_adj.csv`: The option price
3. `Security_adj.csv`: The underlying price
4. `Strike_adj.csv`: The price at which the underlying transaction settles if the option is exercised
