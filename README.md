# Bibliometric analysis

### Companion Paper
This source code and data goes with the peer-reviewed paper :
```
Ignacio J. Dasso, Sébastien Maudet, Renzo E. Navas, Guillaume Andrieux.
"Industrial IoT cybersecurity: a bibliometric analysis"
[Conference info]
2025
```
**Please, if you use or are inspired by this source code, cite our aforementioned article.**

---------------------------

### What we share?

[**[CODE]**](code/)  The main objective of this repository is to share the source code used to reach the results of the paper.  Most of the source code development was made on the second half of the year 2024. The source code is the folder [`/code/`](code/).

[**[DATA]**](data/) We share the data retrieved from the code execution. They are located in the folder [`/data/`](data/).

The rest of this README presents in further detail the content shared.

---------------------------
# Index

 1. [Database queries & results](#queries)
 2. [Python notebook](#pythonNotebook)
 3. [VOSviewer usage](#vosViewerUsage)
 
---------------------------
# 1. Database queries <a name="queries"></a>


##  Database
The bibliometric analysis is based on retrieved information from the [Scopus](https://www.scopus.com/search/form.uri?display=basic#basic) database. The code for the queries is based on [Scopus guidelines](https://service.elsevier.com/app/answers/detail/a_id/11365/supporthub/scopus/).

##  Queries
Queries available (see [`/queries/`](./code/queries/)):
* Query #1 (file: q1.query): base literature search and selection query.
* Query #2 (file: q2.query): includes code that limit the corpus to surveys and similar studies, select publications stating “IIoT” or “cybersecurity” in the title, and limit publications from 2022 to 2024 for recent results.
* Adapted versions of Query #1 (file: q1+keyOptions.query): tailored version of Query #1 for acknowledging publication trend in the top selected keywords. These queries have been used for acknowledging the number of publications per year.


## Queries results
The tools from Scopus allow to download results from queries selecting the specific metadata of interest. Prior to the processing don The results from executing queries #1 and #2  have been exported selecting different information according to the processing thatlead to the following files:
* Query #1 export (file name: 1_2025-01-22_Q1_Year+CitationCount+Publisher+IndexedKeywords.csv)
* Query #21 export (file name: 1_2025-02-11_Q2_Year+Title+CitationCount.csv)

# 3. Python notebook <a name="pythonNotebook"></a>


# 4. VOSviewer usage <a name="vosViewerUsage"></a>
