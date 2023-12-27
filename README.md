# Sentiment-Analysis-with-Tweepy-and-VaderSentiment-
Perform sentiment analysis on tweets using Tweepy and the VaderSentiment library.
import tweepy
from vaderSentiment.vaderSentiment import SentimentIntensityAnalyzer

consumer_key = 'your_consumer_key'
consumer_secret = 'your_consumer_secret'
access_token = 'your_access_token'
access_token_secret = 'your_access_token_secret'

auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, access_token_secret)

api = tweepy.API(auth)
analyzer = SentimentIntensityAnalyzer()

tweets = api.user_timeline(screen_name='username', count=10, tweet_mode='extended')

for tweet in tweets:
    sentiment_score = analyzer.polarity_scores(tweet.full_text)['compound']
    print(f"Tweet: {tweet.full_text}\nSentiment Score: {sentiment_score}\n")
