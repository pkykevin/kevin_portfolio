# Kevin Park          
Welcome to my data science portfolio. I am passionate about data analytics, data visualization, and machine learning that can provide insights and solve real-world problems.
## Predictive models in category based on Carsales datasets

* This project is to build a tool to analyse, compare, predict and visualize the important features and price of different car categories or makes.
* Build such predictive models to facilitate decision making for second hand car buyers and sellers.
* Multiple Linear, Random Forest and Neural Network predictive modelling techniques were employed to create predictive models.
* The study implemented predictive models on actual data from [Carsales](https://www.carsales.com.au) website.
* Observe contributing features in category into different levels of prestige - luxury sports, luxury and economy cars.
* Drill down car categories to discover the price influencing features on different car makes.

### Part 1. Dataset

#### A. Data extraction

The sample dataset of Toyota Corolla extracted from Carsales website.  Python’s Beautiful Soup v4 library used to extract data into a form that can be imported. 

![1](https://user-images.githubusercontent.com/32251175/160815871-c6367950-716f-4555-ada2-23d1bc7b30dd.PNG)

Following is an example of Toyota Corolla dataset in csv file extracted from Carsales website.

![2](https://user-images.githubusercontent.com/32251175/160816821-fb5064f4-2b00-4665-a286-28ab249f6806.PNG)

#### B. Data exploration

The dataset comprises of 21 attributes related to 2030 sold Toyota Corolla cars. The table has 2030 rows and 21 columns. Based on this dataset, the research needs to develop a reliable predictive model to predict the selling price of the cars. Therefore, the target variables applicable for model is ‘Price’.

As we have identified price as the target variable, the research has examined the prices of the Toyota Corolla vehicles by calculating the summary statistic and prepared the histogram, density and box plot of the price variable in the Toyota Corolla dataset. The price is a continuous numerical variable. The following are results of summary statistics and plots created in Python.

![3](https://user-images.githubusercontent.com/32251175/160816828-5deb7f84-9c75-4bb6-9d09-b03a93622880.PNG)

The summary statistic shows that, the selling price for Toyota Corolla has an average value of $16,990, standard deviation of $4,974 and mean of $17,355 (minimum from $1,900 to maximum $35,980) There is also indication of extreme values, which is shown in the histogram, density and boxplot. 

#### C. Check for missing values

We need to check for any missing values in the Toyota Corolla dataset provided using *isnull()* function. Consequently, the plot below shows that, the dataset is free from any missing values.

![4](https://user-images.githubusercontent.com/32251175/160821302-3f4d2a70-e81e-45d8-a5c9-9c3b4d6bcd66.PNG)

Having missing values in a dataset can cause errors with predictive modelling algorithms. The simplest strategy for handling missing data is to remove records that contain a missing value. We can use dropna() to remove all rows with missing data. The table has been cut from 2030 in the original dataset to 1894 with all rows containing a NaN removed.

![5](https://user-images.githubusercontent.com/32251175/160821359-3811f2c6-7c33-46dd-b696-b2079a18553a.PNG)

#### D. Transformation of categorical values into numerical values

As regression models only take on numerical variable, it is important that we need to transform categorical variables into numeric variables to feed into the regression model. In this case, Fuel_Type variable identified as a categorical variable with two possible values which are Petrol and Diesel. 

For transformation purpose, we assigned binary value in which 1 and 0 implies the car has the particular fuel type. The following Python script for transformation process shown below.

![6](https://user-images.githubusercontent.com/32251175/160821472-9fccb2e2-d45a-4103-9619-e88c80d20984.PNG)

#### E. Correlations evaluation and dimensionality reduction

Following section shown the correlations between variables and carried out dimensionality reductions by removing several variables. Prior to evaluating the correlation, five variables were removed from the dataset. The table belows lists 5 variables removed and reasons for it.

![7](https://user-images.githubusercontent.com/32251175/160821616-8b69e981-fdf2-4f54-b76c-ba8752a483b8.PNG)

The correlation plot below is prepared using the heatmap function after the first phase of removal.

![8](https://user-images.githubusercontent.com/32251175/160821690-52620e27-89cd-41f6-8bce-5ee1a608d354.PNG)

Following the correlation between variables shown above, dimensionality reduction is performed by removing high cross-correlation variables. Followed with a merge of target variable ‘Price’. It is also noted year, km, fuel_cost variables have high-correlation, which shows that they are important variables which later will be used in predictive modelling. Variable year, km have negative relationship with the sale price, which implies that older cars and long km are cheaper. Variable weight, emission_standards, engine_size and airbags implying increase the weight of the car has a positive effect on the sale price. Moreover, another features like fuel_capacity and fuel_cost have positive linear relationship implying includes these features have positive effect on the sale price.

### Part 2. Regression Technique using Multiple linear regression

#### a. Regression models 

In this section, multiple linear regression as a technique is applied for predictive modelling of the case study on Toyota Corolla dataset. As the main task for the predictive modelling is to predict the selling price of used Toyota Corolla using the variables selected in Part 1, therefore, price variable will be used as target variable. 

Prior to building the linear regression models, the dataset was partitioned with ⅔ as the training data sample and ⅓ as the testing data. The trained dataset comprises of 1262 training data and 632 testing data. 

![9](https://user-images.githubusercontent.com/32251175/160988349-5ac285ed-475b-4df2-9f0e-586b7274498c.PNG)

This is the process of building a model used backward elimination. 

![10](https://user-images.githubusercontent.com/32251175/160988358-2e4a5ce5-08ef-4bb1-92db-23ba51ecc3f9.PNG)

From step 1, select a significance level to stay in the model, for example, SL = 0.05 applied in this method. Step 2, fit the full model with all possible predictors. After you fit the model, you will see the one with the highest p-value, so if the p-value is greater than the significance level then you go to step 4. Step 4 is to remove that predictor. It is to remove basically the variable that has the highest p-value. And step 5, you fit the model without this variable. The model will be rebuilt with the fewer number of variables. In step 5, continue to fit the model again with one less variable. This process will keep doing that until it comes to a point where the variable of that p-value is still less than the significance level, then go to FIN (means model is ready). 

##### 1) Regression Model 1.

The first regression model technique predictive model has included all of the attributes in the selected variables identified previously section. This model resulted in an adjusted R-squared of 0.817 and Root Mean Square Error (RMSE) of 1856.29. The regression and model evaluation result is shown below.

![11](https://user-images.githubusercontent.com/32251175/160989844-b96bd704-4c00-4d0f-8d3e-0bea6ca5e2ff.PNG)


This is a comparison of predicted values with actual values and the scatter plot for regression model 1.

![12](https://user-images.githubusercontent.com/32251175/160989880-9a5e5d5f-d4e8-413f-acaa-a101ca5799b5.PNG)

##### 2) Regression Model 2.

The attributes applied for regression model 2. comprises age, km, airbags, engine_size, gears, emission_standards, weight and fuel_cost. This model resulted in an adjusted R-squared of 0.817 and Root Mean Square Error (RMSE) of 1841.17. The regression and model evaluation result is shown below.

![13](https://user-images.githubusercontent.com/32251175/160990029-dbcf061c-2cf8-47f9-b6c7-79baf2962b8e.PNG)

This is a comparison of predicted values with actual values and the scatter plot for regression model 2.

![14](https://user-images.githubusercontent.com/32251175/160990039-e3961b8d-a212-4c8e-bb79-3c2a90a653e1.PNG)

##### 3) Regression Model 3.

The attributes applied for regression model 3 comprises age, km and weight. This model resulted in an adjusted R-squared of 0.988 and Root Mean Square Error (RMSE) of 1957.55. The regression and model evaluation result is shown below.

![15](https://user-images.githubusercontent.com/32251175/161185287-2d917a05-42d3-496c-8ca9-44d98d6f49e0.PNG)

This is a comparison of predicted values with actual values and the scatter plot for regression model 3.

![16](https://user-images.githubusercontent.com/32251175/161185340-7166cccb-db90-4920-8b8d-204cfaa999e7.PNG)

#### b. Evaluation

![17](https://user-images.githubusercontent.com/32251175/161185422-fd0a9aa1-9b78-4b71-9def-6903f2955718.PNG)

The table above summarises the results of three linear regression technique predictive models based on the Toyota Corolla dataset. RMSE is used to measure the difference between predicted variable and the actual variable. Therefore, the lower RMSE would be preferred, which implies that the model 2 is the most optimal linear regression predictive model. 

### Part 3. Regression Technique using Random Decision Tree

#### a. Regression models

In this section, random decision tree technique is applied for predictive modelling of Toyota Corolla dataset. This section summarises and evaluates four random decision tree predictive models to predict price.

Prior to building the random decision tree regression models, the dataset was partitioned with ⅔ as the training data sample and ⅓ as the testing data. The trained dataset comprises of 1262 training data and 632 testing data. Then, the number of trees in the forest of 1,000 is selected to fit a number of decision tree classifiers.

Decision trees makes split that maximize the decrease in impurity. By calculating the decrease in impurity for each feature across all trees we can know that feature importance. The Python script and figure of feature importance shown below.

![18](https://user-images.githubusercontent.com/32251175/161185563-aa204a09-ad89-41fd-afc1-5db1044e0c9e.PNG)

![19](https://user-images.githubusercontent.com/32251175/161185601-d80f513b-5cb4-42a3-a6c5-f16e0d9b6b5c.PNG)

As can be seen from the graph, feature importance from Toyota Corolla shows that Age and KM are the highest features contributing to the final price followed by weight, engine size and fuel cost.

##### 1) Regression Model 1.

The first decision tree predictive model is created by applying all selected variables and resulted with RMSE of 1375.09. The python script and model evaluation result shown below.

![20](https://user-images.githubusercontent.com/32251175/161189084-c98cd672-de55-437a-a612-dc9f6fb81f14.PNG)

This is a comparison of predicted values with actual values and the scatter plot for decision tree regression model 1.

![21](https://user-images.githubusercontent.com/32251175/161189116-ea432a6a-fb86-425a-8e09-f43cb687390d.PNG)

##### 2) Regression Model 2.

The second decision tree predictive model is created by applying features that have an importance of more than 0.01. There are 8 selected variables of feature importances, which comprises of age, km, airbags, engine_size, gears, emission_standards, weight and fuel_cost. This resulted with RMSE of 1383.16. The python script, feature importance and model evaluation result shown below.

![22](https://user-images.githubusercontent.com/32251175/161189187-4a5bff2a-69ac-4859-bf5f-57fb4c294054.PNG)

This is a comparison of predicted values with actual values and the scatter plot for decision tree regression model 2.

![23](https://user-images.githubusercontent.com/32251175/161189219-1ca5ba1f-9549-4f5e-a414-6e7387f048e0.PNG)

##### 3) Regression Model 3.

The third decision tree predictive model is created by applying features that have an importance of more than 0.05. There are 3 selected variables of feature importances, which comprises of age, km and weight. This resulted with RMSE of 1581.61. The python script, feature importance and model evaluation result shown below.

![24](https://user-images.githubusercontent.com/32251175/161189289-4577a8a1-c511-4b15-9894-bc7fad52c336.PNG)

This is a comparison of predicted values with actual values and the scatter plot for decision tree regression model 3.


This is a comparison of predicted values with actual values and the scatter plot for decision tree regression model 3.

![25](https://user-images.githubusercontent.com/32251175/161189336-ee022f7b-d9f8-4086-b61e-45fa92dd581d.PNG)

#### b. Evaluation

![26](https://user-images.githubusercontent.com/32251175/161189396-d2950387-bca6-4e80-8e39-29537439da47.PNG)

The table above summarises the results of four random decision tree predictive models, with price as the target variable. As explained in regression model evaluation, a lower RMSE is more preferred, which implies that the random decision regression model 1 is the most optimal decision tree regression predictive model. However, it is important to note that model 3 includes only age, km and weight, which may not be ideal for actual predictive model.

### Part 4. Regression Technique using Neural Network

#### a. Regression models

In this section, neural network technique is applied for predictive modelling of Toyota Corolla dataset. The graph below shows what its looks like in neural network regression (can see some attributes as Inputs(Is) and one output layer which is the Price used Toyota Corollas) The Bs are biases introduced.

![27](https://user-images.githubusercontent.com/32251175/161194432-b0d21289-4cda-4269-843f-239f990e962e.PNG)

Prior to building the neural network regression models, the dataset was partitioned with ⅔ as the training data sample and ⅓ as the testing data. The trained dataset comprises of 1262 training data and 632 testing data. The model optimizes in multilayer perception layer, and the number of neurons (100, 100) applied in the hidden layer(Hs). Then a seed value of 42 used to generate random sampling dataset. Neural network is in general hard to see which input features are relevant and which are not. The reason for this is that each input feature has multiple coefficients that are linked to it - each corresponding to one node of the first hidden layer. Adding additional hidden layers makes it even more complicated to determine how big of an impact the input feature has on the final prediction. On the other hand, for linear models it is very straightforward since each feature has a corresponding coefficient and its magnitude directly determines how big of an impact it has in prediction. This research uses features selected from linear regression models (where reduced the number of features in model 1, 2 and 3) for neural network. 

##### 1) Regression Model 1.

The first neural network predictive model is created by applying all selected variables. This resulted with RMSE of 1495.58. The python script and model evaluation shown below.

![28](https://user-images.githubusercontent.com/32251175/161194560-09fe6980-7b5e-4669-b515-74103faa75e4.PNG)

This is a comparison of predicted values with actual values and the scatter plot for neural network regression model 1.

![29](https://user-images.githubusercontent.com/32251175/161194601-87516ff7-91bb-499b-b587-cb16bb52cb25.PNG)

##### 2) Regression Model 2.

The second neural network predictive model is created by applying selected variables from random regression model 2, which comprises Age, Km, Airbags, Engine Size, Gears, Emission Standards, Weight and Fuel Cost. This resulted with RMSE of 1520.42. The python script and model evaluation shown below.

![30](https://user-images.githubusercontent.com/32251175/161194660-1c2f3c9f-92e3-47a5-9ea6-b36b7a136ddb.PNG)

This is a comparison of predicted values with actual values and the scatter plot for neural network regression model 2.

![31](https://user-images.githubusercontent.com/32251175/161194707-e1094b17-5630-4a8a-b8e0-4a44dbf49a39.PNG)

##### 3) Regression Model 3.

The third neural network predictive model is created by applying selected variables from linear regression model 3, which comprises Age, Km and Weight. This resulted with RMSE of 1548.81. The python script and model evaluation shown below.

![32](https://user-images.githubusercontent.com/32251175/161194741-af7cba58-cc9f-4039-afa5-84752d786bef.PNG)

This is a comparison of predicted values with actual values and the scatter plot for neural network regression model 3.

![33](https://user-images.githubusercontent.com/32251175/161194797-c4e6471c-0559-4dda-b6e2-0704c79cd0c3.PNG)

#### b. Evaluation

![34](https://user-images.githubusercontent.com/32251175/161194847-8d8ae9c2-8c3c-457e-9843-3c288467405d.PNG)

The table above summarises the results of four neural network predictive models, with price as the target variable. As explained in regression model evaluation, a lower RMSE is more preferred, which implies that the neural network regression model 1 is the most optimal neural network regression predictive model. 

### Part 5. Model comparison

![35](https://user-images.githubusercontent.com/32251175/161194938-3d743cdc-eac5-4ea3-983f-a973c1741a43.PNG)
![36](https://user-images.githubusercontent.com/32251175/161194998-972f3d44-97b3-4a93-ace4-7ddbddee85e2.PNG)

The graph above summarizes the results of three regression techniques (multiple linear/random decision tree/neural network) to predict car sales price from Toyota Corolla dataset. The accuracy of the predictive models are compared based on their RMSE. In terms of efficiency, the random forest and neural network regression technique is much more efficient compared to the multiple linear regression. From all of the above predictive models, the random forest regression technique model 1. has the lowest RMSE of 1375.09. The random decision tree algorithms also provide importance features and the relationships between the different variables, which helps to create more accurate models. One key highlights shows that 3 key features: Age, KM and Weight are the most importance features. Moreover, it appears that the results from random decision slightly outperformed the results from neural network models, by providing a more lower of RMSE. Consequently, the random forest tree technique model appears to be more suitable predictive modelling for the Toyota Corolla dataset from Carsales.

### Part 2. Challenge: Categorizing the Used Cars

The car brand names and make for a vehicle tells a lot about the level of prestige of a car, for example, Mercedes-Benz and BMW are luxury car makers, which can be in the luxury segment. In this research, we will categorize and test on used car based on different in the level of prestige. The 3 categories are Luxury Sports, Luxury and Economy. The proposed categories and their respective makes are as follows:

![37](https://user-images.githubusercontent.com/32251175/161197051-c9b87899-fa94-4e98-8697-03012117c4fa.PNG)

#### A. Luxury Sports

The dataset comprises of 21 attributes related to 790 Luxury Sports cars which contains 3 car makes (100 samples from Lamborghini, 109 from Ferrari and 581 from Porsche where extracted from Carsales site). 

##### 1. Multiple Linear Regression

###### a. Regression Model 1.

The first regression model technique predictive model has included all of the attributes in the selected variables identified previously section. This model resulted in a Root Mean Square Error (RMSE) of 104136.05. The regression and model evaluation result is shown below.

![38](https://user-images.githubusercontent.com/32251175/161198361-e98a9e5e-80ec-4bea-a0ef-b5a6b7568d4d.PNG)

###### b. Regression Model 2.

The attributes applied for regression model 2. comprises Age, KM, Airbags, Engine Size, Cylinders, Gears, Fuel Capacity, Emission Standard, Weight, Doors, Seat Capacity and Fuel Cost. This model resulted in a Root Mean Square Error (RMSE) of 109712.18. The regression and model evaluation result is shown below.

![39](https://user-images.githubusercontent.com/32251175/161198425-34fee549-8df6-433c-a22d-4c6ec46ad3a2.PNG)

###### c. Regression Model 3.

The attributes applied for regression model 3. comprises KM, Engine Size and Weight. This model resulted in a Root Mean Square Error (RMSE) of 117433.77. The regression and model evaluation result is shown below.

![40](https://user-images.githubusercontent.com/32251175/161198466-fed201bc-8bb5-4955-8392-63fb68343ebe.PNG)

##### 2. Random Forest Regression

As can be seen from the graph, feature Importance for Luxury Sports shows that KM and Engine Size are the highest features contributing to the final price followed by Weight, Doors and Fuel cost.

![41](https://user-images.githubusercontent.com/32251175/161198537-628cd5b3-4b3e-417f-82ba-52fb8a963bd1.PNG)

###### a. Regression Model 1.

The first decision tree predictive model is created by applying all selected variables and resulted with RMSE of 45260.87. The regression and model evaluation result is shown below.

![42](https://user-images.githubusercontent.com/32251175/161198618-a86b2ff0-c766-490a-bfb2-194dc9e306c4.PNG)

###### b. Regression Model 2.

The second decision tree predictive model is created by applying features that have an importance of more than 0.01. There are 9 selected variables of feature importances, which comprises of Age, KM, Airbags, Engine Size, Cylinders, Fuel Capacity, Weight, Doors and Fuel Cost. This resulted with RMSE of 45771.93. The regression and model evaluation result is shown below.

![43](https://user-images.githubusercontent.com/32251175/161198657-7500e9ee-5356-4467-b947-3f4079862822.PNG)

###### c. Regression Model 3.

The third decision tree predictive model is created by applying features that have an importance of more than 0.05. There are three selected variables of feature importances, which comprises of KM, Engine Size and Weight. This resulted with RMSE of 57912.42. The regression and model evaluation result is shown below.

![44](https://user-images.githubusercontent.com/32251175/161198687-bf660474-5821-49f7-8c5a-de38b3b329c7.PNG)

##### 3. Neural Network Regression

###### a. Regression Model 1.

The first neural network predictive model is created by applying all selected variables. This resulted with RMSE of 44474.13. The regression and model evaluation result is shown below.

![45](https://user-images.githubusercontent.com/32251175/161207031-54ed7455-a7c3-4515-863d-f58800b6ba1e.PNG)

###### b. Regression Model 2.

The second neural network predictive model is created by applying selected variables from random tree regression model 2, which comprises Age, KM, Airbags, Engine Size, Cylinders, Fuel Capacity, Weight, Doors, Fuel Cost. This resulted with RMSE of 38792.73. The regression and model evaluation result is shown below.

![46](https://user-images.githubusercontent.com/32251175/161207108-fd1b38ce-4ff2-45bf-a896-c4d8896cee70.PNG)

###### c. Regression Model 3.

The third neural network predictive model is created by applying selected variables from random tree regression model 3, which comprises KM, Engine Size and Weight. The regression and model evaluation result is shown below.

![47](https://user-images.githubusercontent.com/32251175/161207176-8132bb87-e84d-4a3e-aa1b-9735d0ab9f21.PNG)

##### 4. Model Comparison

![48](https://user-images.githubusercontent.com/32251175/161207284-b9b01691-fc7f-4cf5-afcc-577d040873b4.PNG)

![49](https://user-images.githubusercontent.com/32251175/161207384-ce927615-5c6e-491d-b363-0a6d1f308bde.PNG)

The graph above summarizes the results of three regression techniques (multiple linear/random decision tree/neural network) to predict car sales price from Luxury Sports dataset. The accuracy of the predictive models are compared based on their RMSE. In terms of efficiency, the random forest and neural network regression technique is much more efficient compared to the multiple linear regression. From all of the above predictive models, the neural network regression technique model 2. has the lowest RMSE of 38792. Random forest shows that KM and Engine Size are the most important features. Moreover, it appears that the results from neural network outperformed the results from random forest models, by providing a more lower of RMSE. Consequently, the neural network technique model appears to be more suitable predictive modelling for the Luxury Sports dataset from Carsales.

![50](https://user-images.githubusercontent.com/32251175/161207483-99ba48ec-b104-4613-9bd4-d13dad558365.PNG)

The graph above illustrates all results of three regression techniques (multiple linear/random decision tree/neural network) to predict car sales price from Luxury Sports, Lamborghini and Ferrari dataset. The accuracy of the predictive models are compared based on their RMSE. When we go deep into more specific car makes, for example, Lamborghini and Ferrari in Luxury Sports. As you see from Luxury Sports, neural network outperform multiple linear and random forest, however, random forest and neural network performs similar in Lamborghini dataset. From Ferrari dataset, it appears that the result from neural network Model 1. outperformed all results from multiple linear and random forest, by providing a much more lower of RMSE. However, all multiple linear regression models appears lower RMSE than Random Forest models in Ferrari Dataset. Overall, the neural network technique model appears to be more suitable predictive modeling for all Luxury Sports, Lamborghini and Ferrari cars. 

![51](https://user-images.githubusercontent.com/32251175/161207545-71c46221-e501-4980-8b7f-35f5035ad177.PNG)

The charts above shows all the feature importance using Random Forest regression, compared with Luxury Sports, Lamborghini and Ferrari car makes. The luxury sports data shows that KM and Engine Size are the most influential features to predict car sales price. However, Lamborghini dataset appears that Engine Size is a significant factor contributing to the price more than KM. The weight and age of used cars are the next important characteristics in Lamborghini dataset. On the other hand, it appears that the most substantial features of used cars in Ferrari dataset are Age and KM, not Engine Size. As you can see, most of the Luxury Sports includes Lamborghini car makes, KM and Engine Size are the crucial features of used car sales, but not for Ferrari car makes. Overall, these charts shows that all Luxury Sports, Lamborghini and Ferrari have different car factors vital to the used car prices. 

#### B. Luxury Cars

##### 1. Multiple Linear Regression

The dataset comprises of 21 attributes related to 1809 Luxury cars which contains 3 car makes (1013 from BMW 3 series, 705 Mercedes-Benz E Class and 91 Audi A 8 series where extracted from Carsales website). 

###### a. Regression Model 1.

The first regression model technique predictive model has included all of the attributes in the selected variables identified previously. This model resulted in a Root Mean Square Error (RMSE) of 16551.91. The regression and model evaluation result is shown below.

![52](https://user-images.githubusercontent.com/32251175/161681829-ec4f666d-1611-409a-a46a-bde3ff07459f.PNG)

###### b. Regression Model 2.

The attributes applied for regression model 2. comprises Age, KM, Engine Size, Gears, Weight and Fuel Cost. This model resulted in a Root Mean Square Error (RMSE) of 19334.10. The regression and model evaluation result is shown below.

![53](https://user-images.githubusercontent.com/32251175/161681929-b9eb3f19-c2c8-4937-ab93-535a8160d902.PNG)

###### c. Regression Model 3.

The attributes applied for regression model 3. comprises Age, KM and Weight. This model resulted in a Root Mean Square Error (RMSE) of 26543.85. The regression and model evaluation result is shown below.

![54](https://user-images.githubusercontent.com/32251175/161681980-4762a5a1-2266-44dc-9bb5-f7af8f0b07aa.PNG)

##### 2. Random Forest Regression

As can be seen from the graph, feature Importance for Luxury shows that Age and Weight are the highest features contributing to the final price followed by Gears, Fuel Cost and KM.

![55](https://user-images.githubusercontent.com/32251175/161682039-7f324430-2af6-40a3-9d17-8e2d3f10c3d0.PNG)

###### a. Regression Model 1.

The first decision tree predictive model is created by applying all selected variables and resulted with RMSE of 6176.01. The regression and model evaluation result is shown below.

![56](https://user-images.githubusercontent.com/32251175/161682096-6f694b94-9f8b-485c-9f9b-f89bfd4f80fd.PNG)

###### b. Regression Model 2.

The second decision tree predictive model is created by applying features that have an importance of more than 0.01. There are 6 selected variables of feature importances, which comprises of Age, KM, Engine Size, Gears, Weight and Fuel Cost. This resulted with RMSE of 6216.75. The regression and model evaluation result is shown below.

![57](https://user-images.githubusercontent.com/32251175/161682176-9f27f022-0b2a-46d9-8151-968b942fd150.PNG)

###### c. Regression Model 3.

The third neural network predictive model is created by applying selected variables from random tree regression model 3, which comprises Age, KM and Weight. This resulted with RMSE of 7941.43. The regression and model evaluation result is shown below.

![58](https://user-images.githubusercontent.com/32251175/161682210-48d73930-61c6-4aa0-a608-c21225a8715d.PNG)

##### 3. Neural Network Regression

###### a. Regression Model 1.

The first neural network predictive model is created by applying all selected variables. This resulted with RMSE of 6302.07. The regression and model evaluation result is shown below.

![59](https://user-images.githubusercontent.com/32251175/161682288-87042b0b-4e68-4e1b-8c7b-0c0600c7769a.PNG)

###### b. Regression Model 2.

The second neural network predictive model is created by applying selected variables from random tree regression model 2, which comprises Age, KM, Engine Size, Gears, Weight and Fuel Cost. This resulted with RMSE of 6348.90. The regression and model evaluation result is shown below.

![60](https://user-images.githubusercontent.com/32251175/161682331-64d93bca-5a00-406d-99fc-63cb3a4f77bc.PNG)

###### c. Regression Model 3.

The third neural network predictive model is created by applying selected variables from random tree regression model 3, which comprises Age, KM and Weight. This resulted with RMSE of 8248.36. The regression and model evaluation result is shown below.

![61](https://user-images.githubusercontent.com/32251175/161682378-45526587-8d04-4c13-b1b7-f090fda9bf6d.PNG)

##### 4. Model Comparison

![62](https://user-images.githubusercontent.com/32251175/161682585-9067de9e-ed04-43c8-b420-267acba49c4c.PNG)

![63](https://user-images.githubusercontent.com/32251175/161682670-ff8ca018-2f50-4008-ad9a-e6b15b83587e.PNG)

The graph above summarizes the results of three regression techniques (multiple linear/random decision tree/neural network) to predict car sales price from Luxury dataset. The accuracy of the predictive models are compared based on their RMSE. In terms of efficiency, the random forest and neural network regression technique is much more efficient compared to the multiple linear regression. From all of the above predictive models, the random forest regression technique model 1. has the lowest RMSE of 6176, however both Random Forest and Neural Network predictive models perform almost identical. Random forest shows that Age, KM and Weight are the most important features in Luxury cars. Moreover, it appears that the results from random forest slightly outperformed the results from neural network models. Consequently, both Random Forest and Neural Network models appears to be more suitable predictive modelling for the Luxury car dataset from Carsales.

![64](https://user-images.githubusercontent.com/32251175/161682723-e356df66-d131-4fa5-a44e-bce69a52169e.PNG)

The graph above illustrates all results of three regression techniques (multiple linear/random decision tree/neural network) to predict car sales price from Luxury Cars, BMW 3 series and Mercedes-Benz E Class. The accuracy of the predictive models are compared based on their RMSE. When we go deep into more specific car makes like BMW 3 series or Mercedes-Benz E class in Luxury Cars, they  performs slightly difference compared to Luxury Cars dataset. Although all three dataset shows that random forest and neural network outperformed from all results from multiple linear, by providing a more lower of RMSE. Neural Network regression model 1 from BMW 3 series appears a little lower RMSE than Random Forest models. However, the random forest technique is slightly better efficient compared to the neural network regression in Mercedes-Benz E Class. Overall, the random forest and neural network technique model appears to be more suitable predictive modelling for all Luxury Cars, BMW 3 series and Mercedes-Benz E Class cars from Carsales.

![65](https://user-images.githubusercontent.com/32251175/161682780-a1c5b4ad-9631-4613-81a7-b157bbfd4959.PNG)

The charts above shows all the feature importance using Random Forest regression, compared with Luxury, BMW 3 series and Mercedes-benz E Class car makes. The luxury cars dataset shows that Age and Weight are the most influential features to predict car sales price, come along with Gears, Fuel Cost and KM. However, BMW 3 series dataset appears that Age and KM are the significant factors contributing to the price more than Weight. It appears that Weight and Gears features are much lower importance compared to luxury cars and Mercedes-Benz E Class. It also shows that the most substantial features of used cars are Age and Weight in Mercedes-Benz E Class, which is similar to Luxury Cars data. However, Engine Size and Gears are the next substantial features for the price in Mercedes-Benz E Class, compared to Gears, Fuel Cost and KM in Luxury Cars. As you can see, KM is not an identical features for Luxury Cars and Mercedes-Benz E Class compared to BMW 3 series. Overall, all Luxury Cars, BMW 3 series and Mercedes-Benz E Class have different car factors vital to the used car prices. 

#### C. Economy Cars

The dataset comprises of 21 attributes related to 3992 Economy Cars which contains 3 car makes (2030 samples from Toyota Corolla, 1016 from Mazda 3 and 946 from Hyundai i30 where extracted from Carsales website). 

##### 1. Multiple Linear Regression

###### a. Regression Model 1.

The first regression model technique predictive model has included all of the attributes in the selected variables identified previously section. This model resulted in a Root Mean Square Error (RMSE) of 2371.50. The regression and model evaluation result is shown below.

![66](https://user-images.githubusercontent.com/32251175/161683820-dc0accc6-51ca-4cad-bafe-a992ab116629.PNG)

###### b. Regression Model 2

The attributes applied for regression model 2. comprises Age, KM, Fuel Capacity, Weight and Fuel Cost. This model resulted in a Root Mean Square Error (RMSE) of 2944.35. The regression and model evaluation result is shown below.

![67](https://user-images.githubusercontent.com/32251175/161683839-9c4e2ec2-360f-4dc8-a727-c1e03ebfe652.PNG)

###### c. Regression Model 3

The attributes applied for regression model 3. comprises Age, KM, Weight and Fuel Cost. This model resulted in a Root Mean Square Error (RMSE) of 3284.61. The regression and model evaluation result is shown below.

![68](https://user-images.githubusercontent.com/32251175/161683855-d0a14a76-b05c-4c0f-8f2e-154d82518061.PNG)

##### 2. Random Forest Regression

As can be seen from the graph, feature Importance for Economy Cars shows that Age and KM are the highest features contributing to the final price followed by Fuel Cost.

![69](https://user-images.githubusercontent.com/32251175/161683865-7fbf2b14-a37c-4202-a0b4-f704b58952ca.PNG)

###### a. Regression Model 1.

The first decision tree predictive model is created by applying all selected variables and resulted with RMSE of 1420.28. The regression and model evaluation result is shown below.

![70](https://user-images.githubusercontent.com/32251175/161684162-7546f348-5622-425f-a21e-1ac3f4e787c8.PNG)

###### b. Regression Model 2

The second decision tree predictive model is created by applying features that have an importance of more than 0.01. There are 9 selected variables of feature importances, which comprises of Age, KM, Fuel Capacity, Weight, Fuel Cost. This resulted with RMSE of 1418.63. The regression and model evaluation result is shown below.

![71](https://user-images.githubusercontent.com/32251175/161684178-28ef8bb1-b640-41ee-a9b6-cc1b91c412ce.PNG)

###### c. Regression Model 3

The third decision tree predictive model is created by applying features that have an importance of more than 0.1. There are 4 selected variables of feature importances, which comprises of Age, KM, Fuel Cost and Weight. This resulted with RMSE of 1421.67. The regression and model evaluation result is shown below.

![72](https://user-images.githubusercontent.com/32251175/161684193-413a41eb-a609-426d-a767-fa85c57a1b17.PNG)

##### 3. Neural Network Regression

###### a. Regression Model 1.

The first neural network predictive model is created by applying all selected variables. This resulted with RMSE of 1582.81. The regression and model evaluation result is shown below.

![73](https://user-images.githubusercontent.com/32251175/161684211-ba752ced-16f8-45f5-b395-de0a40dd15a2.PNG)

###### b. Regression Model 2

The second neural network predictive model is created by applying selected variables from random tree regression model 2, which comprises Age, KM, Fuel Capacity, Weight and Fuel Cost. This resulted with RMSE of 1569.02. The regression and model evaluation result is shown below.

![74](https://user-images.githubusercontent.com/32251175/161684237-e19b1ed7-e13e-4864-a7de-f2357d057e08.PNG)

###### c. Regression Model 3

The third neural network predictive model is created by applying selected variables from random tree regression model 3, which comprises Age, KM, Weight and Fuel Cost. The regression and model evaluation result is shown below.

![75](https://user-images.githubusercontent.com/32251175/161684259-acf1df95-a170-4327-a199-84e2b96072f2.PNG)

##### 4. Model Comparison

![76](https://user-images.githubusercontent.com/32251175/161684284-25221322-629a-4061-947e-8b95181ac42c.PNG)

![77](https://user-images.githubusercontent.com/32251175/161684367-b64633c5-e4e9-41b3-99d8-e454ce46ca0d.PNG)

The graph above summarizes the results of three regression techniques (multiple linear/random decision tree/neural network) to predict car sales price from Economy Cars dataset. The accuracy of the predictive models are compared based on their RMSE. In terms of efficiency, the random forest and neural network regression technique is much more efficient compared to the multiple linear regression. In addition, it appears that the results from random forest a little outperformed the results from neural network models, by providing a more lower of RMSE. From all of the above predictive models, the random forest regression technique model 2. has the lowest RMSE of 1418. Moreover, random forest shows that Age, KM and Fuel Cost are the most important features. Overall, the random forest predictive models appears to be more suitable predictive modelling for the Economy Cars from Carsales.

![78](https://user-images.githubusercontent.com/32251175/161684538-bb4eda03-726c-45fc-8bc7-8f528f2e0adb.PNG)

The graph above describes all results of three regression techniques (multiple linear/random decision tree/neural network) to predict car sales price from Economy Cars, Toyota Corolla and Mazda 3. The accuracy of the predictive models are compared based on their RMSE. When we go deep into more specific car makes like Toyota Corolla or Mazda 3 in Economy Cars, they  perform slightly different compared to Economy Cars dataset.  Although all three dataset shows that random forest and neural network outperformed from all results from multiple linear, by providing a more lower of RMSE. Random Forest in Economy Cars and Toyota Corolla appears lower RMSE than Neural Network models. However, in Mazda, the Neural Network technique performs better efficient compared to the random forest regression. Overall, the random forest model appears to be more suitable predictive modelling for Economy Cars, Toyota Corolla, on the other hand, neural network models is more suitable for Mazda 3. 

![79](https://user-images.githubusercontent.com/32251175/161684557-98e81021-8162-4899-89e6-2ba9f5c459b7.PNG)

The charts above describes all the feature importance using Random Forest regression, compared with Economy Cars, Toyota Corolla and Mazda 3 car makes. All three feature importance shows that the most substantial features contributing to the price are Age and KM. However, KM is more important features in Toyota Corolla (more than 0.2), compared to less than 0.2 in Economy Cars and Mazda 3. It appears that the most substantial features of used cars are Age, KM and Fuel Cost in Economy Cars. On the other hand, Toyota Corolla shows feature importance of Age, KM and Weight. Moreover, Age, KM, Weight and Fuel Cost are substantial features for the price in Mazda 3. Overall, all Economy Cars, Toyota Corolla and Mazda 3 have in common importance factors in Age and KM, but have different other car important factors contributing to the final price of used cars. 

### Part 6 Conclusion

 To summarize, it can be concluded that the performance of predictive modelling techniques and important features depends on car categories and makes. Accordingly, a good practice is to compare the performance of different predictive models to find the best one for the particular case in category and make. There are two approaches with Random Forest and Neural Network, which have the most potential to produce optimal regression models. As can see from the data, most of the used car data are predominantly non-linear relationships in Carsales, so multiple linear is always not suitable because it can only capture linear relationships. Both random forest and neural networks, have the ability to model linear as well as complex nonlinear relationships. An important finding in this research is that no single algorithm works best across all possible scenarios. The performance of predictive models varies depending on the application and dimensionality of the dataset depends on the car categories and individual makes. Moreover, important features contributing to the car prices give a variety according to each car category and makes, for example, feature importance of Luxury Sports - KM and Engine Size against feature importance of Ferrari - Age and KM. Following can be summarized the findings from this research.
 
* Use of real data and modelling categories shows that the same model is not effective for all cars.

* Predictive modelling technique performance depends on the car category and make.

* Important features change according to each car category and make.

However, there is often not enough time to test and optimize every algorithm in order to its quality in a specific criteria such as robustness, cost and time expenditure. For example, a model that performs very well with the data used to create it does not necessarily perform equally well with new data. There may contain some errors and outliers in which at any time and often by chances changes in the relationships can occur. The costs and time required for the build predictive models also can be important criteria to calculated and tested. We can expect to measure those criteria in further research.


