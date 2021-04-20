# Aggie_Hack_2021
## Team _Random Jungle_
Using NLP tools (Sentiment Analysis and Topic Modeling) to analyze the impact of COVID-19 on racial issues. 


<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#overview-of-the-problem">Overview of the problem</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
    </li>
    <li><a href="#data-gathering-process-and-storage-option">Data gathering process and storage option</a></li>
    <li><a href="#model-performance">Model Performance</a></li>
    <li><a href="#acknowledgements">Acknowledgements</a></li>
  </ol>
</details>



<!-- OVERVIEW OF THE PROBLEM -->
## Overview of the problem

The 2021 UC Davis Aggie Hacks X Google Cloud COVID-19 Challenge brought together analytics enthusiasts from nine institutions to compete on analyzing the impact of COVID-19 on sectors including education, housing, employment, stock prices, politics, vaccination distribution, misinformation, etc.

The two-week virtual hackathon allowed students to demonstrate their skills and proficiency in data analytics, machine learning, data visualization, and story-telling.

Our project analyzed the social impact of COVID-19 on racism through sentiment analysis and topic modeling of tweets. We measured the impact by analyzing tweets scraped from Twitter two weeks prior and two weeks after the occurrence of two key events: 
* Trump's 'Chinese Virus' tweet on March 17, 2020
![Trump's tweet](https://i.imgur.com/qgtGhwE.png)
![WordCloud1](/relative/path/to/img.jpg?raw=true "worldcloud1.png")

* The Atlanta mass shooting on March 16, 2021.
![AtlantaShooting](https://media3.s-nbcnews.com/j/newscms/2021_11/3457653/210317-atlanta-gold-spa-exterior-ac-1149p_8c1bfeea1350b6d3c8dac9d7ff82c316.fit-760w.jpg)
![WordCloud2](/relative/path/to/img.jpg?raw=true "worldcloud2.png")

The first time period was 2020-03-02 ~ 2020-04-01 (+/- two weeks near 03-17-2020 when Trump sent the first tweet on Chinese Virus). The second time period was 2021-03-01 ~ 2021-03-31 (+/- two weeks near 03-16-2021 when the Atlanta Mass Shooting occurred). For each time period, we used the pre-defined functions to scrape the tweets, conduct exploratory analysis, and build LDA topic models on negative tweets. We specifically used the [SentimentIntensityAnalyzer (SIA)](https://www.nltk.org/api/nltk.sentiment.html) module to classify tweets into positive, negative, and neutral categories using polarity scores. To make the analyzer fit our case study, we added customized weights to the existing SIA lexicon. We also divided each time period into three time-slots, before-event, peak-of-event, and after-event, and then explored the WordCloud and built topic models for each time slot and compared the results.

We concluded that Key Opinion Leader's opinions do matter in shaping people's views on racism. Hate speech is contagious; associating negative events with groups of people stimulates hate speech, and pose community on threats. On the other hand, positive speech is impactful. The #StopAsianHate campaign on social media successfully raised awareness of anti-racism. So people need to speak up; your voice matter!


<!-- GETTING STARTED -->
## Getting Started
To run the code, open the Aggiehack_random_jungle.ipynb file. Jupyter Notebook is preferred.
To run the code in Google Colab, please enable local runtime. 
For detailed instructions, please refer to [Running Colab on Local Runtime](https://research.google.com/colaboratory/local-runtimes.html)

This first library to install is ```snscrape ``` for scraping tweets from tweeter:
  ```sh
  !pip install git+https://github.com/JustAnotherArchivist/snscrape.git
  ```
_For more details, please refer to the [Documentation](https://github.com/JustAnotherArchivist/snscrape)_

Next, install Pandas and Regex if you do not have them installed:
  ```sh
  !pip install pandas
  !pip install re
  ```
Next, download these nltk data:
  ```
  nltk.download('stopwords')
  nltk.download('vader_lexicon')
  nltk.download('punkt')
  ```
Next, install packages for LDA topic modeling:
In conda environment:
  ```sh
  pip install gensim
  conda install -c conda-forge spacy
  python -m spacy download en_core_web_sm 
  conda install -c conda-forge pyldavis
  ```
To view topic model visualizations, please download peak_event1_topic_viz.html and peak_event2_topic_viz.html and open with your browser. 

<!-- DATA GATHERING PROCESS AND STORAGE OPTION -->
## Data gathering process and storage option
We gathered our data by scraping tweets from Twitter through the ```snscrape ``` package. To address our proposed problem, we specified the search keywords and time-slots by modifying the query parameters inside the ```snscrape ``` package:
```
query = '(china OR chinese OR asian) (covid OR virus OR corona OR pandemic) since:{} until:{} lang:en min_faves:{}'.format(startdate, enddate, min_faves)
tweets_df1 = tweets_analysis(startdate = "2020-03-02", enddate = "2020-04-01", min_faves = 100)
tweets_df2 = tweets_analysis(startdate = "2021-03-01", enddate = "2021-03-31", min_faves = 100)
```
We specifically looked for tweets that contain both keywards related to china/chinese/asian and covid/virus/corona/pandemic. We only kept tweets that had a minimum of 100 likes so that our data can be representative. We saved our data in _Pandas_ dataframes for exploratory analysis and topic modelinng.    

<!-- MODEL PERFORMANCE -->
## Model Performance
For topic modeling, we used Latent Dirichlet Allocation(LDA) algorithm provided by Python's _Gensim_ package. Model performance was measured by model perplexity score. The lower the perplexity score, the better the performance. Our models' perplexity scores mainly fell into the -8 ~ -7 range. Our models were also evaluated by the interactive visualizations provided by the _pyLDAvis_ package. 
![ldaviz1](/lda_viz1.jpg?raw=true "lda_viz1.JPG")

![ldaviz2](/relative/path/to/img.jpg?raw=true "lda_viz2.JPG")

Each cricle in the plots represent a topic. The further the circles are away from each other, the more different the topics are. From the plots, we could see that we had big and non-overlapping circles scattered throughout the plot. Therefore, our topic models had good performance. 

<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements
* [snscrape](https://github.com/JustAnotherArchivist/snscrape)
* [twitter-advanced-search](https://github.com/igorbrigadir/twitter-advanced-search)
* [How to Scrape Tweets With snscrape](https://betterprogramming.pub/how-to-scrape-tweets-with-snscrape-90124ed006af)
* [Topic Modeling with Gensim (Python)](https://www.machinelearningplus.com/nlp/topic-modeling-gensim-python/)
