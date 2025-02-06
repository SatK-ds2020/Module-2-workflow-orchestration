## Homework 2: Workflow Orchestration for Data Engineering Zoomcamp 2025

* Assignment: In order to extend the existing flows to include data for the year 2021.
* We configured inline trigger to  backfill ='true ' for 2021-01-01 to 2021-07-31 time frame for both the taxi type while executing '/gcp-kestra/06_gcp_taxi_scheduled.yaml' in Kestra flow.

<img src="pics/Screenshot 2025-02-05 164224.png" alt="backfill" width="700" height="400">

## Yellow taxi scheduled backfill for 2021-01-01 to 2021-07-31 time frame ("gcp-kestra/06_gcp_taxi_scheduled.yaml")

<img src="pics/Screenshot 2025-02-05 165335.png" alt="yellow taxi" width="700" height="400">

<img src="pics/Screenshot 2025-02-05 165320.png" alt="yellow taxi" width="500" height="200">


## Green taxi scheduled backfill for 2021-01-01 to 2021-07-31 time frame ( "gcp-kestra/06_gcp_taxi_scheduled.yaml")

<img src="pics\Screenshot 2025-02-05 164027.png" alt="green taxi" width="500" height="200">

## 1. Within the execution for Yellow Taxi data for the year 2020 and month 12: what is the uncompressed file size (i.e. the output file yellow_tripdata_2020-12.csv of the extract task)?
128.3 MB
134.5 MB
364.7 MB
692.6 MB

## Answer: 334.43 MB
<img src="pics\Screenshot 2025-02-05 150522.png" alt="Y-12-2020" width="500" height="200">

## 2. What is the rendered value of the variable file when the inputs taxi is set to green, year is set to 2020, and month is set to 04 during execution?
{{inputs.taxi}}_tripdata_{{inputs.year}}-{{inputs.month}}.csv
green_tripdata_2020-04.csv
green_tripdata_04_2020.csv
green_tripdata_2020.csv

## Answer: green_tripdata_2020-04.csv
<img src="pics\Screenshot 2025-02-05 154838.png" alt="G-04-2020" width="500" height="200">

## 3. How many rows are there for the Yellow Taxi data for all CSV files in the year 2020?
13,537.299
24,648,499
18,324,219
29,430,127

## Answer: 24,648,499
<img src="pics\Screenshot 2025-02-05 172556.png" alt="Y-total-2020" width="500" height="200">

## 4. How many rows are there for the Green Taxi data for all CSV files in the year 2020?
5,327,301
936,199
1,734,051
1,342,034

## Answer:1,734,051
<img src="pics\Screenshot 2025-02-05 172524.png" alt="G-total-2020" width="500" height="200">



## 5. How many rows are there for the Yellow Taxi data for the March 2021 CSV file?
1,428,092
706,911
1,925,152
2,561,031

## Answer:1,925,152
<img src="pics\Screenshot 2025-02-05 154544.png" alt="Y-03-2021" width="500" height="200">

## 6. How would you configure the timezone to New York in a Schedule trigger?
Add a timezone property set to EST in the Schedule trigger configuration
Add a timezone property set to America/New_York in the Schedule trigger configuration
Add a timezone property set to UTC-5 in the Schedule trigger configuration
Add a location property set to New_York in the Schedule trigger configuration

## Answer: Add a timezone property set to America/New_York in the Schedule trigger configuration

```yaml
triggers:
  - id: green_schedule
    type: io.kestra.plugin.core.trigger.Schedule
    cron: "0 9 1 * *"
    timezone: "America/New_York" 
    inputs:
      taxi: green
```
