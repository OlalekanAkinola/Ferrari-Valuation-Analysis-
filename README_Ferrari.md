# Ferrari: Does Business Performance Justify the Valuation Premium?

**Letter F in my A–Z investment research series**

This project uses Python to examine Ferrari’s valuation, financial performance and stock-market risk. It starts with the price investors are paying, then investigates whether profitability, cash generation and returns on invested capital support that valuation.

Ferrari is the focus throughout. Porsche AG is used for relative valuation, while SPY is the benchmark for historical and year-to-date stock performance.

**[Explore the interactive dashboard](https://ferrari-research-dashboard.akinola-olalekan97.chatgpt.site/)**

## Scope and Measurement Periods

| Component | Period or basis |
|---|---|
| Market valuation | 9 October 2026 closing prices |
| Annual financial performance | FY2020–FY2025 |
| Interim financial comparison | H1 2026 versus H1 2025 |
| Trailing twelve-month earnings | FY2025 + H1 2026 − H1 2025 |
| Historical stock performance | 2020–2025 |
| YTD stock performance | 2026 through 9 October |
| ROIC | FY2025, using average invested capital |
| WACC | Estimate using the valuation-date assumptions |

Financial amounts are presented in euros, generally in millions. Stock-return comparisons use the notebook’s US-listed Ferrari and SPY price series.

## Selected Findings

### Valuation: a premium that depends on the multiple

Ferrari’s estimated market capitalization was **€61.03 billion**, with enterprise value of **€62.72 billion** and a converted share price of **€347.95**.

| TTM valuation multiple | Ferrari | Porsche AG |
|---|---:|---:|
| P/E | 37.30× | 44.89× |
| EV/EBITDA | 22.03× | 9.48× |

Ferrari trades at a substantial premium on EV/EBITDA, but at a lower P/E. The difference shows why one multiple alone can give an incomplete picture: Porsche’s lower current earnings increase its P/E despite its lower enterprise-value multiple.

Applying Porsche’s EV/EBITDA to Ferrari produces a conditional implied price of **€144.29**, approximately **58.53% below** Ferrari’s current euro price. This is a peer-multiple scenario, not a standalone fair-value estimate. It tests how much of Ferrari’s valuation depends on maintaining a premium to Porsche.

### Fundamentals: stronger margins and cash generation

- Revenue increased from **€3.46 billion in FY2020 to €7.15 billion in FY2025**.
- Operating margin improved from **20.69% to 29.53%** over that period.
- Free cash flow rose from **€129 million to €1.41 billion**, with its margin improving from **3.73% to 19.72%**.
- Cash conversion, measured as free cash flow divided by net profit, increased from **21.22% to 88.23%**.
- H1 free cash flow increased from **€779 million to €811 million**, although FCF margin and cash conversion eased slightly.

The simplified ROIC estimate of **31.19%** exceeds estimated WACC of **7.32%**. This supports the discussion of capital efficiency, subject to the calculation’s assumptions and the different measurement dates.

![Ferrari revenue and free cash flow](Ferrari_financial_visuals.png)

### Stock performance: business strength and investor experience differ

| Metric | Ferrari historical | SPY historical | Ferrari YTD | SPY YTD |
|---|---:|---:|---:|---:|
| Return¹ | 18.50% | 16.02% | 6.72% | 15.06% |
| Annualized volatility | 30.58% | 20.75% | 33.55% | 13.01% |
| Sharpe ratio | 0.51 | 0.64 | 0.31 | 1.18 |
| Sortino ratio | 0.74 | 0.89 | 0.47 | 1.77 |
| Maximum drawdown | −38.29% | −33.72% | −19.58% | −8.88% |

¹ Historical return is the arithmetic annualized mean of daily returns, not CAGR. YTD return is the actual cumulative return over the measurement period; the two measures have different horizons.

Ferrari generated a higher historical annualized return, but SPY delivered stronger risk-adjusted performance. That distinction became more pronounced in 2026, when Ferrari lagged SPY while exhibiting greater volatility and drawdown.

Ferrari’s one-day 95% historical VaR and CVaR, calculated from YTD daily returns, were approximately **3.15% and 3.90%**. These describe the observed loss threshold and average tail loss; they do not set a limit on future losses.

![Ferrari and SPY risk-adjusted performance](Ferrari_risk_adjusted.png)

## Analytical Workflow

1. Build Ferrari and Porsche valuation inputs; calculate market capitalization, enterprise value, EPS and multiples.
2. Examine annual and interim revenue, margins, cash generation and investment spending.
3. Estimate NOPAT, average invested capital, ROIC and WACC.
4. Compare Ferrari with SPY using returns, volatility, Sharpe, Sortino, beta, CAPM and drawdown.
5. Measure YTD downside-tail risk using historical VaR and CVaR.
6. Review candlesticks and 50-, 100- and 200-day moving averages, then test a peer-based valuation scenario.

The notebook’s original charts cover financial performance, margins, normalized historical and YTD performance, risk-adjusted performance, tail risk, technical analysis and comparative valuation. The dashboard brings these outputs into one presentation.

## Methodology and Assumptions

- **Free cash flow:** operating cash flow less the capital expenditure used in the notebook. This may differ from company-defined industrial FCF.
- **Enterprise value:** equity market value + debt − cash + non-controlling interests. The implied-equity calculation reverses these adjustments.
- **EPS:** TTM net profit divided by estimated current shares outstanding. This is a simplified valuation EPS, rather than reported diluted EPS based on weighted-average shares.
- **Risk metrics:** calculated from daily simple returns, with 252 trading days for annualization. Average three-month US Treasury yields are used as risk-free proxies: 2.86% historically and 3.80% for YTD.
- **Sortino:** downside deviation uses daily excess returns below zero and includes all observations in the denominator.
- **ROIC and WACC:** simplified group-level estimates. Financial-services activities, the treatment of cash, debt-cost proxies and the use of a US-market beta in a euro valuation affect their interpretation.
- **Peer valuation:** Porsche’s listed preferred-share price is applied to both share classes when estimating market capitalization. Its H1 2026 depreciation and amortization input is estimated. These assumptions affect the implied Ferrari price.

## Working with the Notebook

The analysis uses Python with `pandas`, `numpy`, `yfinance`, `matplotlib`, `seaborn` and `mplfinance` in Jupyter Notebook.

Open the Ferrari notebook and run cells sequentially from a fresh kernel. Some cells change variables’ units, so repeatedly executing those cells can alter results. Financial inputs are entered manually; downloading market prices again may change outputs.

To display the chart previews above on GitHub, upload the original PNG files alongside this README. No generated or replacement charts are required.

## Data Sources

- [Ferrari investor relations](https://www.ferrari.com/en-EN/corporate/investors) — financial reports and company disclosures.
- [Ferrari filings on SEC EDGAR](https://www.sec.gov/edgar/browse/?CIK=1648416&owner=exclude) — annual and interim financial statements.
- [Porsche investor relations](https://investorrelations.porsche.com/) — financial statements and valuation inputs.
- [Yahoo Finance](https://finance.yahoo.com/) — market-price data accessed through `yfinance`.
- [FRED: three-month US Treasury yield](https://fred.stlouisfed.org/series/DGS3MO) — stock-performance risk-free-rate proxy.
- [Deutsche Bundesbank](https://www.bundesbank.de/en/statistics/money-and-capital-markets/interest-rates-and-yields/daily-yields-of-current-federal-securities-772220) — German government-bond yield inputs.
- [Aswath Damodaran’s data](https://pages.stern.nyu.edu/~adamodar/) — equity-risk-premium assumptions.

## Author

**Olalekan Akinola** — research, Python analysis and original charts. The interactive dashboard was developed with ChatGPT using the notebook’s outputs.

This is an independent analytical exercise for educational purposes, not an investment recommendation.
