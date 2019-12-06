# Bitcoin futures trading strategy based on Natural Language Processing
This is a project for the course Text Analytics and Natural Language Processing in Finance at the University of Hong Kong. Our goal is to derive a quantitative trading strategy of bitcoin futures contract based on bitcoin textual data analysis.

## Daily Trading based on Sentiment Analysis
This approach produced poorer results due to the high lag time between the tweet and the actual trade. However, it might be possible to make the strategy profitable by using and hourly time scale and improving the way the sentiment scores are generated.

The Python scripts are located in [Scripts/Sentiment/](https://github.com/noelchia/Bitcoin-NLP/tree/master/Scripts/Sentiment), and run in the following order:
1. [downloadSentiment.py](https://github.com/noelchia/Bitcoin-NLP/blob/master/Scripts/Sentiment/downloadSentiment.py) to download the data from Twitter
    * An example dataset can be found in [Data/Sentiment_Tweets.csv](https://github.com/noelchia/Bitcoin-NLP/blob/master/Data/Sentiment_Tweets.csv)
2. [generateSentiment.py](https://github.com/noelchia/Bitcoin-NLP/blob/master/Scripts/Sentiment/generateSentiment.py) to generate the Sentiment Scores from the Tweets
3. We merged the price data and sentiment scores with SQL code [mergeSentimentBTC_sql.rtf](https://github.com/chenrhcq/Bitcoin-NLP/blob/master/Scripts/Sentiment/mergeSentimentBTC_sql.rtf) and excel.
4. The backtest script is [backtestSentiment.py](https://github.com/chenrhcq/Bitcoin-NLP/blob/master/Scripts/Sentiment/backtestSentiment.py)

## Hourly Trading based on Machine Learning
Our machine learning algorithm produced far better results, but they are trained and tested on a dataset that is only 2 weeks long.

The Python scripts are located in the [Scripts/ML/](https://github.com/noelchia/Bitcoin-NLP/tree/master/Scripts/ML), and run in the following order:
1. [stream.py](https://github.com/noelchia/Bitcoin-NLP/blob/master/Scripts/ML/stream.py) to stream Bitcoin related tweets to a file
    * An example dataset can be found in [Data/data-streaming-tweets.csv](https://github.com/noelchia/Bitcoin-NLP/blob/master/Data/data-streaming-tweets.csv)
2. [dataCleaning.py](https://github.com/noelchia/Bitcoin-NLP/blob/master/Scripts/ML/dataCleaning.py) to create a cleaned and preprocessed dataset for machine learning
3. [bow.py](https://github.com/noelchia/Bitcoin-NLP/blob/master/Scripts/ML/bow.py) and [tf-idf.py](https://github.com/noelchia/Bitcoin-NLP/blob/master/Scripts/ML/tf-idf.py) to train the machine learning algorithms based on Bag of Words or Tf-idf vectorisation. Hourly data of Bitcoin prices at the Coinbase exchange can be downloaded from [CryptoDataDownload](https://www.cryptodatadownload.com/).
    * An example dataset of hourly Bitcoin prices can be found in [Data/Coinbase_BTCUSD_1h.csv](https://github.com/noelchia/Bitcoin-NLP/blob/master/Data/Coinbase_BTCUSD_1h.csv)
4. [backtest.py](https://github.com/noelchia/Bitcoin-NLP/blob/master/Scripts/ML/backtest.py) to backtest the strategy generated by machine learning

## Authors
This is a group project done by Chen Ruohua, Zeng Jia, Huang Xingyao, Yuen Dominic Chi Lok and Noel Chia.
