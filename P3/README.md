# Executive Summary

Depression and Anxiety are mental illnesses that are increasing. They are different illnesses and have different hallmarks but may share common features. By learning to identify them quickly through text, it can help to tailor the treatment for the individual showing signs of Depression or Anxiety. Early intervention aids in management of the condition and can help to prevent tragedies.

Posts are took from Depression and Anxiety sub-reddits. These posts are used to infer that the individual could be displaying symptoms or signs of depression, likewise for Anxiety. Several models will be built and the accuracy will be used to evaluate the performance of the models. Accuracy is chosen as the main metric as it determines if the text came from Depression or Anxiety sub-reddit. The model with the highest accuracy score will be selected as the final model. The final model will be used to determine if the text is about depression or anxiety.

Naive Bayes model with CountVectorizer (nb_cvec) has been found to be the best model. If the text is about depression, nb_cvec can predict with 88.3% accuracy. Whereas, if the text is about anxiety, nb_cvec can predict with 62.3% accuracy.

With this model, it is hoped that it will help the mental health practioners which include counsellors and psychiatrists to have a quick overview if the individual is leaning towards depression behaviour. This will increase the chances of timely intervention and may help reduce the workload of the practioners so that they can reach out to more patients.

# Table of Contents:
- [Problem Statement](#Problem-Statement)
- [Webscrapping sub-Reddit Anxiety using API](#Webscrapping-sub-reddit-Anxiety-using-API)
- [Webscrapping sub-Reddit Depression using API](#Webscrapping-sub-reddit-Depression-using-API)
- [Exploratory Data Analysis](#Exploratory-Data-Analysis-and-Data-Cleaning)
- [Pre-Processing for text data](#Pre-Processing-for-text-data)
- [Modeling Process](#Modeling-using-Processed-Text)
- [Modeling with Multinomial NaiveBayes model (nb) with CountVectorizer (cvec); (nb_cvec)](#Multinomial-NaiveBayes-model-with-CountVectorizer-(nb_cvec))
- [Conclusion for nb_cvec](#Conclusion-for-nb_cvec)
- [Increase stop words](#Increase-stop-words-list-to-remove-more-stop-words-to-try-reduce-overfitting-and-increase-accuracy)
- [Conclusion for nb_cvec re-model with increased stop words](#Conclusion-for-nb_cvec-re-modelled-with-clean_text_2)
- [Summary of Comparison](#Summary-of-Comparison)
- [Modeling with Multinomial NaiveBayes model (nb) with TF-IDF Vectorizer (tvec); (nb_tvec)](#Multinomial-NaiveBayes-model-with-TF-IDF-Vectorizer-(nb_tvec))
- [Conclusion for nb_tvec](#Conclusion-for-nb_tvec)
- [Modeling with Logistic Regression model (lr) with CountVectorizer (cvec); (lr_cvec)](#Logistic-Regression-model-with-CountVectorizer-(lr_cvec))
- [Conclusion for lr_cvec](#Conclusion-for-lr_cvec)
- [Modeling with Logistic Regression model (lr) with TF-IDF Vectorizer (tvec); (lr_tvec)](#Logistic-Regression-model-with-TF-IDF-Vectorizer-(lr_tvec))
- [Conclusion for lr_tvec](#Conclusion-for-lr_tvec)
- [Summary table for nb_cvec, nb_tvec, lr_cvec, lr_tvec](#Summary-table-for-nb_cvec,-nb_tvec,-lr_cvec,-lr_tvec)
- [Results](#Results)
- [Recommendations and Conclusion](#Recommendations-and-Conclusion)

# Problem Statement

I will be building models (naive bayes and logistic regression) which will be classifying and identifying if the text came from either the Anxiety or Depression sub-reddit. The success of the model will be evaluated on the accuracy, sensitivity and specificity. The test accuracy score for model should be at least 80%. For the sensitivity, it is used to determine how well the model can predict if the text came from Depression sub-reddit. For the specificity, it is used to determine how well the model can predict if the text came from Anxiety sub-reddit. Following that, I will look at the top 50 words that is most commonly used in the Depression sub-reddit and Anxiety sub-reddit. From the unique words for Depression and Anxiety, they help to tell us the different features between Anxiety and Depression.


With this information, I hope it will help my target stakeholders, who are the mental health practioners which include counsellors and psychiatrists to have a quick overview if the individual is displaying signs or symptoms of Depression, Anxiety or both. It is hoped that the model can help to give some clues on the pyschological state of these individuals, how the words they used in their posts show if they are leaning towards depressed or anxiety behaviour.

# Webscrapping sub-reddit Anxiety using API
* A loop is built using requests module and the randomized timer to scrape data from Anxiety sub-reddit sequentially using the reddit API.
* The randomized timer is built in the loop to ensure that the server is not overloaded with requests and data is scrapped sequentially with pauses.
* The codes for webscrapping Anxiety sub-reddit is put into the `P3 webscrapping codes`.

# Webscrapping sub-reddit Depression using API
* A loop is built using requests module and the randomized timer to scrape data from Depression sub-reddit sequentially using the reddit API.
* The randomized timer is built in the loop to ensure that the server is not overloaded with requests and data is scrapped sequentially with pauses.
* The codes for webscrapping Depression sub-reddit is put into the P3 webscrapping codes.

# Exploratory Data Analysis and Data Cleaning
* For Depression sub-reddit, there are 11 null values in the 'selftext'. There are no duplicates.
* For Anxiety sub-reddit, there are 21 null values in the 'selftext'. There are 20 duplicates in the dataframe.
* Null values in 'selftext' will be dropped and duplicates will be removed.

# Pre-Processing for text data
* Create function to clean text. Function will remove the punctuations, new lines etc from the string and convert to lowercase. After that it will lemmentize the text.


* Words that vividly describe depression and anxiety will be added to the stop words to see if the model can predict well on other indicative words:

* Words are: depress, depressed, depression, depressing, depressant, anxiety, anxious, anxiously

# Modeling using Processed Text
* Several models will be built and evaluated to determine which model is the most suitable to tackle the issues mentioned in the problem statement.


* The main scoring metric which is accuracy will be used to evaluate the performance of the model. Accuracy is chosen as the main metric as it determines if the text came from Depression or Anxiety sub-reddit. Posts from Depression sub-reddit is used to infer that the individual is displaying symptoms or signs of depression, likewise for Anxiety. With reference to the problem statement, it will help target stakeholders, who are the mental health practioners which include counsellors and psychiatrists to have a quick overview if the individual is leaning towards depression or anxiety behaviour.


* If the model is performing well, where it has at least test score of 80% accuracy, it will be further evaluated with the confusion matrix.

# Multinomial NaiveBayes model with CountVectorizer (nb_cvec)
* For this model, the Multinomial NaiveBayes (nb) will be used to predict if the text came from a Depression or Anxiety sub-reddit. Accuracy is used as the main evaluation metric. The vectorizer used is the CountVectorizer (cvec).

* Multinomial NaiveBayes model is used because the target variable is to predict 2 outcomes; to predict if the post came from Depression or Anxiety sub-reddit. The features are the words and the probability of each word occuring in the text is evaluated to look at their importance in prediction. nb is used as the features' outcome is not binary but multinomially distributed.

## nb_cvec GridSearchCV score vs nb_cvec RandomizedSearchCV score
* GridSearchCV score is 0.8073173 while RandomizedSearchCV score is 0.8051135. The difference is around than 0.02. The run time for GridSearchCV is around 154 seconds (approximately 3 mins) and the runtime for Randomized is around 5 seconds. RandomizedSearchCV will be used so that more parameters can be searched quickly.


* RandomizedSearchCV is useful for searching through multiple parameters quickly. However, it may compensate accuracy for speed. Hence the score of GridSearchCV and RandomizedSearchCV is compared to see if the score of RandomizedSearchCV is comparable to GridSearchCV before deciding to use RandomizedSearchCV.

# Conclusion for nb_cvec
* The training score is around 0.88 and the test score is around 0.76. The model seems to be performing slightly under the benchmark as it is below benchmark score of 80%. The difference between training score and test score is 12%. It is likely that the model is overfitted. It may be due to too many features, which are the words, and too little posts to train the model.


* Out of the top 50 words in Depression and Anxiety, there are 38 common words found to be shared between them. 
* Out of the top 50 words in Depression and Anxiety, there are only 12 words unique to Depression and 12 words unique to Anxiety. 


* There is a possibility that the machine could not learn to differentiate effectively due to limited number of unique words that define Depression and Anxiety. 

# Increase stop words list to remove more stop words to try reduce overfitting and increase accuracy
* After looking at the common words shared between Depression and Anxiety, I will put in words that I think will not help in explaining Depression or Anxiety into the stop words list to see if it reduces the overfitting and increase the accuracy score.

* Re-model with nb_cvec using increased stop words.

## Summary of Comparison
* The list of 50 words in Depression and Anxiety changed by a small margin when additional stop words are added to clean the texts.

* It seems by altering the list of stop words, it will yield different results for the top 50 words in Depression or Anxiety but in this case the change is minimal.

* I will use the data which has the texts cleaned with additional stop words by the function clean_tokenize_lemma to build more models.

# Multinomial NaiveBayes model with TF-IDF Vectorizer (nb_tvec)
* For this model, the Multinomial NaiveBayes (nb) will be used to predict if the text came from a Depression or Anxiety sub-reddit. Accuracy is used as the main evaluation metric. The vectorizer used is the Term Frequency-Inverse Document Frequency (TF-IDF) Vectorizer (tvec).

* Similar to previous model, the nb-cvec, Multinomial NaiveBayes is used in this model, as the nature of the target variable and features is the same as described in nb_cvec.

* TF-IDF is a score that tells us which words are important to one document, relative to all other documents. It is deemed that words that occur often in one document but do not occur in many documents contain more predictive power.

# Conclusion for nb_tvec

* The test accuracy score for nb_tvec is around 71%. It is lower than the expected score of 80% accuracy to evaluate the model further. There are 27 common words found in both Depression and Anxiety. There are 23 words unique to Depression and 23 words unique to Anxiety.


* nb_cvec is performing better than nb_tvec.

# Logistic Regression model with CountVectorizer (lr_cvec)
* For this model, the Logistic Regression (lr) will be used to predict if the text came from a Depression or Anxiety sub-reddit. Accuracy is used as the main evaluation metric. The vectorizer used is the CountVectorizer (cvec).


* Logistic Regression model is used because the target variable is to predict 2 outcomes; to predict if the post came from Depression or Anxiety sub-reddit. The features will be the words in the processed text. In lr, it is assumed that each independent variable  𝑋𝑖  is linearly related to the log of the odds of success. Here, each word is the independent variable 𝑋𝑖. The words are assumed to be independent of one another.


* Depression is assigned to be class 1 and Anxiety as class 0.


* Below is the general lr equation which define the relationship between features and outcomes. In this case, by exponentiating the coefficient of the feature, it shows that if the word is found in the text and other factors remain constant, what are the odds that the text is from an individual having Depression or Anxiety symptoms.  

Where:

- $X_i$ is the word as a feature

- $\beta_i$ is the coefficient of each feature


$$
\begin{eqnarray*}
\log\bigg(\frac{P(Depression=1)}{1-P(Depression=1)}\bigg) &=& \beta_0 + \beta_1X_1 + \beta_2X_2 + \cdots + \beta_pX_p \\
\Rightarrow e^{\Bigg(\log\bigg(\frac{P(Depression=1)}{1-P(Depression=1)}\bigg)\Bigg)} &=& e^{\Bigg(\beta_0 + \beta_1X_1 + \beta_2X_2 + \cdots + \beta_pX_p\Bigg)} \\
\Rightarrow \frac{P(Depression=1)}{1-P(Depression=1)} &=& e^{\Bigg(\beta_0 + \beta_1X_1 + \beta_2X_2 + \cdots + \beta_pX_p\Bigg)} \\
\end{eqnarray*}
$$

Hence, the appearance of the word $X_i$, means the text is $e^{\beta_i}$ times as likely to be from Depression, as the model predicts on class 1.


# Conclusion for lr_cvec

* From the bar plots above, in these top 50 words, `life`, `happy` and `sad` have the largest effect in lr. 

* As the model predicts on class: 1, which is Depression, these words predict for Depression. For example, for every 1 increase in mention of `life` in the text, the odds of the text about depression increases by 1.41 times, if all other factors are kept constant. 

* It is noted that the words need to be put into context, otherwise it is difficult to determine what kind of meaning the words give. 


# Logistic Regression model with TF-IDF Vectorizer (lr_tvec)

* For this model, the Logistic Regression (lr) will be used to predict if the text came from a Depression or Anxiety sub-reddit. Accuracy is used as the main evaluation metric. The vectorizer used is the TF-IDF Vectorizer (tvec).


* Logistic Regression model is used because the target variable is to predict 2 outcomes; to predict if the post came from Depression or Anxiety sub-reddit. The features will be the words in the processed text. In lr, it is assumed that each independent variable 𝑋𝑖 is linearly related to the log of the odds of success. Here, each word is the independent variable 𝑋𝑖. The words are assumed to be independent of one another.


* Depression is assigned to be class 1 and Anxiety as class 0.


* As mentioned previously, by exponentiating the coefficient of the feature, it shows that if the word is found in the text and other factors remain constant, what are the odds that the text is from an individual having Depression or Anxiety symptoms.

# Conclusion for lr_tvec

* The training score is around 0.89 and the test score is around 0.75. The model seems to be performing slightly under the benchmark as it is below benchmark score of 80%. The difference between the train and test score is around 14%. It is likely that the model is overfitted.


* Compared to lr_cvec, lr_cvec and lr_tvec have similar performance (test score of lr_cvec: 75% vs nb_tvec: 75%).


* The model will not be evaluated further due to likely overfitting.

# Summary table for nb_cvec, nb_tvec, lr_cvec, lr_tvec

**Model**: Type of estimator used.


**Vectorizer**: Type of vectorizer used, either CountVectorizer `(cvec)` or TF-IDF Vectorizer `(tvec)`.


**Training**: Accuracy score obtained by using trained model to predict on `train` data.


**Validate**: Accuracy score obtained by using trained model to predict on `validate` data.

**Difference**: Difference in the train score and test score, obtained by (train score - test score).



|Model|Vectorizer|Training (%)|Validate (%)|Difference (%)|
|---|---|---|---|---|
|NaiveBayes Multinomial|cvec|88|76|12|
|NaiveBayes Multinomial|tvec|83|71|12|
|Logistic Regression|cvec|92|75|17|
|Logistic Regression|tvec|89|75|14|


# Results

### Results for nb_cvec

<img width="564" alt="Confusion Matrix" src="https://user-images.githubusercontent.com/72869207/101344882-2e34fc00-38c1-11eb-8951-36020cc7ec3f.PNG">

* Depression = 1
* Anxiety = 0

- In the validation dataset, there were 154 posts from Depression sub-reddit and 147 posts from Anxiety sub-reddit. 51% of the posts are from Depression and 49% are from Anxiety.


- Out of the 154 Depression posts, 125 are correctly predicted. 29 posts are incorrectly predicted as Anxiety posts.
- Out of the 147 Anxiety posts, 102 are correctly predicted. 45 posts are incorrectly predicted as Depression posts.


- **The test score for Accuracy for the model is 76.5%.**

- **The test score for Specificity to predict Anxiety posts is 62.3%.**

- **The test score for Sensitivity to predict Depression posts is 88.3%.**


# Recommendations and Conclusion

**Recommendations**


From the models built, nb_cvec has the highest accuracy. It can be utilized to identify posts from individuals showing signs or symptoms of depression or anxiety. If the text is about depression, nb_cvec can predict with 88.3% accuracy. Whereas, if the text is about anxiety, nb_cvec can predict with 62.3% accuracy. The common words that have high probability of appearing shared between Depression and Anxiety are `like`,`feel`,`make`,`time`,`want` which give clues how depressed or anxious individual express themselves. 

For Depression, some unique words are `someone`, `family`, `friends`, `anymore`, `care`. For Anxiety, some unique words are `month`,`come`,`week`,`happen`,`attack`. Here, it seems that depressed individuals seem to desire for more care and concern while anixety individials are more concerned on the panic bouts.

As the model is able to predict for depression in a text with 88.3% accuracy, the target takeholders, who are the mental health practitioners can try the model to see if it helps them to select for individuals leaning towards depression.


**Conclusion**


For this model nb_cvec, the training score is around 0.88 and the test score is around 0.76. The model is performing slightly under the benchmark score of 80%. The difference between training score and test score is 12%. It is likely that the model is overfitted. This could be due to using too many features, which are the words, with too little posts to train the model.
  
Out of the top 50 words in Depression and Anxiety, there are 38 common words found to be shared between them. 
Out of the top 50 words in Depression and Anxiety, there are only 12 words unique to Depression and 12 words unique to   
Anxiety. It seems that there may be shared features between Depression and Anxiety.

There is a possibility that the machine could not learn to differentiate effectively due to limited number of unique words that define Depression and Anxiety and too many common words. To improve the accuracy of the model, more posts can be collected from the sub-reddits to reduce overfitting in the model. Another factor to look at is to increase the number of stop words so that the machine can learn words specific to depression and anxiety. For this, it will be helpful to enlist the help of the mental health practioners to come up with the list of words as domain expertise is important to help select for words. Boosting may also be attempted to see if it helps the machine to tune the model further.