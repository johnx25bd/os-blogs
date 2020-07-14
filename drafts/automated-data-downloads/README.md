# Automated Data Downloads

Data can be incredibly useful - by analysing or interpreting the information contained in data, better decisions can be made.

 Ordnance Survey is one of the world's oldest data organisations. OS has gathered information about Great Britain since 1791, organising, analysing and disseminating maps and other information. As information technologies have evolved from tables and charts and pen-and-paper calculations to databases, vector graphics and sophisticated machine learning algorithms, OS has been a leader in adopting and innovating new ways to capture, store, process and share valuable location information. 

 ## The Challenge

 As the scale of data grows, so does it's potential usefulness - and the complexity of managing it. Understanding a small table of numbers is easy - less so for a complex database with dozens of tables and millions of rows. With code, though, it has never been easier for programmers to retrieve and manipulate large volumes of data - and extract and understand the valuable information they contain. 

As every data scientist and web developer knows, well-structured datasets are difficult to find, and even harder to create. Data wrangling is a major task, and often overlooked by those less familiar with the data science process. For algorithms to extract accurate and meaningful information from a dataset - especially using a powerful analysis libraries openly available like Python's pandas - the data needs to be consistently structured and clean. 

## The Answer

Consistent with our tradition of working to make accurate and authoritative location data about Great Britain useful to our users and customers, Ordnance Survey is making a wide range of our datasets available for download over the web. Through the new [OS Data Hub](https://osdatahub.os.uk/), users can connect to one of a number of APIs, including the OS Maps, OS Vector Tile, OS Features, OS Names, OS Linked Identifiers and OS Downloads APIs. These resources serve OS data ranging from raster and vector map tiles to vector features to naming and identification data, or even full OS datasets. 

With the OS Maps, OS Vector Tile and OS Features APIs, users authenticate their request with an API key created on their Data Hub account, then can dynamically fetch the data they need when they need it. This is powerfully useful in web maps, data science workflows and desktop GIS applications. These APIs enable developers and spatial analysts to create and customise interactive maps, and to fetch location data with rich attribution - information about a feature useful for visualisation and analysis purposes. 

The OS Downloads API makes a number of OS OpenData datasets available for automated download over the internet. This new service makes collecting useful spatial data from Ordnance Survey as easy as pasting a URL, or sending an HTTP GET request. The [OS Downloads API documentation](https://osdatahub.os.uk/docs/downloads/gettingStarted) has sample code, and we've created a tutorial to help JavaScript developers fetch data programmatically with NodeJS. 

| Name | Description | Data structures | Formats |
| --- | --- | --- | --- |
| 1:250 000 Scale Colour Raster™ | Get the regional view of towns and villages, roads and places of interest. | Raster | TIFF-LZW |
| Boundary-Line™ | From Euro constituencies to council wards, Boundary-Line™ maps every administrative boundary in detail for you. | Vector | ESRI® Shapefile, GML, MapInfo® TAB, GeoPackage |
| Code-Point® Open | Get started with geographical analysis, simple route planning and asset management. | Vector | CSV, GeoPackage |
| GB Overview Maps | Our simplest maps of the British Isles. | Raster | GeoTIFF |
| MiniScale® | A simple overview map of Great Britain. | Raster | Zip file (containing EPS, Illustrator and TIFF-LZW) |
| OS Open GreenSpace | Covering a range of greenspaces in urban and rural areas including playing fields, sports’ facilities, play areas and allotments. | Vector | ESRI® Shapefile, GML, GeoPackage |
| OS OpenMap - Local | Map, visualise and truly understand your data at street level. | Raster, Vector | ESRI® Shapefile, GML, GeoTIFF, GeoPackage |
| OS Open Names | A comprehensive dataset of place names, roads numbers and postcodes for Great Britain. | Vector | CSV, GML, GeoPackage |
| OS Open Rivers | Understand how watercourses in Great Britain join up. | Vector | ESRI® Shapefile, GML, GeoPackage |
| OS Open Roads | Get a high-level view of the road network, from motorways to country lanes. | Vector | ESRI® Shapefile, GML, GeoPackage |
| OS Open ZoomStack | A comprehensive basemap of Great Britain showing coverage from national level right down to street detail. | Vector | GeoPackage, Vector Tiles |
| Strategi® | A regional vector map dataset, railways, airports, rivers, villages, woods, land use and place names. | Vector | DXF, ESRI® Shapefile, MapInfo® TAB |
| OS Terrain® 50 | Visualise simple landscapes in 3D and bring your geographic analysis to life. | Vector | ASCII Grid and GML (Grid), ESRI® Shapefile, GeoPackage, GML |
| OS VectorMap® District | Get started with geographical analysis, simple route planning and asset management. | Vector, Raster | ESRI® Shapefile, GeoTIFF, GeoTIFF, GML, GeoPackage |

## Unlocking value by improving access 

The OS Data Hub APIs are the result of a major effort at Ordnance Survey to make our National Geographic Database easier to access than ever before. A broad range of users in Great Britain - from civil servants to NGO workers, academic researchers, entrepreneurs and large companies - could enhance the quality and efficiency of their work with the insights they could derive from OS data. We're working hard to make sure the path from data to decisionmaking is as short as possible. Automated data downloads are one of the ways we're doing that. 

If you use OS data and want to learn if the OS Data Hub APIs could help, or think that having access to a high resolution dataset with over 500 million features in Britain might be useful - sign up for the OS Data Hub, or reach out on Twitter to [@OrdnanceSurvey](https://twitter.com/ordnancesurvey). 