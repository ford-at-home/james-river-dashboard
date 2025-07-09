# james-river-dashboard
One stop shop for James River quality

🧠 System Overview
Goal: Pull in all relevant datasets (E. coli, river gauge, rainfall, temperature, AQI, CSO alerts, algal blooms, etc.), normalize them, and store them in a queryable and dashboard-friendly format (likely JSON or time-series tables). The frontend dashboard will hit a single, fast API to get fresh values or historical trends.

☁️ Cloud Architecture (AWS-based, serverless, modular)
1. Ingestion Layer (Lambda Functions per Source)
Each data source gets its own dedicated Lambda function, scheduled via EventBridge (cron) based on how often the source updates.

Data Source	Method	Schedule	Notes
USGS (gauge height, flow, temp)	API (REST)	every 15 min	JSON from USGS NWIS
NOAA/NWS river forecast & alerts	API (REST)	hourly	NWS AHPS & weather.gov
JRA James River Watch (E. coli)	Scraper/API(?)	weekly (Fri AM)	HTML scrape unless API found
VDH Algal Bloom Advisories	Scraper/ArcGIS	daily	Optional: ArcGIS REST
Richmond CSO Map	Scraper/ArcGIS	hourly	Look for underlying data API
VDH Recreational Advisories	RSS/HTML	daily	Manual override if needed
AirNow (AQI)	API (keyed)	hourly	ozone + PM2.5 for Richmond
NOAA (Weather + Rainfall)	API (REST)	hourly	weather.gov gridpoint
DWR Access Points (GIS)	Static CSV/GIS	monthly	Reimport if infrastructure changes

→ Each Lambda:

Pulls, parses, and transforms the raw data

Pushes clean JSON to S3 or writes to a database (below)

Use Step Functions for sources that need multiple stages (e.g., CSO: scrape + geoprocess + summary)

2. Storage Layer
Two key pieces:

A. Time-Series / Event Data → Timestream (or DynamoDB)
For anything historical and numeric:

river_level, flow_rate, temperature, AQI, precipitation, etc.

Store with timestamp, source, location, and value

B. Geo & Metadata → S3 (JSON or GeoJSON)
River access points

Algal bloom alerts

Public health advisories

Latest CSO map events (geojson polygons or point events)

Store as {type}/{YYYY-MM-DD}.json

Optionally, ingest into OpenSearch for fast spatial queries.

3. Normalization & Aggregation
Every time new data is ingested, trigger a post-processing Lambda that:

Joins relevant sources (e.g. water level + rainfall + forecast = condition summary)

Generates simplified dashboard bundles:

current_conditions.json (e.g. summary for each access point)

trend_data.json (past 7/30 days of key metrics)

alerts.json (active CSO, HAB, flood, weather alerts)

Stored in S3 for versioning and CDN serving. Also optionally cache in Dynamo.

4. API Layer
Use API Gateway + Lambda to serve frontend requests:

GET /current → returns current conditions per site

GET /site/:id/history → returns time series (water level, temp, etc.)

GET /alerts → returns list of current advisory/warning alerts

GET /access-points → returns GeoJSON for launch sites

Optional: restrict by site or data type.

5. Frontend Dashboard (Public Web App)
Host static React/Vite site on:

S3 + CloudFront (with a CDN cache for /current.json, etc.)

Pulls from the API or directly from S3 if data is versioned there

Uses:

Mapbox or Leaflet for map

Recharts or Chart.js for trends

Real-time alert banners (from alerts.json)

Filters: time range, site, conditions

Mobile-first design

✅ Extra Features (Optional)
🔔 Alerting: Use SNS or email triggers when bacteria levels exceed safe thresholds or flooding is forecast.

🧪 Data QA: Run tests on ingestion (e.g. flag anomalous values or missing fields).

🗂️ Historical Archive: Store daily snapshots of current_conditions and alerts for auditing.

📈 Admin Interface: A simple internal tool to see ingestion status, trigger manual pulls, or override advisories.

🔧 Stack Summary
Layer	Tool/Service
Scheduler	EventBridge (cron)
Ingestion	AWS Lambda (Python)
Processing	AWS Lambda + Step Functions
Storage	S3 (GeoJSON/JSON), Timestream/DynamoDB
API	API Gateway + Lambda
Frontend	React (Vite) + S3 + CloudFront
Alerts	SNS (optional)
Auth (admin)	Cognito or GitHub login (optional)

