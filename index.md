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
Explain global result about sentiment analysis on the quotes concerning Mark Zuckerberg.
present the two main plots and say that we cannot say anyhting.
-> Cambridge analytica

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

# Sentiment Analysis



## Clustering 

As already explained sentiment analysis, considering the sentiments of all the people talking about Mark Zuckerberg simultaneously doesn't give much information. We thought that it might be interesting to try to split the people into different clusters, based on different characteristics, to see if we can spot any trend where a group of people always positively or negatively about Mark Zuckerberg or Facebook. 

#### Clustering on ages

The first type of clustering coming to our mind is the to split people depending on their ages at the moment were the quote was made. We a priori think that younger people should talk more positively about Facebook or his creator as they are more susceptible to use the social network whereas older people might be more suspicious about this new technology. 

But let's look at the data and what they told us. We choose to arbitrarily split the dataset into 4 different ranges of ages: [0,25], [25-50], [51-75] and [76-125]. First of all, we will look in more details about which range of ages speaks the most about Mark. 

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="100%" allowfullscreen="true" src="figures/age_prop.html"></iframe>

From the above plot, we can see that people between 26 and 50 years tend to make the most of the quotes about Mark and Facebook. Indeed, by looking at the data, we can see that they represent around 50% of the quotes over time. Then, comes people from 51 to 75 years. We can once more see that our dataset is not balanced as we have only 10 % of quotes from people younger than 25 years and people older than 76. Let's now see the evolution of the mean compound score of each category of ages over time. 
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="50%" height="100%" allowfullscreen="true" src="figures/age_mean.html"></iframe><iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="50%" height="100%" allowfullscreen="true" src="figures/age_box.html"></iframe>
From the plot, we can see that in general the category [0, 25] tends to speak in a more positive way than any other categories. This visual difference is in fact verified by looking at the box plot about the mean compound score. It can be shown that this difference is statistically significant. The second thing we can read from the plot is that the category [51-75] tends to speak more negatively about Mark than any other category of ages (it can also be shown that this is statistically significant). 

We can also see two big spikes to low score in the plot. The first one is not very significant since it is caused by only 2 persons. The second spikes, on the other hand, corresponds to the [0-25] category and occurred in November 2016. Although that it is only caused by 14 people, it is known that Quotebank collect almost no data during this period of time. Furthermore, it also known that, at that time, Facebook was accused of having allowed Cambridge Analytica to use the personal information of almost 87 millions people on Facebook. These information would have influenced the 2016 US election. We therefore think that this very low average score at that particular point in time from the younger people (maybe the more susceptible to use social networks) represent their anger toward Facebook following this scandal. And even though 14 quotes is not enough, we can suspect that at this time, most of the person using Facebook daily may feel the same way after this revelation. We will see that negative sentiments in the negative in the quotes in November 2016 will come again and again.

#### Clustering based on gender
Let us now analyse the cluster from a gender perspective. Among the quoters of Mark Zuckerberg, there are a lot of different genders. To be precise, we get exactly 18 different genders from the data. As usual, let us first see the proportion of each gender over time among the quoters of Mark. 
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="100%" allowfullscreen="true" src="figures/gender_prop.html"></iframe>
We choose to group genders other than men or women into the "Other" category. From the plot, we can see that even by grouping all of them into the same category, they represent about 0% of the quotes at any time, i.e. they are under-represented at any point in time. For this reason, we chose to exclude them in our subsequent analysis as the results won't have much value with a so small sample size. We can also see that we have a large bias towards men in our data set since they represent 80% of the quotes at any point in time. 

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="50%" height="100%" allowfullscreen="true" src="figures/gender_mean.html"></iframe><iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="50%" height="100%" allowfullscreen="true" src="figures/gender_box.html"></iframe>

By looking at the mean compound score, the first thing that stands out is that the curve of for the women tends to be above the curve of men almost all the time. The only exception is in November 2016 where the small number of quotes we have for this date gives us the overall lowest mean compound score of all time. However, men and women tend to be mostly neutral (a bit biased toward positive) over time. The difference in the sentiment score between the men and women is shown on the second plot and is statistically significant. 


#### Clustering based on continent
Do the Europeans tend to speak more positively than the Americans ? Or maybe, does the Asians have a tendency to give a more negative opinion about Mark Zuckerberg and/or Facebook ? That's the kind of questions we will try to answer in this type of clustering. As before, let us first get an idea of where does the data come from.
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="100%" allowfullscreen="true" src="figures/cont_prop.html"></iframe>
it is absolutely not suprising to see that American gathers almost 60% of the quotes because, as explained in the introduction, the data mostly comes from American newspapers which are more likely to speak about the actuality of their giant country. After the Americans, come the Europeans with around 20% of the quotes. An interesting thing is, despite being the continent with the largest population, Asia comes only in the third places with respect to the proportion of quotes made. It is even worst for Africa which is the second continent in terms of population but that comes in last position on the proportion of quotes ladder. The "Other" category corresponds to Antartica and other similar islands. As they represent almost no data point, we cannot safely remove them from our subsequent analysis. 

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="50%" height="100%" allowfullscreen="true" src="figures/cont_mean.html"></iframe><iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="50%" height="100%" allowfullscreen="true" src="figures/cont_box.html"></iframe>

In term of mean compound score, we can see that there is no continent which seems to be always more positive than the others. The spike on the graph is only caused by one quote so we unfortunately cannot make a global conclusion about Asian people at this point in time. On the other hand, over the whole period of time, it seems that Asia speeks a bit more negatively about Mark and Facebook.
From the last plot, we can see that the above intuition about Asia is confirmed as they have a mean compound score which is statisticallly lower than the other continent. From this plot, we can also see that the European have spoken statistically more positively about Facebook and Mark than the other continent over the 5 years of news article spanned by Quotebank. 

#### Clustering 
Our final try is to let a clsutering algorithm run and see if only based on people demographic attributes, it can create clusters grouping people talking mostly positively or negatively in the quotes. To do so, the clustering algorithm will use demographic attributes that we get from Wikidata. To be more precise, we use the following attributes to cluster people: their age, nationality, profession, religion and gender. We enforce each of the previous attribute to be set so that we gain in efficiency and also we hope to obtain more interpretable clusters. 

Furthermore, we force each clusters to contain at least 2'000 people so that we can have a significant amount of people to perform the analysis we want. The total number of clusters that the algorithm outputs is 9. As before, we start by seeing if there is a cluster which contain more quotes than others. 

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="100%" allowfullscreen="true" src="figures/prop_clusters.html"></iframe>

The first thing we can see is that cluster 4 and 6 have in general less quotes than any other cluster, then come 2,5,7,8 and finally cluster 0 and 1 tends to speaks more about Facebook and Mark Zuckerberg. 

Our second analysis is to see if there is any cluster whose mean compound score is much higher than others.  To facilitate comparisons, we order the clusters in decreasing mean compound score. As shown in the boxplot below, we can see that the 4 first cluster have a much higher median for the compound score than the other clusters. 

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="100%" allowfullscreen="true" src="figures/boxplot_clusters.html"></iframe>

We can also see that at least half of the person in each cluster speaks positively about Mark Zuckerberg. Specifically, in the first 4 clusters, we can see that this percentage is increased to 75%.

As we have seen in the above description of the clusters, the first cluster is composed of women almost integraly. It is therefore expected that this cluster will get a higher mean compound score than the other since the women get a higher mean score (as shown in the clustering by gender). Another interesting fact is that cluster 6 is also mainly composed of women and they obtain a much lower mean compound score.  As the clustering algorithm didn't use the score to cluster the people, we can say that the politican and journalist women (cluster 6) tends to speak more negatively whereas actress/mode women or women working on TV tends to speak positively. We can also notify that the another similar phenomenon occurs with the men. If we take a look at the difference of the mean compound score between cluster 1 (English athletes) and clusters 7 and 8 (american politician), we can see that there is a significant difference in their mean compound score. Overall, since we observe the same phenomenon for both men and women, it is tempting to say that in general politician (irrespective of the gender) tends to talk in a bad way about Facebook and Mark. 
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="100%" allowfullscreen="true" src="figures/mean_clusters.html"></iframe>
If we look at the mean compound score over time, it is really hard to distinguish any specifical trend where everyone talks badly or in good about Mark or Facebook (other than the above comments). Again, the really negative spike from cluster 2 happened during Cambridge Analytica but as it is only one data point it is hard to draw any conclusion from this.  



[1]https://www.techrepublic.com/article/facebook-data-privacy-scandal-a-cheat-sheet/