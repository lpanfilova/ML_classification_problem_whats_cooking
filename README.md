# ML classification problem. What's cooking

This is a competition from Kaggle.com where teams are asked to try to predict the cuisine given a list of ingredients. We have 39773 recipes in json files which we will try to analyse and find patterns. Later we will use these patterns to predict a cuisine type for a new recipe.

### Below are a few examples of recipes:

![image](https://user-images.githubusercontent.com/78988408/134081910-b7a9f353-d149-45d6-a594-6e65140c7acb.png)

### Data Cleaning
Original train dataset showed high variability of the ingredient records. Same or similar ingredients could have been written in multiple ways. To reduce the dimensionality of the dataset and improve the modelling the following data preprocessing steps were taken: removal of special characters, numbers and capital letters, removal of stop words, and stemming.

### Exploratory Data Analysis

![image](https://user-images.githubusercontent.com/78988408/134082044-0b9292ed-2a07-4bbc-ab28-e9cb508f86f9.png)
From the above visualization we can determine that the data is imbalanced, as some cuisines like Italian and Mexican are over-represented, while others Jamaican, Russian and Brazilian are minority classes.

![image](https://user-images.githubusercontent.com/78988408/134082133-24249650-c022-4023-9314-9a2c7237f0ca.png)

![image](https://user-images.githubusercontent.com/78988408/134082166-d139c7da-606f-4d83-a66e-8abb1f88b140.png)


### Creating a logistic regression model to predict cuisine for a new recipe

We are going to apply a statistical model to check whether it is possible to predict the cuisine based on ingredient list. First, we split our data into training and validation parts. Training part is used by our model to find patterns and validation part - to test whether we predict accurately enough. After that, we clean our data from numbers, special characters and non-ingredient words etc. Once we applied our model we get the accuracy result of 0.78. This means that 78% of cuisines were preducted correctly.

#### Logistic Regression
We have a multiclass classification problem of predicting one of 20 cuisines by the recipe. The logistic regression analysis is used for classification problems with binary dependent variables. Therefore, we converted the original problem of predicting cuisine for a recipe into a problem of predicting likelihood of the recipe belonging to each of the 20 cuisines in the dataset with the highest likelihood cuisine being the final answer.

#### Encoding
Cuisines and recipes had to be encoded because all the algorithms which we can potentially leverage can only consume numerical data. Cuisines were encoded in the simplest way, i.e. as integers. Recipes were encoded using one-hot encoding where each recipe is represented by a vector of zeros and ones. Each zero or one stands for whether an ingredient was or was not used in the recipe.

### Accuracy
#### The overall accuracy of our model is 77%, which appears to be a good result given that we have 20 cuisines.

#### Confusion Matrix
The confusion matrix represents how cuisines were predicted by our model. On the vertical axis there are actual cuisines (labels), while on a horizontal axis there are predicted cuisines. So, for example for Brazilian cuisine, 72 recipes were predicted correctly, 12 were falsely predicted as Mexican, 5 as Indian, and 4 as Italian.

![image](https://user-images.githubusercontent.com/78988408/134082468-55e45484-8e61-4ba9-8cda-bb7da62d0a0d.png)

#### Classification report
This classification report shows the precision (percentage of true positives within all predicted positives), recall (percentage of correctly predicted true positives) and f1-score (a weighted average of precision and recall). The overall accuracy of our model is 79%, which appears to be a good result given that we have 20 cuisines. A random guessing would only have 5% accuracy. We can observe the highest precision and recall for Indian, Italian and Mexican cuisines, probably because of the large amount of training data and the ratio of unique ingredients defining it.
![image](https://user-images.githubusercontent.com/78988408/134082534-4e16be1b-f7cf-4b0d-8ebd-4b62c7738a8b.png)

#### Conclusion
In conclusion we were successfully able to create a model with approximately 77% accuracy of determining a type of cuisine based on ingredients. There are several ingredients such as Kimchi, turmeric and snails that are unique to a specific cuisine, which aids the model. Based on the values of precision and accuracy that the model appears to be good enough. However, as identified previously there are many cuisines with similar ingredients in result there was significant false prediction. Therefore, with more data it is possible to reduce error and create clusters of a combination of ingredients and quantities, specific to types of cuisines. This model is a suitable steppingstone in predicting types of cuisines of a recipe using ingredients, with enough accuracy. With additional recipes the model will only improve and yield the intended results.
