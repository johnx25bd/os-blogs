# 4: Spatial for Web Developers

How a web map works: emphasising VISUALISATION.
- This guide is generalizing for Leaflet, Mapbox and OpenLayers.
    - Observable cells that mean you can select which library you want and all examples update? :D this would be coooool.

- A number of ways to create a map in a web page.
- The process usually follows a general pattern: 


1. Set up HTML structure, with an element to hold the map
2. Import / set CSS rules
3. Execute JavaScript, which:
    1. Defines parameters, including keys, endpoints and other options 
    2. Creates a new `Map` instance
        - Must identify containing DOM element 
    3. Adds layers (raster and vector)
    4. Sets event listeners / interactivity


## HTML

HTML defines the structure of a web page, and a web map occupies a part of that structure. Commonly, an HTML `<div>` element is created and positioned where the map is meant to go.
- A common practice is to set `id="map"`, but this is not required. Multiple map instances can be loaded in the same DOM, as long as nodes containing the map are uniquely identified. (Here we'll refer to a `#map` div, but bear in mind it doesn't need to have that id.)
- As standard with any HTML document, typically CSS files are loaded in the `<head>` and JavaScript files are loaded just before the closing body tag. 
- ⚠️: Sometimes JS libraries extend others, so pay attention to the order in which you import external dependencies. Example: [Leaflet geocoder extension](https://labs.os.uk/public/os-data-hub-examples/os-names-api/find-example-geocoder).

```html
<!DOCTYPE html>
<html>
<head>
    <title>OS Maps API | Basic Map ZXY (EPSG:3857) | Leaflet</title>
    <meta charset="utf-8" />
    <meta name="referrer" content="strict-origin-when-cross-origin" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" />
    <style>
        /* Styles will go here */
    </style>
</head>
<body>

<div id="map"></div>

<script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
<script>

// JS will go here

</script>

</body>
</html>



```

## CSS

For most mapping libraries to work (including Leaflet, Mapbox GL JS and OpenLayers), a CSS library is required. This defines the rules that make sure that all elements that are created when a new map instance is created are positioned and styled correctly. 
- ⚠️: If you map and tiles are loading but look wonky and out of place, make sure you are importing the library's CSS file in the `<head>`
    - image of map without stylesheet? Or embed??

In addition to the library stylesheets that must be imported, developers often need to write their own CSS rules for the map instance to work. Typically, these CSS rules define the position and size of the `#map` div: 

```css
#map {
    position:absolute; 
    top:0; 
    bottom:0; 
    width:100%; 
}
```

## JavaScript

With this HTML structure and these CSS rules in place, we are ready to programmatically create and work with our map using JavaScript. 

The typical workflow relies on a few steps happening in a specific order. Broadly, we define some parameters, create a map instance, then set up the instance by adding layers and event listeners. 

First, the code. Then, each step:

```javascript
// Leaflet

// 1. Set parameters
var apiKey = 'OS_DATA_HUB_API_KEY_HERE';
var serviceUrl = 'https://api.os.uk/maps/raster/v1/zxy';
var mapOptions = {
    minZoom: 7,
    maxZoom: 20,
    center: [ 54.425, -2.968 ],
    zoom: 14,
    attributionControl: false
};

// 2. Initialise the map
var map = L.map('map', mapOptions);

// 3. Add ZXY tile layer on the map.
var basemap = L.tileLayer(serviceUrl + '/Light_3857/{z}/{x}/{y}.png?key=' + apiKey, {
    maxZoom: 20
}).addTo(map);

// 4. Add event listeners ...
    // ...

```

### 1. Define parameters

- API key
- Endpoints. This is where the mapping data will be served from - these endpoints, along with information about what type of service is available, is provided to the `Map` instance. (These could be hosted locally! Just must be available through HTTPS (@TIM - true?))
- Stylesheet. For vector tiles. The stylesheet will actually include the VTS endpoint in Mapbox GL JS. (Do we want to go into such detail for individual libraries?) (If Observable: give users the option to examine a sample Mapbox stylesheet.)
- The initial position of the viewport - `center` and `zoom` (or bbox?). 
    - 🔑: the viewport. All map data is available on the server - the viewport is set to only view a few tiles. The JS library requests the appropriate tiles from the server based on initial map state and user interaction.)
- Limits like `minzoom`, `maxzoom` 

### 2. Create a new `library.Map` instance

- Instantiate map 
    - Assign to a variable (often `var map = /* map instance */`, so you can interact with it in subsequent lines
    - Pass in parameters
    - API: ZXY or WMTS - affects parameters and instantiation, but functionally is very similar (@TIM what are differences?)
- Voila!

### 3. Add layers

- Create new layers, possibly with GeoJSON, or other raster or vector tile sources
    - Working with vector tiles, raster tiles, vector geometries, local raster images? 
- Add to map!
- (Sometimes manually adding these layers are required to see anything on the map (Leaflet), sometimes the baselayer is automatically added and visualised when the map is instantiated.)

### 4. Set event listeners / interactivity

- The `map` object has methods that enable you to attach event listeners to layers, and even individual features (@TIM - true? Easy? Link?)
- Table: interaction types like `mouseenter`, `mouseleave`, `click`, `load`, `style.load`, etc. 

> ⚠️: Managing asynchronicity. These operations can take some time - fetching data can be slow. Some processes can be run in parallel (@TIM - is this an accurate use of this term?) - but other lines of code rely on preceding operations to be complete. Keep an eye on asset lifecycle management. Promises and async/await syntax are very useful here. Also you can attach event listeners to `map` instances, so code is only run when that event is detected - like the full map `load`ing, only the `style.load`ing, or a user `click`ing. [Blog](https://www.programmableweb.com/news/four-tips-developers-should-follow-when-building-location-based-apps/analysis/2020/09/02).

- links to code examples where we set event listeners etc on features - [National Park Locator](https://www.programmableweb.com/news/four-tips-developers-should-follow-when-building-location-based-apps/analysis/2020/09/02) etc.

## Canvas vs alternatives

- WebGL 
- png tiles as HTML elements
- SVG overlays in D3 ([tutorial](https://labs.os.uk/public/os-data-hub-tutorials/web-development/d3-overlay)).
- Pros and cons of each

## Back end / front end

- Once you have a map instance created and have connected to a tile server, you have a basemap. What if you have additional geographic data - perhaps user-created - that you want to add to the map? You'd most likely need to have a back end database capable of storing and accessing geographic features or satellite images. This could be a PostGIS instance running on a web server - or maybe a cloud-optimized geotiff - any number of options.

- Anything special about ES6 and using `require` / webpack with mapping libraries? 

## Useful tools: Libraries, utilities, frameworks (table: name, link, function)

Leaflet, Mapbox, OpenLayers, Proj4, vt2geojson etc etc - what do we want to capture here? 

Other tools for working with spatial data.




