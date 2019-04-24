# Reddit Project 3
## Omar Raheem



... There are so many new television shows. So many witty and irreverent shows with memorable characters and with streaming services able to make TV on demand we can watch any show at anytime we choose. But what shows to watch? And why should you watch them? I, as a data scientist for Reddit will present to you two long running shows that are both humorist and charming in their own unique ways. I will use Reddit data and natural language processing to show how these two shows are different and let you be the judge on whether one, both or maybe neither one of these shows are for you. In addition I will build four models that will take a word and predict if it belongs to the AD subreddit or the VB subreddit using .score which measures accuracy. 

Hyperparameters: Hyperparameters fine tune a model to assist in finding the best score. The hyperparameters I will be using in my model include:
Max features- builds a vocabulary that only consider the top max_features ordered by term frequency across the corpus.
Min df - ignores terms that have a document frequency strictly lower than the given threshold. If float, the parameter represents a proportion of documents, integer absolute counts.
Max df- ignore terms that have a document frequency strictly higher than the given threshold (corpus-specific stop words).
N_gram_range- The range of word groups. 
Max_depth- Sets the nodes that are expanded to find purity in the data
Learning_rate- Learning rate shrinks the contribution of each classifier bylearning_rate
Alpha - sets a series of alphas

Model 1: Will use TFID to vectorize the words and give some words more weight than other words thus assisting in assigning a prediction to the word then run a Logistic Regression with a Grid Search to search over the hyper parameters for the model that gives the best  .score.

Find Best Word: I created a function that will take the input of a word or passage from American Dad or Venture Bros and give you back a prediction with an output of either American Dad or Venture Bros.

Model 2: Uses TFID Vectorizer and excludes common english stop words better sort through the words then uses a Random Forest Classifier(RFC). The RFC uses a set number of decision trees to randomly run over the words in the data, predicting the best words. In this case I chose 150 estimators to go over the 8000 words. 

Model 3: Model 3 uses Count Vectorizer to turn the words into a matrix  and LemmaTokenizer to provide context to the parts-of-speech(POS). This done by giving the value to the POS parameter. In addition I used AdaboostClassifier with Decision Tree which builds a better model off the previous model. It does this until it can’t improve anymore.

Model 4: This model uses Count Vectorizer with LemmaTokenizer again but this time runs with MultinomialNB. Multinomial Naive Bayes works as a classifier for a discrete number of features in this case word counts with text classification.

The first show is American Dad.  r/americandad has over 48,000 subscribers to this subreddit and had a core cast of 6 characters that live in the fictional town of Langley Falls, VA a suburb of Washington, DC. My first observation when looking at the data from this subreddit was how many of the post were pictures or video clips from the show. Fans of the show really love reminiscing on their favorite parts of the show. Many of which are absolutely hilarious. 

The comparison show is Venture Brothers. r/venturebros has close to 32,000 subscribers and a core cast of 4. It’s never really revealed but I believe the show starts off with the Ventures and their bodyguard Brock Samson living in a compound somewhere in rural California. Looking at the data from Reddit there are plenty of post in the body that are pictures and video clips but this subreddit lends itself to more fan theory and lore than AD. 

To help you find which show might be the show for you let’s look to my model. When I put in the word “funny” the model returned AD. 

The following words were returned for American Dad:

- God
- Funny
- Dumb
- Midtown Manhattan
- Family Guy
- Alcoholic 
- Rap
- Song

The following words were returned for Venture Brothers:

- Awkward
- Smart
- Self-deprecating
- irreverent 
- Silly
- Sci-fi
- Creative
- Arnold and Danny Devito


Analysing the results, just because “funny” was predicted AD doesn’t not mean VB isn’t funny it just means that the model classified the word with AD. However, that fact that more specific words were predicted to each dataset is more indicative of the show. Sci-Fi is an theme of VB while alcoholism is more a theme of  AD, 

Additionally, I took passages new from r/amerciandad that are not in my scrap and put them in my findword function and it was able to accurately classify the words. In my notebook I attached 2 passages from each subreddit for you to try out yourself.



Model 1: Using Logistic Regression and TFIDVectorizer I was able to return these words and phrases back with 86% accuracy. This was my most accurate model.
Model 2: can predict Venture Bros vs American Dad with 85% accuracy. 
Model 3: can predict Venture Bros vs American Dad with 81% accuracy.
Model 4: can predict Venture Bros vs American Dad with 84% accuracy.

I hope these words and phrases help you find your new favorite show!
