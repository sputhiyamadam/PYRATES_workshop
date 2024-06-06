# Example repsitory for pyrates workshop 

# PYRATES_workshop - Reproducible Study

## Identifying the periodicity in rainfall over the Maritime Continent in relation to different topographical factors.

 Author: Sreedevi Puthiyamadam Vasu
 Date: created on June 4, 
 License:



The codes will repoduce the following image:


## Dataset used for the analysis
Study region: Maritime Continent ( 90°E-160°E; 10°N-11°S)
1. IMERG precipitation daily data for a period of  2000-2023. NASA's Integrated Multi-satellitE Retrievals for GPM (IMERG) Version 6 precipitation estimates (Huffman et al. 2019). Dataset is in netcdf format.
2. ETOPO1 bathymetry/topography data: The ETOPO1 global relief model is a high-resolution (1 arc-minute) digital elevation model (DEM) for Earth's surface. Dataset is in netcdf format.

### links to data:
1. IMERG:
2. ETOPO:

```
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/LijoDXL/OceanographyWithPython/master)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/LijoDXL/OceanographyWithPython/blob/master/LICENSE)

[![Twitter Follow](https://img.shields.io/twitter/follow/lijodxl?style=social)](https://twitter.com/LIJODXL)

```

## Method: 
1. Extract precipitation data over mountainous regions (using information from etopo elevation data) for the study region.
2. Similarly extract precipitation data over planar regions (using information from etopo elevation data) for the study region.
3. Calculate the Fourier transform for analyzing the difference in periodicity of precipitation over high elevation versus planar region.




## Getting started

### The workflow
Here is a simple flow chart:

```mermaid
graph TD;
  id1[A F]-->  id2[B G];
  A-->C;
  B-->D;
  C-->D;
```


Here is the flow chart:

```mermaid
graph TD;
    id1(Data processing)-->id2(reading netcdf)--> slecting the domain of study--> Regriding (same resolution for all variables); 
    Regriding (same resolution for all variables-->elevation data-->topographical factors;
    topographical factors-->slope/relief;
    topographical factors-->distance from coastline;
    topographical factors-->critical elevation;  
    Regriding (same resolution for all variables-->rainfall data-->extract the data based on topographical factor criteria--> take area average to get a time series
```

### Adding packages in your environment

Suppose you want to install a new package`conda install -c <channel-name> <package-name>`in your environment following the envlist.yml

### Do the preprocessing of data using pre


```


````

```{image} /assets/images/phdComic.jpg
:align: "center"
:scale: 50%
:name: PhdComic
```




