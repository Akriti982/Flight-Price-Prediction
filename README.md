# Flight-Price-Prediction
This is an end-to end machine-learning model. Its complete life cycle is decribed in this image:
![image](https://user-images.githubusercontent.com/67294462/189485986-2a49e47e-69c0-43ab-a21f-5eecd71e910d.png)
* Data is cloned from dsrscientist/Data-Science-ML-Capstone-Projects in two parts: train dataset and test dataset.
* Problem Statement:
Flight Price Prediction is a regression based problem statement to predict flight ticket prices based on prices of flight tickets for various airlines between the months of March and June of 2019 and between various cities. There is a train dataset and a test dataset.
* ![newplot - 2022-09-10T192241 289](https://user-images.githubusercontent.com/67294462/189486485-cb60c6f2-94aa-42cf-b4c5-b6a3421a6ebd.png)
<img width="810" alt="image" src="https://user-images.githubusercontent.com/67294462/189486540-4bc5dca6-5b92-4fd8-9652-1ef1e3067704.png">
1. The dataset has no missing values, therefore imputation and filling data are not required.
2. The whole dataset is of 10683 rows * 11 columns, hence, chances of overfitting, that is, model getting trained more than essential are high so we will go through the data thoroughly and try to draw anomalies and code some derived features, that can be of help in making predictions.
3. There are 1 continuous columns and 10 categorical columns, hence, encoding is required.

#  We will understand the data by drawing anomalies and understanding their buying habits:

###    1. There are 10 categorical columns, containing data of popular airlines, example, Jet Airways, Indigo, Air India, etcetera. Jet Airways is dominant with 36% appearance among 12 unique airlines.

###    2. Most of the journeys took place on 18/05/2019.

###    3. Delhi is the most popular source and Cochin is the most popular destination.

###    4. Most of the flights have one stop.

# Q&A Answered

### How many airlines are being surveyed: 12

### How many destinations are covered: 6

### What is the maximum number of total stops: 4 stops, found in 0.00936% data.

<img width="500" alt="image" src="https://user-images.githubusercontent.com/67294462/189486759-2ccbdb0b-a229-4faa-ab78-95c67685753c.png">
<img width="494" alt="image" src="https://user-images.githubusercontent.com/67294462/189486798-e47c3c4e-f09f-4e3d-b629-0c6ed7ea80a7.png">
<img width="493" alt="image" src="https://user-images.githubusercontent.com/67294462/189486823-268e866c-0665-4c20-959f-e5453fc4f414.png">
<img width="503" alt="image" src="https://user-images.githubusercontent.com/67294462/189486841-8ffb0afe-22e4-4b5a-a421-f8463a9f698e.png">

# It can be visualized from above scatter plots against outcome vector that the distribuution is mostly unevenly distributed for most of the columns. For example,
## Additional Info Encoded
## Route Encoded
## Destination Encoded... Many More...

# Anomalies Detected
## Highest price is 79512 received on 1/3/2019.
## In flight meal, business class and red eye flight were some of the prominent  benefits availed by passengers.
## Most significant price pct change is 4.5.
## Highest price is observed for Business Class flight with 1 stop by Jet Airways for route ( BLR → BOM → DEL)


# Q&A Answered
## What is the range of route encoded: 0 to 127.
## What is the range of airline encoded: 0 to 11.
## What is the range of price percentage change: 0 to 10.
## What is the range of total stops encoded: 0 to 4.

<img width="734" alt="image" src="https://user-images.githubusercontent.com/67294462/189486905-e027e4c6-750c-40b6-b750-00d46f01d8c4.png">
<img width="538" alt="image" src="https://user-images.githubusercontent.com/67294462/189486936-936e460e-8e45-44b2-9aac-c01b0072e152.png">

# Verbal Translation Of Above Graph:
## 1. Label has weak positive relationship with these features:

# ['Price', 'Source_encoded', 'Route_encoded', 'Dep_Time_encoded',
#       'Arrival_Time_encoded', 'Price_pct_change', 'Source_encoded_pct_change',
#       'Route_encoded_pct_change', 'Dep_Time_encoded_pct_change']

## 2. Label has weak negative to strong negative relationship with these features in this heatmap:

# ['Airline_encoded', 'Date_of_Journey_encoded', 'Destination_encoded',
#       'Duration_encoded', 'Total_Stops_encoded', 'Additional_Info_encoded',
#       'Airline_encoded_pct_change', 'Date_of_Journey_encoded_pct_change',
#       'Destination_encoded_pct_change', 'Arrival_Time_encoded_pct_change',
#       'Duration_encoded_pct_change', 'Total_Stops_encoded_pct_change',
#       'Additional_Info_encoded_pct_change']


## 3. Strong Multicollinearity is detected among 2 features:

    destination encoded

    source encoded

## 4. Multicollinearity seems to be moderate among all other data points.

## Q&A Answered

        1. Most useful feature is: Total Stops Encoded.

        2. Features that can cause bias are: Destination Encoded And Source Encoded.

        3. Explanatory Power of all variable: Weak to Moderate (due to weak and moderate correlation with label).
        
<img width="459" alt="image" src="https://user-images.githubusercontent.com/67294462/189487041-a92fadc3-d225-417d-bcca-47b47da40d2f.png">

<img width="464" alt="image" src="https://user-images.githubusercontent.com/67294462/189487049-0f68bc60-9079-412f-acbe-a01948c6dbed.png">

<img width="458" alt="image" src="https://user-images.githubusercontent.com/67294462/189487080-a73764e6-1ce0-4f48-9084-cc3213f5a1fa.png">

# Verbal Translation Of Above Graph
# 1. The data has many outliers.
# 2.  To name a few are:

    Airline Encoded

    Date Of Journey Encoded

    Source Encoded

    Destination Encoded

    Route Encoded

    Dep Time Encoded

    Duration Encoded

    Additional Info Encoded

    Source Encoded Pct Change

    Destination Encoded Pct Change

    Route Encoded Pct Change

    Total Stops Encoded Pct Change
    
   <img width="490" alt="image" src="https://user-images.githubusercontent.com/67294462/189487127-0aad1f0f-a9f7-4c67-856d-c8e1dfcd4366.png">
   
   # Conclusion:
## Based On EDA done above in two parts, I will do ftest and pvalue test on these seemingly weak indicators based primarily on skewness, kurtosis and multicollinearity:

    Dep_Time_encoded_pct_change (Skewness & Kurtosis)

    Arrival_Time_encoded_pct_change (Skewness & Kurtosis)

    Duration_encoded_pct_change (Skewness & Kurtosis)

    Date_of_Journey_encoded_pct_change (Skewness & Kurtosis)
    
    Destination Encoded (Multicollinearity)
    
    Source Encoded (Multicollinearity)
      
   * Feature Selection:
   <img width="347" alt="image" src="https://user-images.githubusercontent.com/67294462/189487224-55824654-abf0-4811-8140-016e3a8fe04a.png">

* Model Selection:
# Conclusion
## The best model with right fit is:                                                                                           
   
## Model 7: Ada Boost Regressor With Huber Regressor As Base Estimator

mse_train 5805696.223222722

rmse_train 2409.501239514668

mse_test 6306788.160680427

rmse_test 2511.3319495201004

MSE Out Of Sample:  140735911.4418835

RMSE Out Of Sample:  11863.216740913213


