# Bibliometric analysis

### Companion Paper
This source code and data goes with the peer-reviewed paper:
```
Ignacio J. Dasso, Sébastien Maudet, Renzo E. Navas, Guillaume Andrieux,
"Industrial IoT cybersecurity: a bibliometric analysis,"
in Proceedings of the 10th International Conference on Smart and Sustainable Technologies (SpliTech),
June 2025.
```
**Please, if you use or are inspired by this source code, cite our aforementioned article.**

---------------------------

### What we share?

[**[CODE]**](code/)  The main objective of this repository is to share the source code used to reach the results of the paper.  Most of the source code development was made in the second half of the year 2024. The source code is the folder [`/code/`](code/).

[**[DATA]**](data/) We share the data retrieved from the code execution. They are located in the folder [`/data/`](data/).

The rest of this README present in further detail the content shared.

---------------------------
## Index

 1. [Database queries & results](#1-database-queries-)
 2. [Python notebook](#2-python-notebook-)
 3. [VOSviewer usage](#3-vosviewer-usage-) 

 <!--1. Database queries & results
 2. Python notebook
 3. VOSviewer usage
 4. Closure -->
 
---------------------------
## 1. Database queries <a name="queries"></a>


###  Database
The bibliometric analysis is based on retrieved information from the [Scopus](https://www.scopus.com/search/form.uri?display=basic#basic) database. The code for the queries is based on [Scopus guidelines](https://service.elsevier.com/app/answers/detail/a_id/11365/supporthub/scopus/).

###  Queries
Queries available (see [`/queries/`](./code/queries/)):
* [Query #1](./code/queries/q1.query): base literature search and selection query.
* [Query #2](./code/queries/q2.query): includes code that limits the corpus to surveys and similar studies, select publications stating “IIoT” or “cybersecurity” in the title, and limit publications from 2022 to 2024 for recent results.
* Adapted versions of Query #1 (see [q1+keyOptions.query](./code/queries/q1+keyOptions.query)): tailored version of Query #1 for acknowledging publication trend in the top selected keywords. These queries have been used for acknowledging the number of publications per year.


### Query results
The tools from Scopus allow to download results from queries selecting the specific metadata of interest. Prior to the processing don The results from executing queries #1 and #2  have been exported selecting different information according to the processing that leads to the following files:
* [Query #1 export](./data/0_queriesResults/1_2025-01-22_Q1_Year+CitationCount+Publisher+IndexedKeywords.csv)
* [Query #2 export](./data/0_queriesResults/1_2025-02-11_Q2_Year+Title+CitationCount.csv)

## 2. Python notebook <a name="pythonNotebook"></a>
In this application we have used the [Google Colab](https://colab.research.google.com/notebook) execution environment. Additionally, [Google Drive](https://drive.google.com/drive) provides the storage for the files to be imported/exported to/from the notebook.

There are two sections within the notebook:
* Section #1: From the start up to "Exporting first results"
  * Includes the query result import and the processing to get an automatic association of all alike keywords in terms of their orthographic proximity.
* Section #2: From "Human control and adjustment" until the end
  * Taking advantage of the automatic association, a human-made association version is made to link all the concepts reflecting the same ideas. This association (see the variable `keyword_mapping_create`) will be the specific criteria used to map the keywords from the articles retrieved to a new homogenized version. The exported file at the end of the notebook is fully compatible with VOSviwer.

Files:
* [Notebook](./code/notebook/keywordsProcessing.ipynb)
* [Output file](./data/1_processingResults/bibliometricKeywords-processed.csv) (based on [Query #1 export](./data/0_queriesResults/1_2025-01-22_Q1_Year+CitationCount+Publisher+IndexedKeywords.csv))

## 3. VOSviewer usage <a name="vosViewerUsage"></a>
[VOSviewer](https://www.vosviewer.com/) provides the support for creating bibliometric networks. In order to obtain the graph presented in our article, the following steps have taken place:
* Create graph
  * `Create map based in bibliographic data`
  * `Read data from bibliographic database files`
  * At the `Scopus` tab, browse and select [Output file](./data/1_processingResults/bibliometricKeywords-processed.csv)
  * Select the following parameters: `Co-occurence`, `Fractional counting`, `Index keywords`
  * At `Minimum number of occurrences of a keyword`, select 121
  * At `Number of keywords to be selected`, select 50
  * At the current stage is it possible to inspect the keywords that will be graphed along with their occurrence count and link strength
* Parameter adjusting
  * We suggest setting the `minimum link strength` (right panel) to 37 for ease of readability. In any case, this is a parameter that can be changed at any time since the graph has already been rendered.

The following two files have been exported from VOSviewer after the graph creation and can be used to re-render the graph:
* [Map file](./data/2_networkMap/map-fractionalCount-37strength-1resol-31012025.txt)
* [Network file](./data/2_networkMap/network-fractionalCount-37strength-1resol-31012025.txt)
