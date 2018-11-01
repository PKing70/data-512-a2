# data-512-a2

## Assignment 2: Bias in data

Name: Patrick King

Date: November 1, 2018

Class: University of Washington DATA 512, Winter 2018

Professors: Jonathan Morgan and Os Keyes

## Goal
The goal of this project is to analyze quality metrics against Wikipedia pages about political figures from a variety of different countries. We are to effectively obtain, combine, and analyze data such as a page's predicted ORES score, and evaluate that relative to how many articles have been created, and for which countries' political figures.  Potential for Bias within the data might be discoverable if, say, certain countries' political figures are under (or over-) represented in article count, or in quality assessment.

I'll look for coverage of politicians, meaning total count of articles vs. a countries population, and article quality proportions, meaning the counts of high or low-scoring articles vs. the count of articles available for a country's politicians. 

## Data sources used

This assignment relies upon data from the following sources:

* MediaWiki Wikipedia article data: this dataset includes article ids for pages about political figures, including the page title and the country from which the subject originates. All pages, however, are from English Wikipedia.

* Population data: this dataset contains population by country, in millions of people, as of mid-2018. It was provided as a license-free CSV on a dropox share, apparently originating from WorldPopData.

* The MediaWiki Objective Revision Evaluation Service. This service returns a predicts article quality rating from Good to Stub, used to assess the merits of the content written. The REST API returns JSON containing a quality rating given an article ID.

## Resources used
This analysis was prepared using [Python 3.0](https://docs.python.org/3.0/) running in a [Jupyter Notebook](http://jupyter-notebook.readthedocs.io/en/latest/) environment.  

The following Python packages were used and their documentation can be found at the accompanying links:

|Package|Usage|
|---|---|
|[requests](http://docs.python-requests.org/en/master/)|To support the ORES API call.|
|[numpy](https://docs.scipy.org/doc/numpy/reference/?v=20181101081033)|Replacement of unread values with NaNs.|
|[pandas](https://pandas.pydata.org/pandas-docs/stable/?v=20181101081033)|For dataframing, merging, numeric conversions, and reading CSVs.|

The ORES REST API was used to obtain a ML predicted quality score for articles in question. The quality levels it can return for an article id are:

FA - Featured article
GA - Good article
B - B-class article
C - C-class article
Start - Start-class article
Stub - Stub-class article

## Files Created
The A2 code creates one CSV file of data: data_final.CSV. It corresponds to the format requested by the assignment here.

|Column|Description|Type|
|---|---|---|
|country|Nation for which article and population data has been gathered|String|
|article_name|Topic of political Wikimedia article|String|
|revision_id|Unique id of article|Integer|
|article_quality|Rating for article predicted by ORES|String|
|population|Count (in millions) of people from given country|String|

The data files in this repository are:

|File|Description|
|---|---|
|README.md|Start here! |
|LICENSE|MIT to cover the files in this repo|
|A2 Bias in Data.IPYNB|Jupyter Notebook containing code and steps to execute this project.|
|data_final.CSV|Final output combined data used for analysis|

## Results
The results of this project are primarily available by using the Jupyter Notebook accompanying this assignment.

In summary,  

## Reflection
This project... 

## Licenses and terms of use

This assignment code is released under the [MIT license.](https://github.com/PKing70/data-512-a2/blob/master/LICENSE)

The data sources are licensed as follows:

* Wikipedia data: Released under the [CC-BY-SA 4.0 license.](https://creativecommons.org/licenses/by/4.0/) Usage should follow the mediawiki [terms and conditions of use.](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions)

* Population data: This does not appear to be licensed, as far as I can tell. It is sourced from the class resource [dropbox,](https://www.dropbox.com/s/5u7sy1xt7g0oi2c/WPDS_2018_data.csv?dl=0) apparently acquired from [WorldPopData.](http://www.worldpopdata.org/)

* [ORES:](https://www.mediawiki.org/wiki/ORES) The MediaWiki Objective Revision Evaluation Service. Pages are licensed under [CC-BY-SA 3.0 license.](https://creativecommons.org/licenses/by-sa/3.0/) Usage should follow the mediawiki [terms and conditions of use.](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions)
