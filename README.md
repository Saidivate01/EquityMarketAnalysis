[Equity market.docx](https://github.com/user-attachments/files/25554336/Equity.market.docx)
# EquityMarketAnalysis
This project focuses on analyzing equity market index data to understand price behaviour, volatility and risk patterns over time. using Power BI and DAX the project transforms raw market data into interactive dashboards that highlight trends, dowside risk and stress periods.

Objectives:
a. Analyze historical market index data
b. Study daily price movements and returns
c. Measure market volatility and downside risk
d. Identify stress periods and extreme loss scenarios
e. Build an interactive Power BI dashboards

Metrics & Feature Implemented:
i.	Daily Return:
Measures day to day percentage change in index value.
Daily_Return =
VAR CurrentClose =
 	MAX ( Fact_Nifty[Close] )
VAR PreviousClose =
CALCULATE (
 	MAX ( Fact_Nifty[Close] ), PREVIOUSDAY ( Dim_Date[Date] ))
RETURN
 	DIVIDE ( CurrentClose - PreviousClose, PreviousClose )
ii.	Rolling Volatility (30-Day):
Calculates the rolling std. derivation of daily returns to assess market variability.
Volatility_30D =
STDEVX.P (
 	DATESINPERIOD (
 		Dim_Date[Date],
 		MAX ( Dim_Date[Date] ), -30, DAY),
 		[Daily_Return])
iii.	Drawdown:
Measures decline from historical peak to current value, highlighting stress periods.



















iv.	Max Drawdown:
Identifies the worst peak to trough loss over a selected period.










v.	Value at Rist (VaR -95%):
Estimates the Max expected daily loss at 95% confidence level







vi.	Average Volatility:
Calculates the avg volatility over the selected time period.








Key Insights
Daily Return & Drawdown Analysis
Year	Max	Min	Reason
2021 (From Feb 15)	+3.02% (May 17)	-3.53% (Apr 12)	Reduction of COVID cases vs. 2nd COVID wave lockdown fears.
2022	+3.03% (Feb 15)	-4.78% (Feb 24)	Rebound from oversold levels vs. Russia-Ukraine war onset.
2023	+2.00% (Dec 4)	-1.61% (Jan 27)	Year-end tax planning rally vs. Adani-Hindenburg volatility.
2024	+3.25% (Jun 3)	-5.93% (Jun 4)	Largest swing period: Exit poll euphoria vs. actual election results.
2025	+3.00% (May 12)	-2.00% (Mar 28)	Ind-Pak ceasefire & tariff reduction of china by U.S vs. Corporate earnings slowdown.
2026 (to Feb 7)	+2.55% (Feb 3)	-1.96% (Feb 1)	Positive response to the 2026 Union Budget vs. Increment of STT

Conclusion
2022 was the most stressful year due to Russia Ukraine war
2023 saw more moodswing of the market due to Lok Sabha Elections
