# Flask-API-for-Sentiment-Analysis-and-Indexing-with-ElasticSearch
This repo contain the code for Flask API which has two Microservices for sentiment analysis of reviews data and indexing it with ElasticSearch

![](assets/running-app.gif)
## Description
The api has two Microservices:
### 1. Reviews analyse Microservice<br>
The Microservice is responsible for anlysing the [Hotel Reviews](https://www.kaggle.com/datasets/datafiniti/hotel-reviews?select=7282_1.csv) that downloaded from Kaggle. The data analysed and each review is classified if it is considered a positive or a negative review. The model used in the classification can be found in that [Notebook](https://colab.research.google.com/gist/maidaly/10c95a5e706fe0d7001e11a27c09afad/hotels_reviews_sentiment_analysis_logisticregression.ipynb).
- The result of analysis can be found on the CSV file [hotels_data_with_tone_analysis](https://github.com/maidaly/Flask-API-for-Sentiment-Analysis-and-Indexing-with-ElasticSearch/blob/main/api/results/hotels_data_with_tone_analysis.csv) that located on the result folder. It includes all the original data after adding the sentiment analysis result of each review under the two columns ```postive_score``` and	```negative_score```. and also the normlized postive and negative score per hotel computed and can be found in the ```normlized_pos_score	``` and ```normlized_neg_score``` columns.	
### 2. ElasticSearch indexing<br>
After analysing the reviews, the data for each hotel is grouped and stored in [ElasticSearch](https://www.elastic.co/elasticsearch/) Index. So the schema of the index is ``` {'hotel_name': hotel_name, 'hotel_data': str(hotel_data)}```

#### Note: <br>
>> The app is customized for the [Hotel Reviews](https://www.kaggle.com/datasets/datafiniti/hotel-reviews?select=7282_1.csv) so, it can be used for experiments on that data and also it assumes that the ElasticSearch host is http://localhost:9200. So, if not you can change the host address from the [config.py](/api/config.py) file inside the api folder. 
