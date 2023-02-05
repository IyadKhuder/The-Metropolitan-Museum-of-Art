# The-Metropolitan-Museum-of-Art
Trying to explore the data, infer some interesting insights.
Trying to explore the data, infer some interesting insights, explore the prominent data patterns and present them in an appropriate manner. Particularly of interest are original approaches showing your machine learning expertise. You may opt for methods from natural language understanding, recommender systems, image processing, forecasting, outlier detection, network analysis, you name it.

Based on the above surveillance, I've come up with the following reasoning:

Discussion of the dataset and the plan of attack
Challenges:

The dataset is full of NaN cells
The dataset is full of NaN cells
Very unbalanced
Text data: There is no "sentiment" features in the dataset, such as: Good or bad, expensive or cheap, valuable or not, ...etc. Plus, a majority of the items lack for descriptive text, which could be used to infer such information. Thus, it is very unclear how to perform any NLP Sentimental Analysis or Recommender Model on this dataset, if any.

Therefore

I will work on image classification. Here, there are further obstacles, in addition to the 2 ones mentioned above:

The main challenge is to withdraw the images from the website, for the following reason: The dataset does not provide a direct link to the image (the image URL). It rather includes a field named "Link_Resource", which leads to a "profile page" of the relevant record. The latter page might or might not contain an image, and if it does, it might contain one or more images, which might or might not have the same fileName. In other words:
Not all records have pictures
Those who have pictures, might not have 0.jpg, but instead have other numbers in their names, such as: 1.jpg, 2.jpg, 10.jpg ...etc.
Tips

I will take advantage of the abundance of records in the dataset (almost half a million items) and filter out all records without pictures and also those records with 0.jpg picture, so I don't bother using wildcards and regex to read the name of the available picture.

I noticed that the available images are stored in subfolders, whose names match the Object_ID of the relevant records. I'll use that to link the images to their records in the dataset.

Plan of attack

Withdraw the images using webscraping, which is alone an independent task.
Take a subset of the dataset, by taking just the 2 fields: Object_ID and Classification (renaming it as "label", to comply with the ML terminology)
Add a field named "imgPath", which is the actual path to the relevant image.
Filter out all records without pictures and also those records with 0.jpg picture.
Check the count of remaining items, grouped by their classes (labels), in the newly-formed dataset
Select 5 labels, which have at least 200 items and seem to be easily differentiated from each other. For example: I won't select the label "painting", because we may have anything, any object (a coin, a sculpture or a human face), illustrated in the painting, and therefore it will be too hard for the classifier to differentiate an image labeled "painting" from an image labled coin, a sculpture or a human face!
Preprocess the filtered dataset.
