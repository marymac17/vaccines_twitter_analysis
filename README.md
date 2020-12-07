# What does social media reveal about the world’s reaction to initial approval of a Covid-19 vaccine? 



### Machine learning project for Galvanize Data Science Immersive
### December 4, 2020
### Mary MacCarthy


##  Purpose of this analysis: 
* Over the past decade, discussion of vaccines in media and on social media have focused primarily on the vaxxer/anti-vaxxer debate.
* That debate has been sidelined by the fact that we are in a pandemic, and that much of the world is interested in developing and getting access to a specific vaccine right now (Covid-19).

* I’m interested in...
- What is the sentiment and content of current discussion of vaccines on social media?
- Specifically, I’m looking at Twitter since  it’s used extensively by both experts and non-experts (a good way of “taking the pulse” of a population). 


## My process: 
* Created my own dataset by downloading Tweets containing the keywords “vaccine” or “vaccines”, non-continuously over 72 hours , Nov. 28 - Dec 1st.
* Total number of Tweets after eliminating non-English-language data: 179,672
Incidentally, major news broke during this time: Pfizer announced the very first approval of a Covid-19 vaccine anywhere in the world (in the U.K.) 
* Cleaned text for NLP analysis (lemmatization, part-of-speech tagging, etc.)
* Used machine learning tools to do  get a sense of the overall tone of the Tweets…
* And to try to figure out what topics dominate the Twitter discussions/debates.


## Sentiment analysis: are the Tweets positive  or negative in tone? 
* Used  Vader sentiment analysis  tool, which scored each Tweet on a scale of -1 = negative to 1 = positive  (with 0 = neutral). 
* Looked at individual Tweets to judge the accuracy. My assessment: somewhat accurate, but not a lot of subtlety…
* For many Tweets, the Vader score of positive/negative tone was spot-on.
* For others, it was misguided. For example, it  gave this Tweet a somewhat positive score of 0.27…
    TWEET: “It’'s going to be mandatory. You take the vaccine or they take your livelihood."

That’s a strong statement about a potential dystopian reality - not something I would rate as positive! 
* Final note about Vader: for the full data set, the distribution of scores between 
        very negative  | somewhat negative  |  neutral   | somewhat positive  | positive 
was fairly evenly balanced - the  mean was slightly on the positive side.


## I decided to move on to topic modeling, to find information beyond just a positive/negative sentiment rating... 
* I used two unsupervised machine learning techniques to look for “latent” topics in the Tweets
- NMF (non-negative matrix factorization) 
- LDA (Latent Dirichlet Allocation) 
* Both models created lists of ten latent topics, as indicated by the top ten words in each topic..
* For this data set, the NMF model provided more detailed and nuanced topics than the LDA model... 


## LDA topic selection: not helpful 
* Examples of "top words" lists returned by LDA model: 
Top words for topic #8:
['effective', 'dos', 'emergency', 'approval', 'coronavirus', 'fda', 'pfizer', 'moderna', 'covid'']

Top 10 words for topic #9:
['fauci', 'distribution', 'vaccination', 'expert', 'dr', 'coronavirus', 'health', 'say', 'covid',]

* These lists, and the others returned by the LDA, were largely indistinguishible from each other - making it hard to label "categorities" to any of the lists.


## NMF topics: provided great insights 
* Out of ten topics returned by the NMF model, there were several clearly defined  ideas…
* One example: Topic 3 (list of words below) reveals a "latent topic" of a very focused discussion of NEED regarding/in response to Pfizer vaccine
Topic 3 (8,148 Tweets): Top 10 words for topic #3:['vp', 'asap', 'don need', 'covid pandemic', 'vaccine covid', 'pfizer', 'pandemic', 'vaccine need', 'need vaccine', 'need']

* Another example: Topic 4 reveals a topic focused on U.S. political discussion about the vaccine, specifically regarding whether or not Trump will get credit for the speed of vaccine approval 
Topic 4 (15,253 Tweets) Top 10 words for topic #4: ['president', 'did', 'came vaccine', 'came', 'credit', 'biden', 'realdonaldtrump us_fda', 'us_fda', 'trump', 'realdonaldtrump']

* Another example: Topic 6 reveals a more general U.S. discussion of covid vaccine, regarding politics, business, life (ranging from distribution of the vaccine to whether people will need a vaccine for air travel, etc.) 
Top ten words: 'cdc', 'administration', 'trump administration', 'airline', 'moderna ask', 'dos moderna', 'want', 'distribute', 'https', 'vaccine https'

* Another example: Topic 7 reveals a discussion of the Covid vaccine in relation to flu vaccine (top ten words: 'like flu', 'swine flu', 'swine', 'vaccine flu', 'vaccine year', 'flu shot', 'shot', 'year', 'flu vaccine', 'flu')


## Conclusion & next steps: 
* Many further possible steps with both NMF and LDA modeling of this and similar data sets, to understand major discussions happening in our world…
* Note RE topic modeling: I found that the topic modeling a very useful tool for sentiment analysis. NMF was able to find a category of 15k Tweets, which - according to the top ten words - seemed to express heightened emotions.
Top 10 words for topic #9:
['million people', 'don', 'vaccinated', 'die', 'million', 'want', 'think', 'vaccine people', 'people vaccine', 'people']
* I find this topic modeling much more valuable than Twitter sentiment analysis looking at positive vs. negative sentiment, in terms of understanding the content of 180k Tweets! 












