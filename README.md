# Combining Scopus and Web of Science Databases using R Studio

Welcome to this project! In this repository, we aim to combine two of the most comprehensive academic databases - **Scopus** and **Web of Science (WoS)** - using **R Studio**. 

## Why Combine Scopus and WoS?

Both Scopus and WoS are rich sources of bibliometric data, each with their own strengths. Scopus, with its extensive journal coverage and citation data, and WoS, known for its robust citation indexing, provide complementary insights. By combining these databases, we can leverage the strengths of both, resulting in a more comprehensive and robust dataset for our research.

## How Do We Use R Studio?

R Studio is a powerful tool for data analysis and visualization. It provides a wide range of libraries and functions that make it easier to manipulate, analyze, and visualize complex datasets. In this project, we will use R Studio to clean, merge, and analyze data from Scopus and WoS.

## What's in this Repository?

In this repository, you will find R scripts for downloading, cleaning, and merging data from Scopus and WoS. Additionally, there will be scripts for some preliminary analyses of the combined dataset. 

We hope this project will serve as a valuable resource for researchers looking to harness the power of bibliometric data from Scopus and WoS. We welcome contributions and suggestions to improve the project.

Let's dive into the world of bibliometric analysis with R Studio!

# Processing and Combining Scopus and WoS Databases

Once you have downloaded the Scopus and WoS databases in BibTeX format, the next step is to process and combine these databases using R console. Here's a step-by-step guide on how to do this:

## Step 1: Load the Required Libraries

First, we need to load the necessary R libraries. For this project, we will primarily be using `bib2df` for converting BibTeX files to data frames, and `dplyr` for data manipulation.

```r
library(bibliometrix)
library(openxlsx)

## Step 2: Set your file directory
setwd('/Volumes/PATHTO/')
getwd()


## Step 3: Convert BibTeX to Data Frames
Next, we convert the downloaded BibTeX files into data frames using the convert2df

WOS_df <- convert2df(file = 'your_wos_file_name.bib', dbsource = "wos", format = "bibtex")
SCOPUS_df <- convert2df(file = 'your_scopus_file_name.bib', dbsource = "scopus", format = "bibtex")


## Step 4: Data Cleaning
Before combining the databases, we need to clean the data. This may involve removing duplicates.

Merge_SCO_WOS <- mergeDbSources(SCOPUS_df, WOS_df, remove.duplicated=TRUE)

## Step 5: Check the data Frame 
View(Merge_SCO_WOS)
dim(Merge_SCO_WOS)

## Step 6: Combine the Databases

Finally, we combine the cleaned Scopus and WoS data frames into a single data frame.


write.csv2(Merge_SCO_WOS, file = 'unified2.csv')
write.xlsx(Merge_SCO_WOS, file = 'unified2.xlsx')

## Step 7: Run the biblioshiny library
Biblioshiny is a web-based tool that facilitates the import, gathering, filtering, and analysis of bibliometric data from bibliometrix, providing an interactive interface for comprehensive bibliometric and visual analysis.

biblioshiny()


