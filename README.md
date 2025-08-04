# Data-Collections-and-Storage-SQL-.ipynb
Zuber Ride-Sharing Analysis
Project Description
You are working as an analyst for Zuber, a new ride-sharing company launching in Chicago. The goal of this project is to identify patterns in ride data to help Zuber understand customer preferences and the influence of external factors, such as weather, on ride frequency.

You will work with SQL queries and Python to analyze taxi rides, company performance, and test hypotheses about ride durations.

Data Description
You will be working with a relational database consisting of the following tables:

neighborhoods — Chicago neighborhood information
name: name of the neighborhood

neighborhood_id: neighborhood code

cabs — taxi vehicle information
cab_id: vehicle code

vehicle_id: technical ID of the vehicle

company_name: the company that owns the taxi

trips — data on rides
trip_id: ride code

cab_id: vehicle operating the ride

start_ts: ride start time (rounded to the hour)

end_ts: ride end time (rounded to the hour)

duration_seconds: duration of the ride in seconds

distance_miles: distance in miles

pickup_location_id: neighborhood code for pickup

dropoff_location_id: neighborhood code for dropoff

weather_records — hourly weather data
record_id: weather record ID

ts: timestamp of weather measurement

temperature: measured temperature

description: weather description (e.g., “light rain”, “clear sky”)

🔗 Note: There is no direct foreign key between trips and weather_records. You will need to join them using timestamps: trips.start_ts and weather_records.ts.

Project Workflow
Step 1 — Weather Data Parsing
Parse hourly weather data for Chicago from this source:
https://practicum-content.s3.us-west-1.amazonaws.com/data-analyst-eng/moved_chicago_weather_2017.html

Step 2 — SQL Analysis
Find the number of rides per taxi company for November 15–16, 2017.

Find rides for companies with names containing "Yellow" or "Blue" during November 1–7, 2017.

Compare Flash Cab, Taxi Affiliation Services, and all other companies under “Other”.

Step 3 — SQL Hypothesis Preparation
Find neighborhood IDs for "Loop" and "O'Hare International Airport".

Classify weather conditions as “Good” or “Bad” based on whether the description includes “rain” or “storm”.

Retrieve all rides from Loop to O’Hare on Saturdays and join with weather data.

Focus on the duration of these rides and associated weather.

Step 4 — Python Data Analysis
Files used:

project_sql_result_01.csv — Number of rides per company for Nov 15–16

project_sql_result_04.csv — Average number of drop-offs per neighborhood in Nov

Tasks:

Load and explore the data

Ensure proper data types

Plot graphs:

Bar chart: Top taxi companies by rides

Bar chart: Top 10 dropoff neighborhoods

Summarize insights from each graph

Step 5 — Hypothesis Testing (Python)
File: project_sql_result_07.csv
Contains:

start_ts: ride start time

weather_conditions: classified as “Good” or “Bad”

duration_seconds: ride duration

Hypothesis:

Null (H₀): There is no difference in average ride duration from the Loop to O’Hare on rainy vs. non-rainy Saturdays.

Alternative (H₁): Average ride duration differs between rainy and non-rainy Saturdays.

Choose an appropriate statistical test (e.g., Mann-Whitney U test or t-test, depending on distribution) and set a significance level (commonly α = 0.05).

Key Tools Used
SQL (PostgreSQL-style queries)

Python (Pandas, Matplotlib, Seaborn, SciPy)

Jupyter Notebook
