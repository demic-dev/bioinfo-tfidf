Surname: **De Cillis**
Name: **Michele**

Mail address: [michele.de-cillis@universite-paris-saclay.fr](mail-to:michele.de-cillis@universite-paris-saclay.fr)

Student Number: **22311787**

[GitHub repo.](https://github.com/demic-dev/bioinfo-tfidf)

# TF-IDF

During the class, we've learnt the TF-IDF notation, which represents the importance of a word in a collection of documents. It's really useful because, given a corpus, we can classify the documents inside or understand the key-words and the topics about them.

In this homework I'm going to analyze a small (around ~1000) dataset which contains abstracts of medical paper about COVID-19 [source](https://www.kaggle.com/datasets/allen-institute-for-ai/CORD-19-research-challenge). First, I've reduced the dataset from two millions to six hundered (reduced of the 99,97%) and then I loaded it into my notebook.

Once I loaded it, I started to setup my environnment by loading all the libraries and by coding a preprocess function, where I give my abstract and it starts to tokenize first and then lemmatize the retrieved tokens.

Then, I called the function `TfidfVectorizer` of `scikit-learn` and I printed the results with `panda`.

I've tried to use the function multiple times, with a different size of dataset. First with only **1** document, then with **10** documents and in the end with **50** documents. Here's my results:

## 1 document

By passing only one document, we can see how all the tokens have a percentage bigger than 0 and the words with a bigger frequency (such as the stop words) has an increased percentage.

This is expected, because in the end, since there is only one document, the _idf_ is going to be useless and it will represent only the term frequency.

## 10 documents

Now, we're starting to see a lot more zeros for each term. Plus, the overall percentages are lower, because we're giving more documents. We can see for each documents, beyond the stop words, that the higher percentages are for the keywords.

## 50 documents

With 50 documents, the results are similiar. Of course, on some items where in the previous case there was a percentage, in this case the percentage is different because the number of documents is higher and a word can appear in other documents.

Still, there is a problem that partially invalidates the results just discovered. The stop words appear too often and infect the results just found.

So, during the word preprocessing I added an `if` which removes the stop words, if found.

Now, in each case there will be less columns because the common english terms are removed and now there are tokens only relative to the content of the abstract.
