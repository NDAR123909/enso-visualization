# 75 Years of the Pacific's Mood Swings

An interactive visualization mapping El Niño and La Niña events against river flows in the American West, 1951 to 2026.

**[Live visualization](https://NDAR123909.github.io/enso-visualization/enso-final.html)**

## What it shows

Every few years the tropical Pacific shifts temperature. When the Niño 3.4 region runs warmer than usual for several months, it's El Niño; cooler, La Niña. Both change where rain falls across North America, and you can see it hundreds of miles inland in river discharge.

This charts 75 years of those swings against measured streamflow in three western rivers: the Colorado at Lees Ferry, the Columbia at The Dalles, and the Sacramento at Bend Bridge. Hover any event marker to see how each river responded.

## Data sources

- NOAA PSL ERSSTv5: monthly Niño 3.4 sea surface temperatures
- NCEP/NCAR Reanalysis: atmospheric state variables
- NOAA CPC: oscillation indices (SOI, PDO, MJO)
- USGS National Water Information System: discharge from three river gauges
- NASA OISST v2.1: gridded SST for spatial gradient computation

## Method

Events use the NOAA CPC definition: a Niño 3.4 anomaly of ±0.5°C held for at least five consecutive months against a 1981–2010 baseline. River values are z-scores relative to each gauge's long-term monthly mean. Note that the Colorado and Sacramento run at completely different scales, so raw discharge numbers don't compare across basins.

All five sources were pulled into a PostgreSQL database on Aiven as part of an ETL pipeline I built for ISTA 322. The visualization draws directly from data queried out of that database.

## Stack

D3.js v7, Google Fonts, plain HTML/CSS/JS. There is no build step, the whole thing is one self-contained file.

## Data pipeline

The ETL notebook that builds the underlying database is in `enso_rdb.ipynb`.
It pulls from five federal data sources and loads into PostgreSQL via Aiven.
Note: you'll need to supply your own database and Backblaze credentials. I purposefully 
omitted my credentials to keep them encrypted.

## About

Built by Noah (me), undergraduate in Applied Physics at the University of Arizona. Submitted to the 2026 UA Libraries Data Visualization Challenge.
