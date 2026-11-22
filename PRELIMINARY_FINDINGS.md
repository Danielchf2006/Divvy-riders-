# Preliminary Findings

*Working notes, last updated Nov 17, 2026. Numbers come from `notebooks/01_data_cleaning.ipynb` and `notebooks/02_station_recovery_sean.ipynb`; rerun them to reproduce.*

This is an **exploratory data analysis** project, not a model. Per the course site, predictive modeling or clustering can earn bonus points but must not replace the EDA.

## Shared data cleaning (all members)

| Step | Rides removed | Rides left |
|---|---|---|
| Raw September 2026 file | – | 770,562 |
| Near-duplicate second copies | 4 | 770,558 |
| Shorter than 60 s (false starts / re-docks) | 18,610 | 751,948 |
| Longer than 24 h (lost or stolen bikes) | 633 | **751,315 (97.5%)** |

- **Missing stations come only from e-bikes:** 27.6% of e-bike rides have no start station; classic bikes have almost none missing. Station flows therefore undercount e-bikes (relevant for Daniel's bike-type check).
- **66.6% of kept rides have both stations known**, which is the sample usable for route analysis (Surya).
- **Weather:** Meteostat **Chicago Midway (72534)**. O'Hare has no September precipitation. Temperature and precipitation are observed, not model-filled. There were **7 rainy days** (precipitation > 0), but only 5 fall on weekdays and only 2 weekdays had heavy rain (≥ 2.5 mm). Mimi's comparisons will have small samples.
- **Labor Day is Monday, Sept 7.** It is labeled as its own day type.

## Whole system

| Day type | Deficit station-days | Full recovery by 8 p.m. | Pooled recovery* |
|---|---|---|---|
| Weekday | 8,548 | 38.6% | 56.7% |
| Weekend | 2,570 | 34.2% | 10.2% |
| Labor Day | 290 | 39.0% | 23.0% |

\*Pooled recovery = total later net arrivals ÷ total morning net departures.

The ratio for a single station-day is unstable when the deficit is only 1–2 bikes, so we report median, full-recovery rate, and pooled recovery side by side.

Weekend morning deficits are barely made up later in the day, which suggests weekend riding is not a commute-and-return pattern.

## Sean: station recovery

1. **264 stations are recurring-deficit stations**: they start the day short on at least 15 of 21 weekdays. Most of the other 1,259 weekday-active stations rarely do.
2. **At recurring stations, later traffic replaces about 62% of the morning loss** (pooled), but **full recovery happens on only 39% of deficit days**. The median station fully recovers on 42% of its deficit days, with a wide spread (0% to 94%).
3. **Recovery comes from the evening commute.** Stations that usually recover regain bikes mainly between 3 and 6 p.m.; stations that rarely recover are still short at midnight.
   ![Cumulative hourly flow](figures/sean_cumulative_hourly_flow.png)
4. **The largest daily losses** are at Clark St & Elm St (about 17 bikes a day), Indiana Ave & Roosevelt Rd (13), and Clark St & Lincoln Ave (12). Loomis St & Lexington St, Pine Grove Ave & Irving Park Rd, and Broadway & Cornelia Ave lose bikes almost every weekday and recover less than a third of the loss. Full table: `figures/sean_top_deficit_stations.csv`.
5. **Sensitivity checks:**
   - Counting only deficits of at least 5 bikes lowers full recovery to 28%; pooled recovery barely changes.
   - Extending the recovery window to midnight raises pooled recovery to 77%, but most deficit days still do not fully recover.
   - Changing the morning window (7–9 a.m. or 6–11 a.m.) does not change the conclusion.

   Full table: `figures/sean_sensitivity.csv`.

**Limits:** trip flows cannot show whether a station actually ran empty or was restocked by truck, and dockless e-bike trips are not counted. The data cover one month.

## Still to do

- **Daniel (rider contributions), Surya (route contributions), Mimi (weather and day type):** analyses not started yet. The cleaned tables they need are produced by notebook 01: `station_day_by_rider.csv`, `trips_clean.csv`, and `station_day.csv` with weather joined.
- **Progress check-in, Mon Nov 23 by 1:50 pm:** `checkin/project_checkin.ipynb` is filled in for the team overview, data cleaning, Sean's question, a proposed plan, and mentor questions. **Daniel, Surya, and Mimi each add one early result in their Question section,** and the team picks a presentation session.
