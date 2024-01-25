﻿﻿﻿# Gothenburg Urban Climate data, 2021

Contact: David.Rayner@gu.se
2021-09-15

This dataset contains time-series of hourly climate constructed by merging records from  stations in and near Gothenburg, Sweden. The dataset covers the period 1986-09-01 - 2020-12-31.

## Data sources

The data sources (where data were obtained) are given here. The actual stations are discussed in the next section StationCodes.csv.

- **SMHI** - Swedish Meteorological and Hydrological Institute station observations. 
     Hourly data were downloaded from http://opendata-download-metobs.smhi.se 
     
     Data available under Creative commons Erkännande (CC BY) 4.0 SE
     
     Note that some of the data for SMHI Rantorget (including direct radiation data)  were provided by SMHI in 2013 and are not available for download.
     
- **Miljöförvaltningen**, Göteborgs Stad (City of Gothenburg, Environmental Administration) stations.
     Hourly data for 2015-2020 were downloaded from https://catalog.goteborg.se/catalog/6/datasets/46
     Data available under CC0 1.0 (Public Domain Dedication, No Copyright)
     
     Hourly data for 2009-2014 were kindly provided by Erik Svensson,  Miljöförvaltningen, Göteborgs Stad, and are not available for download.
     
- **University of Gothenburg** - Department of Earth sciences, University of Gothenburg.
     10-minute data downloaded from https://www.gu.se/en/earth-sciences/weather-stations-at-the-department-of-earth-sciences

     No license is specified.

## Data pre-processing

Observations that could be identified as clearly erroneous by visual inspection were replaced by missing  values. No automated quality checks were performed on individual observations.

All dataset have been shifted to UTC+1(Central European Time, ie. Stockholm time without daylight savings) before combining, to the extent this was possible. The observations from Miljöförvaltningen (stations Femman and Lejonet) and University of Gothenburg (station GVC) have been recorded with various time-zone/daylight-savings settings, which unfortunately have not been documented. The historical clock settings for the Miljöförvaltningen and GVC datasets were instead estimated from the time-lag that maximized the absolute-value of the cross-correlation vs the SMHI dataset. The applied clock-correction was then calculated as the average lag over a 20day window centered on each observation, rounded to the nearest whole-hour. Clock offsets were interpolated where SMHI data were missing. The results are described in Visualizations below.

Because the long period of missing SMHI data for relative humidity in 2020 prevented reliable application of the above method, the clock settings for the Miljöförvaltningen relative humidity observations for 2020 were estimated manually by cross-correlation against the SMHI air temperature dataset. This investigation resulted in an an offsetof +1hour being applied to the Miljöförvaltningen RH observations for 2020.

Although global solar radiation for the Miljöförvaltningen stations were not used in the final dataset, clock offsets were calculated for solar radiation to test of the offset-finding algorithm. This is because global solar radiation follows a regular diurnal curve on clear days, allowing the clock offsets relative to UTC+1 to be determined independently, without reference to the SMHI dataset. The clock offsets so determined were consistent with those from the cross-correlation algorithm.

## StationCodes.csv

The file StationCodes.csv lists the stations used, and the codes used in the the `<variable>_code` columns in UCG_merged_2020.csv. 

0 indicates no observation was available for the given hour. 

### Codes and description of weather stations

**1, Miljöförvaltningen Femman** (57.7086106N, 11.9700019E, 62m ASL): Meteorological and air pollution monitoring station run by the City of Gothenburg Environmental Administration, located on the roof of the shopping center Femman in eastern Nordstan. Data were available from 2015.

**2, Miljöförvaltningen Lejonet** (57.6879, 11.9796E, 5m ASL): Meteorological station with both 2m and mast-mounted instruments, run by the City of Gothenburg Environmental Administration, co-located with SMHI Lejonet approx 1.5km northeast of the city center, close to the 17th century fortress *Skansen Lejonet*. Data were available from 2015.

**3, SMHI Chalmers** (57.688N, 11.980E, 84.8m ASL): Solar radiation observation station, run by SMHI as station 71415 (Göteborg Sol), located at Chalmers University of Technology near the building *Linsen*. The only weather variable recorded at *SMHI Chalmers* is global solar radiation.

**4,SMHI Landvetter Flygplats** (57.6764N, 12.2919E, 154m ASL): Weather station operated by SMHI as station 72420 (Landvetter Flygplats), located at Göteborg Landvetter Airport approx 20 km east of Gothenburg. Only MSLP observations were sourced from Landvetter Flygplats.

**5, SMHI Lejonet** (57.6879, 11.9796E, 5m ASL): Currently operated by SMHI as station 71420 (Göteborg), located approx 1.5km northeast of the city center, close to the 17th century fortress *Skansen Lejonet*. **This is the preferred source of meteorological data for the dataset - where data are available for *SMHI Lejonet* they are used in preference to other stations.** 

**6, SMHI Rantorget** (57.708N, 11.992E, 23m ASL). Weather station operated by the Swedish Meteorological and Hydrological Institute (SMHI), located within the city of Gothenburg, approximately 1.5km east of the city center. Data from instruments located at *Rantorget* are included in the station records for SMHI stations 71420 and briefly in 71415. The instruments were located on the roof of the 7-story building *Ellysepalatset* at a height of 23m ASL, with the wind instruments on a mast a further 10m above roof-height. Global- and diffuse solar radiation were measured with a Kipp and Zonen pyranometer; direct solar radiation recorded with a pyrheliometer. Non-solar radiation instruments were moved to the *Lejonet* site during a break in recording 1998-05-31 and 1999-03-01.  Recording of diffuse and direct solar radiation apparently ceased in 2006, and recording of global solar radiation ceased in 2011.

**7, SMHI Säve** (57.7786N, 11.8824E, 20m ASL): Weather station operated by SMHI as station 71470 (Säve) for pressure measuremebt, located at Gothenburg City Airport, approx 10km northwest of the city center. Closed 2006. Only MSLP observations were sourced from Säve.

**8, SMHI Vinga A** (57.6322N, 11.6048E, 18.2m ASL): Weather station operated by SMHI as station 71380 (Vinga A), located on an island in the Gothenburg Archipelago approx 18km west of Gothenburg. Only MSLP observations were sourced from  Vinga A.

**9, University of Gothenburg, GVC.** (57.6890N, 11.9669E, 75m ASL): Operational weather station run by the University of Gothenburg, located on the roof of the 3-story building *Geovetarcentrum*, located approximately 2km south of the city center. Wind measurements taken on a 5m mast. A description of the instrumentation can be found at https://www.gu.se/en/earth-sciences/weather-stations-at-the-department-of-earth-sciences



Visualizations
-------------------------------

### Selection order visualizations:

The images `<variable>_selection_order.png` illustrate the data sources for each variable. The top row in each figure shows the average number of observations per day for each month in the merged dataset. The second row shows the merged dataset, with colors for the different data sources. The subsequent rows show the available data for each station (grey lines) and the actual values used in the dataset (colors), in descending order of preference.

### Clock correction visualizations:

The files `Miljö/GVC_clock_offsets_uncorrected.png` shows the clock offsets (daily averages) of the Miljöförvaltningen/GVC records against the SMHI records from the cross-correlation analysis. The offsets on the y-axes of the plots correspond to the following time conventions:

0 = CET = UTC+1, the reference time for the dataset. 

-1h = CEST = UTC+2 = daylight savings time in Sweden.

+1h = UTC = the SMHI dataset convention.

+/-2h have no obvious correspondence with any sensible time convention, and presumably arise from mistakes. The -2h offset for Femman wind-speed in 2019 is presumably someone changed the clock the wrong-way for daylight savings. The +2h for Lejonet for 2020 is presumably someone removed daylight savings, even though clock was meant to be UTC. But such errors could also be copy/paste errors when the data were aggregated into a spreadsheet, or the random doings of mischievous gremlins. 

Non-integer daily average offsets are presumably when a clock is not accurately synchronized, or when non-standard averaging durations are used before the data are recorded. 

The files `Miljö/GVC_cock_offsets_corrected.png` shows the clock offsets calculated using the same method *after* the clock corrections were applied. Persistent whole-hour offsets have been efficiently removed. 

CSV file UCG_merged_2020.csv:
-----------------------------

The columns in the csv file are:

- Time - (UTC+1) Time as Central European Time, ie Stockholm time without daylight savings.
- tluft - Air temperature (degC) measured at the time-stamp.
- wind - Average wind speed (m/s) for the 10minute period ending at the time-stamp.
- wind_dir - Average wind direction (deg true) for the 10minute period ending at the time-stamp. SMHI data are recorded as degrees-east of true north, the reference alignment for the other stations is unknown.
- rh - Relative humidity (%) measured at the time-stamp. Note that rh and tluft are not always from the same station, because sometimes records from one or the other are missing for a particular station.
- global - Global radiation (short-wave radiation down on a horizontal surface, W/m/m), average for the hour ending on the time-stamp.
- diffuse - Diffuse radiation (diffuse short-wave radiation down on a horizontal surface, W/m/m), average for the hour ending on the time-stamp.
- mslp - Mean sea-level pressure (hPa) at the time-stamp.
- direct - Direct-beam short wave radiation (W/m/m) incident on a plane normal to the solar angle (*not* on a horizontal surface), the average for the hour ending on the time-stamp.
- source_tluft, source_wind, etc - station from which the observation was sourced, indexing into DataSources.csv

Missing data are denoted as "NaN". 





