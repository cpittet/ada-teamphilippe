---
layout: page
title: Opinions in News and Mark Zuckerberg success
subtitle: Data Story
---
Do we put an image on the whole width behind the title ?
---
# Skeleton
# Abstract & introduction (Feez)
<!-- An introduction about project and why it could be useful.
Describe where the data comes from 
One or two sentences on how to extract the data-->

In February 2004, at Harvard University, a student created a website allowing other students to discuss, exchange ideas, publish their best jokes. 
This small project quickly spread to the campus, then to other universities, and finally to the whole world. This is how Mark Zuckerberg became a billionaire in a few years.
However, like any famous person, he is often exposed to a lot of criticism, especially in recent years. It is important that each person can express himself freely by giving his opinion on the decisions and actions of multinationals. 
By relaying these opinions in the media, it not only allows the company to get honest and constructive feedback, but also transmits the information to the customers or users, who might suffer the consequences.
But do these reviews have a real impact on the financial health of the company? 

In this article, we will analyze quotes from 2015 to 2020 from the Quotebank dataset to determine positive and negative thoughts about Mark Zuckerberg and his companies.
Next, we will profile the types of people issuing these quotes and analyze their tendencies to speak kindly or unfavorably about Mark Zuckerberg.
Finally, for each of theses people catergories, we will determine if the impact of these positive and negative reviews is significant on Facebook's stock numbers over time.

# Sentiment analysis<a name="sentiment"></a>
## Global result

We began by doing an overall analysis of sentiment over time, specifically, we look at the proportions of each label (positive, negative, neutral) during each week. 
The majority of quotes are positive (or neutral), so negative quotes are only a small fraction of all quotes in a given week.
We also observe that the proportion of positive quotes decreases slightly around 2018-2019, negative quotes were increasing at the same time.
This corresponds to the period when the Cambridge analytica scandal was revealed.

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="400" allowfullscreen="true" src="figures/sentiments_category.html"></iframe>

We then look at the overall average scores during each week.
As one might expect, the data are rather flat since we are averaging the different opinions and thus there is not much variance in the data. 
We observe, however, that in general the sentiment analyzer tends to assign a rather high neutral score and the quotes tend to be more positive than negative on average.

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="400" allowfullscreen="true" src="figures/means_sentiments.html"></iframe>

To finish with the overall observation, we noticed that the number of citations is not consistent over time. 
The first observation is this high spike in early 2018.
As preceded, This is when the Cambridge Analytica scandal exploded.
As seen above, quotes were becoming more negative at this time as well. 
There are also a few weeks with very few quotes from the source used to harvest the data.

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="400" allowfullscreen="true" src="figures/nb_quotes_by_period.html"></iframe>

## Clustering 

As already explained sentiment analysis, considering the sentiments of all the people talking about Mark Zuckerberg simultaneously doesn't give much information. We thought that it might be interesting to try to split the people into different clusters, based on different characteristics, to see if we can spot any trend where a group of people always positively or negatively about Mark Zuckerberg or Facebook. 

#### Clustering on ages

The first type of clustering coming to our mind is the to split people depending on their ages at the moment were the quote was made. We a priori think that younger people should talk more positively about Facebook or his creator as they are more susceptible to use the social network whereas older people might be more suspicious about this new technology. 

But let's look at the data and what they told us. We choose to arbitrarily split the dataset into 4 different ranges of ages: [0,25], [25-50], [51-75] and [76-125]. First of all, we will look in more details about which range of ages speaks the most about Mark. 

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="400" allowfullscreen="true" src="figures/age_prop.html"></iframe>

From the above plot, we can see that people between 26 and 50 years tend to make the most of the quotes about Mark and Facebook. Indeed, by looking at the data, we can see that they represent around 50% of the quotes over time. Then, comes people from 51 to 75 years. We can once more see that our dataset is not balanced as we have only 10 % of quotes from people younger than 25 years and people older than 76. Let's now see the evolution of the mean compound score of each category of ages over time. 
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="400" allowfullscreen="true" src="figures/age_mean.html"></iframe><iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="400" allowfullscreen="true" src="figures/age_box.html"></iframe>
From the plot, we can see that in general the category [0, 25] tends to speak in a more positive way than any other categories. This visual difference is in fact verified by looking at the box plot about the mean compound score. It can be shown that this difference is statistically significant. The second thing we can read from the plot is that the category [51-75] tends to speak more negatively about Mark than any other category of ages (it can also be shown that this is statistically significant). 

We can also see two big spikes to low score in the plot. The first one is not very significant since it is caused by only 2 persons. The second spikes, on the other hand, corresponds to the [0-25] category and occurred in November 2016. Although that it is only caused by 14 people, it is known that Quotebank collect almost no data during this period of time. Furthermore, it also known that, at that time, Facebook was accused of having allowed Cambridge Analytica to use the personal information of almost 87 millions people on Facebook. These information would have influenced the 2016 US election. We therefore think that this very low average score at that particular point in time from the younger people (maybe the more susceptible to use social networks) represent their anger toward Facebook following this scandal. And even though 14 quotes is not enough, we can suspect that at this time, most of the person using Facebook daily may feel the same way after this revelation. We will see that negative sentiments in the negative in the quotes in November 2016 will come again and again.

#### Clustering based on gender
Let us now analyse the cluster from a gender perspective. Among the quoters of Mark Zuckerberg, there are a lot of different genders. To be precise, we get exactly 18 different genders from the data. As usual, let us first see the proportion of each gender over time among the quoters of Mark. 
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="400" allowfullscreen="true" src="figures/gender_prop.html"></iframe>
We choose to group genders other than men or women into the "Other" category. From the plot, we can see that even by grouping all of them into the same category, they represent about 0% of the quotes at any time, i.e. they are under-represented at any point in time. For this reason, we chose to exclude them in our subsequent analysis as the results won't have much value with a so small sample size. We can also see that we have a large bias towards men in our data set since they represent 80% of the quotes at any point in time. 

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="400" allowfullscreen="true" src="figures/gender_mean.html"></iframe><iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="400" allowfullscreen="true" src="figures/gender_box.html"></iframe>

By looking at the mean compound score, the first thing that stands out is that the curve of for the women tends to be above the curve of men almost all the time. The only exception is in November 2016 where the small number of quotes we have for this date gives us the overall lowest mean compound score of all time. However, men and women tend to be mostly neutral (a bit biased toward positive) over time. The difference in the sentiment score between the men and women is shown on the second plot and is statistically significant. 


#### Clustering based on continent
Do the Europeans tend to speak more positively than the Americans ? Or maybe, does the Asians have a tendency to give a more negative opinion about Mark Zuckerberg and/or Facebook ? That's the kind of questions we will try to answer in this type of clustering. As before, let us first get an idea of where does the data come from.
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="400" allowfullscreen="true" src="figures/cont_prop.html"></iframe>
it is absolutely not suprising to see that American gathers almost 60% of the quotes because, as explained in the introduction, the data mostly comes from American newspapers which are more likely to speak about the actuality of their giant country. After the Americans, come the Europeans with around 20% of the quotes. An interesting thing is, despite being the continent with the largest population, Asia comes only in the third places with respect to the proportion of quotes made. It is even worst for Africa which is the second continent in terms of population but that comes in last position on the proportion of quotes ladder. The "Other" category corresponds to Antartica and other similar islands. As they represent almost no data point, we cannot safely remove them from our subsequent analysis. 

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="400" allowfullscreen="true" src="figures/cont_mean.html"></iframe><iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="400" allowfullscreen="true" src="figures/cont_box.html"></iframe>

In term of mean compound score, we can see that there is no continent which seems to be always more positive than the others. The spike on the graph is only caused by one quote so we unfortunately cannot make a global conclusion about Asian people at this point in time. On the other hand, over the whole period of time, it seems that Asia speeks a bit more negatively about Mark and Facebook.
From the last plot, we can see that the above intuition about Asia is confirmed as they have a mean compound score which is statisticallly lower than the other continent. From this plot, we can also see that the European have spoken statistically more positively about Facebook and Mark than the other continent over the 5 years of news article spanned by Quotebank. 

#### Clustering 
Our final try is to let a clsutering algorithm run and see if only based on people demographic attributes, it can create clusters grouping people talking mostly positively or negatively in the quotes. To do so, the clustering algorithm will use demographic attributes that we get from Wikidata. To be more precise, we use the following attributes to cluster people: their age, nationality, profession, religion and gender. We enforce each of the previous attribute to be set so that we gain in efficiency and also we hope to obtain more interpretable clusters. 

Furthermore, we force each clusters to contain at least 2'000 people so that we can have a significant amount of people to perform the analysis we want. The total number of clusters that the algorithm outputs is 9. As before, we start by seeing if there is a cluster which contain more quotes than others. 

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="400" allowfullscreen="true" src="figures/prop_clusters.html"></iframe>

The first thing we can see is that cluster 4 and 6 have in general less quotes than any other cluster, then come 2,5,7,8 and finally cluster 0 and 1 tends to speaks more about Facebook and Mark Zuckerberg. 

Our second analysis is to see if there is any cluster whose mean compound score is much higher than others.  To facilitate comparisons, we order the clusters in decreasing mean compound score. As shown in the boxplot below, we can see that the 4 first cluster have a much higher median for the compound score than the other clusters. 

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="400" allowfullscreen="true" src="figures/box_clusters.html"></iframe>

We can also see that at least half of the person in each cluster speaks positively about Mark Zuckerberg. Specifically, in the first 4 clusters, we can see that this percentage is increased to 75%.

As we have seen in the above description of the clusters, the first cluster is composed of women almost integraly. It is therefore expected that this cluster will get a higher mean compound score than the other since the women get a higher mean score (as shown in the clustering by gender). Another interesting fact is that cluster 6 is also mainly composed of women and they obtain a much lower mean compound score.  As the clustering algorithm didn't use the score to cluster the people, we can say that the politican and journalist women (cluster 6) tends to speak more negatively whereas actress/mode women or women working on TV tends to speak positively. We can also notify that the another similar phenomenon occurs with the men. If we take a look at the difference of the mean compound score between cluster 1 (English athletes) and clusters 7 and 8 (american politician), we can see that there is a significant difference in their mean compound score. Overall, since we observe the same phenomenon for both men and women, it is tempting to say that in general politician (irrespective of the gender) tends to talk in a bad way about Facebook and Mark. 
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="400" allowfullscreen="true" src="figures/mean_clusters.html"></iframe>
If we look at the mean compound score over time, it is really hard to distinguish any specifical trend where everyone talks badly or in good about Mark or Facebook (other than the above comments). Again, the really negative spike from cluster 2 happened during Cambridge Analytica but as it is only one data point it is hard to draw any conclusion from this.  

## Regression analysis (Cyrille and Alessio)

How do the opinions of different groups of people in the news about Mark Zuckerberg and his companies relate to the
the success his success ? To investigate this question, we use different regression analyses. This
allows us to discover if there are certain trends for a given group, whether these trends are statistically
significant and how they impact his success. We see below how we can quantify the success of Mark Zuckerberg.


### How can we measure the success of an entrepreneur ?

There are different possible ways to quantify the success of an entrepreneur. If we remain down to
earth and do not enter philosophical discussions on what actually is success, we can imagine evaluating
our person of interest, Mark Zuckerberg, by looking at his wealth over time. However, this is not always
easy to do as is since we do not have transparent access to his assets, properties and their values.


Instead, we use a "proxy" for his wealth by considering the stock price on the Nasdaq Market for a
company is well known for, Facebook, now Meta Platforms Inc. Mark Zuckerberg is the CEO and one of the founders of Meta Platforms
that regroups entities such as Facebook, Instagram, Whatsapp. As the stock market is generally reactive
to, for examples, scandals, new improvements on products etc, it is a reasonable way to quantify how
well Mark Zuckerberg is doing. Moreover, this is a reliable source of information for the period we are
treating (2015-2020) as we can easily access daily stock prices for the past years.


As said [above](#sentiment), we consider weekly data. For the stock price, the daily opening and closing
prices are averaged and then these values are averaged over each week to get a single representative 
price for the week. In the figure below, we have the evolution from 2015 to 2020 of this weekly average
stock price. It increases steadily from 2015 until the beginning of 2018. Around March 2018, it falls.
This corresponds to the period where the Cambridge Analytica scandal with Facebook exploded. So this verifies
that the stock market is reactive to external events as we said above.

![Stock price](stock_price.png)

More concretely, the design matrix is built as follows. A datapoint (predictor) is the vector of average positive and negative
scores over a given week as well as the number of quotes made during that week, and this for every group. What 
we would like to investigate is whether trends in the opinions of some groups give some indications about the
futur behavior of the stock price of Meta. Therefore, for a predictor at week n, we consider the stock
price at week n+1 as its response variable. Since the different features do not have the same range (positive score
is between 0 and 1 but the number of quotes may be in the hundreds), we standardize the features.


Note that here the goal is exactly to predict very accurately the stock price of the upcoming week based
on the current week quotes but rather to see if there trends among certain groups that emerges. To accurately
predict the stock prices, we would probably need more complex models as well as other features. However, more complex models
quickly becomes less interpretable (black-box models) and this would prevent us to extract the trends
we look for. So a simple linear regression is well suited for this task.


### Regression analysis on specific attributes

Let's look at different possible characterizations of people. Below, we consider the following one :
 - Gender (named according to WikiData)
 - The continent where the author comes from
 - Her/his age, distributed into 4 ranges : 0-25, 26-50, 51-75 and 75+
 - Using our custom [clustering](#clustering)

The data contained many different genders. Sadly, the genders other than women/men were under-represented.
This means many weeks were not containing any quotes by such authors and therefore would introduce missing
data in our design matrix. So for technical reasons, we focus only on these 2 genders.

#### Analysis by gender

How the different features for each group, here women and men, relate to the stock price. Below, we
have the relation between the stock price at week n+1 and the different features at week n, as well as
a regression line estimated from the given feature only. We directly observe that there is no very clear linear correlation
between a feature and the price. Some features as the positive mean for men even seem to be irrelevant whereas
other features such as the number of quotes made by women seem to exhibit a slight linear relationship.

![Scatter plots gender](assets/img/scatter_gender.png)
![Scatter plots gender1](assets/img/scatter_gender1.png)

To find more accurate insights about these possible trends, let's consider the coefficients obtained 
with a linear regression taking as input all the 6 features above and as output the (delayed) average stock price.
The statistically significant coefficients at level 5% are shown in color, the others in gray. Over the 6 features,
only 3 are statistically significant at level 5%. Surprisingly, the coefficient associated to the negative
sentiment for the men is positive. This means that the more negative the men quotes are the higher the stock prices
tend to be.

Women quotes are a good sign for the price whereas the number of men quotes is a bad omen for the stock price.
Indeed, the number of quotes made by men is negative whereas the one for women is positive.

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="300" allowfullscreen="true" src="figures/coeffs_gender.html"></iframe>

Does the model fit well the data ? Our linear regression model reaches a $R^2$ score of 0.36. So it is able
to capture more variance than a constant model.

#### Where do they come from ?

Comparably to the analysis on genders, the plots of the stock price w.r.t. each of the features do not exhibit very clear
trends, and we omit it here for clarity questions.

Similarly to the regression on genders, the only features that matters here are the number of quotes and the negative
score but the positive score is not relevant (not statistically significant at level 5%). Again, there is
some contrast between the number of quotes in different groups. The more American quotes there is, the lower 
the price tend to be whereas the more quotes there are in Europe or Asia, the higher the price is likely to be.

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="600" allowfullscreen="true" src="figures/coeffs_continent.html"></iframe>

As before, this fit has a $R^2$ score of 0.33.

#### How old are they ? 

Here we look at the different ranges of age in the authors. Namely, we consider the ranges [0-25], [26-50], [51-75], [76+].
As what was done in the two previous analysis, we do not show the plots of the relationships between the features and the stock prices
since they are very similar and do not add much insights.
 
We don't change a winning team... it is again the count of quotes and the negative score that matter most. However,
the positive score for the 76+ authors seem to be relevant as well. But, as surprisingly as before, the corresponding
coefficient is negative, meaning that the more positive the quotes are for these people, the lower the stock price tends to be.

We can also look at the magnitude of the significant coefficient for the negative scores. A larger coefficient
would mean that this group is more "influential" or gives stronger indication that the stock price will be high (as they are all
positive). For example here, the most relevant group would be the 26-50, which tend to be the most active and powerful
in the industry in general, seem to weigh more in the behavior of the stock prices than the other 2 groups. This also
reflect the fact that we have a majority of people in this range of age in our dataset.

A contrast in the count of quotes also emerges. Young people seem to be more critical in their opinions than older people.
Indeed, the coefficient for the count of quotes by young people (0-25) is negative whereas the one for the older people
(76+) is positive. This is in concordance with our previous [analysis](#global-result-neygo).

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="600" allowfullscreen="true" src="figures/coeffs_age.html"></iframe>

For this model, the $R^2$ score is 0.28, so it captures more variance in the data than the constant model.

#### Who are they ?

Similarly to what is done for the other analyses, we omit the features plots for presentations reasons.

Cluster containing mainly women, such as clusters 0 and 6, tend to have a positive influence via their count coefficient.
The count of quotes of American men however rather negative for the stock price as we can see in clusters 1 and 5. This is
what we also observed in the analyses about [continents](#where-do-they-come-from-) and [gender](#analysis-by-gender).

Let's now try to investigate which professions are the most influential. We could expect that professions such as economists,
politicians weigh more in the game than artists, athletes or similar. For example, consider the coefficients corresponding
to the negative score of clusters 1, 5 and 7, which are statistically significant at level 5%. These [clusters](#clustering) mainly contains
American male athletes, American male journalists and American male politicians, respectively. By inspecting
the magnitude of these coefficients, we can deduce that the larger ones are more important for the stock price.
In our case, the most relevant profession is journalist, followed by politician and finally athletes. This is comparable
to what we expected.

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width="100%" height="750" allowfullscreen="true" src="figures/coeffs_cluster.html"></iframe>

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





