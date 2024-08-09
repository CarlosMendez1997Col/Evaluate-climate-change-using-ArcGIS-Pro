# Evaluate climate change projections using GIS

## Description

Models (GCMs) CCCma-CanESM2, MOHC-HadGEM2-ES and MIROC-MIROC5

## Prerequisites and libraries

```python
import foobar

# returns 'words'
foobar.pluralize('word')

# returns 'geese'
foobar.pluralize('goose')

# returns 'phenomenon'
foobar.singularize('phenomena')
```

## Data acquisition and download

### [CORDEX Parameters](https://esgf-node.ipsl.upmc.fr/search/cordex-ipsl/)

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

## How to use and run the project

## 

## Credits and more information

[The Intergovernmental Panel on Climate Change](https://www.ipcc.ch/)

[World Climate Research Programme (WCRP)](https://www.wcrp-climate.org/)

[The Coordinated Regional Downscaling Experiment (CORDEX)](https://cordex.org/)

[The Earth System Grid Federation (ESGF)](https://esgf.llnl.gov/)


## License


## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

## License
