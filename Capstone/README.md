# Classifying Eczema from non-Eczema Images using CNN model


## Problem Statement


Atopic dermatitis (AD), also called atopic eczema, is a common chronic or recurrent inflammatory skin disease and affects 15-20% of children and 1-3% of adults worldwide. It is characterized by acute flare-ups of eczematous pruritic lesions over dry skin.
https://www.karger.com/Article/FullText/370220#:~:text=Introduction,pruritic%20lesions%20over%20dry%20skin.

Eczema can affect an individual's quality of life. It increases the chances of it being more manageable when appropriate interventions and treatments are made when diagnosed early. However, eczema symptoms can be similar to other rashes and itch. By creating a classification model to classify for eczema and sort out from other skin diseases, it will help individuals to self-diagnose and sort appropriate timely medical treatment. 

## Abstract

Skin images are downloaded from a Kaggle dataset (link at end of abstract). Images are manually sorted out to create several datasets:

a) dataset consisting of eczema and non-eczema images of feet (378 images)

b) dataset consisting of eczema images of feet (120 images)

c) 1st dataset consisting of eczema and non-eczema images from various parts of the body (3127 images)

d) 2nd dataset consisting of eczema and non-eczema images from various parts of the body (774 images)

**Non-eczema images for a) are images of feet with tinea (fungal infection).**
**Non-eczema images for c) and d) are images of feet with from other skin diseases such as pityriasis (skin rash) and psoriasis.

For a), it is split into training and validation data. b) is not splitted. For c), it is split into training and validation data. d) is not splitted. The training data is used to train the model and validation data is used to validate the model. 

A standard Convolutional Neural Network (CNN) is built from scratch is trained with a) to classify eczema and non-eczema images of feet. The validation accuracy score is around 75%. b) is used as a test dataset to evaluate if the CNN trained on feet images is able to classify eczema and non-eczema images from other body parts. The CNN is unable to classify eczema and non-eczema images from other body parts when trained on feet images only; the accuracy score is around 55%.

Next, a CNN is built from scratch is trained with c) to classify eczema and non-eczema images from various parts of the body. d) is used as the test data to evaluate the performance of the model. The CNN is not performing well; the accuracy score is around 59%. 

After that, the MobileNet V2 is incorperated into the CNN as a base model to try improve the accuracy. d) is used as the test dataset to obtain the test accuracy score. CNN without fine tuning of base model achieved test accuracy of 68%. CNN with top 25 layers of the base model fine tuned achieved 73% test score and CNN with top 55 layers fine tuned achieved 77% test score. There is an incremental increase from 73% to 77% when the number of top layers in the base model to fine tune is increased. 

The model has a modest accuracy 77% to classify eczema from noneczema images rom various parts of the body. Future work can be done to fine tune the model and deploy it.

## Dataset

Images are sourced and downloaded from kaggle

https://www.kaggle.com/shubhamgoel27/dermnet


## Summary of results of CNN models built

|Model|Number of Images used to train|Number of Images used to validate|Number of Images used to test|Train Accuracy|Validation Accuracy|Test Accuracy|
|---|---|---|---|---|---|---|
|Only feet, no pre-processing, no dropout|303|75|from unseen_data, 120|1.000|0.7467|0.5417|
|Only feet, with pre-processing, with dropout|303|75|from unseen_data, 120|0.7558|0.7733|0.5500|
|Various bodyparts, with pre-processing, no dropout|2502|625|from test_ds, 774|0.6059|0.5920|0.5943|
|Various bodyparts, with pre-processing, with MobileNet V2, with dropout|2502|625|from test_ds, 774|0.6807|0.6336|0.6882|
|Various bodyparts, with pre-processing, with MobileNet V2, with dropout, 25 top layers fine tuned|2502|625|from test_ds, 774|0.8125|0.7216|0.7313|
|Various bodyparts, with pre-processing, with MobileNet V2, with dropout, 55 top layers fine tuned|2502|625|from test_ds, 774|0.8745|0.7424|0.7778|

## Conclusion

- Through the approaches and workflow here, I was able to create a cnn model utilizing the MobileNetV2 as a base model to classify eczema and non-eczema images from various body parts with a modest accuracy of around 77%.
- If there are more images to train and validate the data in the cnn, it may have helped to improve the accuracy of the model.
- Future work can be done by introducing more classes into the project so that the model can classify for multiple skin diseases. After that, the model can be attempted to deploy on smartphones, as MobileNet is a deep learning model that is developed for efficiency and can  be implemented on embedded devices or mobile devices such as smartphones without compromising with resources.

https://www.researchgate.net/publication/343364827_Android_skin_cancer_detection_and_classification_based_on_MobileNet_v2_model