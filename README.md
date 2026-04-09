# Topic 03: Dissecting DNA methylation heterogeneity in cancer

### *Project overview and guidelines*

* [Introduction](#introduction)
* [Objective](#objective)
* [Description of datasets](#description-of-datasets)
* [Literature review](#literature-review)
* [How to structure your project](#how-to-structure-your-project)

  * [Project proposal](#project-proposal)
  * [Project](#project)

## Supervisor

* Supervisor: Michael Scherer - michael.scherer@dkfz.de
* Tutor: Paul Christmann - paul.christmann@stud.uni-heidelberg.de



## Introduction

DNA methylation is a cell-type specific epigenetic modification that is severely altered in multiple diseases, especially in cancers. By the addition or removal of a methyl-group to cytosines in the CpG context in DNA, the transcriptional activity of genes can be modulated. This can, for example, cause the aberrant activation of oncogenes or the suppression of tumor suppressor genes. Beyond transcriptional regulation, DNA methylation also serves to preserve genomic stability and prevents the transcription of transposable elements. DNA methylation is used a biomarker in diseases, especially in the classification of brain tumors (Capper et al, Nature, 2018). It can be read in a high-throughput manner using next-generation sequencing approaches, but also with microarray technologies. Using these microarray technologies, one can readout a subset of 1-5% of all CpGs dinucleotides in the human genome in many samples at a time. The microarrays will generate so-called beta-values limited to the \[0, 1] interval representing the fraction of methylated CpGs in the bulk of cells that have been used as input to the array. We expect that most of the CpGs will have beta values close to either 0 or 1, respectively, since CpGs are either methylated or not in a single cell.



## Objectives and work plan

Within this project, you will analyze a DNA methylation dataset generated using the Illumina Methylation 450k bead array (microarray) technology. The goal is to thoroughly understand technical issues related to the array, to filter CpGs for their quality, and ultimately to perform a differential DNA methylation analysis between cancer and matched normal samples. In addition to an exploratory analysis, including low-dimensional representation plots of the data, you will also investigate the methylation state of individual CpGs in relation to cancer.



## Description of datasets

Your dataset comes in the form of a DNA methylation data matrix. Rows represent the different CpGs (usually between 400,000 and 950,000) and columns contain the samples that we want to analyze. You will have an additional data matrix comprising phenotypic information about the samples, i.e. this matrix will contain as many rows as columns in the data matrix. There is an additional document, called CpG\_annotation.csv, available, which indicates the CpGs and its genomic location in the human reference genome version hg19. Each entry in your data matrix contains the beta values representing the average DNA methylation state of all cells analyzed in an individual sample. The data matrix contains \*unnormalized\* DNA methylation calls.

Data comes from the TCGA project. We have different tumor entities and would like each of the groups to investigate one of the tumor entities:

* Group 1: LUSC = Lung squamous cell carcinoma
* Group 2: THCA = Thyroid carcinoma
* Group 3: KIRC = Kidney renal clear cell carcinoma
* Group 4: BRCA = Breast invasive carcinoma
* Group 5: COAD = Colon adenocarcinoma

Data is available from: https://hub.dkfz.de/s/oeFnRppe6BpfNFa.



## Literature

* Pidsley, R., et al. (2016). Critical evaluation of the Illumina MethylationEPIC BeadChip microarray for whole-genome DNA methylation profiling. Genome Biology, 17(1), 208. https://doi.org/10.1186/s13059-016-1066-1
* Capper, D., et al. (2018). DNA methylation-based classification of central nervous system tumours. Nature 555: 469-474. https://doi.org/10.1038/nature26000
* Bock, C. (2012). Analysing and interpreting DNA methylation data. Nature Reviews Genetics, 13(10), 705–719. https://doi.org/10.1038/nrg3273
* Müller, F., Scherer, M., Assenov, Y., Lutsik, P., Walter, J., Lengauer, T., \& Bock, C. (2019). RnBeads 2.0: comprehensive analysis of DNA methylation data. Genome Biology, 20(1), 55. https://doi.org/10.1186/s13059-019-1664-9



## How to structure your project

### Project proposal

You first task will we to define a **project proposal**, which should
include

* summary of literature
* questions you want to address
* first insights into the project data (what kind of data?)
* approximate timetable

You will present this project proposal together with a literature review
on the subject 3 week after the beginning of the semester (10 minute
presentation + 5 minutes discussion).

### Project

The following points **must** be included in your project:

* **descriptive statistics** about the datasets
* **graphical representations**
* **dimension reduction** analysis (PCA, clustering or k-means)
* **statistical tests** (t-test, proportion tests etc)
* **linear regression** analysis, either uni- or multivariate

#### Data cleanup

You will be analyzing multiple data sets together. It is
essential that you explore each dataset and clean it. Cleaning can refer
to many things:

* Removing/Imputing missing values
* Removing low variance columns/rows
* Removing outlier samples (only if it is due to technical issues !!)
* Making sure that data is in the correct format, for example, numbers
  should be encoded as numeric and not as characters. Categorical
  variables should be factors etc.
* Normalization

#### Data exploration

Now that you have cleaned data, explore your data to understand its
structure. Perform basic exploratory data analysis.

* Look at the distribution of the overall data, specific samples or
  features.
* Visualize the data distribution
* Visualize the inter-dependencies (e.g. correlations) among specific samples/features of
  interest
* Check some of your hypothesis like - is something high/low between
  two conditions etc

#### Data reduction

You have a high dimensional matrix, that is, you have way more features
than observations.

* Try out methods to reduce the dimensionality of this data.
* Cluster your samples to identify similar and dis-similar groups
* Check how well the groups separate based on the features of your
  interest

#### Data modelling

Using data modeling with linear regression, we expect you to perform two tasks:

* Generate linear models to understand the relationship between CpG methylation states and phenotypic information. We want you to compare the *Primary solid Tumor* to the *Solid Tissue Normal* group.
* Use linear models to understand relationships between different CpGs. Are there highly correlated or anti-correlated CpGs?
