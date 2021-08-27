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

We noticed the sqft_living feature (Squarefootage of the homes) has the highest correlation to our Target
  
# Exploring Price Data
  Let's first look at the full price data in a Boxplot.<br>
  <img src="Images/Full_PriceBoxPlot.png" align="center"><br>
  This is no-good. Let's remove outliers.
  <img src="Images/No_Outliers_BoxPlot.png" align="center"><br>
  A lot of the data falls from about $70,000 to about $1,200,000
