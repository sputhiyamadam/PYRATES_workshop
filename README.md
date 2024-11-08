# Reproducibility Study for PYRATES workshop

## Identify the periodicity of rainfall over the Maritime Continent in relation to different topographical factors.

 Author: Sreedevi Puthiyamadam Vasu
 Date: created on June 4, 
 License:
 
[![DOI](https://zenodo.org/badge/810518047.svg)](https://zenodo.org/doi/10.5281/zenodo.11508508)
______________________________________________________________

The codes will reproduce the analysis/results from the manuscript: Sreedevi P. Vasu, Pallav Ray, Nirmal Mathew Alex, Nathaniel C. Johnson, Efthymios I. Nikolopoulos, and Sopia Lestari, 2024b; Spatial distribution of precipitation over the Maritime Continent and its dependence on topography, under preparation.
______________________________________________________________

## Study region and Dataset used for the analysis
Study region: Maritime Continent ( 90°E-160°E; 10°N-11°S)
```geojson
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "id": 1,
      "properties": {
        "ID": 0
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
              [160,-11],
              [160,-11],
              [90,-11],
              [90,10],
              [160,10]
          ]
        ]
      }
    }
  ]
}
```

1. IMERG precipitation monthly data for the period of 2000-2023.
   NASA's Integrated Multi-satellitE Retrievals for GPM (IMERG) Version 6 precipitation estimates (Huffman et al. 2019). The dataset is in NetCDF format.
   https://gpm.nasa.gov/data/directory
2. ETOPO1 bathymetry/topography data:
   The ETOPO1 global relief model is a high-resolution (1 arc-minute) digital elevation model (DEM) for Earth's surface. The dataset is in NetCDF format.
   https://www.ncei.noaa.gov/products/etopo-global-relief-model
3. Derived data from ETOPO1 classifying data points into mountain, hill, and plains.
Link to data:  
  https://drive.google.com/drive/folders/1Ghl4moapgskl_8zOVFx8f_pL9VRa5k2U?usp=drive_link


## Method: 
1. Extract precipitation data over mountainous regions (using information from ETOPO1 elevation data) for the study region.
2. Similarly, precipitation data for the study region will be extracted over planar regions (using information from ETOPO1 elevation data).
3. Calculate the Fourier transform for analyzing the difference in periodicity of precipitation over high elevation versus planar region.



## Getting started

### Adding packages to your environment

Suppose you want to install a new package `conda install -c <channel-name> <package-name>`in your environment following the envlist.yml

### The workflow

Input/Output table:

| Step | Input | Output | Code |
| --- | --- | --- | --- |
| Step 1 | etopo.nc; IMERG_V07_2000_2023_monthly.nc; topographic_factors_etopo.nc| high_rain_lat_avg; high_rain_lon_avg;low_rain_lat_avg; low_rain_lon_avg | L1_prepocessing_data.ipynb | 
| Step 2 | high_rain_lat_avg; high_rain_lon_avg; low_rain_lat_avg; low_rain_lon_avg| diff_lat_avg; FFT_high_rain_lat_avg; FFT_low_rain_lat_avg; diff_lon_avg; FFT_high_rain_lon_avg; FFT_low_rain_lon_avg| L2_spectral_analysis_visualization.ipynb | 


#### Step 1: Getting data ready and preprocessing.
Here is the flow chart for preprocessing:

```mermaid
graph TD;
    id1[Analysis of Rainfall Over High Land and Low Land Regions]-->id2[Importing the Libraries]
    id1[Analysis of Rainfall Over High Land and Low Land Regions]--> id3[Reading NetCDF Files]
    id1[Analysis of Rainfall Over High Land and Low Land Regions]--> id4[Developing Masks for High Land and Planar Regions]; 
    id4[Developing Masks for High Land and Planar Regions]-->id5[Creating High Land and Planar Region Masks]
    id4[Developing Masks for High Land and Planar Regions]-->id6[Plotting the High Land and Planar Points];
    
    id1[Analysis of Rainfall Over High Land and Low Land Regions]--> id7[Extracting Rainfall Data Over High and Low Land Data Points for All Time Steps]-->id8[Plotting the Rainfall Data];

    id1[Analysis of Rainfall Over High Land and Low Land Regions]--> id9[Selecting the Domain of Interest and Calculating Mean Rainfall Along Longitude and Latitude]--> id10[Plotting the Resulting Arrays]
    id10[Plotting the Resulting Arrays]--> id11[Plotting Mean Rainfall Across Different Latitudes]
    id10[Plotting the Resulting Arrays]--> id12[Plotting Mean Rainfall Across Different Longitudes]
```

#### Step 2: Spectral analysis.
Here is the flow chart for step 2:

```mermaid
graph TD;
    id1[Spectral analysis]-->id2[Importing Libraries and Data]
    id1[Spectral analysis]--> id3[Importing the Previous Notebook]
    id1[Spectral analysis]--> id4[Calculating FFT]; 
    id4[Calculating FFT]-->id5[Calculating FFT for High Land Rainfall - Latitude and Longitude Averages]
    id4[Calculating FFT]-->id6[Calculating FFT for Low Land Rainfall - Latitude and Longitude Averages];

    id5[Calculating FFT for High Land Rainfall Latitude and Longitude Averages]-->id7[FFT of High Land Rainfall - Latitude Average]
    id5[Calculating FFT for High Land Rainfall Latitude and Longitude Averages]-->id8[FFT of High Land Rainfall - Longitude Average]
    
    id6[Calculating FFT for Low Land Rainfall - Latitude and Longitude Averages]-->id9[FFT of Low Land Rainfall - Latitude Average]
    id6[Calculating FFT for Low Land Rainfall - Latitude and Longitude Averages]-->id10[FFT of Low Land Rainfall - Longitude Average]
    id1[Spectral analysis]--> id11[Calculating and Plotting the Difference in FFT Magnitude]
   
```





