# California_Wildfire_Analysis
In the recent years, wildfires in California have been in the news very frequently due to the threat they pose to wildlife, environment and human life and property. Due to the ongoing climate change, wilfires have become a common phenomenon. However, unlike other natural disasters, wildfires are tricky to predict and therefore, significantly disrupt the way of life due to lack of timely mediative actions. The unpredictability of wildfires also makes it very difficult for businesses such as construction, utility and insurance companies to accurately gauge the needs of clients in wildfire prone areas. Therefore, it is highly desirable to develop a model to perform wildfire risk assessment. In the presented project, a model is developed to classify wildfires in California into two categories based on the extent of damage: less than 100 acres burnt(Class A,B,C classified as 0) and 100 or more acres burnt(Class D,E,F,G classified as 1). The model is built using supervised machine learning utilizing wilfire incidents from 1992-2015. 
### Data Gathering and Engineering
The data is obtained from a combination of Kaggle dataset (used to obtain date, time, place, and burn acreage) and historical weather station data from RAWS website. Due to the large size of the state of California, the terrestial and climatic conditions significantly vary throughout the state. Therefore, in order to make the model sensitive to geological variety, the state was divided into five sectors as shown below. The 'sector' was used as a feature in the model. In case of multiple weather stations being present within a sector, the averaged data for all the stations was used. Since the weather station data provides a huge number of weather parameters, only parameters that would usually be relevant to a wildfire were included such as: Humidity, Wind Speed, Air Temperature etc.

### Exploratory Data Analysis
#### Missing values
There are no missing values.

#### Normal Distribution and Outliers
Many features have a significant skew in distribution and also have outliers. Therefore, ML algorithmss that are robust to skewness in datat and outliers (not based on euclidean distance analysis) are chosen.

#### Imbalanced data
The data was found to be biased towards Class D and above fire events (more 1s than 0s). This is not conducive to a classification analysis as the classifier can classify all events as True and still give very high performance metrics (Accuracy, Precision, Recall) leading to an inaccurate model and also making it difficult to accurately compare different algorithms. Therefore, the data was oversampled using SMOTE to include more 0 events and balance the data. 

### Feature Selection
There are too many features in the data set so, the following criteria were used to drop features that do not seem to be significant for target prediction. 
1. Low variance: Features with very low variance (<0.001) can be treated as approximately constant and do not impact the traget variable significantly and therefore they can be dropped from the analysis. As the features are not scaled, for each feature the normalized variance is compared to the threshold value. The column dropped due to low variance: 'Year'. This makes sense as the year in which fire occured is redundant to prediction is only relevant to obtain the relevant weather data.
2. Correlation: Features which are highly correlated effectively convey the same information and therefore, only one feature can replace a set of correlated features. A Pearson correlation coefficient with a threshold of 0.8 was used to identify and remove  set of correlated features and replace them with one feature. The features dropped due to high correlation are: 'AvAirT_Max_3', 'MaxWndGst_5', 'AvAirT_AvDMin', 'AvHum_Min_3', 'AvHum_Min', 'AvAirT_AvDMax_3', 'AvAirT_Av_5', 'AvAirT_AvDMax', 'AvAirT_AvDMax_5', 'AvAirT_Max_5', 'AvAirT_AvDMin_3', 'MnWndSp_Av_5', 'AvAirT_AvDMin_5', 'AvHum_Av_5', 'Slr_Tot_5', 'AvHum_Max_5', 'AvHum_Min_5', 'MnWndDir_Av_5', 'AvAirT_Min_5', 'Precip_Tot_5'.
3. Mutual Information: The dependence of the target on the remaining features was calculated using the mutual information classifier and features with mutual information number >0.02 were selected for further analysis and the remaining features were dropped.

### Motivation for the model 
The objective of this project is to create a model that will be able to predict a Class D and above fires (greater than 100 acres burnt) as a 'True' event based on provided weather station data. In this prediction a False Negative(FN) could cause unpreparedness and potential loss of life and property while a False Positive would only cause unnecessary economic costs. Keeping this in mind, the model is developed to maximize Recall (minimize FN) while the Precision is kept above a certain threshold(>90%).

### Classification models
Two different classification algorithms are tested to compare the performance metrics. Due to the presence of outliers and skewed data in many features 'tree-based' models are tested first.
#### Performance Metrics
As mentioned above, Recall is chosen as the most important metric and is maximized due to occurence False Negatives being more hazardous. However, since False positives could also cause unnecessary economic costs, their occurence is minimized by setting a high threshold bar on the Precesion value (>90%)

#### Cross-validation
The classification models are evaluated using the above performance metrics. To avoid overfitting the model to the training data, a Stratified 5-fold cross-validation is used and the avergaed performance metrics are reported.  
#### Decision Tree Classifier



#### Random Forest Classifier
