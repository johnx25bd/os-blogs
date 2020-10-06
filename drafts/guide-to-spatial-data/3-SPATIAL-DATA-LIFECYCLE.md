# 3: The Spatial Data Lifecycle


Capture / Creation
- Raster: Remote sensing
    - Optical, SAR, etc
    - LIDAR
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
    - Visual hierarchy
- Static visualisations
- Interactive visualisations
- UX
- Platforms
- 1D, 2D, 3D, 4D, n-D?
- VR and AR



## Capture / Creation

All data comes from somewhere. There is a moment in time when it is created or captured - a binary representation of the information being recorded is formed by some computer. Often, sensors detect variations in local atmospheric conditions - the temperature, moisture content, chemical properties of the air or water, light. Other times data is created, or generated, by a computer - like when you call `Math.random()` or `numpy.randint()`, or ______(?).

### Raster: Remote sensing

Spatial data most often originates from some edge device like a satellite installed with specialised imaging sensor or a smartphone or GPS handset capable of connected to a GNSS system. This points to the distinction between raster and vector data - raster imagery usually starts with some kind of camera or sensor, which records the characteristics of one or more frequencies, or bands, of electromagnetic radiation (aka light) striking its sensor. By detecting these intensities, that analogue data can be converted into digital data that can be stored on disk and manipulated by algorithms. 

A raster dataset is a regular grid of values - evenly-spaced 2-dimensional cells (called pixels) or 3-dimensional cubes (called voxels) containing one or more numbers. These numbers can represent a measurement of a range of different characteristics of the surface being scanned. 
- Red, Green, Blue - RGB
- Near infrared, far infrared
- Panchromatic, multispectral, superspectral, hyperspectral imaging systems measure successively more bands of electromagnetic radiation.

#### Optical

Optical remote sensors capture images of the Earth by measuring the intensity of the visible and infrared wavelengths of the electromagnetic spectrum. These are typically _passive_ remote sensors, meaning they detect light from natural sources. _Active_ remote sensors emit radiation, much like a camera flash. 

#### SAR, etc


Synthetic aperture RADAR - SAR - captures 2D images and 3D models of surfaces by moving the sensor (radar antenna) over the target surface, measuring radio waves emitted from a transmitter. 

#### LIDAR

LIDAR - "LIght Detection And Ranging" - is a way of capturing very high resolution 3D scans of a target area. A LIDAR scanner essentially shines a laser on the surface of the target. By detecting the amount of time it takes for these lasers to travel from the scanner to the surface and back, a very accurate point cloud representing the object's surface can be calculated. [wikipedia](https://en.wikipedia.org/wiki/Lidar)

LIDAR can be used to map natural or humanmade terrestrial environments, along with bathymetric surfaces (riverbeds and seafloors).

#### Derived raster data

Measurements of different bands are associated with different physical materials and features on the Earth's surface, like [vegetation](google NDVI), [snow](NDSI), asphalt, etc. By analysing the numerical values of each pixel and their surrounding cells, geographic features and other physical characteristics of the land surface can be discerned. In this way, raster images can be created that are derived from raw images and other inputs. 
- Important to understand what the numbers in each cell are, and how they were derived. 
- Feature extraction: using raster imagery to identify vector geometries - image? ([Facebook deep learning road algorithm](https://ai.facebook.com/blog/mapping-roads-through-deep-learning-and-weakly-supervised-training/)) (Fusion Data Science?)

### Vector: Surveying

Vector geospatial data works a bit differently: points, lines and polygons are represented as geographic coordinates - by connecting these coordinates the geographic features are drawn. This raises a few interesting questions: how many coordinates are enough to accurately represent a feature? How precise do the coordinates need to be? And - how do we capture the coordinates in the first place? 

___

#### The surveyor's tools

- theodolite

#### Smartphone / IoT

Not long ago, it required specialised equipment to measure an accurate location. 
- Increases in the use location-enabled devices such as smartphones and IoT devices 
- These devices are capable of capturing vector geometries including points, linestrings and polygons

#### Other vector sources

- Algorithm-derived vector datasets: feature classification of raster imagery (supervised and unsupervised), randomly-generated data 
- Humans creating vector data by drawing on web maps
- Alternatives? 

## Storage

Once captured, spatial data must be stored somewhere. What's more, relationships between records in a spatial database - or geodatabase - differ from non-spatial databases. It can be incredibly useful to be able to `SELECT * FROM running_routes` where the route
-  intersects a certain geometry - say, crosses a river or a certain road, 
- is within a certain distance of another feature
- is greater than a certain length

Spatial joins

### Spatial operations

This points to the need for a specialised set of spatial operations - algorithms that use spatial data types as arguments. These spatial operations are implemented in a number of programming languages and platforms, including PostGIS, Turf.js, PySAL, etc.

These operations include:

| Operation | Input data type | Returns | 
| --- | --- | --- |
| distance | (geometry, geometry) | number | 
| equals | (geometry, geometry) | boolean |
| disjoint | (geometry, geometry | boolean |
| intersects | (geometry, geometry) | boolean |
| touches | (geometry, geometry) | boolean |
| crosses | (geometry, geometry) | boolean |
| overlaps | (geometry, geometry) | boolean |
| contains | (geometry, geometry) | boolean |
| length | (geometry) | number |
| area | (geometry) | number |
| centroid | (geometry) | Point |
| bounding box | [geometry] | (geometry) |

Spatial algorithms often rely on the of trigonometric operations, which are computationally expensive - so finding ways to reduce the number of these calculations to do when querying goes a long way to speeding up the operations.

### Spatial databases

In order to efficiently query a collection of records representing spatial data, the software for managing a geodatabase creates a *spatial index*, which is "a data structure that allows for accessing a spatial object efficiently" ([Zhang and Du 2017](https://gistbok.ucgis.org/bok-topics/spatial-indexing)). these spatial indices enable spatial queries and joins to be executed expediently - a must for large geospatial datasets. 
- Simplifying complex geometries - minimum bounding box - speeds up queries.
- 

#### PostGIS

PostGIS is "a spatial database extender for PostgreSQL" - the software brings spatial and geographic capabilities to PostgreSQL. Initially released almost 20 years ago, PostGIS is a very commonly used spatial database system, enabling developers comfortable with SQL to store, access and edit geographic objects. 

A key point to understand about spatial relational databases generally: stored in tables, records (rows) have attributes (columns) just like in typical SQL tables. The difference: if records represent spatial features - vector geometries representing points, lines or polygons - one of the columns will hold these geometries. **The geometry is an attribute of the record.**

These attributes have a special spatial data type - in PostGIS, `geometry`. 

`spatial_ref_sys` - "defines the spatial references systems known to the database." ([PostGIS: Geometries](http://postgis.net/workshops/postgis-intro/geometries.html)). (See Spatial Reference Systems from Chapter 2)

#### MongoDB

"MongoDB supports query operations on geospatial data" ([MongoDB](https://docs.mongodb.com/manual/geospatial-queries/)).
- Store data as GeoJSON objects
- Uses WGS84 as reference system for geospatial queries (per GeoJSON spec)
- More limited than PostGIS in a lot of ways, but also potentially plays better with web mapping applications since it is oriented towards GeoJSON.

### Spatial operators

Spatial databases have functions that can accept geometries and perform spatial algorithms. These functions are necessary to work with spatial objects - to `SELECT * FROM routes WHERE ST_Length(route_geom) > 500`, for example - or to perform spatial joins. The PostGIS documentation has a very extensive list of spatial functions and how they work - [here](https://postgis.net/docs/PostGIS_Special_Functions_Index.html).

#### Raster data

Some spatial databases do have functionality for working with raster images, including [PostGIS](https://postgis.net/docs/using_raster_dataman.html). 
- Not commonly used


### Raster vs vector

- Spatial databases like PostGIS work well with vector data

### Tiles

#### Raster tile

- How they work: 256px PNGs
    - ZXY scheme
    - Mapping libraries fetch and display appropriate tiles so it appears to be a seamless map
- Servers - ZXY, WMTS, externally hosted like Mapbox
- Distinction: raster data for visualisation vs analysis
- Cloud-Optimized GeoTIFFs, STAC

##### Vector tiles

- How they work
- Advantages (link to [vector tiles blog](https://www.ordnancesurvey.co.uk/blog/2020/07/the-benefits-of-vector-tiles/))
- [Tools for working with vector tiles](https://github.com/mapbox/awesome-vector-tiles):
    - Create - [geojson-vt](https://github.com/mapbox/geojson-vt), [tippecannoe](https://github.com/mapbox/tippecanoe) - (link to blog)
    - Parse / inspect (Observable Dissector notebook for [OS vector tiles](https://observablehq.com/@johnx25bd/os-vector-tile-api-comparison-and-dissector) and [others](https://observablehq.com/@henrythasler/mapbox-vector-tile-dissector).)
    - Visualize - Mapbox GL JS, Leaflet, OpenLayers, others? 
    - Customise - [Maputnik](https://github.com/maputnik/editor)
    
## Analysis

### The spatial dimension

### Feature extraction

Raw satellite imagery data can contain information about the positions and geometries of geographic features like waterways, roads, forests, and buildings, as well as land cover / vegetation types, areas with similar heat dynamics or air quality, and so on, but processing of the imagery is required to identify those feature geometries. This process is called "feature extraction": from the "initial set of measured data", features are derived. 

In the context of geospatial, "features" usually refer to geographic features - the vector coordinates that describe the positions of points, lines and polygons. 
- Examples of features from OS Features API
- How this differs from 'features' in other data science contexts ([wiki](https://en.wikipedia.org/wiki/Feature_extraction))

### Measuring distribution randomness

- Summarise [complete spatial randomness](https://en.wikipedia.org/wiki/Complete_spatial_randomness)
- An important analytical tool to assess [spatial autocorrelation](https://www.sciencedirect.com/topics/computer-science/spatial-autocorrelation
    - Tobler's First Law

### Detecting patterns: clustering and classification

#### Clustering

> "Clustering is the task of dividing the population or data points into a number of groups such that data points in the same groups are more similar to other data points in the same group and dissimilar to the data points in other groups. It is basically a collection of objects on the basis of similarity and dissimilarity between them." [Geeksforgeeks.org](https://www.geeksforgeeks.org/clustering-in-machine-learning/)

Geospatial clustering: 
- KMeans
- DBSCAN
- KNN
- SVM
- Neural networks

#### Classification

- Similar to clustering - assinging labels to records based on similarities.
- Supervised approach: number and type of classes are known beforehand (confirm?) - [GIS&T chapter](https://gistbok.ucgis.org/bok-topics/classification-and-clustering)

Clustering and classification of spatial datasets requires some unique considerations
- Haversine distance
- How spatial and non-spatial dimensions are included, normalised and compared.
- Etc.

### Time series 

Spatial data can be especially useful if there is a temporal dimension. This refers to _when_ the measurements were taken. For example, a time series of satellite imagery enables the comparison or analysis of how a certain area changes over time. Likewise, time series data could show how a vehicle moves around over time, how cities evolve, etc. 

The temporal dimension adds an additional layer of complexity
- working with datetimes can be fidgety, 
- using it as a dimension in querying and analysis

Best practices etc? 

## Visualisation

Having described spatial data capture, analysis and storage processes, the final stage of the spatial data lifecycle is visualisation. Data visualisations seek to convey information contained in data to someone by highlighting relevant signals. 

### Static and dynamic

Location information can be presented in a range of formats. 
- Paper maps as data visualisations
- Historical data visualisations: [Minard](https://en.wikipedia.org/wiki/File:Minard.png)
- Map tile servers enabling dynamic, on-demand data visualisations on digital devices
- Now, data visualisations utilizing location data are ubiquitous. On top of the obvious mapping applications, what apps use spatial data to improve user experience? 

### Cartography

"The study and practice of making maps" ([wiki](https://en.wikipedia.org/wiki/Cartography)): digital cartographers are building on a millennia-old domain of knowledge meant to help people find their way in the world. 
- The learnings of how to clearly and concisely create these abstractions of reality so they are useful are more relevant than ever. 
- Interactive cartography opens up a new realm of possibility to present progressive depth of information.

#### Styling

@CHARLEY and @PAUL

#### Iconography

@CHARLEY and @PAUL

#### Legend

@CHARLEY and @PAUL

#### Compass rose, extent etc

@CHARLEY and @PAUL

#### Visual hierarchy

@CHARLEY and @PAUL

### Static visualisations

@CHARLEY and @PAUL

### Interactive visualisations

@CHARLEY and @PAUL

### UX

@STEVEATTEWELL

### Platforms

Desktop, Web, Mobile
- Considerations for each
- Pros and cons:
    - Desktop - screen size, hover state, usually stronger internet connection, more compute power. 
    - Web - screen size, hover state, internet, compute. No need to download a native application.
    - Mobile - on the go, ability to render vector tiles, live location, camera for AR.
- Key tools for creating maps on each platform

### 1D, 2D, 3D, 4D, n-D?

An interactive digital experience can incorporate any number of spatial and non-spatial dimensions. 
- Challenge of organising and presenting the appropriate information at the appropriate time in an appropriate way.
- Demo / links to good visualisations to give the user inspiration. ?? @ALL - ideas? 

### VR and AR

Maps are meant to help users understand reality. VR and AR are new tools to help that. 
- AR as heads up display - digital overlay on the real world
- VR as an immersive digital environment 
- Tools: Unity (C#), AFrame (HTML / JS), ??
- ??