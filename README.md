---
jupyter:
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
  language_info:
    codemirror_mode:
      name: ipython
      version: 3
    file_extension: .py
    mimetype: text/x-python
    name: python
    nbconvert_exporter: python
    pygments_lexer: ipython3
    version: 3.8.8
  nbformat: 4
  nbformat_minor: 4
---

::: {.cell .markdown}
# Twitter-API-Data-Wrangling-and-EDA-Udacity-Data-Analytics-Nanodegree
:::

::: {.cell .markdown}
The dataset used in this data wrangling (and analyzing and visualizing)
project is the tweet archive of Twitter user \@dog_rates, also known as
WeRateDogs. WeRateDogs is a Twitter account that rates people\'s dogs
with a humorous comment about the dog. These ratings almost always have
a denominator of 10. The numerators, though? Almost always greater than
10. 11/10, 12/10, 13/10, etc. Why? Because \"they\'re good dogs Brent.\"
WeRateDogs has over 4 million followers and has received international
media coverage.
:::

::: {.cell .markdown}
## Wrangling Objective
:::

::: {.cell .markdown}
-   To gather data from the different sources
-   To assess these data and check for quality and tidyness issue
-   To clean these identified issues, merge and produce a clean data for
    analysis
:::

::: {.cell .markdown}
### Data Gathering
:::

::: {.cell .markdown}
Three different data was gathered in this stage, all from three
different data sources

-   Directly download the WeRateDogs Twitter archive data
    (twitter_archive_enhanced.csv): `<br>`{=html} This data was already
    given to be downloaded locally. This was loaded into the notebook
    with pandas read_csv command

-   Tweet image prediction (image_predictions.tsv): `<br>`{=html} This
    data contains the tweet image predictions of the dog. It is hosted
    on Udacity\'s servers and was to be downloaded using the python
    Requests library, as the url link of the data was given

-   Additional data via the Twitter API (tweet_json.txt): `<br>`{=html}
    This data requires me to gather each tweet\'s retweet count and
    favorite (\"like\") count at the minimum. Using the tweet IDs in the
    WeRateDogs Twitter archive, the Twitter API was queried for each
    tweet\'s JSON data using Python\'s Tweepy library and each tweet\'s
    was stored in the form of a JSON data called tweet_json.txt file.
    `<br>`{=html}

    To query the Twitter API, this process required me to have a Twitter
    elevated account authentication details, which i applied for and was
    approved in a couple of hours
:::

::: {.cell .markdown}
### Data Assessment
:::

::: {.cell .markdown}
This stage, i applied both visual and programmatic assessment to
identify and list our various quality and tidyness issue in the data.
`<br>`{=html} These are:

### Quality Issues

##### `twitter_archive` table

1.  tweet text column should only contain the text

2.  Some entries are not original tweets (replies and retweets)

3.  Drop columns that are essentially empty

4.  Timestamp column is not in appropriate format

5.  Ratings not extracted correctly (decimal ratings)

6.  Rating_numerator column contain outlier values (1776, 204,0)

7.  Ratings_denominator column has values more or less than 10

8.  Some dogs name were incorrectly entered (a, an, the)

##### `image_pred` table

1.  Get the final prediction of the dog breed from the two predicted
    values

2.  Capitalize each dog name

##### `tweet_rem` table

1.  rename \'id\' column to \'tweet_id\'

### Tidiness issues

1.  Dog stages should be combined to one column

2.  Merge three DataFrame to One Master dataFrame
:::

::: {.cell .code}
``` {.python}
```
:::
