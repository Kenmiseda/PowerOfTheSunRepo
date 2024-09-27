# The Power of the in Our Hands.

## Exploratory Analysis 

This project aims to test the feasibility of predicting solar energy generation using weather pattern data. 
A whole year’s weather and solar energy generation data was sourced from Kaggle for the same location, North Carolina. A variable description table was generated as below. 
![image](https://github.com/user-attachments/assets/4bb15f7b-ddd5-47ff-acff-93339824a212)

While doing exploratory data analysis there were substantial missing values as shown in the table below.
![image](https://github.com/user-attachments/assets/34538e5e-8b90-4ae1-97b5-bfc47f197f8a)

Multiple Imputation by Chained Equations (MICE) was used, with random forest as the method, to deal with the missing values. After the imputation below is a distribution table of all the numerical variables
![image](https://github.com/user-attachments/assets/6ce1a74e-1a5a-46f8-80fc-2ef6275e2481)

The categorical variables: One-hot encoding to deal with the categorical variable. A correlation analysis was done 
![image](https://github.com/user-attachments/assets/9c449d97-f313-4aed-a143-2287d0c31cfc)

A subset of the top ten correlated variables analysis is tabulated as below.  The top ten variables correlated with Target variable (Energy Discharged ) tabulated as bellow
![image](https://github.com/user-attachments/assets/b2493db7-e802-427a-b897-56382a3660ec)

## Model Training
Model 1: We first trained the model on the subset data and these are the results. 
RMSE which was our chosen measure of best model selection. This model gave us a fairly satisfactory model with an RMSE value of 5123.222

![image](https://github.com/user-attachments/assets/d26fc178-8904-42f6-84ca-59626f76cc6b)  ![image](https://github.com/user-attachments/assets/f43e52d6-67b1-4045-a494-388d510c24e6)

## Model 2:  Training
We decided that since we have already cleaned up the entire data, taken care of any categorical variables, filled up any empty cells, why not use the entire data to make another Random forest regressor. Below are the results.  To note was the improved RMSE of 4491.
![image](https://github.com/user-attachments/assets/ffb5a582-6f82-46e7-a5b3-4f9769a07b41)  ![image](https://github.com/user-attachments/assets/41dd92b5-eacb-4342-b9fd-25247a8ea2bb)

Variable importance from Model 2.
![image](https://github.com/user-attachments/assets/2852b207-2da8-4968-844e-2447d431fbee) ![image](https://github.com/user-attachments/assets/77fc0339-313d-41ba-a58f-a7a34d2f86b1)

### Key Insights:
Cloud Cover is the most important variable: With the highest %IncMSE (28.25), indicating that it has the greatest impact on solar energy prediction. Cloud cover directly reduces the amount of sunlight reaching solar panels, thus affecting energy generation.

Temperature-related variables: Both maximum temperature (21.65) and minimum temperature (15.83) significantly influence solar energy output. High temperatures typically coincide with clearer skies, leading to more sunlight, whereas lower temperatures may correlate with cloudy or rainy conditions.

Relative Humidity and Weather Conditions Matter: Relative humidity (20.04). High levels are often associated with cloudy or rainy conditions, reducing sunlight exposure. Clear skies (17.46) and rain/partially cloudy conditions (13.75) have a strong effect, as clear skies boost solar generation while rain or clouds diminish it.

Overall Patterns: Direct factors like cloud cover, temperature, and weather conditions dominate the prediction of solar energy generation. These variables are directly related to the amount of sunlight received. Indirect factors such as precipitation, visibility, and humidity also play a significant role, as they are tied to weather patterns that can influence solar radiation.

## Model Tuning: 
To  increase the accuracy of the model (model2) we decided to do some tuning. Since we were using the built-in Random Forest (RF) regressor in CARET, we focused our tuning efforts on the "mtry" parameter.  Through testing with our dataset, we determined the optimal "mtry" value to be 10 as shown in the table bellow. 
With this, we trained our final model using these parameters:
Mtry = 10
Repeat CV =  10
Repeated =  50times 
![image](https://github.com/user-attachments/assets/56910bc3-7d3a-4914-9938-2448458fae77)

## Model 3: Final Model 
These are the results are shown below. Our chosen measure RMSE was actually lower at 3434.258, so we decided this was the best model.


![image](https://github.com/user-attachments/assets/caad2fb9-7f64-46ce-b409-21c56165a2b4)

The table below is an overview of the daily energy generation prediction 
![image](https://github.com/user-attachments/assets/0b660213-196f-49f2-82f8-f1f4aa332c92)

## Mean Mode Comparison 
For further analysis, We then put together the Mean and the Median Daily Energy production charts to inform a ranking system among the six sample locations. This was also to help make conclusions for the project

![image](https://github.com/user-attachments/assets/519df939-6883-4626-9de0-f78b1db41c8b)

Insights:
California has the highest predicted yearly mean (19,876.34 KWh) and median (22,279 KWh) energy output among the states listed. 
This reflects California’s favorable weather conditions for solar energy generation, such as high levels of sunlight and relatively low cloud cover. 
The significant gap between the mean and median suggests that there may be some extreme high values (outliers) in the dataset. 

Washington DC shows the lowest predicted yearly mean (10,783.33 KWh) and median (9,904 KWh) output. 
The relatively smaller difference between the mean and median suggests a more consistent solar energy output pattern, with fewer extreme outliers compared to other states.

The variations in predicted solar output are largely driven by the climate and geographic conditions of each state. 
For example, states with more consistent sunlight exposure, such as California and Texas, outperform those with less favorable conditions, like Washington DC. 
States like Montana and Minnesota, while colder, still generate moderate amounts of solar energy, likely due to less cloud cover during sunny periods.

### Box Plot Representation
By interpreting the box plot we could see that the reason the Median for California is so much higher than the Mean was because of outliers on the left side of the California Box-plot. 
![image](https://github.com/user-attachments/assets/883fa55d-122d-4b8d-9fa3-ed8921bb2d53)

## Conclusion 
Contrary to our initial hypothesis, the Mean Daily Energy production data reveals that the central region of the USA emerges as a more favorable location for solar power investments. 
This challenges our original assumption that the conventional characterization of southern states as hot and northern states as cold would correlate with solar energy generation. However, our findings indicate a different reality.

Notably, states situated in the middle of the U.S(longitudinal) exhibited comparable energy generation, whereas the extremities in the east and west displayed significant variations in solar energy production. 

The project concluded that solar energy generation is not strictly correlated with geographical location temperature patterns. The middle latitudes exhibited comparable energy generation to the southern states, 
challenging the assumption that warmer states are more suitable for solar power production.

While this project serves as a proof of concept, it highlights the potential for nationwide predictions with additional data and fine-tuning. 
The model's accuracy can be enhanced with more weather data, advanced algorithms, and a broader dataset. The findings suggest a future where predicting solar energy generation across the country becomes more feasible.










 

