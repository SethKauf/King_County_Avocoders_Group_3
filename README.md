# King County Real Estate
<img src="https://user-images.githubusercontent.com/69225974/131020990-42c7f78c-b675-4899-8e90-541128a70a3e.png" alt="alt text" width="1000" height="450"><br>
<sup>Image courtesy of [iStock](https://www.istockphoto.com/photos/king-county-washington-state)<sub>

# Overview
We looked at the information on homes sold in King County, WA between May 2014 and May 2015 to create a predictive pricing model. <br>

## Business Problem
### A real estate company in Seattle, WA is listing homes on their website.
  They want to develop a model that will give a good ball-park estimate of the house's price before listing.<br>
  Using the information we have from the King County database, what would be an accurate predictor of pricing for these homes?

## Selecting the Target, determining our methods
  * Because the model's goal is to predict price, that will be the target
  * We will use simple linear regression to test multiple linear models

## First we looked at a Heatmap for correlations between Price and all features
<img src="Images/Heatmap.png" align="center"><br>

We noticed the Living Space feature (Squarefootage of the homes) has the highest correlation to our Target, followed by Grade.
  
# Exploring Price Data
  Let's first look at the full price data in a Boxplot.<br>
  <img src="Images/Full_PriceBoxPlot2.png"><br>
  This is no-good. Let's remove outliers.
  <img src="Images/No_Outliers_BoxPlot.png"><br>
  A lot of the data falls from about $70,000 to about $1,200,000, we will stratify our data on this parameter.

# Exploring Living Space data  
  The highest correlated feature was living space.<br>
  Our first model tested directly tested this onto Price, but it had nearly no effect.<br>
  
# Exploring Grade variable
  
  Grade is a feature that helped us better stratify the housing prices in our dataset.<br>
  
  They have a clear upward trend as seen below.<br>
  
  <img src="Images/1price_vs_grade.png"><br>
  
  We then tested it with the similar train-test-split model from Living Space.<br>
  
  Unfortunately, it also did not return anything substantial.<br>

# First Model, Target ~ Two Highest
  We created an OLS model using the top two features.<br>
  Although the r <sup>2</sup> is still low, it's already a little better.<br>
  
# Feature Engineering
  ## Grade
  For Grade, we created dummy variables as numeric stand-ins, so we can add Grade to our upcoming model.<br>
  This will also split Grade into multiple columns for each grade.<br>
  
  ## Zip Code
  We grouped the zip codes together and used their average price per zip code in place of the zip code itself. This gave us our first useful feature.<br>
  
# Second Model, train_test_split on first few features.<br>
  
  We ran our train_test_split on several features, notably Living Space, Waterfront, Zip Code, and Grades.<br>
  
  It returned an r <sup>2</sup> of about 60.9, which is better, but its validation test was weak.<br>
  
  We are on the right track.<br>
  
# Final Model
  First, we stratified price to select houses at $1,200,000 and below, as mentioned earlier.<br>
  
  We kept some of our previously engineered features such as Zip Code means and the Grade columns.<br>
  
  We also dropped a lot more columns. The final used columns are:<br>
    * Living Space<br>
    * Grade (4-13)<br>
    * Zip Code mean<br>
    * Waterfront property<br>
 
  It returned an 80% effective model with a validation score of 80%.<br>
  
  Below is a graph of the actual prices transposed on the predicted prices.<br>
  
  <img src=![image](https://user-images.githubusercontent.com/69225974/131071162-84f43159-e0a7-41d1-a975-990f246302e9.png)>
