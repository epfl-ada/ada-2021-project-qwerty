# Title : What's trending in News? A study on the bias of "viral" news

## Abstract:
We aim to study the bias of media coverage through this dataset. Historically, media outlets have been crucial in determining and shaping public opinion.  Yet, they have generally represented the interests of a few over the masses. More often than not, the media is used as propoganda by authoritarian regimes and even used to decide the outcomes of democracy. In an ever increasing social media world, it becomes even more imperative for us to make sure that our media outlets cover the whole spectrum of the news in an unbiased manner. Thus, in our work, we try to uncover this in greater detail. The goal of our project is to understand what kinds of news topics are more popular with media outlets, does the media have a neutral stance on these topics, What makes certain news more "viral" than others and is a certain section of the society over represented by them? 

Research Questions: (A list of research questions you would like to address during the project)
1. Categorization of news topics: We notice that we are able to extract topics of news items by some processing on the URLs provided. We show preprocessing for New York Times urls in this submission. Using these extracted topics, we aim to study what are the most popular topics trending in different times, who were the most popular speakers on any of the given topics and which news vendors are the most popular for a given topic.
2. Bias in Media: In this submission, we also have shown some preprocessing on textual representations. We aim to develop classification models on quotes which classify a quote's intent as positive or negative. Here, we aim to study for each category of news topics whether the media potrays a positive or a negative outlook. Further, we aim to study which news vendors or speakers are the chief proponents of each outlook in each topic. We also have some information about the speakers itself from the Wikidata dataset. From this, we can also study whether certain sections of the society are represented more than others? Is there a systemic suppression of certain sections of the society and we also learn the stance of each of these societies on different topics
3. Popularity of News: In this part, we aim to study what kind of news is more popular than others. Since for each quote we have the number of news vendors who published it, we can see which quotes and news topics and sentiment are more popular than others. We aim to study whether news vendors publish news topics and sentiments based on popularity. 

The website can be opened here (https://qingbeixi.github.io/qwerty/)

## Datasets
- Quotebank data from 2015 to 2020
- Wikidata with speaker informations
- Wikidata QIDs with labels and description
- Pantheon Dataset

### How we manage the data
For the Quotebank data, we load directly with the help of pandas without unpack the files. We load with chunksize because the data is too big to fit in memory. So we need to handle the data by batch and merge the results (by adding in a list and concatenate this list of results to get the results dataframe). For the Wikidata with speaker information and the wikidata QIDs with labels and description datasets, we directly load all the data because there are much smaller than the first one. We merge these two datasets to get the speaker informations directly (without to look the QIDs in the wikidata QIDs dataset). The merge is done in `parse_speaker_attributes.ipynb`. We load Pantheon directly from the provided URL. After we merge `parse_speaker_attributes` dataset with `quotebank dataset` to get more information about the speaker of the quotations. Before to merge these two dataframes, we take care to only keep the more useful columns to save memory because the data is really to big to fit in memory. We also parse the urls to only keep the base of the urls (for example: www.website.com or website.com) to be more clear and in the same time save memory because the after parts of these urls can be very long. So finally we get the more interesting informations and in the same time we reduce 5-6x the size of the initial files. In a second time, we keep only the nytimes quotations. To do that we filter by the urls. Use the nytimes urls is very interesting because we can extract the different topics from them because these urls follow a pattern. So we build the same kind of dataset like the previous one but we add the new topic columns. The different notebooks use to build the datasets are in the folder `Dataset`.

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
  - Apply the classification model
  - Analysis the results
- Week 13
  - Global visualisation of the results 
- Milestone P3, 17 Dec 2021

## Organization within the team: 
- Anmol: General Exploration on topics and sentiments
- Tushar: Focus on the analysis for NewYork Times
- Luca: Extend the timeline for data analysis + build new datasets
- Qing Jun: Making the website

## P.S
We have uploaded a single notebook (ADA_Project_QWERTY), but it is too long to render on Github, therefore we have uploaded the 3 parts separately
- Sentiment_Topic_2019
- Sentiment-NYT
- News_topic_extraction_and_NYT

We also have more notebooks in the notebooks folder with analysis for each year and the Dataset folder contains some other ones which we used to preprocess the data. 

For viewing the interactive plots, download the files in the Plots_interactive folder and open them in a browser.