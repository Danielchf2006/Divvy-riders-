# Getting the Data

The repo already includes the small cleaned tables in `data/processed/`. The raw files and the two large cleaned files are not in the repo because GitHub rejects files over 100 MB.
You download those yourself. Both sources are free and public.

## Do I need to download anything?

| My analysis needs… | What to do |
|---|---|
| `station_day.csv`, `station_day_by_rider.csv`, `weather_daily.csv`, `exclusions.csv` | **Nothing.** They are already in `data/processed/`. Just `git pull`. |
| `trips_clean.csv` or `station_events.csv` (e.g. routes) | Do steps 1–3 below. |
| To rerun or change the cleaning | Do steps 1–3 below. |

## Step 1 · Download the raw files

Put both files in **`data/raw/`** with these exact names.

| File | Download link | Save as |
|---|---|---|
| Divvy trips, September 2026 (30 MB zip → 154 MB CSV) | https://divvy-tripdata.s3.amazonaws.com/202609-divvy-tripdata.zip | Unzip to get `202609-divvy-tripdata.csv` |
| Meteostat daily weather, Chicago Midway (6 KB) | https://data.meteostat.net/daily/2026/72534.csv.gz | `meteostat_daily_2026_midway_72534.csv.gz` (don't unzip) |

**Option A: click the links.** Your browser saves the files to Downloads.
Move them into `data/raw/`, unzip the Divvy file, and rename the weather file as shown in the table.
On a Mac, unzipping also creates a `__MACOSX` folder, which you can delete.

**Option B: terminal (Mac or Linux).** Run this from the repo's top folder:

```bash
cd data/raw
curl -O https://divvy-tripdata.s3.amazonaws.com/202609-divvy-tripdata.zip
unzip 202609-divvy-tripdata.zip && rm -rf __MACOSX
curl -o meteostat_daily_2026_midway_72534.csv.gz https://data.meteostat.net/daily/2026/72534.csv.gz
cd ../..
```

**Option B: PowerShell (Windows).** Run this from the repo's top folder:

```powershell
cd data\raw
Invoke-WebRequest https://divvy-tripdata.s3.amazonaws.com/202609-divvy-tripdata.zip -OutFile 202609-divvy-tripdata.zip
Expand-Archive 202609-divvy-tripdata.zip -DestinationPath .
Invoke-WebRequest https://data.meteostat.net/daily/2026/72534.csv.gz -OutFile meteostat_daily_2026_midway_72534.csv.gz
cd ..\..
```

When you're done, `data/raw/` should contain:

```
202609-divvy-tripdata.csv
meteostat_daily_2026_midway_72534.csv.gz
```

## Step 2 · Run the cleaning notebook

Open `notebooks/01_data_cleaning.ipynb` in VS Code with the course environment (the `.venv` from `stat303-1`), then click **Run All**.
It takes about a minute and ends with `All checks passed.` and a list of saved files.

## Step 3 · Check the output

`data/processed/` should now contain:

| File | Size | Used by |
|---|---|---|
| `trips_clean.csv` | ~167 MB | Surya (routes) |
| `station_events.csv` | ~139 MB | Sean (hourly flows), Daniel (bike-type check) |
| `station_day.csv` | ~4 MB | everyone |
| `station_day_by_rider.csv` | ~5 MB | Daniel |
| `weather_daily.csv` | < 1 KB | Mimi |
| `exclusions.csv` | < 1 KB | report (cleaning summary) |

The two large files are git-ignored, so they won't be committed by accident.
If you rerun the cleaning, git will show the small tables as changed only if their contents actually changed. Commit them only if the team agreed to the change.

## Troubleshooting

- **`FileNotFoundError` in notebook 01:** the raw file name or folder doesn't match. Check Step 1's table, and run the notebook from the `notebooks/` folder (VS Code does this by default).
- **The weather file looks like gibberish:** that's expected for a `.csv.gz`. Don't unzip or rename it to `.csv`; pandas reads it directly.
- **A download link fails:** Divvy lists all monthly files at https://divvy-tripdata.s3.amazonaws.com/index.html, and Meteostat's data docs are at https://dev.meteostat.net. Tell the team before swapping in a different source.
