# Executive Summary

Depression and Anxiety are mental illnesses that are increasing. They are different illnesses and have different hallmarks but may share common features. By learning to identify them quickly through text, it can help to tailor the treatment for the individual showing signs of Depression or Anxiety. Early intervention aids in management of the condition and can help to prevent tragedies.

Posts are took from Depression and Anxiety sub-reddits. These posts are used to infer that the individual could be displaying symptoms or signs of depression, likewise for Anxiety. Several models will be built and the accuracy will be used to evaluate the performance of the models. Accuracy is chosen as the main metric as it determines if the text came from Depression or Anxiety sub-reddit. The model with the highest accuracy score will be selected as the final model. The final model will be used to determine if the text is about depression or anxiety. 

Linear Regression model with CountVectorizer (lr_cvec) has been found to be the best model. If the text is about depression, lr_cvec can predict with 97.6% accuracy. Whereas, if the text is about anxiety, lr_cvec can predict with 93.1% accuracy.

With this model, it is hoped that it will help the mental health practioners which include counsellors and psychiatrists to have a quick overview if the individual is leaning towards depression or anxiety behaviour. This will increase the chances of timely intervention and may help reduce the workload of the practioners so that they can reach out to more patients. 

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
* Create function to clean text
* Function will remove the punctuations, new lines etc from the string and convert to lowercase. After that it will lemmentize the text.

# Modeling using Processed Text
* Several models will be built and evaluated to determine which model is the most suitable to tackle the issues mentioned in the problem statement.


* The main scoring metric which is accuracy will be used to evaluate the performance of the model. Accuracy is chosen as the main metric as it determines if the text came from Depression or Anxiety sub-reddit. Posts from Depression sub-reddit is used to infer that the individual is displaying symptoms or signs of depression, likewise for Anxiety. With reference to the problem statement, it will help target stakeholders, who are the mental health practioners which include counsellors and psychiatrists to have a quick overview if the individual is leaning towards depression or anxiety behaviour.


* If the model is performing well, where it has at least test score of 80% accuracy, it will be further evaluated with the confusion matrix.

# Multinomial NaiveBayes model with CountVectorizer (nb_cvec)
* For this model, the Multinomial NaiveBayes (nb) will be used to predict if the text came from a Depression or Anxiety sub-reddit. Accuracy is used as the main evaluation metric. The vectorizer used is the CountVectorizer (cvec).

* Multinomial NaiveBayes model is used because the target variable is to predict 2 outcomes; to predict if the post came from Depression or Anxiety sub-reddit. The features are the words and the probability of each word occuring in the text is evaluated to look at their importance in prediction. nb is used as the features' outcome is not binary but multinomially distributed.

## nb_cvec GridSearchCV score vs nb_cvec RandomizedSearchCV score
* GridSearchCV score is 0.8648987 while RandomizedSearchCV score is 0.8648802. The difference is lesser than 0.01. The run time for GridSearchCV is around 160 seconds (approximately 3 mins) and the runtime for Randomized is around 5 seconds. RandomizedSearchCV will be used so that more parameters can be searched quickly.

* RandomizedSearchCV is useful for searching through multiple parameters quickly. However, it may compensate accuracy for speed. Hence the score of GridSearchCV and RandomizedSearchCV is compared to see if the score of RandomizedSearchCV is comparable to GridSearchCV before deciding to use RandomizedSearchCV.

# Conclusion for nb_cvec
* The accuracy for nb_cvec is around 82%. The model seems to be performing well as it passed the benchmark score of 80% and the difference between baseline score and test score is 8%.


* Out of the top 50 words in Depression and Anxiety, there are 37 common words found to be shared between them.


* Out of the top 50 words in Depression and Anxiety, there are only 13 words unique to Depression and 13 words unique to Anxiety.


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
* The test accuracy score for nb_tvec is around 76%. It is lower than the expected score of 80% accuracy to evaluate the model further.

* There are 27 common words found in both Depression and Anxiety. There are 23 words unique to Depression and 23 words unique to Anxiety.
nb_cvec is performing better than nb_tvec.

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

* From the bar plots above, in these top 50 words, `depression`, `depressed` and `life` have the largest effect in lr. 

* As the model predicts on class: 1, which is Depression, these words predict for Depression. For example, for every 1 increase in mention of `depression` in the text, the odds of the text about depression increases by 1.77 times, if all other factors are kept constant. 


# Logistic Regression model with TF-IDF Vectorizer (lr_tvec)

* For this model, the Logistic Regression (lr) will be used to predict if the text came from a Depression or Anxiety sub-reddit. Accuracy is used as the main evaluation metric. The vectorizer used is the TF-IDF Vectorizer (tvec).


* Logistic Regression model is used because the target variable is to predict 2 outcomes; to predict if the post came from Depression or Anxiety sub-reddit. The features will be the words in the processed text. In lr, it is assumed that each independent variable 𝑋𝑖 is linearly related to the log of the odds of success. Here, each word is the independent variable 𝑋𝑖. The words are assumed to be independent of one another.


* Depression is assigned to be class 1 and Anxiety as class 0.


* As mentioned previously, by exponentiating the coefficient of the feature, it shows that if the word is found in the text and other factors remain constant, what are the odds that the text is from an individual having Depression or Anxiety symptoms.

# Conclusion for lr_tvec

* The baseline score is around 0.91 and the test score is around 0.79. The model seems to be performing slightly under the benchmark as it is below benchmark score of 80%. It is likely that the model is overfitted.


* Compared to lr_cvec, lr_cvec is perfoming better (test score of lr_cvec: 87% vs nb_tvec: 79%).


* The model will not be evaluated further due to likely overfitting.

# Summary table for nb_cvec, nb_tvec, lr_cvec, lr_tvec

**Model**: Type of estimator used.


**Vectorizer**: Type of vectorizer used, either CountVectorizer `(cvec)` or TF-IDF Vectorizer `(tvec)`.


**Baseline**: Accuracy score obtained by using trained model to predict on `train` data.


**Validate**: Accuracy score obtained by using trained model to predict on `validate` data.



|Model|Vectorizer|Baseline (%)|Validate (%)|
|---|---|---|---|
|NaiveBayes Multinomial|cvec|91|82|
|NaiveBayes Multinomial|tvec|87|76|
|Logistic Regression|cvec|95|87|
|Logistic Regression|tvec|91|79|

# Results

### Results for lr_cvec

<img width="635" alt="Confusion Matrix" src="https://user-images.githubusercontent.com/72869207/101298361-95729200-3868-11eb-8d22-464f3d172be7.PNG">

* Depression = 1
* Anxiety = 0

- In the validation dataset, there were 154 posts from Depression sub-reddit and 147 posts from Anxiety sub-reddit. 51% of the posts are from Depression and 49% are from Anxiety.


- Out of the 154 Depression posts, 142 are correctly predicted. 12 posts are incorrectly predicted as Anxiety posts.
- Out of the 147 Anxiety posts, 120 are correctly predicted. 27 posts are incorrectly predicted as Depression posts.


- **The test score for Accuracy for the model is 87.0%.**

- **The test score for Specificity to predict Anxiety posts is 93.1%.**

- **The test score for Sensitivity to predict Depression posts is 97.6%.**

# Recommendations and Conclusion

**Recommendations**


From the models built, lr_cvec has the highest accuracy. It can be utilized to identify posts from individuals showing signs or symptoms of depression or anxiety. If the text is about depression, lr_cvec can predict with 97.6% accuracy. Whereas, if the text is about anxiety, lr_cvec can predict with 93.1% accuracy. The notable words that have a great effect in classifying the text as depression are `depression` and `depressed`, which is quite obvious. As mentioned previously, using `depression` as the example, for every 1 increase in mention of `depression` in the text, the odds of the text about depression increases by 1.77 times, if all other factors are kept constant. Other prominent words are `life`, `happy`, `kill`, `suicide`, `sad` and `suicidal`. For `life` and `happy`, if the individual mentions them a lot in their posts, it may mean that they are not happy and are thinking about their lives frequently. Some interesting words like `mom`,`friends`,`family`, `tired`, `hate` can help to classify the post.


**Conclusion**


Stakeholders may wish to use the model to see if it can help identify symptoms of depression or anxiety from depression or anxiety sub-reddit posts. By extrapolating to their current patients, it may help to identify if their patients are leaning towards depression or anxiety.