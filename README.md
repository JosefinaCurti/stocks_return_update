# Energy Sector Cumulative Returns
 
An interactive visualization of cumulative price returns for 58 energy stocks over a rolling 2-year window — built in Python and published as a live web chart.
 
🔗 **[View the live chart](https://josefinacurti.github.io/stocks_return_update/)**
 
---
 
# What This Is
 
Energy is one of the most structurally interesting sectors to track right now: nuclear revival, hydrogen scale-up attempts, solar margin compression, and grid infrastructure buildout are all playing out simultaneously in public markets. This project pulls live price data for 58 publicly traded energy companies across six sub-sectors, calculates their cumulative return from 2 years ago to today, and plots them in a fully interactive chart with multiple views and filters.
 
---
 
## The Chart
 
The interactive Plotly chart (hosted via GitHub Pages) includes four controls:
 
| Control | What it does |
|---------|-------------|
| **Individual View / Aggregated by Sector** | Toggle between per-stock lines and sector-averaged lines |
| **Show All / Top 5 Only** | Filter to the 5 largest companies by market cap (Individual View only) |
| **Company dropdown** | Isolate a single stock; sorted by highest cumulative return |
| **Sector dropdown** | Filter to one sector — context-aware (works in both Individual and Aggregated views) |
 
Hovering shows the full company name, sector, and exact cumulative return for that date. Each trace ends with a badge annotation showing the final period return.
 
---
 
## Stock Universe
 
58 companies across 6 sub-sectors:
 
| Sector | Tickers |
|--------|---------|
| **Solar** | FSLR, ENPH, SEDG, NXT, CSIQ, RUN, SHLS, DQ, JKS, SPWR, MAXN |
| **Wind** | GEV, VWS.CO, BEP, CWEN, ORA, TPIC, ORSTED.CO |
| **Nuclear** | CEG, CCJ, UUUU, LEU, UEC, SMR, OKLO, BWXT, FLR, NXE, DNN, IMSR |
| **Hydrogen** | BE, PLUG, NEL.OL, ITM.L, HYSR, FCEL, BLDP |
| **Storage & Grid** | TSLA, FLNC, STEM, EOSE, GWH, NRGV, GNRC, AYI, HUBB, PWR, VRT, EAT |
| **Integrated Energy** | NEE, XOM, CVX, SHEL, TTE, BP, EQNR, IBE.MC, ENEL.MI |
 
---
 
## How It Works
 
The notebook (`energy_stocks_market_price.ipynb`) runs end-to-end in a single execution:
 
1. **Fetches live data** via `yfinance` for all 58 tickers over a rolling 2-year window
2. **Calculates cumulative return** for each stock: `(price_t / price_t0) - 1`, anchored to the first trading day in the window
3. **Identifies Top 5** by sorting on market capitalization and taking the top 5 tickers
4. **Aggregates by sector** by averaging cumulative returns across all stocks in each sector group, for the Aggregated View
5. **Sorts traces by final return** — both the individual stock traces and sector traces are ordered highest-to-lowest by their last cumulative change value, so the best performers appear at the top of the legend
6. **Builds the interactive Plotly figure** with dual trace layers (individual + sector), four filter controls, per-trace hover labels with sector context, and end-of-line badge annotations
7. **Exports to HTML** (`cumulative_change_chart.html`) — committed to the repo and served via GitHub Pages
---
 
## What the Data Shows (as of June 2026)
 
A few patterns visible in the current chart:
 
- **Nuclear has been the standout sub-sector** over the 2-year window, with SMR, CEG, and OKLO among the top performers — reflecting the market re-rating of nuclear as a credible AI-era power source
- **Hydrogen has underperformed sharply** across the board; PLUG, FCEL, and ITM.L all show deeply negative cumulative returns, consistent with persistent profitability challenges and project delays
- **Solar is bifurcated** — module manufacturers (FSLR) have fared far better than downstream installers (ENPH, SEDG), which faced margin compression from declining incentives and rising customer acquisition costs
- **Integrated majors (XOM, CVX, SHEL)** show moderate but relatively stable returns, acting as a low-volatility anchor against the pure-play clean energy names
---
 
## Usage
 
To regenerate the chart with fresh data, run the notebook locally or in Google Colab:
 
```bash
# Clone the repo
git clone https://github.com/JosefinaCurti/stocks_return_update.git
cd stocks_return_update
 
# Install dependencies
pip install -r requirements.txt
 
# Run the notebook
jupyter notebook energy_stocks_market_price.ipynb
```
 
The final cell writes `cumulative_change_chart.html`. Commit and push to update the live GitHub Pages chart.
 
> **Note:** Data is fetched live from Yahoo Finance at runtime. Results reflect the 2-year window ending on today's date, so the chart updates automatically each time the notebook is re-executed and the output committed.
 
---
 
## Stack
 
- **Python** — data pipeline and chart logic
- **[yfinance](https://github.com/ranaroussi/yfinance)** — Yahoo Finance market data
- **[Plotly](https://plotly.com/python/)** — interactive charting
- **[pandas](https://pandas.pydata.org/)** — data wrangling
- **GitHub Pages** — live chart hosting
---
 
## License
 
Apache-2.0
 
## License
 
Apache-2.0
