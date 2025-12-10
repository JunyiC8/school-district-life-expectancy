# School District Life Expectancy Processing Code

This repository contains the code used to convert USALEEP tract-level life expectancy estimates (2010–2015) into school-district–level measures.

## Data Requirements

### Automatically downloaded by the notebook

* USALEEP (United States Small-Area Life Expectancy Estimates Project) 2010–2015 life table files
* 2010 Census P.L. 94-171 Redistricting Data (BLOCKID, TRACTCE, POP10)

### Manually downloaded

Download the 2010 School District Block Assignment Files (BAFs) and place into `census_files/`:

* SDSEC.txt 
* SDELM.txt
* SDUNI.txt

These files provide the BLOCKID → school district mapping.

## Software Requirements

Python 3.12.7  
Packages: pandas, numpy, tqdm, requests, dbfread, glob, os, geopandas, matplotlib

## How to Run

1. Download the BAF TXT files into the `census_files/` directory.
2. Open and run:

   ```
   01_processing_notebook.ipynb
   ```
3. The notebook will:

   * Download USALEEP files
   * Download and unzip P.L. 94-171
   * Read BAF TXT files and extract BLOCKIDs (PR excluded)
   * Merge block population and tract IDs
   * Assign tract life expectancy to blocks
   * Aggregate block-level values to school districts using population weights

All output CSVs are saved in the **Data_output or same folder as the notebook**.

## Outputs

* Block-level master table (BLOCKID, TRACTID, POP10, district IDs, USALEEP variables)
* School-district–level life expectancy dataset (population-weighted aggregates)
* Summary tables and visualizations

## Reproducibility

This code corresponds to the workflow described in the manuscript Methods section. All steps use publicly available datasets and reproducible Python code.
