# Aggie_Hack_2021
## Team _Random Jungle_
Using NLP tools (Sentiment Analysis and Topic Modeling) to analyze the impact of COVID-19 on racial issues. 


<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
    </li>
    <li><a href="#methods">Methods</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgements">Acknowledgements</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

The 2021 UC Davis Aggie Hacks X Google Cloud COVID-19 Challenge brought together analytics enthusiasts from nine institutions to compete on the analysis of the impact of COVID-19 on sectors including education, housing, employment, stock prices, politics, vaccination distribution, misinformation, etc.

The two-week virtual hackathon allowed students to demonstrate their skills and proficiency in data analytics, machine learning, data visualization, and story-telling.

Our project analyzed the social impact of COVID-19 on racism through sentiment analysis and topic modeling of tweets. We measured the impact by analyzing tweets scraped from Twitter two weeks prior and two weeks after the occurrence of two key events: Trump's 'Chinese Virus' tweet on March 17, 2020, and the Atlanta mass shooting on March 16, 2021.

We concluded that Key Opinion Leader's opinions do matter in shaping people's views on racism. Hate speech is contagious; associating negative events with groups of people stimulates hate speech, and pose community on threats. On the other hand, positive speech is impactful. The #StopAsianHate campaign on social media successfully raised awareness of anti-racism. So people need to speak up; your voice matter!



<!-- GETTING STARTED -->
## Getting Started
To run the code, open the Aggiehack.ipynb file. Jupyter Notebook is preferred.
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


<!-- Methods -->
## Methods

We first define the two time periods near the two key events. The first time period is 2020-03-02 ~ 2020-04-01 (+/- two weeks near 03-17-2020 when Trump sent the first tweet on Chinese Virus). The second time period is 2021-03-01 ~ 2021-03-31 (+/- two weeks near 03-16-2021 when the Atlanta Mass Shooting occurred). For each time period, we used the pre-defined functions to scrape the tweets, conduct exploratory analysis, and build topic models on negative tweets. We specifically used the [SentimentIntensityAnalyzer (SIA)](https://www.nltk.org/api/nltk.sentiment.html) module to classify tweets into positive, negative, and neutral categories using polarity scores. To make the analyzer fit our case study, we added customized weights to the existing SIA lexicon. We also divided each time period into three time-slots, before-event, peak-of-event, and after-event, and then explored the WordCloud and built topic models for each time slot and compared the results.

  
<!-- CONTACT -->
## Contact

* Qihan Guan - [LinkedIn](https://www.linkedin.com/in/qihan-guan/) 
* Kexin Wang - [LinkedIn](linkedin.com/in/kexin-w) 
* Zhitao Zheng - [LinkedIn](https://www.linkedin.com/in/zhitao-zheng/) 


<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements
* [snscrape](https://github.com/JustAnotherArchivist/snscrape)
* [twitter-advanced-search](https://github.com/igorbrigadir/twitter-advanced-search)
* [How to Scrape Tweets With snscrape](https://betterprogramming.pub/how-to-scrape-tweets-with-snscrape-90124ed006af)
* [Topic Modeling with Gensim (Python)](https://www.machinelearningplus.com/nlp/topic-modeling-gensim-python/)
