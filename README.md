
# 📊 Crypto Volatility Visualizer

A **professional, interactive Streamlit dashboard** that combines:

- 📈 Real Bitcoin market data analysis  
- 📉 Mathematical price simulation using Geometric Brownian Motion (GBM)  
- 🎨 Advanced UI design (Glassmorphism + Neon theme + Animated splash screen)  
- ⚡ Interactive volatility modeling & comparison tools

---

## 🚀 Project Overview

**Crypto Volatility Visualizer** is a financial analytics application that merges:

- Real-world cryptocurrency data (BTC-USD)
- Statistical indicators (MA50, MA200, RSI, Volatility)
- Mathematical stochastic modeling
- Advanced UI/UX financial dashboard styling

Built using:

- <a href="https://streamlit.io/" target="_blank">Streamlit</a>  
- <a href="https://plotly.com/python/" target="_blank">Plotly</a>  
- <a href="https://pandas.pydata.org/" target="_blank">Pandas</a>  
- <a href="https://numpy.org/" target="_blank">NumPy</a>  
- <a href="https://pypi.org/project/yfinance/" target="_blank">yFinance</a>  

---
## 🧩 Project Storyboard

Below is the original design storyboard for the application:
<img width="1036" height="580" alt="Screenshot 2026-03-04 162747" src="https://github.com/user-attachments/assets/c03b938e-ce0a-4e18-b2bf-928e6d953c6d" />


## 📌 Features

### 🎬 1. Cinematic Splash Screen
- Neon financial theme
- Animated gradient glow
- Professional dashboard introduction
- Session-based display (only once per run)

---

### 🎨 2. Advanced UI Design

#### ✔ Glassmorphism Theme
- Blurred panels
- Gradient background
- Soft neon glow
- Modern fintech aesthetic

#### ✔ Animated Particles Background
- Interactive JavaScript particle system
- Subtle moving grid for financial theme

#### ✔ Styled Sidebar Controls
- Custom toggles
- Custom sliders
- Neon buttons
- Market Mode switch (Bull/Bear)

---

## 📊 Real Market Analysis (Tab 1)

Uses live data from Yahoo Finance:

```python
yf.download("BTC-USD", period="5y", interval="1d")
```
### Includes:

#### 📈 1. Bitcoin Close Price

Interactive time-series line chart

#### 📊 2. Volume Analysis

Daily trading volume bar chart

#### 📉 3. Rolling Volatility Index

10-period rolling standard deviation of returns:
``` python
Volatility = pct_change().rolling(10).std()
```
#### 📊 4. Technical Indicators (If CSV Uploaded)

MA50 (50-day moving average)

MA200 (200-day moving average)

RSI (14-period Relative Strength Index)

## 📈 Mathematical Simulation (Tab 2)
### Geometric Brownian Motion (GBM)

Implements stochastic differential equation:

``` python
dS = μSdt + σSdW
```
Discrete version used:

```python
(t+1) = S(t) * exp((μ - 0.5σ²)dt + σ√dt * Z)
```
Where:

μ = Drift (trend direction)

σ = Volatility

Z = Random normal shock

### 🎛 Simulation Controls
#### Market Mode

Bull Market → μ = 0.25

Bear Market → μ = -0.15

#### Adjustable Parameters

Volatility (σ)

Time Steps

Noise

Drift

Amplitude

Frequency

### Pattern Type

#### 🔁 Comparison Mode

Toggle option:

Switches to high vs low volatility comparison page

Enables scenario-based analysis

## 📂 Dataset Options
### Option 1 — Auto Fetch (Default)

Fetches BTC data using `yfinance`

Last 5 years daily data

Cached using `@st.cache_data`

### Option 2 — Upload CSV

Upload Kaggle Bitcoin dataset:

Must contain `Timestamp`

Must contain `Close`

Must contain `Volume`

Automatically computes:

Moving averages

RSI

Volatility metrics

## 🧠 Core Function
```python
def gbm_simulation(S0, mu, sigma, T=1, steps=252):
    dt = T / steps
    prices = [S0]

    for _ in range(steps):
        shock = np.random.normal(0, 1)
        St = prices[-1] * np.exp((mu - 0.5 * sigma**2)*dt + sigma*np.sqrt(dt)*shock)
        prices.append(St)

    return prices
```
## 🛠 Installation
### 1️⃣ Clone Repository
```bash
git clone https://github.com/your-username/crypto-volatility-visualizer.git
cd crypto-volatility-visualizer
```
### 2️⃣ Install Required Dependencies
```bash
pip install -r requirements.txt
```
Or manually:
```bash
pip install streamlit pandas numpy plotly yfinance
```
### 3️⃣ Run the Application
```bash
streamlit run app.py
```
## 📦 Requirements.txt
```txt
streamlit
pandas
numpy
plotly
yfinance
```
## 📐 Mathematical Concepts Used

Stochastic Processes

Geometric Brownian Motion

Drift & Diffusion Modeling

Rolling Standard Deviation

Technical Analysis Indicators

Time Series Simulation

## 🖥 Architecture Overview
Streamlit Frontend
        ↓
Sidebar Controls
        ↓
Data Layer (yFinance / CSV Upload)
        ↓
Analytics Engine (Pandas + NumPy)
        ↓
Simulation Engine (GBM Model)
        ↓
Plotly Visualization Layer
🎓 Academic Context

## Designed for:
Mathematics for AI-II

Financial Modeling

Volatility Simulation

Market Behavior Analysis

## ⚡ Performance Optimizations

`@st.cache_data` for dataset caching

Limited dataset to last 500 rows for speed

Efficient NumPy-based GBM simulation

Session-state splash screen control

## 📊 Example Use Cases

Understanding crypto volatility

Demonstrating stochastic models

Comparing bullish vs bearish simulations

Teaching financial mathematics

AI-based market modeling experiments

## 🔮 Future Improvements

Monte Carlo multiple path simulation

Value at Risk (VaR)

Sharpe Ratio calculation

Portfolio optimization

Live WebSocket crypto feed

AI-based volatility prediction model

## 📜 License

This project is built for educational and academic purposes.

## 👨‍💻 Authors

Mann Paresh Patel- WACP Candidate Registration Number- 1000428

Jashith Hemendra Rathod- WACP Candidate Registration Number- 1000422

Nishtha Priyesh Shah- WACP Candidate Registration Number- 1000436

## ⭐ If You Like This Project

### Consider:

Starring the repository

Forking for improvements

Adding advanced financial metrics

### Crypto Volatility Visualizer — Where Mathematics Meets Market Chaos 📈
