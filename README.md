# Systematic Portfolio Architecture

This repository outlines the structure and logic of a **Systematic Multi-Asset Portfolio**.  
It is designed to adaptively allocate risk across asset classes based on macro regimes, while selecting securities through quantitative factor models.  
The architecture integrates top-down allocation, bottom-up security selection, centralized optimization, and continuous execution monitoring.

---

## Core Components

### **Top-Down Regime**
The top-down layer identifies macroeconomic and market regimes using growth, inflation, liquidity, and volatility indicators.  
Each regime (Expansion, Stagflation, Disinflation, Recession) informs the **expected Sharpe ratio** for each asset class.  
The system dynamically allocates portfolio risk based on these expectations, maintaining a constant volatility target while shifting exposure toward the most favorable sleeves.

### **Bottom-Up Security Selection**
Within each asset sleeve, the model ranks and weights individual instruments using **factor-based signals** such as Value, Momentum, Quality, Carry, and Volatility.  
This process transforms high-level regime allocations into specific security positions, subject to sector, region, and liquidity constraints.  
Each sleeve operates its own independent factor engine, calibrated to its unique market structure and data frequency.

### **Integration and Risk Control**
All sleeves are aggregated through a centralized optimizer that maximizes expected Sharpe subject to volatility, correlation, and concentration constraints.  
A unified risk engine monitors exposures across factors, asset classes, and regimes.  
Volatility targeting, drawdown protection, and position-level scaling are enforced at this layer to maintain portfolio stability.

### **Execution and Monitoring**
Orders are executed algorithmically to minimize market impact and transaction costs.  
The system continuously monitors performance attribution, signal decay, and slippage.  
Rebalancing occurs on a fixed or adaptive schedule depending on signal half-life, liquidity, and volatility conditions.

---

## Systematically Allocated Asset Classes

### **Equities**
- **Why:** Core growth engine, sensitive to macro expansion and liquidity conditions.  
- **Universe:** Developed and emerging market indices or individual stocks (S&P 500, MSCI World, Russell 3000, MSCI EM).  
- **Factors:** Value, Momentum, Quality, Size, Volatility.

### **Fixed Income**
- **Why:** Provides diversification and defensive carry in disinflationary or recessionary regimes.  
- **Universe:** Sovereign bonds (UST, Bunds, JGBs), credit indices, and interest-rate futures.  
- **Factors:** Carry, Duration, Roll-down, Momentum, Spread compression.

### **Commodities**
- **Why:** Inflation hedge and real-asset exposure; behaves differently across regimes.  
- **Universe:** Energy, metals, and agricultural futures (CL, GC, HG, ZS).  
- **Factors:** Carry (term structure), Momentum, Seasonal patterns.

### **Currencies (FX)**
- **Why:** Expresses global macro views and relative monetary policy divergence.  
- **Universe:** G10 and liquid EM pairs.  
- **Factors:** Carry (interest differential), Momentum, Value (PPP deviation).

### **Volatility**
- **Why:** Provides tail-risk protection and exposure to changing risk premia.  
- **Universe:** Volatility futures, variance swaps, or volatility-linked ETFs.  
- **Factors:** Term structure, Vol-of-Vol, Skew dynamics.

### **Cash / Collateral**
- **Why:** Acts as liquidity buffer and volatility target anchor.  
- **Universe:** Short-term T-bills, repo instruments, or money-market funds.

---

## Summary

The **Systematic Portfolio** combines regime-adaptive allocation with cross-sectional security selection to maximize long-term risk-adjusted returns.  
It is data-driven, model-agnostic, and continuously learning from market feedback.  
Each layer—top-down, bottom-up, integration, and execution—operates as an independent system connected through a unified optimization and monitoring framework.
