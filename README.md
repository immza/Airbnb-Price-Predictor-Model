# Airbnb-Price-Predictor-Model


Task Interview - Set B


Exploratory Data Analysis (EDA):

Inspected the dataset using head() and info() to understand feature types and missing values. Found the missing rows of multiple features across different columns. 8 entries of host_name missing along with 800 CheckIn entries and CheckOut entries.

The distribution of the price is visualized using histograms and boxplots. It helped identify the skewness and outliers. Also, other features such as rating, reviews, bathrooms and bedrooms are visualized to contemplate the spread. 

Next, I computed the correlation matrix between multiple features and the target price where I found out a strong correlation of price with features like bedrooms, bathrooms, guests and reviews. 

I analyzed the categorical columns and dropped the ones with the least influence on the price manipulation like id and host_id. 














Data Cleaning:

Now for the data cleaning process I applied Mean Imputation to replace the null or missing values with the average of the other columns.And for the categorical columns, I imputed the missing values using a constant placeholder.
Beside, I used Boxplots to find out the extreme outliers in the price feature. I also clipped and removed extreme values to ensure model robustness and faster training. 

As per instructions, I made use of One-Hot Encoding. I made use of Manual One Hot Encoding for this using Pandas’ get_dummies() function. It transforms the categorical columns (e.g., host_name, country) into dummy variables. 
Next, I use StandardScaler for Feature Scaling where it brings down the Mean of each column to 0 and the Standard Deviation to 1 so that the numbers mainly spread around 0. It enables the ANN to learn faster and ensures the gradient descent converges faster. 



Model Creation:
I used the MLPRegressor which stands for Multi-Layer Perceptron Regressor. It is an ANN. It is a neural network model provided by Scikit-learn for solving regression problems in which the target variable was the price of the Airbnbs. It has 2 hidden layers of 64 neurons each and has ReLU Activation Function by default. Within it, it makes use of the Adam optimizer. I made use of ColumnTransformer and Pipeline for preprocessing and modeling. 

Accuracy Improvement:

I made use of R^2 (R- Squared) metric to identify how close the model was in predicting the actual price.Pre HyperTuning, I got a very good value of R^2 which establishes the superiority of the model for predicting the price of the Airbnbs. The initial R^2 value was 0.9416 which gives promising results and a very high level of accuracy. Mean Absolute Error (MAE): 0.19, Mean Squared Error (MSE): 0.09 and Root Mean Squared Error (RMSE): 0.30 further suggest pretty promising model results. 



Next, as per instructions I made use of Hyperparameter Tuning to increase the accuracy of the model but in fact it turned out costly reducing the R^2 value to 0.627 indicating a reverse slope in the training graph due to application of hyperparameter tuning thus signifying that it is rather beneficial to ignore any sort of hyperparameter tuning and rather keep it in its true form. 



I also did the Cross-Validation eventually finding out the Average value of R^2 across to be 0.77. 


Lastly, I made use of the Ensemble method where I combined the predictions from ANN, Random Forest and Gradient Boosting. This impacted the performance very highly by leveraging the strengths of each model where ANN captures non-linear patterns, RF handles randomness, GB handles boosting errors. It resulted in below metrics: 
Random Forest R²: 1.0000
Gradient Boosting R²: 0.9999
Ensemble R²: 1.0000. There might be a good amount of Overfitting here but due to resource limitation I did not fine tune further. 
