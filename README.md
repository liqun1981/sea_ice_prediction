# sea_ice_prediction
Sea ice concentration prediction using large scale modes of climate variability

## Setup and execution 
Download data from 'Data' section below and then see setup.md file 


## Background 

Sea ice is the phenomenon where sea water freezes. Sea ice concentration is the relative frozen area to the total 
at a given point. Sea-ice extent is defined as the total area of grid cells with sea ice concentration greater than 15%. The reduction in sea ice concentration on the one hand opens up new opprtunities for fishery and shipping, but may lead to adverse effects on the Arctic ecosystem, weather, and climate (source: https://journals.ametsoc.org/doi/10.1175/JCLI-D-15-0313.1). Understanding the natural variablitiy and future predictability of sea ice will help us understand better the obstacles we are facing and the opprtunities accompanying them.    


## Data 
We use as features four modes of variability 
```
NAO: North arctic osciliation - The daily NAO index correpsponds to the NAO patterns, which vary from one month to the next 
- see more details at source : https://www.cpc.ncep.noaa.gov/products/precip/CWlink/pna/nao.shtml

AO: Arctic oscilation - the daily AO index is constructed by projecting the daily (00Z) 1000mb height anomalies poleward of 20°N onto the loading pattern of the AO 
- see more details at source : https://www.cpc.ncep.noaa.gov/products/precip/CWlink/daily_ao_index/ao.shtml

co2: The mole fraction of CO2, expressed as parts per million
# (ppm) is the number of molecules of CO2 in every one million molecules of dried air (water vapor removed)
- Note that missing values in the average column are noted by -99.99  (can use interpollated column instead)
- see more details at the link below for co2
```


Data is extracted from four sources - please download the data below:

```
nao:  https://www.cpc.ncep.noaa.gov/products/precip/CWlink/pna/norm.nao.monthly.b5001.current.ascii.table
nino: https://www.esrl.noaa.gov/psd/gcos_wgsp/Timeseries/Data/nino34.long.anom.data
ao:   https://www.esrl.noaa.gov/psd/data/correlation/ao.data
co2:  ftp://aftp.cmdl.noaa.gov/products/trends/co2/co2_mm_mlo.txt 
SIC:

```

## Modeling 

We would like to regress the SIC from climate modes, not forgetting the location and time features (seasonality).

Will it help us to create a model using all loations in the model? 
if we create one model for all locations features will lose their meaning in prediction since they are the same for all locations at a certain timestamp.

The idea here is not only to check how well we can regress on the large scale modes 
of climate variability, but also to see the differential to models that don't use any of
these features at all.


Models that are used are Decision Trees, Random Forest, and Gradient Boosting.

For details see for example: 
1. Book: Classification and Regression Trees by Breiman 
2. Random Forest : https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf by Breiman
3. Gradient Boosting: https://statweb.stanford.edu/~jhf/ftp/trebst.pdf by Friedman


Why these models ? 

The tree-based models will enable us:
 -  No assumptions on the data distribution (only heuristic of mse loss when splitting tree)
 -  Treat both the features(e.g. CO2) and the seasonality (e.g. last 3 months avg.) - we would like to have both.
 -  Easier to explain and interpret 
 -  Typically less sensetive to outliers 
 - 	Don't require scaling of variables
 - 	Don't require de-seasonlization to treat time 
 -  Empirical strength


## Future steps

- Hyperparam. optimization 

- We pay attention that there are areas that behave in the same SIC manner e.g. (lat 0 lon 0 and lat 3 lon 0)
This means we can combine them into one model per area (instead per lat/lon combo).

- It will be interesting to conduct a paired T-test over the different combo of lat/lon values to see that 
One algorithm is really better than the other.

Create auto-correllation for each combination of lat/lon values (or area) and add the correlated lags as features per model.
- Add cross validation to create more informed trees.

- Add features measured locally --> so we can combine all data to one model.

- Explore further seasonality - add more features like quantiles/ median etc.

- It might be useful to think also about spatial location: perhaps close locations can tell us somethin about current location.

- Explore auto-regressive models.



