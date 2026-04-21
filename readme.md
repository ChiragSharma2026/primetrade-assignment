# Trader Performance vs Market Sentiment — Primetrade.ai Assignment

## Setup

Install dependencies:
pip install pandas matplotlib seaborn scikit-learn

Place both CSV files in the same folder as the notebook:
- fear_greed_index.csv
- historical_data.csv

Open and run trader_sentiment_analysis.ipynb top to bottom.

---

## Datasets
- fear_greed_index.csv: 2644 rows, daily Bitcoin Fear/Greed index from 2018
- historical_data.csv: 211,224 rows, Hyperliquid trader transaction history

---

## Methodology
1. Filtered trader data to closed trades only (Closed PnL ≠ 0) — 104,408 rows retained
2. Parsed timestamps, merged datasets on date using left join
3. Simplified sentiment to 3 buckets: Fear, Neutral, Greed
4. Aggregated to daily level per trader — 1,692 rows
5. Segmented 32 traders into Low/Mid/High Performers by total PnL

---

## Key Insights
1. Greed days show 37% higher overall median PnL than Fear days ($909 vs $663)
2. High Performers earn 67% MORE on Fear days than Greed days ($2168 vs $1294) — the aggregate result is misleading
3. Long/short ratio doubles from Fear (0.13) to Greed (0.27) — sentiment drives directional bias

---

## Strategy Recommendations
1. High Performers should increase activity during Fear — their edge is strongest then
2. Mid Performers should reduce exposure during Fear and wait for Greed confirmation
3. Avoid long-biased positions during Fear periods regardless of segment

## Bonus — Behavioral Archetype Clustering
Traders clustered into 3 archetypes using KMeans on win rate, trade volume, position size, and total PnL:

* Power Traders — high volume, large positions, dominant PnL ($940K median)
* Precision Traders — highest win rate (95.3%), low volume, selective but accurate
* Active Mid-Tier — moderate across all metrics, room to develop in either direction

Key finding: Win rate alone does not predict PnL. Power Traders have lower win rates
than Precision Traders but 9x higher total PnL.

---

## Output Charts
- pnl_by_sentiment.png
- behavior_by_sentiment.png
- segment_sentiment.png
- clustering.png