

# Notes from ASI course activites
---

## Oyster DESeq experiment


---

### 1. Getting started. You must have:
* R Console (download from <http://www.r-project.org>)
* Reads count table from RNA-seq experiment
* DESeq program in R console

### 2. Obtaining DESeq in R console
* Enter to R console and type:

````
#source("http://bioconductor.org/biocLite.R")
#biocLite("DESeq2")
````
### 3. Prepare your data 
* Assign a library to DESeq in R console

````
data <- read.table("./data/Cgigas-HS-count.txt", header = T, sep = "\t")
rownames(data) <- data$Feature
data <- data[,-1]
````
* Specify which columns are in which groups


````
deseq2.colData <- data.frame(condition=factor(c(rep("Control", 3), rep("Heat-shock", 3))), 
    type=factor(rep("single-read", 6)))
	rownames(deseq2.colData) <- colnames(data)
	deseq2.dds <- DESeqDataSetFromMatrix(countData = data,
    colData = deseq2.colData, 
    design = ~ condition)
````

### 4. 
                                    