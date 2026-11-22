# Getting the Data

`station_day.csv`, `station_day_by_rider.csv`, `weather_daily.csv`, and `exclusions.csv` are already in `data/processed/`. If that's all you need, just `git pull`.

`trips_clean.csv` and `station_events.csv` are too big for GitHub (over 100 MB), so you need to make them yourself:

1. Download the raw files into `data/raw/`:

   ```bash
   cd data/raw
   curl -O https://divvy-tripdata.s3.amazonaws.com/202609-divvy-tripdata.zip
   unzip 202609-divvy-tripdata.zip && rm -rf __MACOSX
   curl -o meteostat_daily_2026_midway_72534.csv.gz https://data.meteostat.net/daily/2026/72534.csv.gz
   ```

   Or download the two links in a browser, unzip the Divvy file, and rename the weather file to `meteostat_daily_2026_midway_72534.csv.gz` (leave it gzipped).

2. Run `notebooks/01_data_cleaning.ipynb` top to bottom (about a minute). It ends with `All checks passed.` and writes everything to `data/processed/`.
