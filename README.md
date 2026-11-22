# Divvy-riders-
Do Divvy riders bring bikes back by evening?

STAT 303-1 (Fall 2026) final project, team p1zz@: Sean Qin, Daniel Cai, Surya Venkataraman, Anjeli Noémi (Mimi).

We look at September 2026 Divvy station-days and ask when later rides offset a station's morning net bike outflow, and how rider groups, routes, and weather relate to that recovery. Morning is 6–10 a.m. and recovery is measured from 10 a.m. to 8 p.m.

The proposal is in [proposal/proposal.ipynb](proposal/proposal.ipynb) and early results are in [PRELIMINARY_FINDINGS.md](PRELIMINARY_FINDINGS.md).

## Repo layout

| Path | Contents |
|---|---|
| `proposal/` | Submitted proposal |
| `checkin/project_checkin.ipynb` | Progress check-in (each member fills in their own question) |
| `notebooks/01_data_cleaning.ipynb` | Shared cleaning; run this first |
| `notebooks/02_station_recovery_sean.ipynb` | Sean: station recovery |
| `notebooks/05_weather_daytype_mimi.ipynb` | Mimi: weather and day type |
| `data/raw/`, `data/processed/` | Raw downloads and cleaned tables |
| `figures/` | Saved plots and tables, prefixed by owner |

## Data

The small cleaned tables are already in `data/processed/`. To get the raw files and build the large ones (`trips_clean.csv`, `station_events.csv`), see [data/README.md](data/README.md).

## Who did what

| Member | Cleaning / preparation | Analysis |
|---|---|---|
| Sean | Station events (departures/arrivals per station-hour) | Station recovery |
| Daniel | Rider categories (member/casual, bike type) | Rider contributions |
| Surya | Routes and duplicates | Route contributions |
| Mimi | Timestamps and weather | Weather and day type |
