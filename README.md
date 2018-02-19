# CARTO basemap styles
CARTO Basemap styles for web and mobile

This repository has working copies of basemap cartographic styles for different targets

## The cartography

All the styles are "soft" in a sense that they are meant to be used as background or basemap below data layers. These are not really meant to be used as stand-alone map by itself, something you'l get from Google, Here and other general maps.

1. **Voyager** - colored map, the default basemap in CARTO Builder
2. **Positron** - light gray map, good for point data
3. **Dark Matter** - dark gray map, good for polygon/line data


<img src="/cartocss/web/voyager.tm2/.thumb.png" alt = "voyager" width="270"/> <img src="/cartocss/web/positron.tm2/.thumb.png" alt = "positron" width="270"/> <img src="/cartocss/web/dark-matter.tm2/.thumb.png" alt = "dark-matter" width="270"/>

## 1. Web raster basemaps

* Service public info: https://carto.com/location-data-services/basemaps/
* Style is written in CartoCSS using Mapbox Studio Classic (https://www.mapbox.com/mapbox-studio-classic/), and shared here as Mapbox Studio Classic project
* Raster tiles generated by Mapnik tilelive-vector using Mapnik-XML styling. 
* File folder in this repo: **/cartocss/web**

### File structure 

Styles use as much shared styling as possible. 
Shared cartocss (.mss) files are in /shared folder, and linked with symlinks to different style projects, as MB Studio requires files in single folder. 
Same symlink-based sharing is used for **Fonts** and **Images** subfolders.
Every style has following unique files:
* project.yml - main project file. It is important to have here list of layers, as this determines order of layer rendering
* style.mss - specific values for style variables
* project.xml - generated file by MB Studio Classic. Normally is not edited manually, but real server uses this for real styling

## 2. CARTO Mobile SDK live basemaps 
* folder **cartocss/mobile-sdk-styles**
* these are taken from "Web Basemaps" .mss files (CartoCSS) and are modified to have vector rendering specifics - e.g. language and 3D display, smooth zoom variables
* Style modification from web basemap to mobile basemap is manual process
* Every style has mobile-specific .json metafile (e.g. voyager.json). This is SDK-specific format, somewhat similar to project.yml file in MB Studio Classic. Defines also order of layers, and some SDK-specific additional parameters. It has also file sizes and checksums, this is used in online style server to identify style updates.
* Note that MBStudio generated .xml is **not** used here

## 3. Vector styles for web
### Mapbox-gl style
* folder: **/mapboxgl**
* Master style is file **/tools/style_tpl.json** . It uses template placeholders for variable values for different styles
* Different styles are **/style-name/style-name_vars.json** files
* You should use **tools/styler.py** script to generate specific style from template and *_vars.json* file. The ready-made style-name.json files are generated and for reference only.
* Master style and variables files are manually created from a working style

### Openlayers
* It can use mapbox-gl style, which is auto-converted using https://github.com/boundlessgeo/ol-mapbox-style

### Tangram styles
* folder: **/tangram**
* Can be edited using Tangram Play

