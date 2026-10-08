Dataset: Hourly Anomaly Scores and Leak Labels from a Multi-Source Urban Water Distribution Network Dataset

Description:
This dataset includes hourly time series from an anonymized urban Water Distribution Network (WDN), combining SCADA sensor readings, operational energy usage, and environmental conditions. 
Anomaly scores were generated using Elastic ML and Isolation Forest algorithms. Binary labels indicate proximity (±7 days) to real leak events recorded in the PTIS system.

Columns:
- timestamp: DD-MM-YYYY HH:00 (datetime string)
- fault_d7: Binary leak proximity label (0/1) for ±7 days around known leak events
- *_kW, *_power_hour: Anomaly scores for energy consumption metrics from pumping stations
- *_ws_temp, *_ws_vigor, *_ws_level: Anomaly scores from SCADA-based water source sensors
- temp_site1_anomaly_score: Environmental temperature anomaly from site 1 (formerly Zikava)
- sfc_temp_site1_anomaly_score: Surface temperature anomaly from site 1
- gw_lvl_site2_anomaly_score: Groundwater level anomaly from site 2 (formerly Machulince)
- gw_temp_site2_anomaly_score: Groundwater temperature anomaly from site 2

All anomaly scores are on a 0–100 scale, where higher values indicate more statistically unusual readings. NULL values indicate sensor downtime or unavailable data.

License: CC-BY 4.0
DOI: 10.5281/zenodo.15096167
Contact: Jan Babela, Constantine the Philosopher University in Nitra, jan.babela@ukf.sk


======================================================================
NOTE ADDED BY THIS PROJECT (not part of the original dataset README)
======================================================================
Timestamp format: the description above says "DD-MM-YYYY HH:00". In the CSV
file, rows whose day of the month is 1-12 are actually written MONTH-first
(MM-DD-YYYY), while rows with day 13-31 are written day-first (DD-MM-YYYY).
Example: "01-12-2022 23:00" is 12 January 2022, and the next row is
"13-01-2022 0:00".

Parsing every row as DD-MM-YYYY and sorting by the result silently shuffles
about 40% of the rows (the first 12 days of each month) while still giving a
gap-free hourly sequence without duplicates.

Rule used in the notebook: if the first number is 12 or less it is the month,
otherwise it is the day. With this rule the file is already in strict
chronological order (8,736 steps of exactly 1 hour), and the fault_d7 label
forms 17 blocks; the shortest class-1 block is exactly 15 days, matching the
documented +/-7-day window. This was inferred by the project author and
should be confirmed by the dataset authors.
