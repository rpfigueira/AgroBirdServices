### Contents of this folder

This folder contains a sample file of the eBird dataset in parquet format. The file
with all records (80M) cannot be added here due to storage limitations.

The full dataset dataset can be downloaded from eBird platform.

### Reduce original file size

In order to reduce original file size and improve performance, the last two 
columns of the downloaded eBird file were discarded.

To do that, the shell script `transform_awk.sh` was used. After that, the parquet 
file was created using the notebook `pre01_convert_ebird_to_parquet`.