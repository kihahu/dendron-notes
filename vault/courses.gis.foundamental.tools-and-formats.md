---
id: 4cb91877-d9b8-48e7-bf3f-c8e082c34701
title: Tools & Formats
desc: ''
updated: 1614537039723
created: 1605118559183
---

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

- backup software: e.g. CrashPlan 

### Formats 

- Shapefile
    - specific ESRI format
    - standard format used by most 
    - comprised of 3-7 files
    - rely on old dBase IV data tables 
    - slow, large, limiting, but useful for interchange

- The [**GeoPackage open format**](https://www.geopackage.org/) is a SQLite container for GIS data (layers) in a single file. Unlike the ESRI Shapefile format, a single GeoPackage file can contain various data (both vector and raster) in different coordinate reference systems, as well as tables without spatial information
- SpatiaLite database format, like GeoPackage, is also an extension of the SQLite library