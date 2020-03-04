# A Web Developer's Guide to Working With Spatial Data

_Crash course for web devs on how to work with maps and mapping data._

## Intro 

What is a map? Representing reality on an abstracted image. 

Coordinates - xyz, plus time. Extra dimensions (attributes).

Viewing the map in a browser. Center or bounding box, zoom, pitch, bearing. Visible layers. etc.

_Spheres and planes_: why is spatial special? 

_Servers and clients_: why is web special?

Focus: get you up and running. I will approach this using a specific set of technologies - each step has many ways to solve the same problem. I'll indicate those where possible. (Which technologies should I use?)

⚠️ emoji: snags and pitfalls

## Key concepts

Terms defined

- Coordinates
    - coordinate formats: decimal degrees, deg min sec, radians, etc.
    - Coordinate reference systems. <- this deserves a link to a deeper reference probably. What do they _need_ to know? Recognizing the issue, troubleshooting. Read more: (OS blog)[https://www.ordnancesurvey.co.uk/blog/2016/09/ostn15-new-geoid-britain/], (more technical)[https://www.ordnancesurvey.co.uk/documents/resources/guide-coordinate-systems-great-britain.pdf].
    - ⚠️: [lon, lat] vs [lat, lon].  
    ![image](./image-of-coordinate-system.png).

- Vector
    - "Feature": Points, Lines, Polygons, Multi* (image) (types)
    - "Layer": collection of similar features  (?? multi-type layers?)
    - Formats: geojson, shp, geopackage, vector tiles (code examples - at least of geojson)
    - Labels.
    - geometries and attributes
    - Features vs Vector Tiles
    - SVG
    - Pop-ups
    - Advantages and disadvantages
- Raster
    - Tiles
    - Placing tiles
    - Fetching tiles as we zoom
    - ZXY, WMTS 
    - Popular tile servers
    - Advantages and disadvantages
    - Digital elevation model and hillshade
- SVG, canvas, divs.

- Mapping terms
    - Map state: refers to the state of hte map visualization including zoom level, center or bounding box, pitch, bearing 
    - Zoom to or fly to
    - 

## How a typical web map works

1. Include div where map will be placed in HTML document
2. Initialize basemap. Create instance of map class - examples from Leaflet, Mapbox, etc. (Explain this uses raster tiles. <- does it also use vector tiles?). Include intial view parameters including where, zoom level etc. (Behind the scenes.)
3. Fetch and add custom layers.
4. Attach event listeners and do custom styling. 

⚠️ Asset management. Like any webpage, managing data fetched asynchronously can be tricky - especially true as map data can often be quite large. Using async await or promises helps this massively. 

## A basic web map

Code example loading raster basemap, placing vector features on top. 