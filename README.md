# Stock-Market-Prediction

## Types of data available with us:
1. News data 
2. Quant Data of Company listed in NSE (National Stock Exchange India) 

The model is based on correlating the stock and news data.

## Data Analysis:
Since, stock data is almost normally distributed we can use various statistical analysis techniques like mean, std. deviation, correlation, covariance, regression models, confidence interval,  leverage, beta hedging, etc to get insights. 

Using combination of regression models and other statistics we have developed following techniques to study key behaviour of time-series data of different equities and further relating them to corresponding news.

* **Breakpoints:**

This is to target certain maxima and minima in the quant data of companies, which can further be trained with news and their sentiments. Breakpoints can also be analysed to find the optimum buy and sell time for maximizing profit. Breakpoint can be characterised on the basis of skewness, kurtosis, etc.

* **News impact analysis using volume:**

We can determine the sentiment of the news by the change in price, as to check wether the news was positive or negative. But to measure the impact a news carry we should use volume as one of the factor. Volume of a stock is very volatile, and thus, it is difficult to analyse the impact by simply calculating percentage change in the volume itself. 

* **Pairs trading:**

Pairs traders wait for weakness in the correlation and then go long the under-performer while simultaneously short selling the over-performer, closing the positions as the relationship returns to statistical norms. Thus, here we try to club togather assetes that are uncorrelated so that we can save ourselves from heavy loss. The basic strategy is to create a stable porfolio and keep earning on it. 

## Series of steps must be followed for predicting the stock price based on news:

1. Collecting Data: Mainly company related news which are listed nse India
  * Using twitter API 
  * Webscraping
  * Crawling
  * Kaggle

2. Preprocessing the data
  * Cleaning the news.
  * Associating company name to news article.

3. Predicting Sentiment based on previous sentiments:
  * Using Classifiers present in scipy library of python: Naive bayes, Bernaulli etc.
  * Nltk's Sentiment Intensity Analyser
  * The deeplearning model.

4. Preprocessing the data:
  * Using regression to find out news effect on stock price and volume
  
5. Correlating news with the stock data present:
  * Deeplearning model for correlating news impact on stock price and volume.
  * Using LSTM for predicting stock price.
  

### Explanation

**DATA COLLECTION**

I started collecting the news from different sources. I have scraped news from Moneycontrol, IIFL, Economic Times, Business Standard, Reuters and LiveMint. Attributes such as Tags, Title, Subtitle, Categories and Content along with the time and date of the news was scraped. Data from twitter is also scraped for better real-time collection of data. Also scraped twitter for getting realtime data and we used crawler to get the annual reports.

**PREPROCESSING DATA (Stage 1)**

Cleaning the news: Stemming, chunking, chinking, stopwords removal etc. Associating company names to the news article to know which news was related to which company. 

**SENTIMENT ANALYSIS OF NEWS**

It is important to find the sentiment of each news. The sentiment value gives us a better understanding whether the news was a positive, negative, mixed or neutral one. This also helps in sorting out the neutral news. News of announcements and political parties have little role to play in building the model for forecasting. Hence these can be ignored. 

The accuracy of the deeplearning model is **97%**!

**PREPROCESSING THE DATA (Stage 2)**

I labeled the news with quant data regression line slope value.
So for that we first open the news file and checked its date-time, now that date-time is searched in quant data. If the time is present in market hours of stock market then the text is labeled with slope value of regression line.Else if news is not in market hours then closing value of previous day and opening value of current days' regression line acts as its label.


**Training model based on the prepared data**

Now we have two values the sentiment value of the text and slope value of quant when the news broke out in the market.
I made a deep learning model such that the input was the sentiment value and the target value will be the slope value.
So from this we can predict if a news about a company comes in market what will be the impact of it on the price and volume of the stocks of that company. 


**Predicting stock value using Quant Data only (LSTM model)**

I also created a LSTM model which will be predicting a future price of stocks and this model is trained on just the stock data. The input of the model is closing value of previous day and target value was set to opening value of current day. This model was not as accurate but it can predict the possibility and flow. 
