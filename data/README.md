# Data

## Source

This dashboard uses the U.S. Department of Transportation, Bureau of Transportation Statistics dataset **Airline On-Time Statistics and Delay Causes**.

Official sources:

- [BTS Airline On-Time Statistics](https://www.bts.gov/browse-statistical-products-and-data/statistical-products/airline-time-statistics)
- [Airline On-Time Performance and Causes of Flight Delays](https://www.bts.gov/explore-topics-and-geography/topics/airline-time-performance-and-causes-flight-delays)

The project covers **2017–2022**.

## Granularity

Each row is a monthly aggregate for a combination of:

- Year
- Month
- Airline
- Airport

It is not an individual-flight dataset.

## Field dictionary

| Field | Description |
|---|---|
| `year` | Reporting year |
| `month` | Reporting month |
| `carrier` | Airline code |
| `carrier_name` | Airline name |
| `airport` | Airport code |
| `airport_name` | Airport name |
| `arr_flights` | Total arriving flights |
| `arr_del15` | Arriving flights delayed by at least 15 minutes |
| `arr_cancelled` | Cancelled flights |
| `arr_diverted` | Diverted flights |
| `arr_delay` | Total arrival-delay minutes |
| `carrier_ct` | Delayed-flight count attributed to the carrier |
| `weather_ct` | Delayed-flight count attributed to weather |
| `nas_ct` | Delayed-flight count attributed to the National Airspace System |
| `security_ct` | Delayed-flight count attributed to security |
| `late_aircraft_ct` | Delayed-flight count attributed to a late-arriving aircraft |
| `carrier_delay` | Carrier-related delay minutes |
| `weather_delay` | Weather-related delay minutes |
| `nas_delay` | National Airspace System delay minutes |
| `security_delay` | Security-related delay minutes |
| `late_aircraft_delay` | Delay minutes caused by a late-arriving aircraft |

## Repository note

The raw source files are not included in this repository. The PBIX file contains the imported model used to produce the dashboard.
