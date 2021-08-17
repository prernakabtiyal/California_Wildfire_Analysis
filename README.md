# California_Wildfire_Analysis

### Data Gathering and Engineering

### Exploratory Data Analysis
There are 44 columns in the dataset. None of the columns have missing values. 13 features have outlier values and 17 features have a skewed normal distribution.
Features with outliers: 1.Burn 2.MnWndSp_Av 3.AvAirT_Min 4.AvHum_Max 5.Precip_Tot 6.BurnFrCh 7.AvAirT_Min_3 8.AvHum_Max_3 9.AvAirT_Av_5 10.AvAirT_AvDMin_5 11.AvAirT_Min_5 12.AvHum_Av_5 13.AvHum_Max_5
Features with skewed distribution: 1.Burn 2.Slr_Tot 3.MaxWndGst 4.AvHum_Min 5.Precip_Tot 6.Slr_Tot_3 7.MaxWndGst_3 8.AvAirT_Av_3 9.AvAirT_AvDMin_3 10.Precip_Tot_3 11.Slr_Tot_5 12.MaxWndGst_5 13.AvAirT_Max_5 14.AvAirT_AvDMin_5 15.AvHumAv_5 16.Precip_tot_5 17.BurnFrCh
The 'Burn' column quantifies the acres burned in each fire incident. This column was used to define a threshold for qaulifying an event as a fire event. A 45th column 'Fire' was added to classify fire events above the threshold as 1 and below threshold as 0.
### Feature Selection

### Feature Engineering

### Classification models
