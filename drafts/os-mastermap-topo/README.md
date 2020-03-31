# All about OS MasterMap Topo

Ordnance Survey is responsible for keeping accurate, up-to-date maps of Great Britain for use by the private, public and third sectors.

Topography is &quot;the arrangement of the natural and artificial physical features of an area&quot; ([Oxford](https://www.lexico.com/en/definition/topography)) - and OS maps Britain&#39;s topography. Every day a team of surveyors, pilots and analysts explore the country to discover changes to the physical topography, take measurements and record these changes in a database.

![OS Surveyor Aircraft](https://www.ordnancesurvey.co.uk/blog/wp-content/uploads/2012/02/2007-07-19-G_NOSE_03.jpg)

After much processing, tagging and organizing, OS makes this available as the most detailed, current and comprehensive map dataset of Great Britain: Ordnance Survey&#39;s MasterMap Topography Layer.

## What is OS MasterMap Topo?

The OS MasterMap Topography layer is Ordnance Survey&#39;s most detailed, current and comprehensive map dataset of Great Britain.

The resource was created to provide businesses, governments and other organizations a detailed understanding of the country. The dataset is used by customers ranging from energy and utility companies to logistics firms, insurers, emergency service providers, government offices and so on.

OS MasterMap Topo includes vector features - points, lines and polygons - with high accuracy and rich attribution. This includes information about geographic features like roads, buildings, natural spaces - plus cartographic elements like labels.

## Opening up OS MasterMap Topo

Supporting a mandate &quot;[to unlock the government&#39;s mapping and location data to boost the economy by £130m a year](https://www.ordnancesurvey.co.uk/business-government/tools-support/open-mastermap-programme)&quot;, Ordnance Survey is opening geospatial data, including OS MasterMap Topo, in new ways. Data that was previously only available for purchase will now be accessible through our OS Data Hub. Additionally, OS is launching a suite of APIs that enable users to access the data they need, when they need it, without the overhead of maintaining geospatial databases in-house.

Now public and non-profits can access OS MasterMap Topo for free. And, for the first time, private sector users can access high resolution spatial data of GB for free, up to a significant threshold of usage. The goal is to enable innovation in spatial data visualization and analytics.

## Let&#39;s look at the data

So - what is in the OS MasterMap Topography layer? Defining some key terms will help.

### Features

Maps represent the world. On maps both real-world objects (like buildings and forests) and abstract objects (like constituency or ward boundaries) provide context for map users. Mapmakers capture these as location data, represented as &quot;features&quot;.

With OS MasterMap Topo, each feature is a record in a database. Each of these records has information about the feature&#39;s position and shape on Earth - its geometry - as well as details about it - called &quot;attributes&quot;. Attributes add meaning to the geometry - describing a polygon as a building, road segment or piece of land, for example.

The OS MasterMap Topography layer contains detailed features representing buildings, heritage &amp; antiquities locations, roads, railways, water and much more. The OS MasterMap Sites layer includes information about education, medical care, rail transport, road transport, water transport, utility, and industrial locations.

![OS MasterMap Topo](https://ordnancesurvey.co.uk/image-library/products/osmm-topo-lambeth.xa1b02a96.jpg?w=1000&q=100)

OS MasterMap Topography layer includes:

- Administrative boundaries like parliamentary constituencies and wards
- Buildings
- Heritage and antiquities sites
- Land and landforms like parks, golf courses, slopes, cliffs, gardens and woodlands
- Railways
- Roads, tracks and paths
- Structures like fountains, pylons, weirs and glass houses
- Triangulation stations and other point height features
- Ponds, lakes, tidal gauges and other water features

For a more detailed specification of the OS MasterMap Topography layer, read the [product guide](https://www.ordnancesurvey.co.uk/documents/os-mastermap-topography-layer-product-guide.pdf).

#### **Identifying Features**

The OS MasterMap Topo dataset is comprised of 500 million individual features, each assigned a unique Topographic Identifier, or TOID. This identifier is connected to that feature throughout its lifespan and retired when the feature is removed - if, for example, a building is demolished. This persistent identifier is useful because it allows analysts, developers and data scientists cross-reference topographic features across datasets and over time. More on TOIDs can be found [here](https://www.ordnancesurvey.co.uk/business-government/tools-support/mastermap-topography-support/toids).

#### **Building Height Attribute**

Knowing the height of a building can be useful in many contexts, including analysis and visualisation. So, as a beta dataset, Ordnance Survey also offers building height attributes. This information is provided in a separate file with buildings referenced by TOID, enabling the two datasets to be easily joined.

![OS Building Height Attribute](https://ordnancesurvey.co.uk/image-library/banners/osmm-topo-and-build-heights-place1.xaa2e6841.jpg?w=1000&q=100)

#### **OS MasterMap Sites layer**

Ordnance Survey data underpins many functions of services critical for British society to function. OS recognized the need for users to have information about key geographic sites, so we created OS MasterMap Sites. This layer provides details of important sites like access points. With this information emergency services can be more efficiently routed to the scene of an accident, mapping companies can provide more accurate directions and planners can have a better understanding of how a change in the road network might affect traffic. This data is accessible through OS Features API, on the Data Hub.

## Accessing OS MasterMap Topo

Through the Data Hub, Ordnance Survey is making it easier than ever to access the MasterMap Topography layer, Building Height Attribution, and OS MasterMap Sites layer. OS Maps API provides a pre-rendered map on which you can overlay your own data to give it detailed location context. OS Features API allows users to access the features they need, when they need it - including rich attributes. And OS Vector Tiles API lets users access customisable, scalable, detailed backdrop map data in a lightweight format.

Our aim is to help users derive benefit from this rich trove of location data about Great Britain. You can learn more on the OS Data Hub [here](https://osdatahub.os.uk/).