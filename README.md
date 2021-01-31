# Project 3: Web APIs & Classification

### Riche Ngo, SG-DSI-18

## Introduction

As the we progress further in the Information Age and technologies continuously improve, we see a growing interest in digital nomadism. [Digital nomads](https://en.wikipedia.org/wiki/Digital_nomad) are people who use telecommunications technologies to earn a living and, more generally, conduct their life in a nomadic manner. This [rising workforce trend](https://www.mbopartners.com/state-of-independence/research-trends-digital-nomads/) is further fueled by the increase in co-living/coworking spaces, the growth of online talent marketplaces, even the escalating work-from-home trend due to Covid-19. While it may seem like the life of a digital nomad is all rainbows and unicorns, there are downsides to adopting this nomadic lifestyle. The work that is available may not always pay all that well, and also to many, nomad life and love relationships have proven to be a bad combination. One of the most commonly cited qualms with the lifestyle is the [inevitable isolation and loneliness](https://psiloveyou.xyz/dating-as-a-digital-nomad-how-to-approach-love-in-the-laptop-lifestyle-75911313f865) that comes with it and this loneliness is an issue for sustaining meaningful relationships. 

## Problem Statement

To keep up with current trends, companies, especially start-ups, are more willing to employ digital nomads to be part of their workforce. However, organisations are also worried about the mental stability of their potential employees and the risk of poor work quality. As part of the data scientist team in a recruitment agency, we want to understand the demographic of digital nomads and whether there is truly a correlation between the nomadic lifestyle and people who do not have relationship. We want to develop a classification model that could identify traits between digital nomads and people who are not in a relationship using Natural Language Processing. Essentially, what we want to know is, are freedom and love mutually exclusive?

## Executive Summary

This project explores data collected from two subreddits using Reddit's API, namely '[digitalnomad](https://www.reddit.com/r/digitalnomad/)' and '[marriagefree](https://www.reddit.com/r/marriagefree/)'. We focus on analyzing the textual content posted by each Reddit user, together with the titles of the posts, using Natural Language Processing techniques.

The data was found to be relatively clean since the Reddit platform enables us to scrape the data in a *.json* format. However, since we are extracting only the title and main content of each post, we had to drop many duplicates which resulted in an imbalanced number of posts between the two subreddits. The average length of posts for each subreddit was quite similar, about 115-131 words. 

Preprocessing was done by removing common stopwords within the `nltk` library and the remaining words were lemmatized. Looking at the top frequently occurring words in each subreddit, we found that people in 'digitalnomad' were often discussing about work and travel while people in 'marriagefree' were often discussing about relationships and life.

While developing the classifier model, we built several pipelines, each containing a vectorizer and a classification model. We tuned the models' hyperparameters to obtain the best cross-validated score for each pipeline. Comparing the cross-validated scores, which give an estimate of the model's accuracy on unseen data, the best model was found to be a Multinomial Naive Bayes model. Since the hold-out method was also adopted, we could compare acuracy scores between train and test(hold-out) data, which were 0.98 and 0.97 respectively. Although it indicated slight overfitting of the data, the small difference was acceptable by our means. The high accuracy scores also suggest that digital nomads and single/unmarried people are very distinguishable.

The prominent words which the Naive Bayes model used to classify the textual data into 'digitalnomad' posts are words relating to travel, countries, and accomodation while posts with words relating to relationships, family, and disharmony. Incidentally, the posts that the model misclassified under the 'digitalnomad' subreddit have words that are more related to finance while posts that are misclassified under the 'marriagefree' subreddit have words relating to family or females. We also observed that words like 'depressing' appeared over more than one post that were misclassified under the 'digitalnomal' subreddit. This may suggest some sort of correlation between distress and digital nomadism.

## Data Sources

For this project, data was collected from two subreddit communities, namely 'digitalnomad' and 'marriagefree'. These communities were chose since the goal was to study if there are similar traits between digital nomads and people who are not in a relationship.

Description of the subreddits:  
* **r/digitalnomad** - This community consists of individuals that leverage technology in order to work remotely and live an independent and nomadic lifestyle. It was created in Oct 2009 and as of Dec 2020, there are 1,000,000 members.
* **r/marriagefree** - This community is for people of all genders who are single or unmarried by choice. It was created in Sep 2012 and as of Dec 2020, there are 5,100 members. The subreddit disallows gender politics, misogyny, or misandry and hate speeches.

## Conclusions

Through this project, we gained many useful insights about the discussions among people within the 'digitalnomad' and 'marriagefree' subreddits. Using the lemmatized textual data scraped from Reddit's API, we were able to develop a Multinomial Naive Bayes model with tuned hyperparameters to classify the users' posts into the two subreddits. In the process of constructing the model, we learnt that digital nomads and single/unmarried people talk about very different things. This may mean that freedom in digital nomadism and love are mutually exclusive and companies looking to recruit digital nomads should not be too worried about the mental instability caused by the loss of a relationship or the lack thereof. Despite that, this project is limited to analyzing data collected from two subreddit communities and it may not be sufficient to make such a bold claim.

The classification model which we developed had a high accuracy score of 0.98, performing much better than the baseline score of 0.85. The model classified data into 'digitalnomad' posts using words relating to travel, countries, and accomodation and classified data into 'marriagefree' posts using words relating to relationships, family, and disharmony. 3% of the test values are predicted incorrectly, which comprises of 6 False Positives and 16 False Negatives (posts originating from the 'marriagefree' subreddit considered as positive class). Posts misclassified under the 'digitalnomad' subreddit have words relating to finance while posts misclassified under the 'marriagefree' subreddit have words relating to family or females.

Further studies could be done if we were to analyze more discussions from other social media platforms such as Twitter, Facebook, Youtube, on digital nomadism. From these discussions we could continue to discover other traits and characteristics about people who decided to live the nomadic lifestyle. It is also possible to develop a survey targeted at digital nomads to obtain more information about their demographics. With deeper understanding, we would be able to provide better professional advice to organizations looking to employ digital nomads, and boosting reputation as a recruitment agency.
