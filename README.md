# Data-Collections-and-Storage-SQL-.ipynb

# 🚖 Zuber Ride-Sharing Analysis

## 📝 Project Description

You're working as an analyst for **Zuber**, a new ride-sharing company that's launching in Chicago. Your task is to find patterns in the available data to help understand passenger preferences and how external factors, like weather, affect ride frequency.

You’ll analyze ride data from competitors and test a hypothesis about the impact of weather on ride duration using SQL and Python.

---

## 🗃️ Description of the Data

The database consists of four main tables:

### `neighborhoods` — Chicago neighborhoods
- `name`: name of the neighborhood
- `neighborhood_id`: neighborhood code

### `cabs` — taxi company vehicles
- `cab_id`: vehicle code
- `vehicle_id`: technical ID of the vehicle
- `company_name`: name of the company

### `trips` — ride data
- `trip_id`: ride code
- `cab_id`: code of the vehicle operating the ride
- `start_ts`: ride start time (rounded to the hour)
- `end_ts`: ride end time (rounded to the hour)
- `duration_seconds`: ride duration in seconds
- `distance_miles`: ride distance in miles
- `pickup_location_id`: pickup neighborhood code
- `dropoff_location_id`: dropoff neighborhood code

### `weather_records` — hourly weather info
- `record_id`: weather record code
- `ts`: timestamp (rounded to the hour)
- `temperature`: recorded temperature
- `description`: weather conditions (e.g. `"light rain"`, `"clear sky"`)

> **Note**: There is no direct key between `trips` and `weather_records`. To link them, use `trips.start_ts` and `weather_records.ts`.

---

## ✅ Project Steps

### Step 1: Parse Weather Data
- Extract weather data for November 2017 from:  
  `https://practicum-content.s3.us-west-1.amazonaws.com/data-analyst-eng/moved_chicago_weather_2017.html`

---

### Step 2: Exploratory SQL Analysis

- Find the number of taxi rides per company for **November 15–16, 2017**  
  - Field name: `trips_amount`, sorted by trip count (descending)

- Find rides for companies with names containing **"Yellow"** or **"Blue"** for **November 1–7, 2017**  
  - Field name: `trips_amount`, grouped by `company_name`

- Compare top 2 companies ("Flash Cab", "Taxi Affiliation Services") vs. others  
  - Create group `"Other"` for all remaining companies  
  - Field name: `company`, sorted by `trips_amount`

---

### Step 3: SQL-Based Hypothesis Prep

- Get neighborhood IDs for:
  - `"Loop"` → `neighborhood_id: 50`
  - `"O'Hare International Airport"` → `neighborhood_id: 63`

- Create a `weather_conditions` field:
  - `"Bad"` → if `description` includes `"rain"` or `"storm"`
  - `"Good"` → all other conditions

- Filter trips:
  - From Loop (50) to O'Hare (63)
  - Only **Saturdays**
  - Join with weather data by hour
  - Only include trips with weather data
  - Output fields: `start_ts`, `weather_conditions`, `duration_seconds`

---

### Step 4: Data Analysis in Python

You'll receive the following CSV files:

#### `project_sql_result_01.csv`
- Fields: `company_name`, `trips_amount`  
- Rides per company for Nov 15–16

#### `project_sql_result_04.csv`
- Fields: `dropoff_location_name`, `average_trips`  
- Avg rides ending in each neighborhood (November)

#### Tasks:
- Import and inspect the data
- Check data types
- Identify top 10 neighborhoods by drop-offs
- Create visuals:
  - Taxi companies vs. rides
  - Top 10 neighborhoods by drop-offs
- Draw conclusions for each graph

---

### Step 5: Hypothesis Testing (Python)

#### File: `project_sql_result_07.csv`
- `start_ts`: ride start time
- `weather_conditions`: “Good” or “Bad”
- `duration_seconds`: ride duration

#### Hypothesis:
- **H₀ (Null):** Average duration of rides from Loop to O'Hare **does not differ** between rainy and non-rainy Saturdays.
- **H₁ (Alt):** Average duration of rides **does differ** between rainy and non-rainy Saturdays.

#### Instructions:
- Choose significance level (α), e.g., `0.05`
- Use an appropriate statistical test (e.g., t-test or Mann-Whitney U)
- Justify your test selection
- Interpret the result and conclusion

---

## 🧰 Tools & Technologies

- SQL (PostgreSQL syntax)
- Python (Pandas, Matplotlib, Seaborn, SciPy)
- Jupyter Notebook

---

## 📌 Deliverables

- SQL queries for each step
- Python notebook with:
  - Data cleaning & validation
  - Visual analysis
  - Hypothesis testing
  - Clear, well-commented code
  - Business conclusions

