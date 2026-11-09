# Oil Shocks and Capital Reallocation toward Green Firms

**Evidence from the Iran-War Shock of 2026**

Code, figures and thesis for my MA thesis in Economics, Data, and Policy at Central European University (Vienna, 2026), supervised by Tomy Lee.

## Research question

Does a geopolitical oil shock push investors to move capital toward green firms?

On 28 February 2026, US and Israeli strikes on Iran disrupted crude-oil transit through the Strait of Hormuz. I use this shock as an event study to compare how green (clean-energy) and brown (fossil-fuel) U.S.-listed firms and ETFs reacted.

Two hypotheses are tested:

- **H1:** Green firms and ETFs earn positive cumulative abnormal returns (CARs) after the shock.
- **H2:** Part of these abnormal returns is explained by oil-market volatility.

## Main findings

- Fossil-fuel firms gained significantly after the shock, and the gains persisted over the 25-day post-event window.
- Green firms fell around the event and did not recover durably.
- A short positive green effect in equal-weighted portfolios disappeared under value weighting and once oil volatility was controlled for, suggesting it reflected oil-market uncertainty rather than genuine reallocation.
- Green ETFs showed no positive abnormal returns.
- Placebo tests on 100 pseudo-event dates show no comparable pattern, so the results are specific to the shock.

The full thesis is in [`docs/Final_Thesis.pdf`](docs/Final_Thesis.pdf).

## Data

| Source | Data |
|---|---|
| LSEG (Refinitiv) | Daily prices, volume, turnover, market capitalisation, shares outstanding, ETF net assets; Brent, WTI and natural gas futures |
| Yahoo Finance | VIX and OVX volatility indices |
| Kenneth French data library | Daily Fama-French factors and risk-free rate |

**Sample period:** January 2021 to April 2026
**Final sample:** 106 green firms, 153 brown firms, 12 green ETFs and 17 brown ETFs (NYSE and NASDAQ)

Firms are classified as green or brown by their core business: clean-energy activities (solar, wind, storage, hydrogen, EVs, nuclear, geothermal and others) versus fossil-fuel extraction, processing and distribution.

**The raw data are not included** in this repository because LSEG data are licensed. The `data/` folder is excluded via `.gitignore`. Reproducing the results requires LSEG access.

## Method

- **Event date:** t = 0 is 2 March 2026, the first U.S. trading day after the strikes.
- **Expected returns:** CAPM and Fama-French three-factor models, estimated over trading days [-285, -35] with Newey-West (HAC) standard errors.
- **Sample filter:** an asset is kept only if its CAPM beta and at least one FF3 loading are significant at the 10% level, using estimation-window data only.
- **Abnormal returns:** CARs over several event windows, aggregated with equal and value weights.
- **Oil-volatility extension (H2):** models augmented with Brent and WTI Parkinson realised volatility and OVX; the change in CAR measures how much oil volatility explains.
- **Robustness:** residual diagnostics (Jarque-Bera, Ljung-Box, Durbin-Watson, ARCH), principal-component factors, sector-level CARs, and placebo tests on 100 pseudo-event dates.

## Repository structure

```
Oil-Shock-and-Capital-Reallocation/
├── notebooks/
│   ├── 01_collect.ipynb        # Data collection from LSEG, Yahoo Finance and the French library
│   ├── 02_explanatory.ipynb    # Data cleaning and exploratory analysis
│   └── 03_event_study.ipynb    # Event study, oil-volatility extension and placebo tests
├── figures/
│   ├── eda/                    # Exploratory figures
│   └── event_study/            # CAR plots, daily abnormal returns, placebo and sector figures
├── docs/
│   └── Final_Thesis.pdf
└── README.md
```

## How to run

1. Install the packages:

   ```bash
   pip install pandas numpy scipy statsmodels scikit-learn matplotlib seaborn yfinance requests lseg-data jupyter
   ```

2. Set up an LSEG Data Library session (requires an LSEG licence).
3. Run the notebooks in order: `01_collect`, `02_explanatory`, `03_event_study`.


## Citation

Dehghannezhad, Shirin. 2026. *Oil Shocks and Capital Reallocation toward Green Firms: Evidence from the Iran-War Shock of 2026.* MA thesis, Department of Economics and Business, Central European University, Vienna.

The thesis is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

## Contact

Shirin Dehghannezhad · [shirindehghannezhad7624@gmail.com](mailto:shirindehghannezhad7624@gmail.com) · [LinkedIn](https://www.linkedin.com/in/shirin-dehghannezhad)
