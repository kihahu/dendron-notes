---
id: ae4197f7-ef66-4d95-8500-f54327559d1d
title: Week1
desc: ''
updated: 1605030720696
created: 1605022904291
---

- Definition of GIS: software and data that enables to answer questions involving location and spatial info. Yelp, G maps, etc. all count
- Desktop GIS - editting, processing, 
- Web GIS - mostly for displaying 

### terminology

https://www.coursera.org/learn/gis/supplement/lMYp2/glossary-of-terms

- **Vector** and feature **data**
    - categorical and multivariate data 
        - e.g. each watershed has an **attribute table** 
    - Points, lines, polygons
        - Lines: 1D, can have an attribute record
        - Polygons: 2D, can have an attribute record
- **Raster data** - continuous data 
    - grid of fixed-size pixels - uniform value within in pixel
    - imagery (multiband raster data e.g. RGB) is raster data

- shapefiles
    - specific ESRI format
    - standard format used by most 
    - comprised of 3-7 files
    - rely on old dBase IV data tables 
    - slow, large, limiting, but useful for interchange
- map documents in ArcGIS 
    - stores representation of data, provide a workspace
    - ext: .mxd
    - the map data is not embeded. 
- Orthophoto: arieal photo after location corrected to the map
- Watershed Analysis
    - NHD – National Hydrography Dataset – A dataset that contains water bodies and streamlines for the United States
        - Flowlines – the streamlines contained within NHD
        - NHDPlus – an enhanced version of NHD that adds additional attributes for each streamline, such as contributing area, flow, elevation, WBD, etc. Often used in place of NHD.
    - WBD – Watershed Boundary Dataset – a dataset containing nested watershed boundaries for the United States 
        - HUCs – Hydrologic Unit Codes – the watersheds created by the WBD   

### Software

- ArcGIS 
    - heavyweight - the "microsoft"
    - expensive, fast, stable
    - industry standard, used by government, university, etc. 
- Quantum GIS 
    - newcomer 
    - easiest, free, open source GIS 
    - great complement to ArcGIS 
- Grass GIS
    - old school
    - cmd line based, GUI available 
    - free and open source 
- Others: Erdas Imagine, Mapinfo, Mapwindow, GvSig, Envi, Youdig, Saga, OpenJump. 
- some CAD software work with GIS data atoo 
- https://en.wikipedia.org/wiki/Comparison_of_geographic_information_systems_software

## resources 

- [resources pdf](/assets/pdfs/gis-resources.pdf)
    - source:  https://www.coursera.org/learn/gis/supplement/UFDWI/resources-and-help-for-gis
- https://gis.stackexchange.com/ 
- http://geonet.esri.com/ 
- reddit/askgis

### Data 

Data Finders
- List of High Quality Datasets: https://github.com/nickrsan/awesome-public-datasets/
- NRCS Geospatial Data Gateway: http://datagateway.nrcs.usda.gov/GDGOrder.aspx
- List of worldwide GIS data sources from the US Geological Survey: http://education.usgs.gov/lessons/geospatialwebsites.html
- An incredible list of data links from Humboldt State University: http://library.humboldt.edu/infoservices/staff/rls/geospatial/intgis.htm
- National Map: http://viewer.nationalmap.gov/viewer/
- American Factfinder (US Census data): http://factfinder2.census.gov
- Book: The GIS Guide to Public Domain Data: https://spatialreserves.wordpress.com/about-thebook/

Datasets
- Enhanced National Hydrography Dataset (NHDPlus): http://www.horizon-systems.com/nhdplus/
- GeoNames (GNIS): http://geonames.usgs.gov/domestic/download_data.htm
- National Land Cover Dataset (NLCD): http://www.mrlc.gov/
- TIGER (National lines and boundaries – Census):
http://www.census.gov/geo/maps-data/data/tiger.html
- USGS Water Data for the Nation: http://waterdata.usgs.gov/nwis
- Listing of Global Terrain Data: http://vterrain.org/Elevation/global.html
- World Terrain Data: http://www.naturalearthdata.com/
- World Borders: http://thematicmapping.org/downloads/world_borders.php

- backup software: e.g. CrashPlan 