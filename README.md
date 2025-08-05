Issues In Data Sets:
1. No Date column present.
  Solution: --
  Create Separate Date Column For DEPARTURE / ARRIVAL

2. Departure and scheduled Time column is completely messed up.
  Solution: --
  Create separate Date/ Time column for DEPARTURE / ARRIVAL

3. No time bucked column present.
  Solution: --
  Create Time Bucked forDEPARTURE_TIME/ ARRIVAL_TIME
  Extract Hours From DEPARTURE_TIME / ARRIVAL_TIME for
  DEPARTURE_TIME_BUCKET and ARRIVAL_TIME_BUCKET Column.

4. The Flight Data set is too big, nearly 560MB CSV file, I tried for days to upload it to the MySQL table but it won’t.
Also faced lost connection to MySQL server during query: Because of null values changed the datatypes to varchar

(Error Code: 1366. Incorrect integer value: '' for column 'ARRIVAL_TIME' at row 33)
My sql server time out: Error Code: 2013.
  Solution: --
  I switched to PostGreSQL.

Other Possible Solution for better analysis:
  Data Base Normalisation (2nf) creating a separate data table for cancelled, and delayed flights , but no flight Id present in the dataset.
  Python-Pandas EDA and machine learning implementation can make the analysis better.


Problem Statement:
  Flight delays and cancellations are significant issues in the U.S. aviation industry, impacting passengers, airlines, and the economy. Your task is to perform an in-depth analysis of historical flight data to identify key drivers of these disruptions, assess performance, and propose actionable insights.
  Business Use Cases:

The project's solution can be implemented in various scenarios, including:
  ● Analyzing the primary causes and patterns of flight delays and cancellations for strategic operational adjustments.
  ● Benchmarking the on-time performance, delay severity, and cancellation rates of different airlines for competitive analysis and improvement initiatives.
  ● Evaluating the operational performance of various U.S. airports to identify bottlenecks and areas for infrastructure or process improvement.
  ● Investigating how factors like time of day, day of week, month, and specific routes affect flight operations to optimize scheduling and resource allocation.
  ● Providing data-driven recommendations to stakeholders (airlines, airports, regulatory bodies) to enhance passenger experience and operational efficiency.
Approach:

Phase 1: Project Setup & Data Ingestion
  ● Set up your SQL database environment.
  ● Create appropriate table structures for flights, airlines, and airports data. Consider data types carefully.
  ● Import the data from the CSV files into your SQL database.
  ● Perform initial verification (e.g., row counts, sample data review) to ensure data is loaded correctly.
  
Phase 2: Data Cleaning, Preparation & Integration (SQL)
  ● Time/Date Handling: Convert text-based time and date fields (e.g., SCHEDULED_DEPARTURE) into proper datetime formats. This may involve creating new columns. Think about how to combine year, month, day, and HHMM time strings.
  ● Missing Values: Investigate and handle missing values (NULLs) in key columns (e.g., delay columns, cancellation reason). Decide on an appropriate strategy (e.g., replace with 0 where logical, leave as NULL, or flag).

  ● Data Enrichment:
    o Create a more descriptive CANCELLATION_REASON_DESC column based on the CANCELLATION_REASON code.
    o Consider creating a FLIGHT_DATE column for easier time-based analysis.
  ● Integration: Create a unified analytical dataset (e.g., a comprehensive SQL View or a new table) by joining flights data with airlines and airports (for both origin and destination) to include descriptive names and locations.

Phase 3: Exploratory Data Analysis (EDA) & KPI Definition (SQL)
  ● Using SQL queries on your integrated dataset, explore:
    o Overall flight volumes, cancellations (total, by reason), and diversions.
    o Basic statistics for departure and arrival delays (average, median, min, max).
    o The distribution of different types of delays (airline, weather, NAS, etc.).

  ● Define Key Performance Indicators (KPIs) relevant to the project objectives. Examples include:
    o On-Time Performance (OTP) Rate (e.g., flights arriving within 15 minutes of schedule).
    o Average Arrival/Departure Delay (in minutes).
    o Cancellation Rate (%).
    o Percentage contribution of each delay type.

  ● Perform initial aggregations to understand how these KPIs vary by:
    o Airline
    o Origin/Destination Airport
    o Month, Day of Week, Time of Day (requires robust time parsing)

Phase 4: Dashboard Development (Power BI / Tableau)
  ● Connect your BI tool to your SQL database (or the integrated view/table).
  ● Data Modeling in BI Tool:
    o Define necessary relationships if you load multiple tables.
    o Create calculated measures/fields required for your KPIs (e.g., Total Flights, OTP Rate, Avg Delay, Cancellation Rate). You will need to translate your KPI definitions into the BI tool's formula language (DAX for Power BI, or Tableau's functions).
  ● Design and build your interactive dashboard. Consider including pages/views for:
    o Overview: Key KPIs, overall delay/cancellation reasons.
    o Airline Performance: Comparative analysis of airlines against KPIs.
    o Airport Performance: Comparative analysis of airports; consider a map visualization.
    o Temporal Trends: How KPIs change by month, day of week, or hour.
  ● Ensure your dashboard includes filters/slicers for interactive exploration (e.g., by airline, airport, date).

Phase 5: Insight Generation & Recommendation Formulation
  ● Analyze your dashboards and SQL query results deeply. Ask "why?" and "so what?".
  ● Identify significant trends, patterns, anomalies, and correlations.
  ● Based on your findings, formulate 2-3 actionable and data-driven recommendations for potential stakeholders (e.g., airlines, airport authorities). Consider what changes could realistically lead to improvements.
