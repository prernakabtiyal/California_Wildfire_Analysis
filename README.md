# California_Wildfire_Analysis

### Data Gathering and Engineering

### Exploratory Data Analysis
There are 44 columns in the dataset. None of the columns have missing values. 13 features have outlier values and 17 features have a skewed normal distribution.\
Features with outliers: 1.Burn 2.MnWndSp_Av 3.AvAirT_Min 4.AvHum_Max 5.Precip_Tot 6.BurnFrCh 7.AvAirT_Min_3 8.AvHum_Max_3 9.AvAirT_Av_5 10.AvAirT_AvDMin_5 11.AvAirT_Min_5 12.AvHum_Av_5 13.AvHum_Max_5\
Features with skewed distribution: 1.Burn 2.Slr_Tot 3.MaxWndGst 4.AvHum_Min 5.Precip_Tot 6.Slr_Tot_3 7.MaxWndGst_3 8.AvAirT_Av_3 9.AvAirT_AvDMin_3 10.Precip_Tot_3 11.Slr_Tot_5 12.MaxWndGst_5 13.AvAirT_Max_5 14.AvAirT_AvDMin_5 15.AvHumAv_5 16.Precip_tot_5 17.BurnFrCh\
The 'Burn' column quantifies the acres burnt in each fire incident. This column was used to define a threshold for qaulifying an event as a fire event. A 45th column 'Fire' was added to classify fire events above the threshold as 1 and below threshold as 0.\
For the second analysis the 'Burn' channel values were used to categorize the fire events into 4 categories. Class 1: Acres burnt<100; Class 2:100<Acres burnt<50,000; Class 3: 50,000<Acres Burnt<100,000; Class 4: Acres Burnt>100,000.  
### Feature Selection
There are too many features in the data set so following criteria were used to drop features that do not seem to be significant for target prediction. 
1. Low variance: Features with very low variance (<0.001) can be treated as approximately constant and do not impact the traget variable significantly and therefore they can be dropped from the analysis. The columns dropped due to low variance are: 'AvAirT_Av_3','AvAirT_AvDMax_3','AvAirT_Max_3','AvAirT_AvDMin_3','AvHum_Max_3','AvAirT_Av_5','AvAirT_AvDMax_5','AvAirT_Max_5','AvAirT_AvDMin_5','AvHum_Max_5'
2. Correlation: Features which are highly correlated effectively convey the same information and therefore, only one feature can replace a set of correlated features. A Pearson correlation coefficient with a threshold of 0.8 was used to identify and remove  set of correlated features and replace them with one feature. The features dropped due to high correlation are: 'AvAirT_AvDMax', 'Slr_Tot_5', 'MnWndDir_Av_5', 'Precip_Tot_5', 'MnWndSp_Av_5', 'AvAirT_Min_5', 'AvAirT_AvDMin', 'AvHum_Min_5', 'MaxWndGst_5', 'AvHum_Min_3', 'AvHum_Av_5'
3. Mutual Information: The dependence of the target on the remaining features was calculated using the mutual information classifier and features with mutual information number >=0.009 were selected for further analysis and the remaining features were dropped.
### Feature Engineering

### Classification models
