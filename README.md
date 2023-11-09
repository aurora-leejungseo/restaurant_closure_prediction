# Restaurant Closure Prediction


## Introduction
The pandemic has brought about lasting changes in our world, leaving the economy in a fragile state and numerous restaurants grappling with challenges. My objective is to tackle this issue by forecasting the survival of restaurants over the next two years. Although the Yelp API offers valuable data, I've acknowledged the importance of incorporating demographic and geographic information to conduct a thorough analysis. Elements such as location, population density, racial demographics, income, and education significantly influence the prediction of restaurant success. Following extensive data research and validation of the machine learning model, I have created a predictive model aimed at assisting struggling local businesses and aiding in the economic recovery of affected communities.


## Data
The main dataset used combines the 2020 Yelp dataset, Yelp API, and demographic data. 

`yelp_academic_dataset_business_2020`: This is the base dataset and was obtained from [sdkramer10’s GitHub repository](https://github.com/sdkramer10/13fund-covid-analysis/blob/master/yelp_academic_dataset_business.json.zip) as Yelp does not officially offer the previous dataset. All the dataset we used is accessible under the data folder.

`yelp_academic_dataset_business_2022`: Obtained from publicly available [Yelp API](https://docs.developer.yelp.com/docs) for services on Yelp. Registration for the API key is required and there is a daily limit to the number of callings that can be made with the key received. We used business_id from the 2020 data to call the current business details. Starting with 209,393 data points, I filtered it down to 56,936 rows by focusing on restaurants and their current 'is_open' status. I used the Yelp API to obtain the most up-to-date restaurant features, with 675 values indicating 'close' or 'open' status. 

`outer_source_data.csv`: DemographicTo enhance our dataset, we added demographic data from the FBI and Census sources, resulting in a final dataset of 36,365 restaurants.

The full process of generating `df` used in the main `restaurant_closure_prediction.ipynb` file can be found on `df_creation.ipynb`.


< Data Features Description >
* stars: Star rating of the restaurant in 2020
* review_count: Number of reviews in 2020
* review_change: Changes in the number of reviews in 2022 since 2020
* rating_change: Changes in the star rating in 2022 since 2020
* num_categories: Number of categories
* price range: Price range of the restaurant
* 0: First value from singular value decomposition from the values of the attributes
* 1: Second value from singular value decomposition from the values of the attributes
* 2: Third value from singular value decomposition from the values of the attributes
* num_attributes: Number of attributes/details describing restaurant
* counts: Number of restaurants in same names
* population: Population of state
* property_crime: Property crime includes the offenses of burglary, larceny-theft, motor vehicle theft, and arson (FBI)
* larceny_theft: Larceny-theft is the unlawful taking, carrying, leading, or riding away of property from the possession or constructive possession of another (FBI)
* median_gross_rent: Median gross rent from 2016 to 2020
* Median_household_income: Median household income (in 2020 dollars) from 2016 to 2020
* bach_deg_edu: Percentage of people with Bachelor's degree or higher
* insurance_und65: Percentage of people under age 65 with health insurance
* white_perc: Percentage of population who are white alone
* black_perc: Percentage of population who are Black or African American alone
* asian_perc: Percentage of population who are Asian alone
* hispanic_perc: Percentage of population who are hispanic or latino alone
* is_open: Current status of the restaurant


## Model
Using classification models available in scikit-learn, I applied our dataset to logistic regression, ridge regression, support vector machine, k-nearest neighbor, random forest, gradient boost, ada boost, XGBoost, and multi-layer perceptron. The selection of these models is based on the knowledge and experience gained from our coursework. I have initialized these models with their default hyperparameters, with the intention of fine-tuning the parameters after model selection. In the model development process, 75% of the dataset was allocated for training, while the remaining 25% was used for testing.

## Evaluation and Analysis
There are 6 different metrics commonly used to evaluate the classification models: 1) Accuracy 2) Confusion Matrix 3) Precision 4) Recall 5) F1-score 6) ROC-AUC

## Project Results
Among the models, random forest had the highest roc-auc score as of 0.85
