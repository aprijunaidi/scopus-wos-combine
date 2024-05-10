
![combine](https://github.com/aprijunaidi/scopus-wos-combine/assets/7279471/b6743d5c-38e6-4d39-9468-72fde96191dd)

# Combining Scopus and Web of Science Databases using R Studio

Welcome to this project! In this repository, we aim to combine two of the most comprehensive academic databases - **Scopus** and **Web of Science (WoS)** - using **R Studio**. 

## Why Combine Scopus and WoS?

Both Scopus and WoS are rich sources of bibliometric data, each with their own strengths. Scopus, with its extensive journal coverage and citation data, and WoS, known for its robust citation indexing, provide complementary insights. By combining these databases, we can leverage the strengths of both, resulting in a more comprehensive and robust dataset for our research or create your own SLR.

## How Do We Use R Studio?

R Studio is a powerful tool for data analysis and visualization. It provides a wide range of libraries and functions that make it easier to manipulate, analyze, and visualize complex datasets. In this project, we will use R Studio to clean, merge, and analyze data from Scopus and WoS.

## What's in this Repository?

In this repository, you will find R scripts for downloading, cleaning, and merging data from Scopus and WoS. Additionally, there will be scripts for some preliminary analyses of the combined dataset. 

We hope this project will serve as a valuable resource for researchers looking to harness the power of bibliometric data from Scopus and WoS. We welcome contributions and suggestions to improve the project.

Let's dive into the world of bibliometric analysis with R Studio!

# Processing and Combining Scopus and WoS Databases

Once you have downloaded the Scopus and WoS databases in BibTeX format, the next step is to process and combine these databases using R console. Here's a step-by-step guide on how to do this:

## Step 1: Load the Required Libraries

First, we need to load the necessary R libraries. For this project, we will primarily be using 'convert2df' for converting BibTeX files to data frames, and `mergeDbSources` for data merger (combine).

```r
library(bibliometrix)
library(openxlsx)
```

## Step 2: Set your file directory
setwd('/Volumes/PATHTO/')
getwd()
```

## Step 3: Convert BibTeX to Data Frames
Next, we convert the downloaded BibTeX files into data frames using the convert2df

```r
WOS_df <- convert2df(file = 'your_wos_file_name.bib', dbsource = "wos", format = "bibtex")
SCOPUS_df <- convert2df(file = 'your_scopus_file_name.bib', dbsource = "scopus", format = "bibtex")
```

## Step 4: Data Cleaning
Before combining the databases, we need to clean the data. This may involve removing duplicates.

```r
Merge_SCO_WOS <- mergeDbSources(SCOPUS_df, WOS_df, remove.duplicated=TRUE)
```

## Step 5: Check the data Frame 

```r
View(Merge_SCO_WOS)
dim(Merge_SCO_WOS)
```

## Step 6: Combine the Databases

Finally, we combine the cleaned Scopus and WoS data frames into a single data frame.

```r
write.csv2(Merge_SCO_WOS, file = 'scopus-wos-combine.csv')
write.xlsx(Merge_SCO_WOS, file = 'scopus-wos-combine.xlsx')
```

## Step 7: Run the biblioshiny library
Biblioshiny is a web-based tool that facilitates the import, gathering, filtering, and analysis of bibliometric data from bibliometrix, providing an interactive interface for comprehensive bibliometric and visual analysis.


```r
biblioshiny()
```

# Conclusion

We have successfully combined the Scopus and Web of Science databases using R Studio and performed some preliminary analyses. This project demonstrates the power of bibliometric data and the insights that can be gained from it. We hope this repository serves as a useful resource for researchers and data analysts alike.

Thank you for visiting this project. If you have any questions, suggestions, or would like to contribute, please feel free to give Star and Fork. Happy analyzing!

# Contribution :hammer_and_wrench:

Please [create an Issue] (https://github.com/aprijunaidi/scopus-wos-combine/issues) for any improvements, suggestions, or errors in the content.

![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Faprijunaidi%2Fscopus-wos-combine&countColor=%23263759)
