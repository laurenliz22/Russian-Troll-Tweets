# Russian Troll Tweets

## Kaggle Notebook
Please find the work for this Project completed here: https://www.kaggle.com/laurenliz22/russian-troll-tweets

### Purpose

The purpose of this project is to determine if the account categories, as coded by Linvill and Warren, in the 3 Million Russian Troll Tweets shared by FiveThirtyEight can be classified by the tweets themselves. The Twitter handles within the dataset are connected to the Internet Research Agency, which is a Russian “troll factory” and a defendant in an indictment as part of Robert Mueller’s Russia investigation. The tweets in the dataset are between February 2012 and May 2018.  This analysis is to help determine how Russian Trolls use language in their Tweets to target audiences in future endeavors, such as influencing future elections.

### Data

The analysis for this project has been completed within a Kaggle Notebook, link above, using the 7 csv data files inluded.  To reproduce results, you can fork the notebook at the link above.

The initial data files have the following columns: 

Header | Definition
---|---------
`external_author_id` | An author account ID from Twitter 
`author` | The handle sending the tweet
`content` | The text of the tweet
`region` | A region classification, as [determined by Social Studio](https://help.salesforce.com/articleView?   id=000199367&type=1)
`language` | The language of the tweet
`publish_date` | The date and time the tweet was sent
`harvested_date` | The date and time the tweet was collected by Social Studio
`following` | The number of accounts the handle was following at the time of the tweet
`followers` | The number of followers the handle had at the time of the tweet
`updates` | The number of “update actions” on the account that authored the tweet, including tweets, retweets and likes
`post_type` | Indicates if the tweet was a retweet or a quote-tweet
`account_type` | Specific account theme, as coded by Linvill and Warren
`retweet` | A binary indicator of whether or not the tweet is a retweet
`account_category` | General account theme, as coded by Linvill and Warren
`new_june_2018` | A binary indicator of whether the handle was newly listed in June 2018


### Methodology Taken:
- Initially the data is contained in 7 separate csv files. These data files will be combined to analyze all 3 Million tweets.
- The data files will be cleaned to remove, keep or replace any missing or limited values for analysis purposes.
- After cleaning begins the exploratory phase. This will include:
    - Producing follower/following graphs based on account category;
    - Producing tweet frequency by publish date; and
    - Producing wordclouds split by popular account categories to view language patterns.
- Once the data has been explored feature engineering and classification modeling of the tweets is next:
    - A combination of Word2Vec and TF-IDF Vectorization will be used for modeling
    - Random Forest Classifiers and Neural Network Classifiers will be examined to determine the best fit model.


### Conclusion

After modeling the dataset I’ve uncovered the following findings and recommendation for determining future Russian Trolls:

- 72% of all tweets were in English followed by 21% in Russian. It appears that most handlers use the English language when they tweet.
- 87% of all tweets were classified as being from the region of the United States. They could have been using a VPN or tweeting within the United States.
- Most tweets are split between Retweets and Non-Retweets and from the following 3 account categories:
    - News Feed
    - Right Troll
    - Left Troll
- Right Trolls have the largest number of followers and have more followers than those they are following compared to Left Trolls and News Feed account categories. There is a small subsection of Left Trolls and News Feed account categories that do have more followers than those they are following; however, for the most part they are balanced.
    - The most tweeted words used by Right Trolls are “Trump”, “Hillary”, “Obama”, “New”, "People" and “n’t” to target audiences.
    - The most tweeted words used by Left Trolls are “Trump”, “Black”, “White”, “New”, "People" and “n’t” to target audiences.
    - The differences between Left Trolls and Right Trolls are the focus on Democrats for Right Trolls, with the words “Hillary” and “Obama” used often, over race, with Left Trolls using the words “Black” and “White” more.
    - The most tweeted words used by News Feeds are “Sport”, “Politic”, “Police”, “New”, "World" and “Man”, which makes sense as these are common words used by the news
- There was a huge spike in tweets on 10/6/2016 with 17,984 tweets. This is followed by the second most tweeted day on 10/7/2016 with 9,620 tweets. Most of these tweets came from Left Trolls.
    - When looking at the language used on 10/6/2016 the words "Trump", "Hillary", "Black", "New", "People" and "n't" were the most tweeted words to target audiences.
    - 10/6/2016, the day before 10/7/2016, when 30 minutes after the Access Hollywood tape was first published where Trump spoke crudely about groping women, WikiLeaks began publishing thousands of emails from John Podesta’s Gmail account. Hurricane Matthew was also taking place in early/mid October. These events probably caused the huge rush of tweets on that day.

After looking at a Random Forest Classifier and various Neural Network Classifiers to predict account category based on tweet, a Random Forest Classifier with the simple parameters above is the best model I found, with 80% accuracy!

Future work could include performing a grid search to see if there could be any futher improvement on the Random Forest model.
