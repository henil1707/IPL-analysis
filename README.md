# IPL Analysis — Exploratory Data Analysis (2021 & 2022)

> **End-to-end cricket analytics project** — two Jupyter notebooks covering IPL 2021 season-wide EDA and a deep-dive performance analysis of Gujarat Titans' inaugural 2022 championship season, built using Python, Pandas, and Matplotlib/Seaborn.

---

## Project Overview

This repo contains two distinct analyses across two IPL seasons:

| Notebook | Season | Focus |
|---|---|---|
| [`Ipl 2021 EDA.ipynb`](Ipl%202021%20EDA.ipynb) | IPL 2021 | Full season EDA — batting, bowling, team performance |
| [`Gujrat TitansTeam Perfomance Analysis.ipynb`](Gujrat%20TitansTeam%20Perfomance%20Analysis.ipynb) | IPL 2022 | Gujarat Titans — ball-by-ball team performance analysis |

Gujarat Titans won the IPL in their debut season (2022) — this analysis explores *how* they did it, drilling into their batting patterns, bowling economy, powerplay strategy, and match-winning moments.

---

## Datasets

| File | Description |
|---|---|
| `IPL_Matches_2022.csv` | Match-level data — teams, venues, toss, results, margin of victory |
| `IPL_Ball_by_Ball_2022.csv` | Delivery-level data — every ball bowled in IPL 2022 with batsman, bowler, runs, extras, dismissal |
| `Most Runs - 2021.csv` | Top run-scorers in IPL 2021 with strike rate, average, boundaries |
| `Most Wickets - 2021.csv` | Top wicket-takers in IPL 2021 with economy rate, bowling average |

---

## Notebook 1 — IPL 2021 Season EDA

### Analysis areas

**Batting analysis**
- Top run-scorers of the season ranked by total runs
- Strike rate vs average scatter — identifying aggressive vs consistent batters
- Boundary percentage (4s and 6s as % of total runs) by player
- Highest individual scores in the season

**Bowling analysis**
- Top wicket-takers ranked by total dismissals
- Economy rate comparison across bowlers (runs per over)
- Bowling average vs strike rate — identifying match-winners
- Most economical bowlers in powerplay vs death overs

**Team performance**
- Win/loss record by team across the season
- Toss impact — win % when batting first vs chasing
- Average first innings score by team
- Run rate trends across match phases (powerplay, middle, death)

### Key Python techniques used

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Run rate by phase
df['phase'] = pd.cut(df['over'], bins=[0,6,15,20],
                     labels=['Powerplay', 'Middle', 'Death'])

# Top scorers
top_scorers = df.groupby('batter')['batsman_runs'].sum().sort_values(ascending=False).head(10)

# Economy rate
economy = df.groupby('bowler').agg(
    runs=('total_runs','sum'),
    overs=('over','nunique')
).assign(economy=lambda x: x['runs']/x['overs']).sort_values('economy')
```

---

## Notebook 2 — Gujarat Titans 2022 Performance Analysis

Gujarat Titans entered the IPL in 2022 as a brand new franchise and won the title in their debut season — one of the most remarkable stories in IPL history. This notebook dissects their performance ball-by-ball.

### Analysis areas

**Match results & win patterns**
- GT's win/loss record across the season, league stage vs playoffs
- Margin of victory — wins by runs (batting first) vs wickets (chasing)
- Venue-wise performance breakdown

**Batting deep dive**
- Top GT run-scorers and their contribution to team totals
- Partnership analysis — which batting pairs built the innings
- Powerplay scoring patterns (first 6 overs) — GT's approach to setting/chasing
- Strike rate by batting position (top order vs finishers)
- Boundary hitting — 4s and 6s distribution across the innings

**Bowling deep dive**
- GT's bowling attack breakdown — runs conceded and wickets by each bowler
- Economy rate by bowling phase (powerplay, middle overs, death)
- Most impactful bowling spells (wickets in a spell, economy in context)
- Dismissal types — caught, bowled, LBW, run out distribution

**Match-phase analysis (ball-by-ball)**
- Run rate progression across the 20 overs for batting innings
- Wicket fall patterns — when GT lost/took wickets
- Death over (overs 16–20) performance — GT's defining strength

### Why Gujarat Titans won — what the data shows

```
GT's 2022 title recipe (from the analysis):

Powerplay (overs 1–6):   Solid platform — preserved wickets, scored at par
Middle overs (7–15):      Built partnerships — minimised dot balls
Death overs (16–20):      Explosive finishing — highest scoring phase
Bowling:                  Death bowling economy was among the best in the tournament
```

---

## Tech Stack

```
Python 3.x
├── Pandas        — data loading, transformation, groupby aggregations
├── NumPy         — numerical operations
├── Matplotlib    — base visualisation (bar charts, line plots, scatter)
├── Seaborn       — statistical visualisation (heatmaps, distribution plots)
└── Jupyter       — interactive notebook environment
```

---

## Getting Started

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### Run
```bash
git clone https://github.com/henil1707/IPL-analysis.git
cd IPL-analysis

# Season-wide 2021 EDA
jupyter notebook "Ipl 2021 EDA.ipynb"

# Gujarat Titans 2022 deep dive
jupyter notebook "Gujrat TitansTeam Perfomance Analysis.ipynb"
```

All CSV datasets are included in the repo — no external downloads needed.

---

## Project Structure

```
IPL-analysis/
│
├── Ipl 2021 EDA.ipynb                          # IPL 2021 full season analysis
├── Gujrat TitansTeam Perfomance Analysis.ipynb # GT 2022 team deep dive
│
├── IPL_Matches_2022.csv                        # Match-level 2022 data
├── IPL_Ball_by_Ball_2022.csv                   # Ball-by-ball 2022 data
├── Most Runs - 2021.csv                        # Top batters 2021
├── Most Wickets - 2021.csv                     # Top bowlers 2021
│
└── README.md
```

---

## Skills Demonstrated

This project was built as a hands-on exercise in applying core data analysis skills to a familiar, real-world dataset:

- **Data cleaning** — handling missing values, type casting, filtering by team/player
- **GroupBy aggregations** — multi-level grouping for phase-wise and player-wise stats
- **Derived metrics** — computing economy rate, strike rate, boundary %, NRR
- **Visualisation** — bar charts, scatter plots, heatmaps, line charts for time-series run rate
- **Domain-specific segmentation** — splitting innings into powerplay/middle/death phases

The same analytical thinking applied here — segmentation, trend analysis, performance ranking — directly maps to business analytics work in sales territory analysis, product performance tracking, and operational KPI dashboards.

---

## Related Projects

- [inventory-automation-system](https://github.com/henil1707/inventory-automation-system) — Python automation for pharma inventory (same Pandas + data wrangling skills)
- [SQL-Sale_Distribution-Tableau](https://github.com/henil1707/SQL-Sale_Distribution-Tableau) — SQL + Tableau sales distribution analysis
- [Recommendation_system](https://github.com/henil1707/Recommendation_system) — ML-based recommendation engine with collaborative filtering

---

## Author

**Henil Jariwala** — Senior Data Analyst, Pharma Industry

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://linkedin.com/in/henil-jariwala)
[![GitHub](https://img.shields.io/badge/GitHub-henil1707-black?style=flat&logo=github)](https://github.com/henil1707)
[![Tableau Public](https://img.shields.io/badge/Tableau-View_Dashboard-blue?style=flat&logo=tableau)](https://public.tableau.com/app/profile/henil3827/viz/ExploringSaledata/Dashboard1)

---

*Built with Python · Pandas · Matplotlib · Seaborn · Jupyter Notebook*

