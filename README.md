# Evaluate climate change using ArcGIS API for Python and ArcGIS Maps SDK for JavaScript

## Description

Evaluation of `Climate Change Projections ` of the Global Climate Models (GCM) CCCma-CanESM2, MOHC-HadGEM2-ES and MIROC-MIROC5, using Arcgis for Python and ArcGIS Maps SDK for JavaScript.

Each chapter is described below:

1. The first chapter, shows how to Geoprocess NetCDF files and convert them to CRF (Cloud Raster Format).

2. The second section, explain how to analyze trends/patterns in multidimensional data. Also, calculate results using the following tools: Generate Multidimensional Anomaly, Generate Trend Raster and Predict Using Trend Raster.

3. The third section, shows how to create animations and timelines of climate data using the `19 Bioclimate Projections of WorldClim` using ArcGIS Maps SDK for JavaScript. 

4. The fourth and final section shows how to convert and export multidimensional data to tables and shapefile formats.

## Prerequisites and libraries

### ArcGIS API for Python

```python
import arcpy
import datetime as dt
import os
import arcgis
import NetCDF4
import csv

# Arcpy
from arcpy.ia import*

# arcgis
from arcgis.gis import GIS
from arcgis.raster import *
from arcgis.raster.functions import *
from arcgis.raster.analytics import *

```
### ArcGIS Maps SDK for JavaScript

```html
<script>
    require([
      "esri/Map",
      "esri/views/MapView",
      "esri/layers/ImageryTileLayer",
      "esri/layers/support/DimensionalDefinition",
      "esri/layers/support/MultidimensionalSubset",    
      "esri/widgets/Slider",
      "esri/widgets/TimeSlider",
      "esri/widgets/Legend",
      "esri/request",
      "esri/Color",
      "esri/widgets/LayerList",
      "esri/widgets/Expand",
      "esri/layers/TileLayer",
      "esri/layers/BaseTileLayer", 
       "esri/Basemap",
       ], 
            (Map, MapView, ImageryTileLayer, DimensionalDefinition, MultidimensionalSubset,
            Slider,TimeSlider, Legend, esriRequest, Color,LayerList, Expand, TileLayer, BaseTileLayer,Basemap) =>  
<script>
```


## Data acquisition and download

The data used in this program come from the Coordinated Regional Downscaling Experiment (CORDEX) [Website](https://esgf-node.ipsl.upmc.fr/projects/esgf-ipsl/) and the World Climate Research Program (WCRP), using the CCCma-CanESM2, MOHC-HadGEM2-ES and MIROC-MIROC5 models.


| Item                    | Precipitation 2021-2030 SAM                                 | Near Surface Air Temperature 2021-2030 SAM                  |
|-------------------------|-------------------------------------------------------------|-------------------------------------------------------------|
| Project                 | CORDEX                                                      | CORDEX                                                      |
| Product                 | output                                                      | output                                                      |
| Domain                  | SAM-20                                                      | SAM-20                                                      |
| Institute               | INPE                                                        | INPE                                                        |
| Driving Model           | CCCma-CanESM2 (1), MIROC-MIROC5 (1) and MOHC-HadGEM2-ES (1) | CCCma-CanESM2 (1), MIROC-MIROC5 (1) and MOHC-HadGEM2-ES (1) |
| Experiment              | rcp45                                                       | rcp45                                                       |
| Experiment Family       | RCP                                                         | RCP                                                         |
| Ensemble                | r1i1p1                                                      | r1i1p1                                                      |
| RCM Model               | Eta                                                         | Eta                                                         |
| Downscaling Realisation | v1                                                          | v1                                                          |
| Bias Adjustment         | None                                                        | None                                                        |
| Time Frequency          | mon                                                         | mon                                                         |
| Variable                | pr                                                          | tas                                                         |
| Variable Long Name      | Precipitation                                               | Near-Surface Air Temperature                                |
| CF Satandard Name       | precipitation flux                                          | air temperature                                             |
| Datanode                | esg-dn1.nsc.liu.se                                          | esg-dn1.nsc.liu.se                                          |

CCMa-CanESM2 Model
The second generation Canadian Earth System Model (CanESM2) (CanESM2) is the fourth generation coupled global climate model developed by the Canadian Centre for Climate Modelling and Analysis (CCCma) of Environment and Climate Change Canada. CanESM2 represents the Canadian contribution to the IPCC Fifth Assessment Report (AR5).

[Model CCCma-CanESM2 information](https://climate-modelling.canada.ca/climatemodeldata/cgcm4/CanESM2/index.shtml)

MOHC-HadGEM2-ES Model

The HadGEM2 family includes a coupled atmosphere-ocean configuration, with or without a vertical extension in the atmosphere to include a well-resolved stratosphere, and an Earth-System configuration which includes dynamic vegetation, ocean biology and atmospheric chemistry.

[Model MOHC-HadGEM2-ES information](https://www.metoffice.gov.uk/research/approach/modelling-systems/unified-model/climate-models/hadgem2)

MIROC-MIROC5 Model 

Model for Interdisciplinary Research On Climate

[Model MIROC-MIROC5 information](https://catalogue.ceda.ac.uk/uuid/d90ca0077e3344c7840ca56e49f89ee7/?jump=related-docs-anchor)

## Projection and scenario RCP45 of precipitation 2021-2030 SAM  

[Data of CCma-CanESM2 precipitation](http://esg-dn1.nsc.liu.se/thredds/fileServer/esg_dataroot3/cordexdata/cordex/output/SAM-20/INPE/CCCma-CanESM2/rcp45/r1i1p1/INPE-Eta/v1/mon/pr/v20180507/pr_SAM-20_CCCma-CanESM2_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc)

[Data of MOHC-HadGEM2-ES precipitation](http://esg-dn1.nsc.liu.se/thredds/fileServer/esg_dataroot3/cordexdata/cordex/output/SAM-20/INPE/MOHC-HadGEM2-ES/rcp45/r1i1p1/INPE-Eta/v1/mon/pr/v20180507/pr_SAM-20_MOHC-HadGEM2-ES_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc)

[Data of MIROC-MIROC5 precipitation](http://esg-dn1.nsc.liu.se/thredds/fileServer/esg_dataroot3/cordexdata/cordex/output/SAM-20/INPE/MIROC-MIROC5/rcp45/r1i1p1/INPE-Eta/v1/mon/pr/v20180507/pr_SAM-20_MIROC-MIROC5_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc)

## Projection and scenario RCP45 of Near Surface Air Temperature 2021-2030 SAM 

[Data of CCma-CanESM2 temperature](http://esg-dn1.nsc.liu.se/thredds/fileServer/esg_dataroot3/cordexdata/cordex/output/SAM-20/INPE/CCCma-CanESM2/rcp45/r1i1p1/INPE-Eta/v1/mon/tas/v20180507/tas_SAM-20_CCCma-CanESM2_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc)

[Data of MOHC-HadGEM2-ES temperature](http://esg-dn1.nsc.liu.se/thredds/fileServer/esg_dataroot3/cordexdata/cordex/output/SAM-20/INPE/MOHC-HadGEM2-ES/rcp45/r1i1p1/INPE-Eta/v1/mon/tas/v20180507/tas_SAM-20_MOHC-HadGEM2-ES_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc)

[Data of MIROC-MIROC5 temperature](http://esg-dn1.nsc.liu.se/thredds/fileServer/esg_dataroot3/cordexdata/cordex/output/SAM-20/INPE/MIROC-MIROC5/rcp45/r1i1p1/INPE-Eta/v1/mon/tas/v20180507/tas_SAM-20_MIROC-MIROC5_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc)

## Credits and more information

[The Intergovernmental Panel on Climate Change](https://www.ipcc.ch/)
[World Climate Research Programme (WCRP)](https://www.wcrp-climate.org/)
[The Coordinated Regional Downscaling Experiment (CORDEX)](https://cordex.org/)
[The Earth System Grid Federation (ESGF)](https://esgf.llnl.gov/)

## Conflict of Interest.

The authors declare that there is no conflict of interest in the publication of this map and that all authors have approved it for publication.

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.
