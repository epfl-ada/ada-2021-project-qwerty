# Title : What's trending in News? A study on the bias of "viral" news

## Abstract:
With this dataset, we can get the popularity of a person by watching his number of quotations and the number of occurrences. After having identified the popularity of the people, we can determine why certain person loses or increases his populary during the time. For instance, discovering what event makes a person famous according to the quotations he made last year, and what event made lose popularity. We could analyze the impact on the popularity when a president finish his term or when he begins his term. Or for example to infer when something append (for example: Donald Trump became president) just looking at his popularity variation. So watching the poplarity can give us a lot of informations.

Alternate Abstract: We aim to study the bias of media coverage through this dataset. Historically, media outlets have been crucial in determining and shaping public opinion.  Yet, they have generally represented the interests of a few over the masses. More often than not, the media is used as propoganda by authoritarian regimes and even used to decide the outcomes of democracy. In an ever increasing social media world, it becomes even more imperative for us to make sure that our media outlets cover the whole spectrum of the news in an unbiased manner. Thus, in our work, we try to uncover this in greater detail. The goal of our project is to understand what kinds of news topics are more popular with media outlets, does the media have a neutral stance on these topics, What makes certain news more "viral" than others and is a certain section of the society over represented by them? 

Research Questions: (A list of research questions you would like to address during the project)
1. Categorization of news topics: We notice that we are able to extract topics of news items by some processing on the URLs provided. We show preprocessing for New York Times urls in this submission. Using these extracted topics, we aim to study what are the most popular topics trending in different times, who were the most popular speakers on any of the given topics and which news vendors are the most popular for a given topic.
2. Bias in Media: In this submission, we also have shown some preprocessing on textual representations. We aim to develop classification models on quotes which classify a quote's intent as positive or negative. Here, we aim to study for each category of news topics whether the media potrays a positive or a negative outlook. Further, we aim to study which news vendors or speakers are the chief proponents of each outlook in each topic. We also have some information about the speakers itself from the Wikidata dataset. From this, we can also study whether certain sections of the society are represented more than others? Is there a systemic suppression of certain sections of the society and we also learn the stance of each of these societies on different topics
3. Popularity of News: In this part, we aim to study what kind of news is more popular than others. Since for each quote we have the number of news vendors who published it, we can see which quotes and news topics and sentiment are more popular than others. We aim to study whether news vendors publish news topics and sentiments based on popularity. 


## Datasets
- Quotebank data from 2015 to 2020
- Wikidata with speaker informations
- Wikidata QIDs with labels and description
- Pantheon Dataset

### How we manage the data
For the Quotebank data, we load directly with the help of pandas without unpack the files. We load with chunksize because the data is too big to fit in memory. So we need to handle the data by batch and merge the results (by adding in a list and concatenate this list of results to get the results dataframe). For the Wikidata with speaker information and the wikidata QIDs with labels and description datasets, we directly load all the data because there are much smaller than the first one. We merge these two datasets to get the speaker informations directly (without to look the QIDs in the wikidata QIDs dataset). The merge is done in `parse_speaker_attributes.ipynb`. We load Pantheon directly from the provided URL.

## Methods : 
- Data Preprocessing : We first preprocess the data to only keep the relevant columns and merge it with the other datasets to augment it.
- Category Extraction: We use the url information to extract information about different categories. We have done this for the NYT data and will either use a pretrained topic extraction model or try to get the value using text mining.
- Sentiment Analysis: Each quote of the dataset is analyzed to predict the sentiment. We do this using pretrained models. If needed, we will also extract emotion information for more interesting insights.


## Proposed timeline :
- Milestone P2, 12 Nov 2021
- Week 9
  - Data preprocessing
- Week 10
  - Topic Trending Analysis
- Week 11
  - Implementation of a classification model
- Week 12
- Week 13
  - Global visualisation of the results 
- Milestone P3, 17 Dec 2021

## Organization within the team: 

Questions for TAs (optional): 
