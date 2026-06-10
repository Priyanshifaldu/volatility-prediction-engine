# Volatility Prediction Engine v3.0

**S&P 500 & Multi-Asset Quantitative Risk Dashboard**

## Quick Start (Windows)

1. Double-click `INSTALL.bat` — one-time setup (installs all dependencies)
2. Double-click `START.bat` — launches server and opens browser automatically

Or manually:
```cmd
cd volatility_engine
venv\Scripts\activate
uvicorn main:app --reload --port 8000
```
Then open: **http://localhost:8000**

## Dashboard Tabs

| Tab | Contents |
|-----|----------|
| Overview | Live stat cards, VIX vs Realised chart with event markers, Rolling vol, GARCH forecast |
| Volatility | All 6 estimators overlay, Range estimators, Regime timeline, Snapshot table |
| VIX Analysis | VIX history, Fear premium divergence, GARCH vs VIX signal |
| Event Study | Shock ratios by event, Category filters, Full event detail table |
| Risk Report | Return histogram, VaR/CVaR, Full metrics table |
| Forecast | GARCH bars, VIX benchmark, Historical + Forecast overlay |

## Supported Tickers
- `^GSPC` — S&P 500 (default)
- `^NSEI` — Nifty 50
- `^DJI` — Dow Jones
- `^IXIC` — NASDAQ
- `^FTSE` — FTSE 100
- `^N225` — Nikkei 225
- `GC=F` — Gold Futures
- `CL=F` — Crude Oil WTI
- `BTC-USD` — Bitcoin

## API Endpoints

| Endpoint | Description |
|----------|-------------|
| `GET /volatility/current` | Live snapshot — all estimators |
| `GET /volatility/rolling` | Full rolling vol time-series |
| `GET /volatility/compare` | Estimator comparison table |
| `GET /volatility/risk-metrics` | Sharpe, Sortino, VaR, CVaR, drawdown |
| `GET /predict/garch` | GARCH/EGARCH/GJR-GARCH forecast |
| `GET /predict/xgboost` | XGBoost N-day forecast |
| `GET /predict/random-forest` | Random Forest N-day forecast |
| `GET /predict/lstm` | LSTM N-day forecast |
| `GET /events/study` | Full macro event study |
| `GET /events/calendar` | Event calendar |
| `GET /vix/snapshot` | Current VIX + fear regime |
| `GET /vix/history` | Full VIX time-series |
| `GET /vix/compare` | VIX vs realised vol comparison |
| `GET /vix/forecast-compare` | GARCH vs VIX signal |
| Interactive docs | http://localhost:8000/docs |

## Project Structure
```
volatility_engine/
├── main.py                    FastAPI entry point
├── config.py                  Central settings
├── INSTALL.bat                One-click Windows setup
├── START.bat                  One-click launcher
├── data/
│   ├── loader.py              yfinance + CSV ingestion
│   ├── preprocessor.py        Feature engineering
│   └── vix.py                 VIX data & divergence
├── models/
│   ├── statistical.py         Snapshot & comparison
│   ├── garch_model.py         GARCH/EGARCH/GJR-GARCH
│   ├── lstm_model.py          PyTorch LSTM
│   └── ml_models.py           XGBoost + Random Forest
├── events/
│   ├── calendar.py            42 built-in macro events
│   └── analyzer.py            Event study + shock ratios
├── api/routes/
│   ├── data.py
│   ├── volatility.py
│   ├── predict.py
│   ├── events.py
│   └── vix.py
├── utils/
│   └── metrics.py             Risk metrics
└── frontend/
    └── index.html             Full dashboard (served at /)
```

## Team
- Priyanshi Faldu (23070126042)
- Sammit Borekar (24070126504)  
- Lakshya Joshi (23070126065)

Department of AI & ML | Semester IV | Batch 2023–27
