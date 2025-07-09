Datasets for a James River Water Conditions & Health Dashboard
To build a public-facing dashboard for paddlers on the James River (Richmond, VA), the following key datasets are needed. Each dataset listing below includes its name/description, source organization (with links), spatial/temporal coverage and update frequency, data format and access method, and notes on usability (licensing, reliability, etc.). Federal, state, and local sources are included, with an emphasis on real-time or frequently updated information (while also noting historical data for trends):
James River Watch – Volunteer Water Quality Monitoring (Bacteria & More)
Source: James River Association (local NGO) – Link: [James River Watch]
news.vcu.edu
thejamesriver.org
. This program enlists citizen volunteers to collect water quality data at popular river recreation spots from the upper James to the Richmond area. It focuses on E. coli bacteria levels as an indicator of health risk, along with basic parameters like water temperature and turbidity
news.vcu.edu
. Volunteers take samples weekly each summer (Memorial Day through Labor Day), and results are posted every Friday on an interactive map
thejamesriver.org
.
Coverage & Update Frequency: ~31 monitoring sites basin-wide (including Richmond city locations), sampled weekly in summer (seasonal program)
thejamesriver.org
. Data represent recent bacteria counts (E. coli CFU/100mL) and field measurements (temp, turbidity, etc.) at each site. Because sampling is weekly, data are not real-time; they provide a Friday “snapshot” to gauge weekend conditions
thejamesriver.org
. (Historical data since 2013 are available for trend analysis of summer bacteria levels
thejamesriver.org
.)
Format & Access: Results are displayed on JRA’s James River Watch web map (with color-coded indicators for safe/unsafe bacteria levels)
thejamesriver.org
. There is no open API, but data can be accessed via the website or by contacting JRA. JRA’s map also integrates other layers (river gauges, weather alerts) for context. The program is supported by Virginia DEQ’s citizen monitoring program
thejamesriver.org
, so data may also feed into state water quality databases.
Usability Notes: Licensing: Data is public; JRA provides it as a community service (with attribution)
thejamesriver.org
. Reliability: Bacteria results are lab-analyzed and quality-controlled by JRA staff/volunteers. However, since conditions can change rapidly after rainfall, JRA includes a disclaimer that bacterial conditions may degrade between weekly samples
thejamesriver.org
. The dashboard should warn users (e.g. “rainfall may cause higher bacteria before next sample”). Overall, this dataset is crucial for public health advisories about swimming/paddling safety on the James, and it is the primary source of E. coli data for the river in Richmond
news.vcu.edu
.
Virginia DEQ Water Quality Data (Pollutants & Historical Trends)
Source: Virginia Department of Environmental Quality (state) – Link: [VA DEQ Water Quality]. DEQ conducts periodic water quality monitoring of rivers (e.g. nutrients, dissolved oxygen, chemical contaminants) and publishes Integrated Water Quality reports and data. While not real-time, these datasets provide historical and seasonal context on pollutants in the James River (e.g. nitrogen, phosphorus, sediment, or toxic substances) and overall river health. Much of this data is available via the EPA/USGS Water Quality Portal (a federal data hub) for stations on the James.
Coverage & Update Frequency: DEQ’s monitoring stations on the James (including near Richmond) are sampled monthly or quarterly for various water chemistry parameters. Data spans decades in some cases, supporting trend analysis (e.g. improvement in nutrient levels or identification of impaired segments). Updates occur as new lab results are added (not real-time; often with weeks of lag). The spatial coverage includes main stem James and tributaries. For example, DEQ/USGS have collected thousands of samples in the James near Richmond for parameters like nutrients and metals
nwis.waterdata.usgs.gov
.
Format & Access: Historical water quality data can be retrieved through the Water Quality Portal (REST API or CSV download). The Portal aggregates DEQ’s data (as well as EPA and USGS water-quality sampling) – one can query by geographic area or station ID and obtain results in CSV or JSON. DEQ also provides summary data in reports (PDF/Excel) via its website. There is an ArcGIS Open Data Hub for DEQ, which includes GIS layers of water quality assessment results and stations.
Usability Notes: Licensing: Public domain (government data). Reliability: DEQ data is high quality (laboratory analyzed) and suitable for historical trend visualizations or understanding pollutant levels (e.g. to show that a segment meets water quality standards or has impairments). However, because it’s not in real-time, this dataset is more for context (e.g. showing long-term river health or pollutant load reductions) rather than day-to-day advisories. It complements the real-time bacterial data by covering a broader array of pollutants. For a paddler dashboard, DEQ’s data might be used in background info or a “River Health” section rather than for immediate conditions.
USGS Real-Time River Gauge – James River at Richmond (Westham)
Source: U.S. Geological Survey (federal) – Link: [USGS Gauge 02037500]
howsthejamesrva.com
. The USGS operates a stream gage “James River near Richmond (Westham)” which provides real-time river conditions: gage height (water level in feet above a reference) and discharge (flow in cubic feet per second). This is the primary gauge for Richmond’s James River, located upstream of the city (near Westham). It’s critical for tracking river height, flow, and flood stage in real time
thejamesriver.org
.
Coverage & Update Frequency: The Westham gauge records data continuously, updating every 15–30 minutes (with data transmitted hourly in many cases). It covers a drainage area of ~6,753 sq mi (the James and its tributaries above Richmond)
waterdata.usgs.gov
. Data is available historically from 1934 to present for flow
nwis.waterdata.usgs.gov
, which means the dashboard can show long-term flow averages, records, and trend graphs. Flood stage benchmarks are defined by the National Weather Service for this gauge (e.g. minor flood at 12 feet)
weatherusa.net
. The gauge is maintained in cooperation with VA DEQ
waterdata.usgs.gov
, ensuring reliability.
Format & Access: USGS provides an open Water Services API
waterdata.usgs.gov
 to query gauge data in formats like JSON, XML, or CSV. One can request real-time or recent time-series for specific parameters (00060 = discharge, 00065 = gage height). Additionally, USGS offers a web interface and embeddable graphs. Data can also be pulled into the dashboard via the USGS National Water Dashboard or the WaterAlert system for thresholds. The gauge ID is 02037500, which is used in API calls.
Usability Notes: Licensing: USGS data are public domain (free to use with attribution). Reliability: Extremely high – this is an official, calibrated gauge. It updates in near real-time and is the backbone for river condition warnings in Richmond. For the dashboard, this dataset will power features like current river level, flow rate, and trend charts, as well as any high-water alerts. Because historical data is extensive, it’s useful for putting current conditions in context (e.g. comparing today’s flow to long-term averages
nwis.waterdata.usgs.gov
). The data is highly reliable; however, note that very rapid changes (e.g. flash floods) might have a ~1-hour reporting delay. This gauge does not measure water temperature currently (it did historically), so a separate data source is needed for temperature.
NOAA/NWS River Forecast & Flood Stages – James River at Richmond
Source: NOAA National Weather Service (Middle Atlantic River Forecast Center) – Link: [NWS AHPS]. The NWS uses the USGS gauge above in its Advanced Hydrologic Prediction Service (AHPS) to provide river flood forecasts. This dataset includes defined flood stage levels and forecasted river levels for the James at Richmond-Westham up to 3 days out
water.noaa.gov
. It is essential for safety: paddlers can know if the river is expected to rise to dangerous levels even if not yet there.
Coverage & Update Frequency: Forecasts cover the James River at Richmond Westham gauge location. The NWS issues updates at least twice daily or more often during flood events. Forecasts typically project river levels for the next 72 hours, factoring in recent and expected rainfall
water.noaa.gov
. The dataset also defines flood categories: e.g. Action Stage (~ Richmond caution), Minor Flood (12 ft at Westham), Moderate, Major flood levels, etc., each with associated impacts
thejamesriver.org
weatherusa.net
. These categories can be displayed on the dashboard to interpret current gauge readings (e.g. “No Flooding” vs “Minor Flooding” status).
Format & Access: NOAA’s AHPS data can be accessed via the AHPS XML/JSON feed or REST API (the NWS API). There are RSS/ATOM feeds for river observations and forecasts by gauge. Additionally, NWS provides a web interface with graphs. The forecast data points (time-series of predicted stage) can be ingested in JSON via the NWS API (api.weather.gov) under the “/alerts” or “/stations” endpoints, or via NOAA’s National Water Model. Many third-party weather services (and NOAA’s own websites) also publish this data in machine-readable format.
Usability Notes: Licensing: U.S. Government data (open use). Reliability: Forecasts are generated by hydrologists and models; they are generally reliable within 1–3 days but have uncertainty (especially for large rain forecasts). For the dashboard, showing current NWS status (“River at 7 ft and rising, minor flood expected tomorrow”) is very useful for planning. The flood stage thresholds themselves are static and well-established
weatherusa.net
. Including these will allow color-coded warnings (e.g. NWS flood warnings) on the dashboard. This dataset ensures timely warnings about flooding or unsafe high flows beyond the raw USGS observations.
USGS Water Temperature – James River at Cartersville Gauge
Source: U.S. Geological Survey – Link: [USGS Gauge 02035000]. Upstream of Richmond, the James River at Cartersville gauge (Goochland County) measures water temperature in addition to flow. This is a useful proxy for Richmond’s water temperature, as there is no real-time temp sensor at the Richmond gauge. Cartersville’s temperature readings can inform paddlers of current water temperature (important for safety, hypothermia risk, and ecological context).
Coverage & Update Frequency: The Cartersville gauge records water temp (°C) continuously, updating multiple times per hour (typically 15–30 min intervals) in real-time
waterdata.usgs.gov
. It covers the James ~40 miles upstream of Richmond. In summer, temperature differences are minor; in cooler months there may be a few degrees difference by the time water reaches Richmond, but Cartersville gives a ballpark. This gauge’s temperature record goes back to 2007 (and older intermittent periods)
nwis.waterdata.usgs.gov
, enabling comparisons of seasonal trends or heat waves.
Format & Access: Like Westham, Cartersville’s data is available via the USGS Water Services API in JSON/XML/CSV. The parameter code is 00010 for water temperature. For example, an API call can retrieve the latest value (e.g. 28.1°C on July 7, 2025
waterdata.usgs.gov
). Data is also viewable on USGS’s site or the National Water Dashboard. The gauge ID is 02035000.
Usability Notes: Licensing: Public domain USGS data. Reliability: High – readings are from a calibrated in-stream sensor. Occasional outages can occur due to sensor fouling or maintenance, but generally the data is robust. Displaying water temperature on the dashboard is valuable for paddlers (e.g. to decide on wetsuits or note when combined air+water temp is below 100°F, a hypothermia risk guideline
thejamesriver.org
). The Cartersville data was used by local projects (like “How’s the James”) to feed Richmond conditions
howsthejamesrva.com
, so it’s a trusted source. If finer location resolution is needed, one might incorporate any local temperature spot-readings (e.g. volunteers measure it during weekly bacteria sampling
news.vcu.edu
), but USGS provides continuous coverage.
VDH Harmful Algal Bloom (HAB) Alerts
Source: Virginia Department of Health – Link: [VDH HAB Dashboard]
vdh.virginia.gov
vdh.virginia.gov
. VDH operates a Harmful Algal Bloom surveillance program and dashboard for Virginia water bodies. When algal blooms (often cyanobacteria) occur and pose a risk to human or animal health, VDH issues advisories or closures. The HAB dashboard provides data on confirmed blooms: location, date, and status of any advisories (e.g. “James River – near Wilcox Landing: sample on 6/10/2025” and whether toxins were detected)
vdh.virginia.gov
. This is important for paddlers because certain algae can cause skin rashes or other illnesses on contact.
Coverage & Update Frequency: Statewide – includes James River sections (more common in slow-moving tidal sections or backwaters). In the Richmond area, blooms are relatively rare but not impossible (e.g. downstream tidal James in summer). The dashboard is updated whenever a HAB is reported and confirmed, mostly in warmer months. There is no fixed schedule; updates occur as investigations happen. Each entry typically includes a date/time of sample and the current advisory status (ongoing or lifted). VDH also provides a map interface with bloom markers.
Format & Access: The HAB dashboard is available as a web map and table on VDH’s site. The data behind it might be accessible via an ArcGIS REST service or by contacting VDH. (For example, VDH’s site shows entries like “James River – near Herring Creek: 6/10/2025 11:30 AM”
vdh.virginia.gov
). If automating, one could scrape the dashboard or use VDH’s open data (if provided). Alternatively, VDH publishes news releases for major HAB events which could be parsed.
Usability Notes: Licensing: Public health data – free to use. Reliability: VDH confirmations of HABs are authoritative. However, not all algal blooms get reported immediately; there could be a lag from observation to advisory. For the dashboard, including this dataset means showing active advisories (e.g. “No swimming – HAB at XYZ location”). If no current blooms in the Richmond area, the dashboard can simply note “No harmful algal bloom advisories at this time” or omit it. This data is critical if a HAB occurs since it directly impacts recreational safety. (Debris alerts, by contrast, are less formal; see Public Advisories below for debris-related warnings.)
Richmond Combined Sewer Overflow (CSO) Discharge Data
Source: City of Richmond Department of Public Utilities (local) – Link: [Richmond CSO Map]
thejamesriver.org
. Richmond’s older urban core has a combined sewer system, which can overflow raw sewage into the James River during heavy rains. The city provides a real-time CSO notification map (via a system called BLU-X by EmNet) that shows which outfall locations have recently discharged. This is a crucial dataset for bacteria/health advisories, as CSO events greatly elevate E. coli in the river. JRA explicitly directs users to this map after rain events
thejamesriver.org
.
Coverage & Update Frequency: All 25 CSO outfalls in Richmond are monitored
rva.gov
. The map updates in real-time (or near-real-time) whenever an overflow occurs, highlighting the outfall and presumably showing the time of the last event. During dry weather there are no overflows; after storms, multiple outfalls may activate. The city also publishes monthly CSO reports (with aggregated data on overflow volumes)
rva.gov
, but the map is for immediate notification.
Format & Access: The primary access is through an interactive web map (ArcGIS/JavaScript based). While it doesn’t have an openly documented API, it’s possible the map pulls from an underlying data feed (perhaps JSON or ArcGIS Feature Service). Alternatively, scraping or manual data extraction can be done. The city’s RVA311/RVAH2O website provides a StoryMap and possibly CSV downloads of overflow events. The monthly PDFs are available on the city site
rva.gov
 which list dates of each overflow, but for a dashboard we prefer immediate data.
Usability Notes: Licensing: City data, presumably open for public use (the map is public). Reliability: The system is maintained by the city’s contractors; it should be fairly reliable in detecting overflows. For the dashboard, this dataset can trigger “no-go” advisories: e.g. if any CSO outfall in the Richmond stretch has overflowed in the last 48 hours, a warning could be displayed (“Recent sewer overflow – avoid contact with water”)
thejamesriver.org
. It essentially serves as a public health warning for contamination. Because the map itself requires user interaction, integrating it might involve pulling a simplified status (e.g. number of active overflows). This data is highly relevant after storms and complements rainfall data and bacteria monitoring.
VDH Recreational Water Advisories (Sewage Spills, etc.)
Source: Virginia Department of Health / Local Health District – Link: [VDH News Releases]
vdh.virginia.gov
. Beyond the routine CSO events, occasionally major pollution incidents occur (e.g. a sewer line break or chemical spill) that prompt VDH to issue formal recreational water advisories or closures. An example is the July 2024 advisory where a ruptured sewer pipe caused VDH to close the James River from Richmond’s Manchester Bridge down to Henrico’s Osborne Landing
vdh.virginia.gov
. Such advisories are critical for paddler safety and need to be reflected on the dashboard.
Coverage & Update Frequency: These advisories are event-based and relatively rare. They cover specific river stretches and are active until water quality returns to safe levels. VDH and DEQ coordinate monitoring during the event
vdh.virginia.gov
. Updates might come through press releases and the Swim Healthy VA website. While not a regularly “updating dataset,” it’s important to include the capability to display current advisories (if any).
Format & Access: VDH typically announces advisories via press releases (HTML pages or PDFs) and sometimes updates their website with maps
vdh.virginia.gov
. The data (which segment is affected, dates, reason) would likely need to be input manually or via an RSS feed of VDH news. Another approach is to subscribe to VDH’s alerts. There is no structured API for these sporadic events, so human curation is involved.
Usability Notes: Licensing: Public info. Reliability: The information is official and reliable when issued. The challenge is timely integration – someone must be aware of new advisories. For the dashboard, one could incorporate an “Advisory Alerts” banner that can be quickly updated. Fortunately, these events (like a large sewage spill) are often covered in local media as well. Including this ensures the dashboard isn’t giving an “all clear” when an official warning is in effect. (In summary: this dataset is essentially an alert feed for extraordinary hazards like a major pollution release or flooding that triggers a health warning.)
EPA AirNow – Air Quality Index (AQI) for Richmond Area
Source: U.S. EPA AirNow program (federal, in partnership with VA DEQ) – Link: [AirNow API]
airnowapi.org
. This dataset provides air quality conditions – specifically the Air Quality Index (AQI) and pollutant concentrations (ozone and PM₂.₅ are most relevant) for the Richmond region. Since paddlers are outdoors and exerting themselves, air pollution (smog, smoke) can be a concern. The AirNow system aggregates data from DEQ’s monitoring stations and provides both current AQI values and forecasts.
Coverage & Update Frequency: Richmond City/central Virginia area. The data is updated hourly for current conditions (based on continuous monitors)
airnowapi.org
. Forecasts for today and tomorrow’s AQI are updated daily (usually in the afternoon for the next day). The AQI covers ozone (in summer) and particulate matter (year-round) primarily, reported on the 0–500 scale (with categories Good/Moderate/Unhealthy, etc.). For example, AirNow might report “AQI 55 (Moderate) due to ozone” on a hot summer afternoon, along with an ozone forecast for the next day.
Format & Access: AirNow provides a public API (JSON/XML). Developers can obtain an API key (free) and query current observations by area (or by station) and forecasts by city/zip code. Data can also be fetched as CSV. Another source is VA DEQ’s own air quality page which embeds AirNow info
deq.virginia.gov
deq.virginia.gov
. The EPA also offers an “AirNow widgets” toolkit and map layers. For the dashboard, using the AirNow API by zip code (e.g. 23219 for Richmond) is convenient.
Usability Notes: Licensing: Free for public use (with courtesy attribution to AirNow/DEQ). Reliability: Very good – AirNow is the official source for air quality and health messages (like Code Orange ozone alerts). It receives data from calibrated monitors in Richmond. One consideration: ozone is typically higher in the afternoon, whereas many paddlers go out in mornings or evenings, so showing current and forecast conditions allows users to plan. The dashboard can display an AQI number and category (and perhaps pollutant-specific info: e.g. high ozone vs wildfire smoke). If the AQI is in an unhealthy range, it’s effectively a health advisory for sensitive groups. Including this dataset broadens the dashboard from water-only to overall environmental conditions that affect outdoor recreation.
NOAA/NWS Weather and Rainfall Data
Source: National Weather Service / NOAA (federal) – Link: [NWS API]
weather.gov
. Weather has a direct impact on river safety (storms, lightning, flooding rainfall) and on water quality (rain can wash pollution into the river). Key data from NWS includes current weather observations, forecasts, and precipitation data. Specifically, a James River dashboard should incorporate: recent rainfall totals, weather forecasts (especially storm warnings), and possibly radar/precip maps. The NWS provides comprehensive data through an API.
Coverage & Update Frequency: Local weather for Richmond area. Current conditions (temperature, humidity, etc.) update hourly from airport stations; radar and precipitation estimates update every 5-15 minutes; forecasts update several times a day. For rainfall, one can look at 24-hour precipitation totals at Richmond or use multi-sensor estimates for the watershed (to see where heavy rain might cause river rises). The NWS also issues weather alerts (severe thunderstorm warnings, flood advisories, etc.) that should be included for paddler safety
thejamesriver.org
.
Format & Access: The NWS REST API (api.weather.gov) provides forecasts in JSON for specific grid points (latitude/longitude) and current conditions from nearby stations
weather.gov
. It also provides active alerts in GeoJSON/JSON format (filterable by area or zone). For rainfall, NOAA’s Observed Precipitation maps can be accessed via web services, and local rain gauge data may be available through NOAA’s hydrology APIs. Data like river basin rainfall could also come from USGS if they have rain gauges, but NOAA’s data is more extensive. The format can be JSON or XML; for example, one could parse the forecast to display “Today: Scattered thunderstorms, high 85°F” on the dashboard.
Usability Notes: Licensing: U.S. government data (open). Reliability: NWS data is the authoritative source for weather. To avoid clutter, the dashboard might show a brief forecast and any active weather hazard alerts (lightning is a major risk for paddlers, as are high winds). Also, showing recent rainfall (e.g. “1.2 inches of rain in the past 24h in Richmond”) helps users infer water quality – heavy rain often correlates with high E. coli and debris flows
thejamesriver.org
thejamesriver.org
. The dashboard may integrate NWS alerts to automatically display warnings (e.g. a Flood Advisory or Thunderstorm Warning). In summary, this dataset ensures the dashboard is timely about weather-driven safety issues. It updates frequently and can be trusted; however, integration requires using the API (which the NWS supports with good documentation).
Public River Access Points Map (GIS)
Source: Virginia DWR (Dept. of Wildlife Resources) & James River Association – Links: [DWR Access Data], [James River Explorer]
dwr.virginia.gov
thejamesriver.org
. An important informational layer for a paddling dashboard is a map of public access points: boat landings, ramps, canoe launches, etc., along with any notes on facilities or hazards. The Virginia DWR maintains the official inventory of boating access sites statewide (including several on the James in Richmond and surrounding counties)
dwr.virginia.gov
. Additionally, the James River Association’s James River Explorer interactive map compiles river access sites and points of interest in the James River basin
thejamesriver.org
.
Coverage & Update Frequency: Spatial coverage: All major access points on the James from the headwaters to the tidal section. For example, around Richmond this includes city parks (Huguenot Flatwater, Pony Pasture), boat ramps (Ancarrow’s Landing
dwr.virginia.gov
, Osborne Landing, Deep Bottom, etc.), and outfitters. DWR’s list is comprehensive and updated whenever a new ramp is added or status changes (infrequently). JRA’s Explorer map is updated occasionally with new points of interest or corrections. Essentially, this is static GIS data that changes only with new facilities or as details are refined.
Format & Access: The DWR boating access data is available on their website as an interactive table (with coordinates)
dwr.virginia.gov
. While not directly offered as a downloadable file on that page, one can parse the HTML or contact DWR for a GIS dataset. DWR likely has an internal shapefile or GeoJSON for all access points (with fields like name, type of ramp, latitude/longitude, handicap accessibility, etc.). The snippet above, for instance, lists Ancarrow’s Landing in Richmond with coordinates and a notice
dwr.virginia.gov
. JRA’s James River Explorer is an ArcGIS Online map
thejamesriver.org
 – it likely has a REST endpoint for the data layers (river access sites, campsites, etc.). JRA provided that map as a public resource, so one could use the ArcGIS REST API to fetch those points if needed.
Usability Notes: Licensing: DWR data is public information (boating access points), and JRA’s data is also public-facing (with a disclaimer of no warranty)
thejamesriver.org
. For the dashboard, integrating this means an interactive map where users can click on launches and see names and maybe any safety notes (e.g. “Deep Bottom – caution: strong currents at ramp”). Reliability: These locations are well-known; the data quality is good. JRA’s compilation might have additional sites like unofficial launches or parks. It’s wise to use the official DWR data for accuracy on coordinates and then augment with any local knowledge. Update frequency is low (changes only when infrastructure changes), so a one-time import with periodic checks is sufficient. Including this dataset greatly enhances user experience, allowing paddlers to plan where to put in/take out and to be aware of what amenities or warnings each access point has (some sources include notes like “mud and debris may be present on ramp”
dwr.virginia.gov
). This fulfills the dashboard’s goal to include maps of public access, paddling zones, and safety notes.
Each of the above datasets contributes to a comprehensive picture of James River conditions. In summary, real-time data from USGS and NOAA cover the physical river and weather conditions, state and local data (JRA, VDH, DEQ, City) cover water quality and health advisories, and maps/GIS data provide the recreational context. By combining these, a paddler dashboard can display current water quality (E. coli counts, algal bloom warnings), real-time river level/flow and temperature, alert users to any pollution or flood advisories, show air quality and weather hazards, and help paddlers locate safe entry/exit points – all using publicly available datasets updated at appropriate intervals. This ensures paddlers can “know before you go” with trustworthy information
thejamesriver.org
thejamesriver.org
. Sources: James River Association (James River Watch)
news.vcu.edu
thejamesriver.org
; U.S. Geological Survey (NWIS)
nwis.waterdata.usgs.gov
howsthejamesrva.com
; NOAA/NWS (AHPS and weather API)
weatherusa.net
weather.gov
; Virginia Dept. of Health (HAB Dashboard, advisories)
vdh.virginia.gov
vdh.virginia.gov
; City of Richmond (DPU CSO data)
thejamesriver.org
; Virginia DEQ & EPA (water quality, air quality via AirNow)
airnowapi.org
; Virginia DWR (boating access)
dwr.virginia.gov
; James River Explorer Map
thejamesriver.org
. Each of these data sources is publicly available and suitable for a real-time environmental health dashboard for the James River.
