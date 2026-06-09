# Energy Sector Cumulative Returns
 
An interactive visualization of cumulative price returns for 58 energy stocks over a rolling 2-year window — built in Python and published as a live web chart.
 
🔗 **[View the live chart →](https://josefinacurti.github.io/stocks_return_update/)**
 
---
 
## What This Is
 
Energy is one of the most structurally interesting sectors to track right now: nuclear revival, hydrogen scale-up attempts, solar margin compression, and grid infrastructure buildout are all playing out simultaneously in public markets. This project pulls live price data for 58 publicly traded energy companies across six sub-sectors, calculates their cumulative return from 2 years ago to today, and plots them in a single interactive chart.
 
The result is a real-time view of which energy themes the market is rewarding — and which it isn't.
 
---
 
## The Chart
 
The interactive Plotly chart (hosted via GitHub Pages) lets you:
 
- **Hover** over any line to see the company's full name and exact cumulative return on that date
- **Toggle "Top 5 Only"** to isolate the five largest companies by market cap and reduce noise
- **Click legend items** to show/hide individual tickers
- **Zoom and pan** across the 2-year time range
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
 
The universe was selected to span the full clean energy stack — from upstream fuel (uranium miners) to downstream infrastructure (grid equipment) — alongside traditional integrated majors as a benchmark reference.
 
---
 
## How It Works
 
The notebook (`energy_stocks_market_price.ipynb`) runs end-to-end in a single execution:
 
1. **Fetches live data** via `yfinance` for all 58 tickers from 2 years ago to today
2. **Calculates cumulative return** for each stock: `(price_t / price_t0) - 1`, anchored to the first trading day in the window
3. **Ranks by market cap** to identify the Top 5 for the filter toggle
4. **Builds the interactive Plotly figure** with per-trace hover labels, end-of-line markers, and the Top 5 filter button
5. **Exports to HTML** (`index.html`) — committed to the repo and served via GitHub Pages
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
 
The final cell writes `index.html`. Commit and push to update the live GitHub Pages chart.
 
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
