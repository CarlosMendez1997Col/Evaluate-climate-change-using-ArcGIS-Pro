# Evaluate climate change projections using GIS

## Description

Evaluation of the `Climate Change Models (GCM)` CCCma-CanESM2, MOHC-HadGEM2-ES and MIROC-MIROC5, using Arcgis for Python. 

Each section is described below:

1. The first section shows how to Geoprocess NetCDF files and convert them to CRF (Cloud Raster Format).

2. The second section evidences how to analyze trends and patterns in multidimensional data.

3. The third section shows how to create animations and timelines of climate data. 

4. The fourth and final section shows how to convert and export multidimensional data to tables and shapefile formats.

## Prerequisites and libraries

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

## Data acquisition and download

### [CORDEX Program](https://esgf-node.ipsl.upmc.fr/projects/esgf-ipsl/)

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

### Projection and scenario RCP45 of precipitation 2021-2030 SAM  

#### Model CCCma-CanESM2
[pr_SAM-20_CCCma-CanESM2_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc](http://esg-dn1.nsc.liu.se/thredds/fileServer/esg_dataroot3/cordexdata/cordex/output/SAM-20/INPE/CCCma-CanESM2/rcp45/r1i1p1/INPE-Eta/v1/mon/pr/v20180507/pr_SAM-20_CCCma-CanESM2_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc)
#### Model MOHC-HadGEM2-ES
[pr_SAM-20_MOHC-HadGEM2-ES_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc](http://esg-dn1.nsc.liu.se/thredds/fileServer/esg_dataroot3/cordexdata/cordex/output/SAM-20/INPE/MOHC-HadGEM2-ES/rcp45/r1i1p1/INPE-Eta/v1/mon/pr/v20180507/pr_SAM-20_MOHC-HadGEM2-ES_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc)
#### Model MIROC-MIROC5
[pr_SAM-20_MIROC-MIROC5_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012](http://esg-dn1.nsc.liu.se/thredds/fileServer/esg_dataroot3/cordexdata/cordex/output/SAM-20/INPE/MIROC-MIROC5/rcp45/r1i1p1/INPE-Eta/v1/mon/pr/v20180507/pr_SAM-20_MIROC-MIROC5_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc)

### Projection and scenario RCP45 of Near Surface Air Temperature 2021-2030 SAM 

#### Model CCCma-CanESM2
[tas_SAM-20_CCCma-CanESM2_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc](http://esg-dn1.nsc.liu.se/thredds/fileServer/esg_dataroot3/cordexdata/cordex/output/SAM-20/INPE/CCCma-CanESM2/rcp45/r1i1p1/INPE-Eta/v1/mon/tas/v20180507/tas_SAM-20_CCCma-CanESM2_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc)
#### Model MOHC-HadGEM2-ES
[tas_SAM-20_MOHC-HadGEM2-ES_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc](http://esg-dn1.nsc.liu.se/thredds/fileServer/esg_dataroot3/cordexdata/cordex/output/SAM-20/INPE/MOHC-HadGEM2-ES/rcp45/r1i1p1/INPE-Eta/v1/mon/tas/v20180507/tas_SAM-20_MOHC-HadGEM2-ES_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc)
#### Model MIROC-MIROC5
[tas_SAM-20_MIROC-MIROC5_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc](http://esg-dn1.nsc.liu.se/thredds/fileServer/esg_dataroot3/cordexdata/cordex/output/SAM-20/INPE/MIROC-MIROC5/rcp45/r1i1p1/INPE-Eta/v1/mon/tas/v20180507/tas_SAM-20_MIROC-MIROC5_rcp45_r1i1p1_INPE-Eta_v1_mon_202101-203012.nc)

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
