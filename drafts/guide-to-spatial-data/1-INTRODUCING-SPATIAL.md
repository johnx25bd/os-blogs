
## Chapter 1: Introduction

What is a map? 

The purpose and goals of this guide.

Introducing data
- What is data?
- Structured vs unstructured data
- Tidy data
- Data types (?)
- Enter spatial: what is spatial data? 
- Raster and vector
    - Raster data
    - Vector data
        - Points, Lines, Polygons
- Why is spatial special?

---

Maps are incredibly useful things. We use maps to understand reality, to decide on where to navigate, make sense of where we are - without maps, we are, quite often, lost. Maps are tools we have come to rely on to survive and thrive. 

What is a map? [Wikipedia puts it concisely:](https://en.wikipedia.org/wiki/Map) "A map is a _symbolic depiction_ emphasizing _relationships_ between _elements_ of some _space_." This definition captures the breadth of things we describe as "maps": from the traditional - paper [LandRanger maps](https://www.ordnancesurvey.co.uk/shop/maps.html) hikers use to explore the Scottish Highlands - to the more conceptual - a mind map of ideas around a topic, or a site map of pages of a website, or a map representing a network of firms competing in a market. In every case, accurate maps can help us understand a space in a more complete way than we can by simply observing it directly. Mapmakers do this by designing abstract representations of the space and the features within it.

![Image of some map or maps. Embed? Gif?]()

This guide will focus on physical space, and symbolic depictions of physical space on the scale most familiar to humans: geographic maps. Ordnance Survey has been making maps and collecting location data [for centuries](https://www.ordnancesurvey.co.uk/about/history). We have always operating at the cutting edge of cartography, and remain committed to this tradition of innovation as we look forward into the 21st century. Our goal in creating this resource is to provide competent programmers and analytical thinkers a strong enough grounding in the _theory_ of spatial data to build and develop sophisticated _applied_ uses of spatial data. 

This is a practical guide. We are writing for an audience of web developers and data scientists - but the guide is intended to explain technical concepts in clear terms and be useful for non-technical audiences. We also link to external resources whenever possible, to give readers the ability to dig deeper into any of the topics covered.

## What is spatial data?

Before we can answer this question, it is worth defining another term - one that is very often glazed over. **What is _data?_**

Luciano Floridi - Professor of Philosophy of Information at Oxford - defines data as _a lack of uniformity_ (Floridi 2010). Data can be thought of as variations in physical matter - ink on a page, bumps on a silicon disk, pulses in an electrical current. Critically, these variations - the data - can contain information, or meaning.

Our focus here is on digital data, or, more specifically, binary data: data where variations represent individual symbols, 1s and 0s (also known as bits). The sequence of these bits (i.e. the variations in the data) encodes information that can be interpreted and processed.

[ am I losing the plot here ? 😂 ]

https://www.safe.com/what-is/spatial-data/

### Structure in data

Data can be "structured" or "unstructured" - that is, organised in a standardised way, or not. The Data Management Association specifies that unstructured data "has not been tagged or otherwise structured into rows and columns or records." ([Geospatial Commission 2020](https://www.gov.uk/government/publications/geospatial-glossary/geospatial-glossary)) This is relevant when we try to automate the processing of data - computers work very well with structured data, and have a harder time processing unstructured data.

Structured data organises information in a formal, consistent structure. These datasets are composed of "records", individual "observations" described in the data. These observations might represent any range of things - geographic features like road segments, train stations or post codes; financial transactions; human beings - just about anything you can imagine, physical or intangible. 

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

### Data Types, Briefly

A key insight: on computers, all of this information is represented in _binary format_. Data is encoded as sequences of **b**inary dig**its**, or **bits**. A bit is "a basic unit of information in information theory" ([Wikipedia](https://en.wikipedia.org/wiki/Bit#:~:text=The%20bit%20is%20a%20basic,a%20portmanteau%20of%20binary%20digit.)), a logical state with exactly two possible values. We can imagine these values as 1 or 0, yes or no, true or false, on / off, + or -. Sets of eight bits are called **bytes**.

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

Meaning - in UTF-8 encoding - "Ordnance Survey" is stored and transmitted as the 15 byte binary sequence `01001111 01110010 01100100 01101110 01100001 01101110 01100011 01100101 00100000 01010011 01110101 01110010 01110110 01100101 01111001`. (Conversion performed in JavaScript based on [this StackOverflow answer](https://stackoverflow.com/questions/18729405/how-to-convert-utf8-string-to-byte-array).)

UTF-8 is a global standard used across the Internet. Try pasting the sequence above into the "binary bits" field on [onlineutf8tools.com](https://onlineutf8tools.com/convert-binary-to-utf8). As long as the software has the UTF-8 encoding, it will correctly decode this binary sequence as "Ordnance Survey". (Note that lower case "o" and capital "O" must be represented as different bytes.)

Similarly, audio can be representing digitally by using audio coding formats like MP3, AAC, FLAC. These formats encode the "audio information in terms of frequencies and amplitudes" ([Wikipedia](https://en.wikipedia.org/wiki/MP3)). Images can also be represented digitally in binary - we'll go over how shortly. 

Interestingly - _the same byte can have different meanings depending on the encoding!_ A byte - `0100 1111` might mean the character "O" in UTF-8 - but it also represents the unsigned integer 79. The computer processes each bit in this context - according to its 'data type'. In strongly-typed programming languages, when a variable is declared, developers need to declare the data type of that variable - `uint`, `float`, `char`, `bool`. Dynamically-typed languages like JavaScript and Python are more flexible, can be easier to code in, and perhaps more error prone. This is because variables can be reassigned to a value of another type - and the computer can *usually* adapt accordingly. 

[ too much? not enough? ]

For the encoded information to be useful, it needs to be parsed and interpreted by a computer processor. This would include displaying the characters or images visually on a screen, or sending a signal to an audio speaker that would create the sounds encoded. 

### 🌐 Enter spatial 

So: what is _spatial data_?

Spatial data is any data that contains information about where observations are. Usually, this means that **one of the dimensions associated with each observation describes that record's position in space.**

So, if we look back at the table we saw earlier - but as a spatial dataset:

| id | name | age (years) | favorite_color | has_smartphone | coordinates `[lat, lon]` | city |
| --- | --- | --- | --- | --- | --- | --- |
| 0 | "Helena Espinosa" | 29 | "blue" | true | `[-5.930, 54.596]` | Belfast |
| 1 | "Dorian Beach" | 17 | "green" | false | `[3.189, 55.953]` | Edinburgh |
| 2 | "Lukas Craft" | 44 | "purple" | false | `[-3.183, 51.483]` | Cardiff |
| 3 | "Vishal Needham" | 83 | "grey" | true | `[-0.128, 51.507]` | London |
(Coordinates from Wikipedia.)

By including the geographic coordinates in the dataset, it becomes spatial data. With this additional dimension, much deeper insights about the records in a dataset - and their relationships - can often be drawn. In fact, often the spatial dimension is the key to understanding relationships and answering questions an analyst might want to understand.

### Raster and Vector

Spatial data typically falls into two categories: raster and vector. Both are ways to describe space and represent features, but they work quite differently.

#### Raster Data

A raster is a “grid of regularly sized pixels”. By assigning each cell in the grid a value — or a few values — images can be described numerically, as multidimensional arrays.

For example, take a 3x3 grid that looked like this:

![A raster grid](./assets/raster.png)

_A 3x3 raster grid._

If 1 means black and 0 means white, we could represent it numerically like this:

```
img = [[ 1, 0, 1 ],
       [ 0, 1, 0 ], 
       [ 1, 0, 1 ]]
```

The numbers in raster cells can mean lots of things — the altitude of the land or depth of the sea at that specific point, the amount of ice or snow on that point, the number of people living within that pixel, and so on. Further, just about any color in the visible spectrum can be described by a combination of three numbers representing the intensity of Red, Green and Blue (RGB) — satellite images are raster data structures. GeoTiff, jpg, png and bitmap files contain raster data.

[ image ]

_A raster image of population in Africa, from http://www.ncgia.ucsb.edu/pubs/gdp/pop.html._

### Vector Data

Vector data is a bit more abstract. In a vector dataset, features are individual units in the dataset, and each feature typically represents a point, line or polygon. These features are represented mathematically, usually by numbers that signify either the coordinates of the point, or the vertices (corners) of the geometry.

Image for post

_Vector features from Saylor Academy._

#### Points, Lines, Polygons
As a quick example, here’s a bare-bones numerical representation of each of these types of features:

```
point =   [ 45.841616, 6.212074 ]

line =    [[ -0.131838, 51.52241 ],
           [ -3.142085, 51.50190 ],
           [ -3.175046, 55.96150 ]]

polygon = [[ -43.06640, 17.47643 ],
           [ -46.40625, 10.83330 ],
           [ -37.26562, 11.52308 ],
           [ -43.06640, 17.47643 ]]
           // ^^ The first and last coordinate are the same
```

Vector features will often have some metadata included that describes the feature — the name of a road, say, or the population of a state. These extra, non-spatial metadata of a feature are usually called “attributes”, and are often represented in an “attribute table”. Very often spatial data scientists will combine the spatial dimensions (coordinates — for points, or coordinate arrays — for lines and polygons) with non-spatial dimensions in their analysis. GeoJSON and .shp files commonly contain vector data.

### Why is spatial special?

In the spatial data community you'll often hear the phrase "spatial is special". Why is this? 

Very often - in the physical world, at least - location matters. Events near one another tend to be more correlated that with distant ones, a phenomenon captured in Waldo Tobler's First Law of Geography: "Everything is related to everything else, but near things are more related than distant things." ([Wikipedia](https://en.wikipedia.org/wiki/Tobler%27s_first_law_of_geography#:~:text=The%20First%20Law%20of%20Geography,specifically%20for%20the%20inverse%20distance)) 

Because of this 'spatial autocorrelation', special statistical techniques are required to draw meaningful insights out of spatial datasets. 

> **Further Reading:** 
> 
>  [Modifiable unit areal problem (MAUP)](https://en.wikipedia.org/wiki/Modifiable_areal_unit_problem#:~:text=The%20modifiable%20areal%20unit%20problem%20(MAUP)%20is%20a%20source%20of,population%20density%20or%20illness%20rates.)<br />
>  
> MORE HERE!!