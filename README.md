# Machine-Learning

The main objective of this project was to predict the number of shares in social networks (popularity). To prepare the data for training I have performed these steps: (note: each of the below mentioned phase is explained in detail in each snippet precisely).

•	First phase: -
  <h2> <b> Data Cleaning </b> </h2>
  
Firstly, I tried to load the dataset where I had to deal with some noise because the dataset could not be loaded perfectly with the first try as it contained an extra column. After fixing this issue, I perfeclty loaded the dataset. I noticed that the dataset contained several types of noises like null, 'nan' and NAN values which I surely removed all of them. I also dropped every null value in those rows of the dataset which had at least one missing value. The other type of problem that i dealt with was interesting as different features had Object data types, other had String type instead of integers, and nan values. Since, a machine learning algorithm cannot understand the Object data types, I converted the type of the numerical features into integers. After making sure that this conversion went well I proceeded next with the separation of the features into specific groups: numerical features (discrete and continuous) and categorical features. I computed the total number of each group of the features and the length of each one of them to have a better overview of them. I also dropped the unimportant features such as ‘url’ as it did not give any important information for our target.

•	Second phase: Data Preprocessing
The next step I followed: is the split of the data into training and testing. I decided to put the test set size 20% and the train set 80%. To keep all the values of the train and test set in the same range, I performed feature scaling. Then, I converted the target values from continuous feature to discrete feature by using the KBinsDiscretizer library with 5 classes (from 0 to 4) using the strategy ‘quantile’ in order to have the data balanced. Also, I printed the most important features in the dataset by using the RandomForestClassifier algorithm. Based on the impurity, it calculates the score for each feature. The results i got were as follows: num_videos = 0.311882, num_imgs = 0.311546, weekday_is_sunday = 0.286785. So, here I got a better overview of the features(the first three in this case) by plotting a figure and also by printing each one of their values that give a valuable information about our prediction. When I had a look in the article, I observed that 'timedelta' feature might be missleading to our target'. Hence, it gave a bad performance on our model and I decided to remove it. In order to try to deal with the categorical features issue, I tried to use PCA but the results were not good enough.

•	Third phase: Model Selection
In model selection phase, I performed hyperparameter tuning using RandomizedSearchCV to choose the best parameters and the best scores for all our learning algorithms.I performed cross validation in all the models with k-fold default which is 5. In the end, I did the comparison between the models I trained and I selected the best one which is SVC. I chose this model, because its accuracy was the highest among others and with the smallest variance.

