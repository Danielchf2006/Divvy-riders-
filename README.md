# Divvy-riders-
Do Divvy riders bring bikes back by evening?

STAT 303-1 (Fall 2026) final project, team **p1zz@**: Sean Qin, Daniel Cai, Surya Venkataraman, Anjeli Noémi (Mimi).

**Shared question:** When do later rides offset Divvy stations' morning net bike outflow, and how do rider groups, routes, and weather relate to recovery? We use September 2026 station-days. Morning is 6–10 a.m. and recovery is measured from 10 a.m. to 8 p.m.

See [proposal/proposal.ipynb](proposal/proposal.ipynb) for each member's question and [PRELIMINARY_FINDINGS.md](PRELIMINARY_FINDINGS.md) for early results.

## Repo layout

| Path | What it holds |
|---|---|
| `proposal/` | Submitted project proposal |
| `notebooks/01_data_cleaning.ipynb` | Shared cleaning: run this first |
| `notebooks/02_station_recovery_sean.ipynb` | Sean: station recovery |
| `notebooks/03_…`, `04_…`, `05_…` | Daniel, Surya, Mimi: to be added |
| `data/raw/` | Downloaded source files (not committed) |
| `data/processed/` | Cleaned outputs from notebook 01 (not committed) |
| `figures/` | Saved plots and tables for the report and slides, prefixed by owner |

Notebooks use only methods from the [course coursebook](https://lizhen0909.github.io/stat303-1-sec20-coursebook/), and each one follows the cleaning notebook's style.

## Getting the data

Data files are too large for GitHub, so `data/` is git-ignored. Each member downloads them locally into `data/raw/`:

1. **Divvy trips, September 2026:** download https://divvy-tripdata.s3.amazonaws.com/202609-divvy-tripdata.zip and unzip it.
2. **Weather:** download https://data.meteostat.net/daily/2026/72534.csv.gz (Chicago Midway) and save it as `meteostat_daily_2026_midway_72534.csv.gz`.

Then run `notebooks/01_data_cleaning.ipynb` top to bottom to create the cleaned files in `data/processed/`.

**Shortcut:** the small cleaned tables are already in the repo: `station_day.csv`, `station_day_by_rider.csv`, `weather_daily.csv`, and `exclusions.csv`.
If your analysis only needs those, you can skip the download. `trips_clean.csv` (167 MB, needed for route analysis) and `station_events.csv` (139 MB) are over GitHub's 100 MB limit, so you have to create them by running notebook 01.

## Who did what

Preparation is split by owner, and all four of us validate it together:

| Member | Cleaning / preparation | Analysis |
|---|---|---|
| Sean | Station events (departures/arrivals per station-hour) | Station recovery |
| Daniel | Rider categories (member/casual, bike type) | Rider contributions |
| Surya | Routes and duplicates | Route contributions |
| Mimi | Timestamps and weather | Weather and day type |
