# RNA-Seq Data Analysis with Kallisto and NetworkAnalyst

## Objective
The process of analyzing RNA-Seq data using Kallisto for quantification and NetworkAnalyst.ca for data interpretation.

## Prerequisites
- Discovery Cluster
- Kallisto installed via Bioconda
- R installed with `readr` and `dplyr` packages

### Input Data
- RNA-Seq data files located at: `/courses/BINF6310.202410/data/rnaseq-mus-musculus-GSE240196`

### 3. Load Miniconda and Activate Environment
Load Miniconda and activate the environment:

```bash
module load miniconda3/23.5.2
source activate binf6310
conda install -c bioconda kallisto
```

### 4. Download the Transcriptome File
- Visit Ensembl Mouse Genome
- Navigate to the "cdna" folder under Gene Annotation and download the `Mus_musculus.GRCm39.cdna.all.fa.gz` file.

### 5. Build the Index with Kallisto
Run the following command to build the index:

```bash
kallisto index -i Mus_musculus.idx Mus_musculus.GRCm39.cdna.all.fa.gz
```

### 6. Create an Output Directory
Create a directory for the Kallisto outputs:

```bash
mkdir kallisto-output
```

### 7. Run Kallisto for Quantification
Use the provided or custom bash script to run Kallisto and quantify transcript abundances.

### 8. Combine Kallisto Outputs in R
Load R and install the required packages:

```r
module load R
install.packages("readr")
install.packages("dplyr")
q()
```

Run the script to join the results:

```bash
Rscript kallisto-output-join.R
```

### 9. Download and Edit the Output File
Generate the `count_matrix.csv` file from the `kallisto-output`, 
then add the necessary annotation headers for NetworkAnalyst and save it as a tab-delimited file.

### 11. Analyze in NetworkAnalyst.ca
- Go to [NetworkAnalyst.ca](https://www.networkanalyst.ca).
- Choose the "Gene Expression Table" module.
- Select the "Metadata included" option and upload your edited file.
- Fill in options based on your understanding of the data.
- Generate visualizations and perform differential expression and enrichment analyses.

## Final Report
- Visualizations
- Differentially Expressed Genes (DEGs)
- Enrichment analysis results
