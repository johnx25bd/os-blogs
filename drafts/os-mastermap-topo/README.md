# OS MasterMap Topo

All about OS MasterMap Topo (including Sites and Building Height Attribute)

## Intro 

Ordnance Survey is responsible for keeping accurate, up-to-date maps of Great Britain. Every day a team of surveyors, pilots and analysts explore the country to discover changes to the physical topography, and record these changes in a database. After much processing, tagging and organizing, OS makes this available to the public as the most detailed, current and comprehensive map dataset of Great Britain: Ordnance Survey's MasterMap Topography Layer.

## What is OS MasterMap Topo?

The OS MasterMap Topo product was created in x, designed to serve x and y users. The problem was xx - OS MasterMap Topo solved this by x. 
- How it is created.
Every day OS has x surveyors and y planes captured high resolution data of the Great Britain's topography. This data is x y z collection, analysis, warehousing, delivery. ![photo!](photo!)
- How data has been and is being used
OS MasterMap Topo data has been used by x to y (interesting story - emergency services? Environmental? Law enforcement? Utilities?) 
- Now: opening geospatial data
    - Why? 
    - The opportunity - public and non-profits for free. And, for the first time, private sector users can access high resolution spatial data of GB for free, up to a significant threshold of usage. The goal is to enable innovation in spatial data visualization and analytics.

## Let's look at the data

- Key terms: layers, features, attributes
    - Interesting layers, plus table of all layers ![img](graphic showing layers, features, attributes - build in illustrator?)


### Features

Maps represent the real world. A real-world object - a geographic entity that can be captured and represented in the data (from the [https://www.ordnancesurvey.co.uk/documents/os-mastermap-topography-layer-product-guide.pdf](Product Guide)) - is represented by a "feature" in OS MasterMap data. 

You can think of a feature as a record in a database. (Diagram) Each feature has a number of characteristics or details - called "attributes". One of these attributes describes the geometry of the feature. Depending on the feature type, the real-world object will be represented as a point, line or polygon. 

As an example, in OS MasterMap Topo x features represent y. Here is what they look like .... ***

 Real-world features are described mathematically by using numbers to specify where they exist in space - on the Earth's surface. Points are represented by [x, y] - or [longitude, latitude] - coordinates. Lines are an ordered series of points, and polygons are series of points where the last one closes the shape, back where it started.

// What resolution is OSMMT? What does that mean? 

#### Other Attributes

Each feature is tagged with several attributes - contextual information like xxxx. These attributes are useful for analysts, visualizers and cartographers, etc ...

#### The TOID

Unique ID

#### Building Height Attribute

Beta dimension.

### Themes

In OS MasterMap Topography Layer, features are grouped into themes, such as buildings, land and water and so on, to enable more flexible data selection by customers.






## Questions

Do we use OS MasterMap Topo in OS Vector Tiles API? 

"In addition to the traditional GIS MasterMap Topo data users, Ordnance Survey is extending access to web developers and data scientists via rich APIs, now available in beta on the OS DataHub. With the OS Maps API users can access individual features or sets of up to 100 features based on semantic or geospatial queries."





## Call to Action: 

Check out the new APIs, available via the DataHub.