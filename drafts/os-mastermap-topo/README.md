# All about OS MasterMap Topo

Ordnance Survey is responsible for keeping accurate, up-to-date maps of Great Britain for use by the private, public and third sectors. 

Topography is "the arrangement of the natural and artificial physical features of an area" ([Oxford](https://www.lexico.com/en/definition/topography)) - and OS maps Britain's topography. Every day a team of surveyors, pilots and analysts explore the country to discover changes to the physical topography, take measurements and record these changes in a database. 

![photo!](photo of surveying plane!)

After much processing, tagging and organizing, OS makes this available as the most detailed, current and comprehensive map dataset of Great Britain: Ordnance Survey's MasterMap Topography Layer.

## What is OS MasterMap Topo?

The OS MasterMap Topography layer was created to provide businesses, governments and other organizations a detailed understanding of Britain. The dataset - which has been one of OS's premium products - is used by customers ranging from energy and utility companies to logistics firms, insurers, emergency service providers, government offices and so on.  

The dataset includes vector features - points, lines and polygons - with high accuracy and rich attribution. This includes information about geographic features like roads, buildings, natural spaces, [*** What other features? ] - plus cartographic elements like intentionally-placed labels. 

## Opening up OS MasterMap Topo



[*** Why is OS opening this up? @Charley], Ordnance Survey is opening geospatial data - including OS MasterMap Topo - in new ways. Data that was previously only available for purchase will now be accessible through our OS Data Hub. Additionally, OS is launching a suite of APIs that enable users to access the data they need, when they need it - without the overhead of maintaining geospatial databases in-house. 

Now public and non-profits can access OS MasterMap Topo for free. And, for the first time, private sector users can access high resolution spatial data of GB for free, up to a significant threshold of usage. The goal is to enable innovation in spatial data visualization and analytics.

## Let's look at the data

- Key terms: layers, features, attributes
    - Interesting layers, plus table of all layers ![img](graphic showing layers, features, attributes - build in illustrator?)


### Features

Maps represent the real world. A real-world object - a geographic entity that can be captured and represented in the data (from the [https://www.ordnancesurvey.co.uk/documents/os-mastermap-topography-layer-product-guide.pdf](Product Guide)) - is represented by a "feature" in OS MasterMap data. 

Each feature is a record in a database. Each of these records has information about the feature's position and shape on Earth - its geometry - as well as details about it - called "attributes". Attributes add meaning to the geometry - describing a polygon as a building, road segment or piece of land, for example. 

The OS MasterMap Topography layer contains detailed features representing buildings, heritage & antiquities locations, roads, railways, water and much more. The OS MasterMap Sites layer includes  information about education, medical care, rail transport, road transport, water transport, utility, and industrial locations.

So - what is in the OS MasterMap Topography layer?
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

The OS MasterMap Topo dataset is comprised of x individual vector features, each assigned a unique Topographic Identifier, or TOID. This identifier is connected to that feature throughout it's lifespan and retired when the feature is removed (***retired?) - for example, if a building is demolished. This persistent identifier is useful because it allows analysts, developers and data scientists cross-reference topographic features across datasets and over time. [*** Does HMLR use TOIDs? Other agencies that have adopted them? ] More on TOIDs can be found [here](https://www.ordnancesurvey.co.uk/business-government/tools-support/mastermap-topography-support/toids).

#### Building Height Attribute

Knowing the height of a building can be useful in many contexts, including analysis and visualisation. So, as a beta dataset, Ordnance Survey also offers building height attributes. This information is provided in a separate file with buildings referenced by TOID, enabling the two datasets to be easily joined. 

#### OS MasterMap Sites layer

Ordnance Survey data underpins many functions of services critical for British society to function. OS recognized the need for users to have information about key geographic sites, so we created OS MasterMap Sites. This layer provides details of important sites like access points. With this information emergency services can be more efficiently routed to the scene of an accident, mapping companies can provide more accurate directions and planners can have a better understanding of how a change in the road network might affect traffic. This data is accessible through OS Data Hub. [ *** Can OS MM Sites be accessed through Data Hub? @CHARLEY??? ].

## Questions

Do we use OS MasterMap Topo in OS Vector Tiles API? 

"In addition to the traditional GIS MasterMap Topo data users, Ordnance Survey is extending access to web developers and data scientists via rich APIs, now available in beta on the OS DataHub. With the OS Maps API users can access individual features or sets of up to 100 features based on semantic or geospatial queries."





## Call to Action: 

Check out the new APIs, available via the OS Data Hub.