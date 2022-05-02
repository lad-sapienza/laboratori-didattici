---
tags:
  - vectors
---
# Gestione vettori
A differenza di altri ambienti software che gestiscono grafica vettoriale, i GIS si caratterizzano per la forte associazione tra geometrie e dati testuali, organizzati in formato tabellare, associati tra loro.

Dal punto di vista delle geometrie che contengono, i file vettoriali possono rappresentare:

#### Punti
Zero-dimensional points data is most commonly used to represent nonadjacent features and geographical features that can be expressed by single point and to represent discrete data points. Points have zero dimensions, therefore you can measure neither length or area with this dataset. Examples would be schools, points of interest, wells, peaks. Points features are also used to represent areas when displayed at a small scale and abstract points. For instance, point locations could represent city locations or place names. Measurement is not possible by using point data.
    
#### Linee
Line (or arc) or Polyline data is used to represent linear features. Common examples would be rivers, railroads, trails, streets and topographic lines. Liner features are displayed at a small scale and it only have one dimension and therefore can only be used to measure length.  Line features have a starting and ending point. Common examples would be road center-lines and hydrology. Line features can measure distance.
    
#### Poligoni
Two-dimensional polygons are used to represent areas such as the boundary of a city (on a large scale map), lake, or forest.  Polygon features are two dimensional and therefore can be used to measure the particular area and perimeter of a geographic feature. Polygon features are most commonly distinguished using either a thematic mapping symbology (color schemes), patterns, or in the case of numeric gradation, a color gradation scheme could be used. Polygons convey the most amount of information of the file types. Polygon features can measure perimeter and area.
    
Per quanto riguarda i tipi di file, i principali sono
### Shapefile
The Shapefile format is a popular geospatial vector data format for geographic information system (GIS) software for storing the location, shape, and attributes of geographic features. It is developed and regulated by Esri as a (mostly) open specification for data interoperability among Esri and other GIS software products.  
    A Shapefile is stored in a set of related files and contains one feature class. The Shapefile is BY FAR the most common geospatial file type you’ll encounter. It’s become the industry standard. You’ll need a complete set of files that are mandatory to make up a Shapefile.
    
The required files are:
- **shp** is a mandatory Esri file that gives features their geometry. Every Shapefile has its own .shp file that represent spatial vector data. For example, it could be points, lines and polygons in a map.
- **shx** are mandatory Esri and AutoCAD shape index position. This type of file is used to search forward and backwards.
 - **dbf** is a standard database file used to store attribute data and object IDs. A .dbf file is mandatory for shape files. You can open .DBF files in Microsoft Access or Excel.
 - **prj** is an optional file that contains the metadata associated with the shapefiles coordinate and projection system. If this file does not exist, you will get the error “unknown coordinate system”. If you want to fix this error, you have to use the “define projection” tool which generates .prj files.
 -**xml** file types contains the metadata associated with the shapefile. If you delete this file, you essentially delete your metadata. You can open and edit this optional file type (.xml) in any text editor.
- **sbn** is an optional spatial index file that optimizes spatial queries. This file type is saved together with a .sbx file. These two files make up a shape index to speed up spatial queries.
- **sbx** are similar to .sbn files in Which they speed up loading times. It works with .sbn files to optimize spatial queries. We tested .sbn and .sbx extensions and found that there were faster load times When these files existed. It was 6 seconds faster (27.3 sec versus 33.3 sec) compared with/without .sbn and .sbx files.
- **cpg** are optional plain text files that describes the encoding applied to create the Shapefile. If your Shapefile doesn’t have a cpg file, then it has the system default encoding.
    
### ArcInfo Coverage
This is a data model for storing geographic features using ArcInfo software. A coverage stores a set of thematically associated data considered to be a unit. The ArcInfo coverage GIS format is a georelational data model that stores vector data. It has no extension, just a set of folders. Coverages use feature classes, stored as points, arcs, polygons or annotation. Feature attributes are stored in the ArcInfo Coverage’s .adf or INFOb files. It is stored as a directory. Each feature is identified with a unique number. These feature numbers are a way to link attribute data with each spatial feature.

### OGC Geopackage
GeoPackage is an open, standards-based, platform-independent, portable, self-describing, compact format for transferring geospatial information. The GeoPackage Encoding Standard describes a set of conventions for storing the following within an SQLite database: vector features, tile matrix sets of imagery and raster maps at various scales.

#### PostGIS
PostGIS is a spatial database extender for PostgreSQL object-relational database. It adds support for geographic objects allowing location queries to be run in SQL. In addition to basic location awareness, PostGIS offers many features rarely found in other competing spatial databases such as Oracle Locator/Spatial and SQL Server.

### Spatial Database engine (ArcSDE)
ArcSDE serves data in a centralized way over an entire organization using a relational database management system. GIS users can seamlessly access spatial data using Esri ArcMap, ArcEditor, ArcInfo and other products.  
ArcSDE facilitates versioned editing with multiple users over the same network. Users can easily publish to the web. ArcSDE geodatabases with several DBMS storage models including Oracle, Microsoft SQL Server, IBM DB2, IBM Informix and PostgreSQL.
    
### GeoJSON
 GeoJSON is a lightweight format based on JSON, used by many open source GIS packages. GeoJSON’s feature includes points, line strings, polygons and multipart collection of these types. Therefore it represents addresses, locations, streets, highways, countries, tracts of lands and many like this. GeoJSON features doesn’t only represent physical world but mobile routing and navigation apps also describe their service coverage using GeoJSON.
    
### AutoCAD DXF
AutoCAD Drawing Interchange File (DXF) is an exchange format for content of AutoCAD Drawing Files (DWG). The DXF format specification is maintained and has been openly published by AutoDesk. DXF coordinates are always without dimensions so that the reader or user needs to know the drawing unit or has to extract it from the textual comments in the sheets.  It does not have topology, but offers good detail on drawings, line widths and styles, colors, and text. DXF is typically constructed in 64 layers. Each layer consists of different features; allowing the user to separate features.
    
### Keyhole Markup Language (KML)
This GIS format is XML-based and is primarily used for Google Earth. KML was developed by Keyhole Inc which was later acquired by Google. KML is an XML notation for expressing geographic annotation and visualization within two-dimensional maps and three-dimensional browsers.  
KML has its own zipped version KMZ (KML-Zipped) which replaced KML and now is the default Google Earth geospatial format because it is much compressed version. KML is an international standard of OGC. KML specifies an interesting set of feature like place marks, image, polygons, textual description and many for displaying in many geospatial software. KML comes with an extension ._kmz ._

### Esri TIN
 Triangular irregular networks (TIN) are a digital means to represent surface morphology. This format can spatially describe elevation information including breaking edge features. TINs are a form of vector-based digital geographic data and are constructed by triangulating a set of vertices (points). The vertices are connected with a series of edges to form a network of triangles. Each points and triangle can carry a tag information. A TIN stored in this file format can have any shape, cover multiple regions (e.g. islands) and contain holes (e.g. lakes).
    
### Geography Markup Language (GML)
The Geography Markup Language (GML) is an XML grammar defined by OGC for expressing geographical features. The GML specification defines (a) a language for expressing application schemas for feature types and (b) predefined properties and schemas commonly required to describe geographical features, such as polygons, curves, points, coordinate reference systems, units of measure, observations, coverages, etc. GML serves as a language for geographic systems as well as an open interchange format for geographic transactions.  
GML has the ability to integrate all forms of geographic information, including not only conventional “vector” or discrete objects, but coverages and sensor data.
    
### SpatiaLite
SpatiaLite is an open source library intended to extend the SQLite core to support fully fledged Spatial SQL capabilities. It is similar to PostGIS, Oracle Spatial, and SQL Server with spatial extensions, although SQLite/SpatiaLite aren’t based on client-server architecture: they adopt a simpler personal architecture. SpatiaLite is smoothly integrated into SQLite to provide a complete and powerful Spatial DBMS (mostly OGC-SFS compliant). It isn’t necessary to use SpatiaLite to manage spatial data in SQLite, which has its own implementation of R-tree indexes and geometry types. But SpatiaLite is needed for advanced spatial queries and to support multiple map projections.
    
### OSM (OpenStreetMap)
OpenStreetMap is the largest crowdsourcing GIS data project of the planet Earth.  
The GIS format .OSM is OpenStreetMap’s XML-based file format. The more efficient, smaller PBF Format (“Protocolbuffer Binary Format”) is an alternative to the XML-based format.  
The data interoperability in QGIS can load native .OSM files. The OpenStreetMap plugin can convert PBF to OSM, which then can be used in QGIS.
    
### Scalable Vector Graphics
An SVG is an image that is an extension of the XML language. Any program that recognizes XML can display the SVG image. The scalable part of the term emphasizes that you can zoom- in on an image and not lose resolution. SVG files also have the advantages of being smaller, and arriving faster, than conventional image files such as GIF, PDF, and JPEG.
   
### MapInfo TAB format
The MapInfo TAB format is a popular data format for GIS software. It is developed and regulated by MapInfo Corporation as a proprietary format. MapInfo Professional data set should relate to the two basic environments for working in MapInfo; “Browser View” and “Mapper View” as a basic file component. This environment provides storage of attribute or object data and is represented like a spreadsheet. In this simplified scenario, no geographic information is available. And the minimum files required for the basic MapInfo environment are .TAB and .DAT .

[Credits: https://www.igismap.com/vector-data-file-formats/]