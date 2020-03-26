# All about OS MasterMap Topo

Ordnance Survey is responsible for keeping accurate, up-to-date maps of Great Britain for use by the private, public and third sectors. 

Topography is "the arrangement of the natural and artificial physical features of an area" ([Oxford](https://www.lexico.com/en/definition/topography)) - and OS maps Britain's topography. Every day a team of surveyors, pilots and analysts explore the country to discover changes to the physical topography, take measurements and record these changes in a database. 

![photo!](photo of surveying plane!)

After much processing, tagging and organizing, OS makes this available as the most detailed, current and comprehensive map dataset of Great Britain: Ordnance Survey's MasterMap Topography Layer.

## What is OS MasterMap Topo?

The OS MasterMap Topography layer is Ordnance Survey's most detailed, current and comprehensive map dataset of Great Britain. 

The resource was created to provide businesses, governments and other organizations a detailed understanding of the country. The dataset is used by customers ranging from energy and utility companies to logistics firms, insurers, emergency service providers, government offices and so on.  

OS MasterMap Topo includes vector features - points, lines and polygons - with high accuracy and rich attribution. This includes information about geographic features like roads, buildings, natural spaces - plus cartographic elements like labels. 

## Opening up OS MasterMap Topo

[*** Why is OS opening this up? @Charley], Ordnance Survey is opening geospatial data, including OS MasterMap Topo, in new ways. Data that was previously only available for purchase will now be accessible through our OS Data Hub. Additionally, OS is launching a suite of APIs that enable users to access the data they need, when they need it, without the overhead of maintaining geospatial databases in-house. 

Now public and non-profits can access OS MasterMap Topo for free. And, for the first time, private sector users can access high resolution spatial data of GB for free, up to a significant threshold of usage. The goal is to enable innovation in spatial data visualization and analytics.

## Let's look at the data

So - what is in the OS MasterMap Topography layer? Defining some key terms will help.

### Features

Maps represent the world. On maps both real-world objects (like buildings and forests) and abstract objects (like constituency or ward boundaries) provide context for map users. Mapmakers capture these as location data, represented as "features". 

With OS MasterMap Topo, each feature is a record in a database. Each of these records has information about the feature's position and shape on Earth - its geometry - as well as details about it - called "attributes". Attributes add meaning to the geometry - describing a polygon as a building, road segment or piece of land, for example. 

The OS MasterMap Topography layer contains detailed features representing buildings, heritage & antiquities locations, roads, railways, water and much more. The OS MasterMap Sites layer includes  information about education, medical care, rail transport, road transport, water transport, utility, and industrial locations.

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

#### Identifying Features

The OS MasterMap Topo dataset is comprised of [ - How many features is OS MasterMap Topo @Charley? ] individual vector features, each assigned a unique Topographic Identifier, or TOID. This identifier is connected to that feature throughout it's lifespan and retired when the feature is removed ( [***retired?*** ]) - if, for example, a building is demolished. This persistent identifier is useful because it allows analysts, developers and data scientists cross-reference topographic features across datasets and over time. [*** Does HMLR use TOIDs? Other agencies that have adopted them? ] More on TOIDs can be found [here](https://www.ordnancesurvey.co.uk/business-government/tools-support/mastermap-topography-support/toids).

#### Building Height Attribute

Knowing the height of a building can be useful in many contexts, including analysis and visualisation. So, as a beta dataset, Ordnance Survey also offers building height attributes. This information is provided in a separate file with buildings referenced by TOID, enabling the two datasets to be easily joined. 

#### OS MasterMap Sites layer

Ordnance Survey data underpins many functions of services critical for British society to function. OS recognized the need for users to have information about key geographic sites, so we created OS MasterMap Sites. This layer provides details of important sites like access points. With this information emergency services can be more efficiently routed to the scene of an accident, mapping companies can provide more accurate directions and planners can have a better understanding of how a change in the road network might affect traffic. This data is accessible through OS Data Hub. [ *** Can OS MM Sites be accessed through Data Hub? @CHARLEY??? ].

--

Through the Data Hub, Ornance Survey is making it easier than ever to access the MasterMap Topography layer, Building Height Attribution, and OS MasterMap Sites layer. Our aim is to help users derive benefit from this rich trove of location data about Great Britain. You can learn more on the OS Data Hub [here](https://osdatahub.os.uk/).
