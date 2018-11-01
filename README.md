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

For the top 10 countries that had high-quality articles per capita, low-population countries dominated the list with Tuvalo #1 and Nauru #2. Clearly, it seems to help a country's proportion to not have many people. For the bottom 10 coutrues in high-quality articles per capita, countries with much higher populations tended to show up, with Indonesia #1 and Uzbekistan #2. (Though Uzbekistand is not that high of a population country, with 32.9 million people.)

In analyzing the ten highest-ranked countries by article quality per article written, it was interesting that North Korea was #1 and Saudi Arabia was #2. For the the ten lowest-ranked countries by article quality per article written, it was interesting that Tanzania was #1 and Peru was #2. I also had to note that the "low" proportion and rankings rely upon there being at least one highly rated article to construct a proportion/ranking with. There were 37 countries that had no highly rated articles so were omitted from the "lowest-ranked" table. Instead, I separated them from the other countries and produced a dataset that lists all the countries that lack highly rated articles at the end of the Python notebook. Essentially, these are all equally "the worst rated" as they have a proportion of zero.

It seems likely that the data is easily biased in this sort of analysis when the population figure is extrememly low, as one or just a few articles about a politician result in fairly significant impact on coverage. It also seems likely that countries with well-known "public relations" issues might even be effectively impacting the data with "high quality" articles more often than countries that aren't as politically extreme (North Korea and Saudi being #1 and #2). Perhaps their "in-the-news" nature for things like aggression and civil rights violations results in more interest and in-depth coverage, or perhaps the countries themselves sponsure writers to provide such coverage; more investigation might be worthwhile.
 
## Reflection
This project required considerable effort with merging datasets, which I tried to solve using pandas. The data itself is well-defined and essentially provided from the combination of WorldPopData, Wikimedia, and ORES, but each dataset needed to be carefully merged and joined to provide the calculations of proportions and totals needed.

The results of the analysis show that there is a big disparity between countries in both coverage (count of political articles per capita) and quality (count of highly rated articles per article set). 

I also put significant time into trying to make this research reproducible, by using clear documentation, copious linking to resources, and proper licensing and attribution. As far as I can tell, all the steps necessary to repro or expand upon this work is included in this repository. If there are any missing ingredients or questions to be answered, please let me know here on Github.

### Future Considerations
I think with more exploration, more insight into this data and the questions about bias could be garnered. There is room to experiment with ORES predictions vs. other models or services that might rate articles differently; if there is bias within ORES then it would manifest as dubious quality proportions in my results.

What if a different data scientist who values longer (or shorter) articles used different standards? Then ORES would change its predictions accordingly, or perhaps an alternative to ORES would be produced to compare to ORES predictions. Culturally, I would expect not only "objective" data like article length or level of detail or usage of graphics or tabular data vs. prose to produce differing assessments of "high quality." So, some investigation into how ORES works and how alternatives to ORES might work would be interesting.

Also, non-English Wikipedia pages likely differ in count and substance from English Wikipedia. I'm not sure we know much about this content considering our analysis accounted for only English pages. Not only do I expect English pages to provide more coverage to English-language-based politics and politicians, but I also expect, culturally that English-speaking cultures might assess non-English speaking political figures differently than those from other languages/cultures. So, I'd like to compare and contrast non-English page coverage and quality to the dataset I used here.

## Licenses and terms of use

This assignment code is released under the [MIT license.](https://github.com/PKing70/data-512-a2/blob/master/LICENSE)

The data sources are licensed as follows:

* Wikipedia data: Released under the [CC-BY-SA 4.0 license.](https://creativecommons.org/licenses/by/4.0/) Usage should follow the mediawiki [terms and conditions of use.](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions)

* Population data: This does not appear to be licensed, as far as I can tell. It is sourced from the class resource [dropbox,](https://www.dropbox.com/s/5u7sy1xt7g0oi2c/WPDS_2018_data.csv?dl=0) apparently acquired from [WorldPopData.](http://www.worldpopdata.org/)

* [ORES:](https://www.mediawiki.org/wiki/ORES) The MediaWiki Objective Revision Evaluation Service. Pages are licensed under [CC-BY-SA 3.0 license.](https://creativecommons.org/licenses/by-sa/3.0/) Usage should follow the mediawiki [terms and conditions of use.](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions)
