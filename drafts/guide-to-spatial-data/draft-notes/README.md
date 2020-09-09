# A Programmer's (Practical?) Guide to Working With Spatial Data

_A crash course for web developers and data scientists on how to work with maps and mapping data._

## Intro 

Maps are incredibly useful things. We use maps to understand reality, to decide on where to navigate, make sense of where we are - without maps, we are, quite often, lost. Maps are tools we have come to rely on to survive and thrive. 

What is a map? [Wikipedia puts it concisely:](https://en.wikipedia.org/wiki/Map) "A map is a _symbolic depiction_ emphasizing _relationships_ between _elements_ of some _space_." This definition captures the breadth of things we describe as "maps": from the traditional - paper LandRanger maps hikers use to explore the Scottish Highlands - to the more conceptual - a mind map of ideas around a topic, or a site map of pages of a website, or a map representing a network of firms competing in a market. In every case, accurate maps can help us understand a space in a more complete way than we can by simply observing it directly. 

![Image of some map or maps. Embed? Gif?]()

This guide will focus on physical space, and symbolic depictions of physical space on the scale most familiar to humans: geographic maps. Ordnance Survey has been making maps and collecting location data for centuries, always operating at the cutting edge of cartography. We remain committed to this tradition of innovation in the 21st century. Our goal in creating this resource is to provide competent programmers and analytical thinkers a strong enough grounding in the _theory_ of spatial data to build and develop sophisticated _applied_ uses of spatial data. 

This is a practical guide. We are writing for an audience of web developers and data scientists - but the guide is intended to explain technical concepts in clear terms and be useful for non-technical audiences. Most of the chapters will not deal with code, though we do include a chapter with [a workflow and tools for web developers](#) familiar with JavaScript, and one with [tools for data scientists](#) working in Python. We also link to external resources whenever possible, to give readers the ability to dig deeper into any of the topics covered.

## Housekeeping

This guide is designed to be a reference on the concepts unique to working with spatial data. It is meant to be useful to read from start to finish, but also for readers referring to relevant sections as needed. We use a few symbols to indicate points to take note of:

| |  |
| --- | --- |
| 👍 | A rule of thumb or helpful tip |
| 🔑 | A key term or concept |
| ⚠️ | A common snag or pitfall |

We're hosting the guide as a living document on Github - so feel free to ask questions, suggest improvements and raise issues if you see something that could be better! 

## Topics

- What is spatial data?
- Coordinates in three dimensions
- Relative vs absolute positions
- Spheres and planes: why is spatial special? 

## Chapter 1: What is spatial data? 

Before we can answer this question, it is worth defining another term - one that is very often glazed over. What is _data?_

[  what is data ?  ] Data contains information - meaning.

Data can be "structured" or "unstructured" - that is, organised in a standardised way, or not. The Data Management Association specifies that unstructured data "has not been tagged or otherwise structured into rows and columns or records." This is relevant when we try to automate the processing of data - computers work very well with structured data, and have a harder time processing unstructured data.

Structured data contains information that has a formal structure. These datasets are composed of "records", or "observations" - individual units described in the data. These observations might represent any range of things - geographic features like road segments, train stations or post codes; financial transactions; human beings - just about anything you can imagine, physical or intangible. 

Structured data comes in many forms, but it is often useful to imagine it as a table, with rows and columns. In properly-structured data (["tidy" data](https://vita.had.co.nz/papers/tidy-data.pdf) (Wickham 2014)), each row represents an individual _observation_, and each column represents a _dimension_ to the observation, or variable that describes it. If we think of a table where each observation represents a person, a tidy, structured dataset might look like this: 

| id | name | age (years) | favorite_color | has_smartphone |
| --- | --- | --- | --- | --- |
| 0 | "Helena Espinosa" | 29 | "blue" | true |
| 1 | "Dorian Beach" | 17 | "green" | false |
| 2 | "Lukas Craft" | 44 | "purple" | false |
| 3 | "Vishal Needham" | 83 | "grey" | true |

(Names randomly generated with [name-generator.org.uk](https://www.name-generator.org.uk/)).

Because this data is structured in a standardised way, computer programs can parse and analyse this dataset much more easily than if the data were unstructured, like this: 

> "We met four people the other day. Helena was 29 - her birthday was last week. She loves the color green, but her favorite is blue. She called Vishal on her smartphone - he's 83, and lives in Dorset. They met up with Dorian (17) and Lukas (44) at the park for a walk. Dorian and Lukas needed to use Vishal's smartphone for their walking directions, since they don't have smartphones. The three like green, purple and grey respectively."

Both datasets contain the same information - but the structured data is organised in such a way that analysing the information programmatically is quite straighforward. Processes for the automated extraction of these details from the unstructured dataset are maturing (like [natural language processing](https://en.wikipedia.org/wiki/Natural_language_processing)).

### Structured Data Formats

CSV

JSON

XML

SQL


> 👍 : When creating a new dataset or recording manually, make sure you plan the structure of your data carefully. Make sure your data adheres to the principles of tidy data design, and make efforts to ensure that data is consistently entered. This will save *loads* of time when you get to the analysis phase, especially if you intend to analyse the data algorithmically.

### Data Types, Briefly

A key insight: on computers, all of this information is represented in _binary format_. Data is encoded as sequences of **b**inary dig**its**, or **bits**. A bit is "a basic unit of information in information theory" ([Wikipedia](https://en.wikipedia.org/wiki/Bit#:~:text=The%20bit%20is%20a%20basic,a%20portmanteau%20of%20binary%20digit.)), a logical state with exactly two possible values. We can imagine these values as 1 or 0, yes or no, true or false, on / off, + or -. 

So how do sequences of bits represent the incredible complexity of information that can be accessed, analysed and visualised by computers? Computers work with data that has been encoded. Image, audio and video information, as well as characters like letters or other symbols, are converted in a standardised way to be represented as these binary sequences. 

An easy example: letters and numbers are encoded into binary using a character encoding standard, like ASCII or UTF-8. To convert the binary encoded data back into the characters represented, a computer just needs to have the encoding rules - it can then parse the binary sequence and derive the character sequence. 

So how would we represent the string "Ordnance Survey" in binary? 

| Character | UTF-8 (binary) | 
| --- | ---- |
| "O" | 1001111 |
| "r" | 1110010 |
| "d" | 1100100 |
| "n" | 1101110 |
| "a" | 1100001 |
| "n" | 1101110 |
| "c" | 1100011 |
| "e" | 1100101 |
| " " | 0100000 |
| "S" | 1010011 |
| "u" | 1110101 |
| "r" | 1110010 |
| "v" | 1110110 |
| "e" | 1100101 |
| "y" | 1111001 |

Meaning - in UTF-8 encoding - "Ordnance Survey" is stored and transmitted as the binary sequence `01001111 01110010 01100100 01101110 01100001 01101110 01100011 01100101 00100000 01010011 01110101 01110010 01110110 01100101 01111001`. (Conversion performed in JavaScript based on [this StackOverflow answer](https://stackoverflow.com/questions/18729405/how-to-convert-utf8-string-to-byte-array).)

Similarly, audio can be representing digitally by using audio coding formats like MP3, AAC, FLAC. These formats encode the "audio information in terms of frequencies and amplitudes" ([Wikipedia](https://en.wikipedia.org/wiki/MP3)). Images can similarly be represented digitally - we'll go over how shortly. 

For the encoded information to be useful, it needs to be parsed and interpreted by a computer processor. This would include displaying the characters or images visually on a screen, or sending a signal to an audio speaker that would create the sounds encoded. 

Further explanation of how information is encoded in binary is beyond the scope of this resource. 

### So - what is spatial data? 

Spatial data is a subset of data. In a spatial dataset, the relative positions of the features represented are described in the data. These relative locations may refer to physical space - the space occupied by a building, mountain range, cell or galaxy - but also could refer to an abstract, intangible space, like how closely two words are associated in an article, or the relationship between two people in a social network. As long as a dataset includes information about where things are in relation to each other, it can be considered spatial data. 

This said, the focus of this guide is on spatial data representing geographic features. Again, the definition of "geographic features" is quite broad. Of course physical features such as hills, shorelines, rivers, canals, buildings, bridges and the like are included. But more abstract things like parliamentary constituencies or topographic contour lines or connection points in path networks are also geographic features. 

### Vector and Raster



#### How is spatial data collected?

To understand what spatial data is, it helps to get a sense of how it is collected. Spatial data is captured in a number of ways. This includes by physical sensors - specialized cameras - that record different wavelengths of light reflecting off of the topography. This results in *raster* imagery - photos where different land features are visible due to how they contrast with other parts of the image. It's important to note that to be most useful these images must be georeferenced, where each pixel is associated with an area on the ground. This is often done by identifying the coordinates of the corner of an image, as well as the width and height of each pixel, making it easy to calculate the exact real-world position of every pixel represented.

However, usually raster imagery still must be carefully analysed to become useful to spatial data analysts, cartographers and other users. Using both human and machine analysts, different geographic features are identified in the 

![ example raster image ] ( )

In addition to capturing spatial data using remote sensing techniques, human surveyors use specialised equipment to capture very precise measurements of various geographic features. As they do they mark down additional information about these features, called attributes. A surveyor might record a geometry representing a segment of road by measuring the coordinates of points along the road segment edge. Then they'd input additional data with those measurements - maybe that it is a "road", the name of the road - "Turner Lane" - and so on. Including these attributes in the information representing the physical feature gives context to that geometry, enabling sorting, indexing and so on.

! [ photo of surveyor and equipment ] ( )

(quote from surveyor? Link to blogs?)


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

https://www.ordnancesurvey.co.uk/documents/resources/guide-coordinate-systems-great-britain.pdf

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

[awesome earth observation code](https://github.com/acgeospatial/awesome-earthobservation-code)

[Spatial Data on the Web Best Practices](https://www.w3.org/TR/sdw-bp/)


[Geospatial Glossary](https://www.gov.uk/government/publications/geospatial-glossary/geospatial-glossary) (Geospatial Commission)

[Tidy Data](https://vita.had.co.nz/papers/tidy-data.pdf). Wickham 2014.

[MacWright on Lon/Lat](https://macwright.org/lonlat/)

[Web Programming for Cartographers](https://medium.com/@ralucagnicola/web-programming-for-cartographers-beyond-the-basics-cecac632551a)

[GIS Free Online Book by Victor Olaya](https://volaya.github.io/gis-book/en/index.html)