# AgroBirdServices
Workflow to estimate invertebrate pest consumption in agricultural valleys by birds.
The repository contains the scripts used in the paper by Messina et al (2023) *A 
multidisciplinary workflow to estimate pest control services by birds in farmlands: 
landscape and species conservation decision making support*, to be submitted to 
*Ecological Informatics* Journal.

## Purpose of the workflow
The purpose of the workflow is to quantify the amount of invertebrate crop pests
consumed by birds in a crop landscape. 

This analysis workflow is based on the study by [Messina et al. (2023)](https://doi.org/10.1016/j.ecoser.2023.101556), 
which, based on field work, determined that pest consumption by birds in an 
agricultural valley is dependent on the presence of trees in the 
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

The workflow implements the following steps:



| Step | Name | Description | Prerequisites | Notebooks |
|------|---------|----------|---------------|----------|
| 1.   | Prepare bird trait database | Classify bird species based on habitat, food and feeding traits, define species selection criteria and collect species range | Trait classification of bird species. Checklists are mandatory for this step to represent the community at local levels. Information on the reproduction period is also needed as it is directly related to the feeding behaviour during this period. |  |
| 2. | Selection of area of interest (aoi), bird sampling events and occurrence records | Spatially define the limits of the agricultural valley, set bird sampling protocol criteria,  apply species selection criteria and species range match with aoi | Land use layers | 01_select_records_and_area |
| 3. |  Collect crop and land use data | From a land crop/land use data source, clip the aoi and obtain a list of existing crops. Match crop classification table with standard list of crops | List of crops with standard codes, classification of crops as temporary of permanent crops |  02_clip_crop_classification |
| 4. | Determine crop features at the bird observation points | Create a spatial buffer at bird observation points and obtain crop and landscape description data | List of bird point locations filtered by quality criteria | 03_spatial_buffer_occurrences |
| 5. | Create list of potential pests | Get a list of potential invertebrate crop pests occurring in the area, based on a database of pests in crops | Database on pest-specific information for crops |  04_create_pest_list |
| 6. |  Identify pests consumed by occurring birds | Cross bird, crop and pest data to identify which pests are predated by bird species occurring in the aoi. This is done for each point buffer | List of bird species in the aoi. List of crops and corresponding pests in the aoi | 05_determine_predation |
| 7. | Calculate pest consumption | Determine pest consumption, based on bird energy requirements, daily food intake, number of bird individuals and proportion of crop in the point buffer  | Cross table of birds, crops and pests, Data on Daily Energy Expenditure for birds, and moisture content and assimilation efficiency for pests | 06_calculate_crop_fraction <br> 07_calculate_DFI <br> 08_calculate_consumption |
| 8. |Develop model of pest consumption | Combine data about pest consumption, crop cover and landscape description, bird and community and guild data at point level for modelling. Develop consumption model and assess model quality | | 09_calcultate_indices <br> 10_EDA <br> 11_Data_transformation <br> 12-1_RandomForest_model_temporary <br> 12-2_RandomForest_model_permanent |
| 9. | Implement simulation tool | Implement the model to allow the simulation of pest consumption with the change of landscape features. The simulation includes a tool for the classification of the relevance of pests in the local crops by the local stakeholders | Pest consumption model for the agricultural valley of the simulation area | TODO |

