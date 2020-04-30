# The Benefits of Vector Tiles

_Fast, customisable, versatile web maps_

Web mapping has come a long way since the first map server was built in 1993 at the famed Xerox Palo Alto Research Center. Since then, users have come to expect intuitive, beautiful and blazing fast maps on their desktop and mobile devices.

## Why Tiles?

The typical modern map user accesses map data on devices that typically don't have the storage capacity for high resolution maps of the entire world. Instead, apps and websites show mapping data that is served as needed over the web. 

When a web map is loaded, it is set to a zoom level and extent, which defines the level of detail and the area that will be visible in the viewport. A map server sends grid sections of the map, called "tiles", to the client, where they are arranged in the right configuration to appear as a map. As the user pans and zoom in and out, requests for the correct tiles are sent, and the response is used to update the screen.

(image of tiles)

## Raster and Vector

Location data comes in two broad forms. **Raster** data represents space as grids of regular pixels. By assigning each pixel in the grid a value — or a few values — images can be described with numbers. This is useful because it means images can be represented, processed and stored by computers as **bits**, or **bi**nary dig**its**. 

A raster tile service (like the OS Maps API) serves binary data representing these raster (png) images to a mapping client, where they are processed and displayed on the screen for the user. 

Raster tiles are created by rendering a dataset of spatial vector features on the server based on a style - in our case, a style designed by OS cartographers. 

So - what is vector spatial data? 

**Vector** data is a bit different, in a subtle way. Rather than representing space in a regular grid, entire geographic features are represented mathematically. Points are stored as [x,y]  (or [longitude, latitude]) coordinate pairs; Lines as arrays (or sequences) of coordinate pairs; and Polygons as sequences of coordinate pairs that end where they start. For lines and polygons each coordinate pair represents a vertex, or corner, of a shape - this sequence of numbers can represent geographic features like rivers, buildings or rail stations at a range of resolutions.

Feature types are organised in layers. For example, a layer of LineStrings might represent railways, while another might represent country borders. The feature type is described in the layer metadata, enabling web mappers and data scientists to identify what each feature represents, and style or analyse it accordingly.

Just like with raster data, vector data can be represented in binary, and therefore stored and processed by computers. 

## Vector Tiles

Vector tiles are exactly that: clipped tiles, or grid squares, composed of layers of vector features. They are served in a similar way to raster tiles - a client application requests tiles based on a zoom level and extent, and the server responds with binary data representing the vector tiles containing the layers to be visualised on that map. 

Rendering is done in the client. As personal computers and mobile phones have gotten more powerful, vector tiles have become an increasingly attractive way to create interactive web maps. But why?

## The Benefits of Vector Tiles

Vector tiles offer a number of advantages over raster map tiles for web mappers. 

First: they can be customised extensively by the user. Styles can be customised, and even adapted based on user interaction - to highlight a particular layer or feature, for example. Because they are rendered in the client, custom styles can be defined and applied when the map is created. Designers can adapt the style of their maps so the match organisational colour schemes. (Check out [Maputnik](https://maputnik.github.io/) for a great tool to create vector tile styles.)

Second: maps made with vector tiles are fast. A vector tile service will send much less data than a raster service would send for the same map - meaning lower bandwidth use, and lower disk space requirements. Features are represented in a very lightweight manner, and styles are only defined once, then applied to a layer no matter how many features. This makes vector tile maps great for mobile and low-bandwidth uses.

Additionally, vector tile maps have a much smoother zooming effect than raster services. Because raster data is represented as pixels, maps can get grainy as a user zooms in, until a higher-resolution tile is received from the server. Vector tiles instead maintain a smooth zooming and scaling effect.

Another major advantage of vector tiles (which include labels as vector features): rotation, tilting and other 3D effects are possible. Buildings can be extruded to create 3D cities and camera pitch can be adjusted to give the effect of looking across land, rather than only straight down on it. 

Vector tile maps are well supported, and can be developed with common mapping libraries including [Leaflet.js](https://leafletjs.com/), [Mapbox GL JS](https://docs.mapbox.com/mapbox-gl-js/api/), [OpenLayers](https://openlayers.org/) and the [ArcGIS API for JavaScript](https://developers.arcgis.com/javascript/). 

One last advantage: vector features are often served with some attribution. This means that features include some metadata, which are properties that describe or identify the feature. Many vector tile services include minimal attribution data to make sure maps load quickly, but with even minimal attribution map developers can apply styles and interactivity to vector features that are not possible with raster maps.

## Vector Tiles from Ordnance Survey

With all these advantages, vector tile maps are a must-know for any modern web map developer. With Ordnance Survey's [Vector Tiles API](https://osdatahub.os.uk/docs/vts/overview), available on the [OS Data Hub](https://osdatahub.os.uk/), developers can create these fast and versatile maps of Great Britain. All that is needed is an API key!