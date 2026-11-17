# Divvy-riders-
Do Divvy riders bring bikes back by evening?

STAT 303-1 (Fall 2026) final project, team **p1zz@**: Sean Qin, Daniel Cai, Surya Venkataraman, Anjeli Noémi (Mimi).

**Shared question:** When do later rides offset Divvy stations' morning net bike outflow, and how do rider groups, routes, and weather relate to recovery? We use September 2026 station-days. Morning is 6–10 a.m. and recovery is measured from 10 a.m. to 8 p.m.

See [proposal/proposal.ipynb](proposal/proposal.ipynb) for each member's question.

## Repo layout

| Path | What it holds |
|---|---|
| `proposal/` | Submitted project proposal |
| `notebooks/01_data_cleaning.ipynb` | Shared cleaning: run this first |
| `notebooks/` (others) | One analysis notebook per member |
| `data/raw/` | Downloaded source files (not committed) |
| `data/processed/` | Cleaned outputs from notebook 01 (not committed) |
| `figures/` | Saved plots for the report and slides |

## Getting the data

Data files are too large for GitHub, so `data/` is git-ignored. Each member downloads them locally:

1. **Divvy trips, September 2026:** download https://divvy-tripdata.s3.amazonaws.com/202609-divvy-tripdata.zip and unzip it into `data/raw/`.
2. **Weather:** Meteostat daily data for one Chicago station, September 2026 (details in notebook 01).

Then run `notebooks/01_data_cleaning.ipynb` top to bottom to create the cleaned files in `data/processed/`.

## Who did what

Preparation is split by owner, and all four of us validate it together:

| Member | Cleaning / preparation | Analysis |
|---|---|---|
| Sean | Station events (departures/arrivals per station-hour) | Station recovery |
| Daniel | Rider categories (member/casual, bike type) | Rider contributions |
| Surya | Routes and duplicates | Route contributions |
| Mimi | Timestamps and weather | Weather and day type |
