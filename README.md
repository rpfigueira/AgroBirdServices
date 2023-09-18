# AgroBirdServices
Workflow to estimate invertebrate pest consumption in crop landscapes by birds.

## Purpose of the workflow
The purpose of the workflow is to quantify the amount of invertebrate crop pest
consumed by birds in a crop landscape. 

This analysis workflow is based on the study by [Messina et al. (2023)](#), 
which, based on field work, determined that pest consumption by birds in an 
agricultural valley in Portugal is dependent on the presence of trees in the 
landscape.

This analysis expands that result to a general application, using public 
available data to estimate the agricultural crop intensive valleys. As a case
study the Agricultural Valley of California is tested. The following
data is combined to produce the estimates of pest consumption:
- bird occurrence data recorded by birdwatchers through [eBird](https://ebird.org)
- bird trait data from [AVONET database](https://doi.org/10.6084/m9.figshare.16586228.v5) and [Pigot et al. (2020)](https://doi.org/10.1038/s41559-019-1070-4)
- crop pests from [EPPO Global Database](https://gd.eppo.int/)
- LULC data including crop classification from [CroplandCROS](https://croplandcros.scinet.usda.gov/)
- bird predation of invertebrates from [Global Biotic Interactions](https://www.globalbioticinteractions.org/)



## Workflow

The workflow implements the following steps (diagram):

1. Spatially select bird occurrence data for the California Agricultural Valley area of 
interest
2. 
2. Select bird occurrences 

The data gathering and 


| Step | nb name | description | link | status | output |
|------|---------|-------------|------|--------|--------|
| 1 | 01_select_records | filter data for the polygon area and sample randomly 10%of records | https://gbif01:8888/notebooks/projects/TainanMessina/article2/01_select_records_and_area.ipynb | functional | |
| 1 | 01_select_area | select the area polygon, clip eBird data, clip the land cover layer, calculate area for crops | https://gbif01:8888/notebooks/projects/TainanMessina/article2/01_select_area.ipynb | functional | df_points_parquet.csv, crop_data.csv, Cropland_clip1.tif |
| 2 | 02_select_occ | select bird occurrences based on the criteria | https://gbif01:8888/notebooks/projects/TainanMessina/article2/02_select_occ.ipynb | functional | eBird_sel.csv |
| 3 | 03_bird_groups | set bird functional groups and bird counts | https://gbif01:8888/notebooks/projects/TainanMessina/article2/03_bird_groups.ipynb | TODO |
| 4 | 04_crop_list | calculate the list of crops and its area for the selected polygon |https://gbif01:8888/notebooks/projects/TainanMessina/article2/04_crop_list.ipynb | TODO |
| 5 | 05_pest_list | calculate the list of pests for the selected crops and area |https://gbif01:8888/notebooks/projects/TainanMessina/article2/05_pest_list.ipynb | funtcional | eppo_crop_pest_data.csv |
| 6 | 06_predation | determine predation preys by birds | https://gbif01:8888/notebooks/projects/TainanMessina/article2/06_predation.ipynb | functional | bird_prey.csv |
| 7 | 07_consumption | calculate pest consumption | https://gbif01:8888/notebooks/projects/TainanMessina/article2/07_consumption.ipynb | TODO |
| 8 | 08_simulation | simulate land cover change | | TODO |
