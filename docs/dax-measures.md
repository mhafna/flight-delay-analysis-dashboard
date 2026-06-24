# DAX Measures

## Date column

```DAX
MonthDate =
DATE(
    airline[year],
    airline[month],
    1
)
```

## Core flight measures

```DAX
Total Flights =
SUM(airline[arr_flights])
```

```DAX
Delayed Flights =
SUM(airline[arr_del15])
```

```DAX
Cancelled Flights =
SUM(airline[arr_cancelled])
```

```DAX
Diverted Flights =
SUM(airline[arr_diverted])
```

```DAX
Total Delay Minutes =
SUM(airline[arr_delay])
```

## Rate and duration measures

```DAX
Arrival Delay Rate =
DIVIDE(
    [Delayed Flights],
    [Total Flights],
    0
)
```

```DAX
Cancellation Rate =
DIVIDE(
    [Cancelled Flights],
    [Total Flights],
    0
)
```

```DAX
Diversion Rate =
DIVIDE(
    [Diverted Flights],
    [Total Flights],
    0
)
```

```DAX
Avg. Delay per Flight (min) =
DIVIDE(
    [Total Delay Minutes],
    [Total Flights],
    0
)
```

```DAX
Avg. Delay per Delayed Flight (min) =
DIVIDE(
    [Total Delay Minutes],
    [Delayed Flights],
    0
)
```

## Delay-cause measures

```DAX
Carrier Delay Minutes =
SUM(airline[carrier_delay])
```

```DAX
Weather Delay Minutes =
SUM(airline[weather_delay])
```

```DAX
NAS Delay Minutes =
SUM(airline[nas_delay])
```

```DAX
Security Delay Minutes =
SUM(airline[security_delay])
```

```DAX
Late Aircraft Delay Minutes =
SUM(airline[late_aircraft_delay])
```

## Disconnected delay-cause table

```DAX
Delay Causes =
DATATABLE(
    "Cause", STRING,
    {
        {"Carrier"},
        {"Weather"},
        {"NAS"},
        {"Security"},
        {"Late Aircraft"}
    }
)
```

No relationship is created between `Delay Causes` and the main `airline` table.

## Dynamic cause measures

```DAX
Delay Minutes by Cause =
SWITCH(
    SELECTEDVALUE('Delay Causes'[Cause]),
    "Carrier", [Carrier Delay Minutes],
    "Weather", [Weather Delay Minutes],
    "NAS", [NAS Delay Minutes],
    "Security", [Security Delay Minutes],
    "Late Aircraft", [Late Aircraft Delay Minutes],
    BLANK()
)
```

```DAX
Total Cause Delay Minutes =
    [Carrier Delay Minutes]
    + [Weather Delay Minutes]
    + [NAS Delay Minutes]
    + [Security Delay Minutes]
    + [Late Aircraft Delay Minutes]
```

```DAX
Delay Cause Share =
DIVIDE(
    [Delay Minutes by Cause],
    [Total Cause Delay Minutes],
    0
)
```

## Formatting

- Flight counts and delay minutes: whole number
- Delay and cancellation rates: percentage with one decimal place
- Average delay measures: decimal number with one decimal place
- `MonthDate`: `MMMM yyyy`
