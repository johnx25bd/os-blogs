# 5: Spatial for Data Scientists


A typical spatial data science workflow: emphasising ANALYSIS. IPython Notebooks. @STEVE ... ? Do we want to include R?

1. Import libraries / modules
2. Fetch relevant data into notebook
3. Spatial join?
4. Clean, typecast etc.
5. Feature engineering
6. Analysis: clustering, classification, etc etc?
7. Validation
8. Visualisation

## 1. Libraries / Modules

Table - name | link | use
- Geopandas
- numpy
- Shapely
- rasterio
- matplotlib / seaborn
- Folium
- pysal
- ??

## 2. Fetch data

- Access data
    - CSV
    - JSON
    - Shp
    - Tif
    - PostGIS
    - WFS
    - ??

## 3. Spatial Join? 

- Perform spatial join based on some geospatial dimension to the dataset

## 4. Clean and validate

- Identify outliers and null / faulty values
- Cast columns to appropriate types
- ??

## 5. Exploratory Spatial Data Analysis

How to check the shape and overall characteristics of a spatial dataset? 
- Key aggregate values

[`pysal.esda`](https://pysal.org/esda/)

## 5. Feature engineering

- Derived values based on existing dimensions
- Normalised values? 
- Transformations like log, etc
- ??
-

## 6. Analysis

- A section on various analytics techniques unique to spatial data and best practies on engaging
    - Clustering
    - Classification
    - Regression


- Import into analysis
    - Python
        - Pandas / geopandas
        - Shapely
    - R
- Analytical techniques
    - Clustering and classification
    - ML and neural networks
    - Refer to resources

## 7. Validation

How to assess the accuracy of the analysis? 
- Interpreting statistics that indicate confidence in spatial analyses
- k-fold cross validation
- ??

## 8. Visualisation

Spatial and non-spatial visualisation tools in Python
- Folium
- matplotlib
- seaborn
- ?