# Text_classification with BoW & Naive_Bayes model, and investigating effect of Lemmatization & Stemming on on the model performance

<img src ="https://miro.medium.com/max/1200/1*t0mjBlwMTtuoQBEN-pb6Fg.png">

## Findings -:-

In this use case I tried to investigate how Naive Bayes performs if we use CountVectorizer as feature extractor. 

I also wanted to investigate how does lemmatization and Stemming can affect the model performace given the same text cleaning was used for both (cleaning html tags, stopwords, punctuations)

- Total training sentences,labels = 25000

- Total Validation sentences,labels = 10000

Below are the observations listed - 

1. Comparing Performance of Naive Bayes model

    Both lemmatizer(WordNetLemmatizer) and stemmer(PorterStemmer) performed quiet good with ~ 82% accuracy and f1-score around 83% & 81% for class 0 and 1 respectively. Since there were no significant class imbalance in both training and validation set, so the accuarcy_score would be a reliable metric in this case.

2. A little overfitting was noticed (accuracy on training sentences was ~88% and this is expected as I've used maximum_features for the Vecorizer to be 20000 only, so it might be the case that many of the words in the validation data may not be present in the training data during creating BoW. Default ngram_range = (1,1) was taken.

3. When used nltk.word_tokenize( ) on the stemmed sentences, it was seen that no. of tokens generated a little less than when used lemmatized senetences.

  - Total no. of tokens generated from Lemmatized sentences = 3041167
  - Total no. of tokens generated from Stemmed sentences = 3041155
  - % of unique tokens generated from Lemmatized sentences = 4.07%
  - % of unique tokens generated from Stemmed sentences = 3.44%

4. On using maximum_features = None crashes runtime Google Colab multiple times