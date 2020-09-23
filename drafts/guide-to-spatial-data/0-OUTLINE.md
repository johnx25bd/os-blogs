# A Programmer's Guide to Spatial Data: OUTLINE

## 1: Introduction: thinking geo

What is a map? 

The purpose and goals of this guide.

Introducing data
- What is data?
- Structured vs unstructured data
- Tidy data
- Data types (?)
- Enter spatial: what is spatial data? 
- Raster and vector
    - Raster data
    - Vector data
        - Points, Lines, Polygons
- Why is spatial special?

GIS

## 2: Thinking Geo

Where am I? 
- Latitude
- [Longitude](./2-THINKING-GEO.md#longitude)
- Representing coordinates
    - Precision
- Bearing
- 3D -> 2D: projections

Fast forward: 
- GNSS. TopoNet?
- Coordinate reference systems
    - SRS, CRS, projection, datum, etc.

Representing Spatial Data
Raster
- Definition
    - What is an "observation"?
- Georeferencing
- Tiles
- Examples
    - DEM
    - Hillshade
    - Satellite
    - Rendered cartography
    - Heatmaps
- Alternative grids
    - Hex (hexbin, uber)
    - Triangle 
- Uses
    - Overlay: intensity
    - Satellite imagery
    - etc

Vector
- Definition
    - What is an "observation"?
- "Features"
    - Feature types
        - Points
        - Lines
        - Polygons
        - Multi*
        - FeatureCollections
    - Attribution / properties
    - Topological relationships
- "Layers"
    - A thematic (?) grouping of features
    - Example


## 3: The Spatial Data Lifecycle

Capture / Creation
- Raster: Remote sensing
    - Optical, SAR, etc
    - Airborne sensors
    - UAVs
    - ??
- Vector: Surveying
    - The surveyor's tools
- Synthesized data (for modelling)?

Storage
- Spatial databases
    - PostGIS
    - ?? (MongoDB, Spatialite, etc? ) @Tim - which to focus on? 
- Spatial queries
- Spatial indexing
- Other concepts?
- Raster vs vector
- Tiles

Analysis
- The spatial dimension
- Feature extraction
- Clustering
    - Measuring distribution randomness
- Classification
    - Spatial and non-spatial dimensions
- Time series 

Visualisation
- Static and dynamic
- Cartography
    - Styling
    - Iconography
    - Legend
    - Compass rose, extent etc
- Static visualisations
- Interactive visualisations
- UX
- Platforms
- 1D, 2D, 3D, 4D, n-D?
- VR and AR

## 4. Spatial Data for Web Developers

How a web map works
- HTML
- CSS
- JavaScript
    - API: ZXY or WMTS
    - Raster or vector tiles
    - Overlays
        - Raster layers
        - Vector features
- Useful tools
    - JS libraries
    - Utitilies
    - Frameworks
    - etc

## 5. Spatial Data for Data Scientists

A typical spatial data science workflow
- Access data
    - CSV
    - JSON
    - Shp
    - Tif
- Clean and validate
- Import into analysis
    - Python
        - Pandas / geopandas
        - Shapely
    - R
- Analytical techniques
    - Clustering and classification
    - ML and neural networks
    - Refer to resources


## 6. What's next in the geospatial world? 

Geovation

Project Iceberg (NUAR)

Mapping the pandemic

Remote sensing

## 7. Appendix

Spatial Data in practice (tables? appendix?)
- Raster
    - Formats
        - tif
        - ASCII
        - png
        - jpg
        - COG
        - GeoJSON??
    - Tools
        - GDAL
        - COG
        - Geotiff.js (?)
        - geoblaze
        - ???
- Vector
    - Formats
        - GeoJSON
            - TopoJSON + encoding topologies
        - Vector tiles
            - PBF
            - MBTiles
        - KML
        - Polylines
        - Shapefiles
        - GML
        - Geopackage
        - WKT
        - sf?
    - Tools

Glossary