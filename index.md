---
layout: home
title: Opinions in news and success of Meta (or Mark Zuckerberg)
subtitle: Data Story
---

---
# Skeleton
# Abstract & introduction (Feez)
An introduction about project and why it could be useful.
Describe where the data comes from 
One or two sentences on how to extract the data

# Sentiment analysis 
## Global result (Neygo)

We began by doing an overall analysis of sentiment over time, specifically, we look at the proportions of each label (positive, negative, neutral) during each week. 
The majority of quotes are positive (or neutral), so negative quotes are only a small fraction of all quotes in a given week.
We also observe that the proportion of positive quotes decreases slightly around 2018-2019, negative quotes were increasing at the same time.
This corresponds to the period when the Cambridge analytica scandal was revealed.

[fig 1]

We then look at the overall average scores during each week.
As one might expect, the data are rather flat since we are averaging the different opinions and thus there is not much variance in the data. 
We observe, however, that in general the sentiment analyzer tends to assign a rather high neutral score and the quotes tend to be more positive than negative on average.

[fig 2]

To finish with the overall observation, we noticed that the number of citations is not consistent over time. 
The first observation is this high spike in early 2018.
As preceded, This is when the Cambridge Analytica scandal exploded.
As seen above, quotes were becoming more negative at this time as well. 
There are also a few weeks with very few quotes from the source used to harvest the data.

[fig 3]

## Clustering (Alessio)
Decompose the analysis into smaller groups.
### Investigate clusters (Neygo)
Result of the custom K medioids algorithm and small investigation of the clusters.

## Regression analysis (Cyrille and Alessio)
### Stock price
Explain how we will quantify the success of the companies.
Recall of Cambridge analytica

### Regression analysis on specific attributes
Explain how we did regression analysis and present the results when splitting on different attribute values.
### regression analysis on the clustering
Show and comment the regression analysis result on the group extracted via clustering.
un espace

# Conclusion (Feez)
Answer to the question
Limitations
---
# Introduction
## Abstract
With the world getting more and more connected, in particular the domain of news and journalism,
we get access to opinions of huge amount of people. These opinions can express negative, positive or
simply neutral sentiments about a subject or person. Public personalities like Mark Zuckerberg are
particularly exposed to criticism, being positive or negative. But do these online opinions really affect
his success ? Opinions of specific groups of people may indicate a rise or a fall
in his career.


In this article, we will identify the polarity of opinions in the news and try to identify different types
of authors. The study of the polarity of the opinions of each of these groups will then allow us to
potentially identify specific types of people that are a good indicators of the success of Mark Zuckerberg. 

## Data
We use a subset of the [QuoteBank dataset](https://dlab.epfl.ch/people/west/pub/Vaucher-Spitz-Catasta-West_WSDM-21.pdf)
which contains quotes made in English-speaking news articles published between 2015 and 2020. To measure the success
of Mark Zuckerberg, we use the stock price of his company Meta on the [Nasdaq Stock Market](https://www.nasdaq.com/market-activity/stocks/fb/historical).


