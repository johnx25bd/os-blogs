# A Programmer's (Practical?) Guide to Working With Spatial Data

_A crash course for web developers and data scientists on how to work with maps and mapping data._

## Intro 

Maps are incredibly useful things. We use maps to understand reality, to decide on where to navigate, make sense of our sense of place - without maps, we are, quite often, lost. Maps are tools we have come to rely on to survive and thrive. 

What is a map? [Wikipedia puts it concisely](https://en.wikipedia.org/wiki/Map): "A map is a _symbolic depiction_ emphasizing _relationships_ between _elements_ of some _space_." This definition captures the breadth of things we describe as "maps": from the traditional - paper LandRanger maps hikers use to explore the Scottish Highlands - to the more conceptual - a mind map of ideas around a topic, or a site map of pages of a website, or a network of firms competing in a market. In every case, maps can help us understand a space in a more complete way than we can by simply observing it directly. 

![Image of some map or maps. Embed? Gif?]()


This guide will focus on physical space, and symbolic depictions of physical space on the scale most familiar to humans: geographic maps. Our goal is to provide competent programmers and analytical thinkers a strong enough grounding in the _theory_ of spatial data to build and develop sophisticated _applied_ uses of spatial data. 

This is a practical guide. We are writing for an audience of web developers and data scientists - but the guide is intended to explain technical concepts in clear terms and be useful for non-technical audiences. Most of the chapters will not deal with code, though we do include a chapter with [a workflow and tools for web developers](#) familiar with JavaScript, and one with [tools for data scientists](#) working in Python. We also link to external resources whenever possible, to give readers the ability to dig deeper into any of the topics covered.

## Housekeeping

This guide is designed to be a reference on the concepts unique to working with spatial data. It is meant to be useful to read from start to finish, but also for readers referring to relevant sections as needed. We use a few symbols to indicate points to take note of:

| |  |
| --- | --- |
| 👍 | A rule of thumb or helpful tip |
| 🔑 | A key term or concept |
| ⚠️ | Common snags and pitfalls |

We're hosting the guide as a living document on Github - so feel free to ask questions, suggest improvements and raise issues if you see something that could be better! 

## Topics

- What is spatial data?
- Coordinates in three dimensions
- Relative vs absolute positions
- Spheres and planes: why is spatial special? 

## What is spatial data? 

Spatial data is a subset of data, where the relative positions of the features represented are described in the data. 

It may refer to physical space - the space occupied by a building, mountain range, cell or galaxy - but also could refer to an abstract, intangible space, like a 


Representing reality on an abstracted image. 

What is spatial data?
- "data that describes anything with spatial extent (i.e. size, shape or position)" [w3c/](https://www.w3.org/TR/sdw-bp/)
- "AKA location information or mapping data"

Representing location on a plane using coordinates - xyz, plus time. Extra dimensions (attributes).

Viewing the map in a browser. Center or bounding box, zoom, pitch, bearing. Visible layers. etc.

_Spheres and planes_: why is spatial special? 
- The importance of where - illustrate with sorted table vs map of countries
- "As location is often the common factor across multiple datasets, spatial data is an especially useful addition to the Web of data." [w3c](https://www.w3.org/TR/sdw-bp/)
- Spatial relationships
- Where does spatial data come from? 
    - Remote sensing
    - Surveyors
    - ??
![Gif of D3 projections transitions]()

_Servers and clients_: why is web special?
- Mobile browsers deliver the web to users wherever they go

Focus: get you up and running. I will approach this using a specific set of technologies - each step has many ways to solve the same problem. I'll indicate those where possible. (Which technologies should I use?)



## Key concepts

### Coordinates
- coordinate formats: decimal degrees, deg min sec, radians, etc.
- Locating points on the surface of a sphere.
- Is this getting too in depth? Could be its own post. Don't want to lose people here.

#### Coordinate Reference Systems
- Geographic Reference Systems
- What it is and why it matters
- CRSs vs Projections
- 👍 - use Web Mercator. Or BNG? (I'd like this to be applicable to a global audience).
- Read more: [OS blog](https://www.ordnancesurvey.co.uk/blog/2016/09/ostn15-new-geoid-britain/), [more technical](https://www.ordnancesurvey.co.uk/documents/resources/guide-coordinate-systems-great-britain.pdf).
- ⚠️: [lon, lat] vs [lat, lon].  

![image](./assets/image-of-coordinate-system.png). <- Do we have OS graphics we want to use? 

#### Projections

### Representing Spatial Data

### Raster 
- Grids of regular pixels, each pixel assigned numerical values.
    - Values could be RGB, elevation, multispectral satellite imagery etc.
- Pixels are positioned in space. 
- Formats: tif, png, jpg, cogs (cloud-optimized geotiff)
- Placing tiles
    - Libraries
    - ![Image or zooming gif of map with png borders]()
- Fetching tiles as we zoom
- ZXY ("Zoom X Y"!), WMTS 
- Popular tile servers - Ordnance Survey, OSM, Bing, Mapbox, Stamen
- Advantages and disadvantages  (inspiration [here](https://en.wikipedia.org/wiki/GIS_file_formats#Advantages_and_disadvantages))
- Digital elevation model and hillshade
- Satellite
- Rendered vector maps
- Heatmaps and other raster maps
- Opacity
- Alternative types of rasters - like hex, triangle grids etc.
- Uses - images, indices, etc. 

SVG, canvas, divs.

### Vector
- Define "Feature".
- Points, Lines, Polygons
    - Representing geometries: arrays of coordinate pairs.
    - Talk about Multi* / FeatureCollections (image) (types)
    - Complex polygons
- "Layer": collection of similar features  (?? multi-type layers?)
- Formats: geojson, shp, kml, gml, geopackage, vector tiles, WKT, sf (code examples - at least of geojson)
    - An aside: topojson and encoding topologies.
- Accuracy
    - 👍 `geojson-precision` to reduce file size
- Labels.
- geometries and attributes
- Vector Tiles
- SVG
- Canvas
- Pop-ups and tooltips
- Advantages and disadvantages (inspiration [here](https://en.wikipedia.org/wiki/GIS_file_formats#Advantages_and_disadvantages))

Data sources
- OS Data Hub
- Tile server
- PostGIS
- Geoserver
- CartoDB
- ArcGIS MapServer
- Mapbox
- ??

Styling 

Mapping terms
- Map state: refers to the state of the map visualization including zoom level, center or bounding box, pitch, bearing 
- Zoom to or fly to
- Pop-up
- Geocoding
- Gazetteer
- Temporal or spatiotemporal
- Buffer

Common tools / libraries
- Mapboxgl.js
- Leaflet.js
- Openlayers.js
- D3.js
- Turf.js


## Web Developers

### How a typical web map works

1. Include div where map will be placed in HTML document
2. Initialize basemap. Create instance of map class - examples from Leaflet, Mapbox, etc. (Explain this uses raster tiles. <- does it also use vector tiles?). Include intial view parameters including where, zoom level etc. (Behind the scenes.)
3. Fetch and add custom layers.
4. Attach event listeners and do custom styling. 

⚠️ Asset management. Like any webpage, managing data fetched asynchronously can be tricky - especially true as map data can often be quite large. Using async / await or promises helps this massively. 

### A basic web map

Code example loading raster basemap, placing vector features on top. 

### Frameworks

React

Angular

### Working with maps on mobile

## Data Scientists

- Python (geopandas, shapely, matplotlib, seaborn, folium, ipyleaflet)
- R (ggplot, sf, etc)
    - [leaflet for R](https://rstudio.github.io/leaflet/)
- Reading data
- 👍 Haversine distance! (clustering, feature engineering)
- Spatial toolkits (sklearn)
- Styling


## Resources

[Spatial Data Science](https://keen-swartz-3146c4.netlify.com/) in R. (Edzer Pebesma and Roger Bivand 2020)




