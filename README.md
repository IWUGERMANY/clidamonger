# clidamonger

### Climate Data Monthly Germany

The R data package "clidamonger" is based on the data tables of the Excel workbook "Gradtagzahlen-Deutschland.xlsx" (published and updated twice a year by the ["Institut Wohnen und Umwelt GmbH"](https://iwu.de) in Germany). The dataframes derived from the workbook tables are usable for heating and cooling calculations (external temperature, heating / cooling days, solar radiation).

The version 1.3.0 includes DWD climate data from January 1991 to December 2024. The next update is planned for June 2025.

The package consists of the following dataframes:

- **"data.ta.hd"**
  By month and by DWD climate station: average external air temperature (TA) in °C; for specific base temperatures: heating and cooling days (HD_10, HD_12, HD_15, CD_18, CD_20, CD_22), external air temperature during heating and during cooling days (TA_10, TA_12, TA_15, TAc_18, TAc_20, TAc_22).

- **"data.sol"**
  Monthly values published by CM SAF
  Geographical coordinates for Germany (latitude and longitude distances 0.02°): average shortwave radiation on horizontal surfaces (I_Hor) in W/m², listed .

- **"list.station.ta"**
  By DWD station: geographical coordinates.

- **"tab.stationmapping"**
  By postal code: geographical coordinates and the three closest DWD weather stations.

- **"tab.estim.sol.orient"**
  By orientation and inclination: parameters for estimating the solar radiation for vertical and inclined surfaces on the basis of horizontal radiation data.

A description of the method can be found in

Loga, Tobias & Großklos, Marc & Landgraf, Katrin. (2020). Klimadaten für die Realbilanzierung - Grundlagen des Tools „Gradtagzahlen-Deutschland.xlsx“ - MOBASY-Teilbericht. 10.13140/RG.2.2.25695.28324.

### Data sources

The tabled values have been calculated by IWU - [Institut Wohnen und Umwelt](https://iwu.de) by use of the following data sources:

**Source of the temperature data:** [DWD - Deutscher Wetterdienst](https://www.dwd.de)

CDC (Climate Data Center) DE
[https://opendata.dwd.de/climate_environment/CDC/observations_germany/climate/daily/kl/historical/](https://opendata.dwd.de/climate_environment/CDC/observations_germany/climate/daily/kl/historical/)

[https://opendata.dwd.de/climate_environment/CDC/observations_germany/climate/daily/kl/recent/](https://opendata.dwd.de/climate_environment/CDC/observations_germany/climate/daily/kl/recent/)

**Source of the solar radiation data:** DWD - Deutsche Wetterdienst | www.dwd.de

EUMETSAT / Satellite Application Facility on Climate Monitoring (CM SAF)
www.cmsaf.eu

---

## Installation

Install the latest published release from CRAN:

```r
install.package("clidamonger")
```

Install the latest Master branch of "clidamonger" using the R "devtools"-package:

```r
# install.packages(devtools)
library("devtools")

devtools::install_github("https://github.com/IWUGERMANY/clidamonger")
```

## Usage

```r
library(clidamonger)

```

## License

<a rel="license" href="https://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="https://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.

---

## Explanations

### Explanation of the quantities (indications in the data field "Code_Quantity")

    "TA" - External air temperature

    	External air temperatures, measured by weather stations
    	Monthly averages of daily values in °C
    	Averaged for days if value is equal or below the mentioned base temperature (heating days*).
    	Listed by weather station of the German weather service DWD (including geographical coordinates)

    	Code
    	"TA"
    	"TA_10"
    	"TA_12"
    	"TA_15"


    "HD" - Heating days

    	Heating days by base temperature, measured in Germany
    	Monthly values in days
    	Number of days, during which the average external air temperature*  is equal or below the mentioned base temperature.
    	Listed by weather station of the German weather service DWD (including geographical coordinates)

    	Code
    	"HD10"
    	"HD12"
    	"HD15"

    "CD" - Cooling days

    	Cooling days by base temperature, measured in Germany
    	Monthly values in days
    	Number of days, during which the average external air temperature*  is equal or above the mentioned base temperature.
    	Listed by weather station of the German weather service DWD (including geographical coordinates)

    	Code
    	"CD18"
    	"CD20"
    	"CD22"

    "I_Hor" - Shortwave radiation on horizontal surfaces

    	SIS - Surface incoming shortwave radiation
    	Monthly averages in W/m²
    	Listed by geographical coordinates for Germany (latitude and longitude distances 0.02°)


    Further quantities

    	Code
    	"D"
    	"CT"

Explanation of the data types (indications in the data field "Code_DataType")
Code
"STD"
"MET"

### Data analyses / error handling during compilation

**Table "Data.TA.HD"**

Monthly values determined on the basis of daily data published by DWD (average, summation)

Handling of missing daily temperatures:

- Average temperatures: none (Average completed if at least one value is available for a given month)
- Heating days: none (days fulfilling the condition are counted for a given month)

Missing values are indicated by the completeness indicator (code "CT", value range 0.0 … 1.0): count of temperature values divided by count of days for a given month

**Table "Data.Sol"**

Monthly values published by CM SAF (see above)
Handling of missing values: Cells are empty

---

IWU 2025-01-31
