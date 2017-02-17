---
layout: post
title: 2/17/2017
---
# Housing Prices


## Introduction
In project 3 for General Assembly's Data Science Immersive program we were tasked with taking on the role of a consultant for a real estate firm located in Ames, Iowa. Our goal was to build a regression model to predict prices. We also tried to to give some insight into which areas had the highest sales prices and highest sales volume.

## The Data
The dataset set was taken as a subset from Kaggle.com. We selected 19 features from the total 82 feature data set:

      LotArea          int64
      Utilities       object
      Neighborhood    object
      BldgType        object
      HouseStyle      object
      OverallQual      int64
      OverallCond      int64
      YearBuilt        int64
      YearRemodAdd     int64
      RoofStyle       object
      RoofMatl        object
      GrLivArea        int64
      FullBath         int64
      HalfBath         int64
      BedroomAbvGr     int64
      KitchenAbvGr     int64
      MoSold           int64
      YrSold           int64
      SalePrice        int64

## Data Exploration
For the purposes of initial data exploration I was concerned primarily with the target variable 'Sale Price' as well as the features 'Neighborhood' and 'YearBuilt'.

Looking at a histogram of 'Sale Price' we see a positively skewed distribution with a few high priced outliers.

![](../images/Sales_Price_hist.png)

Looking at 'YearBuilt' we see a negatively skewed distribution with a few outlier values representing very old homes. The distribution also shows two peaks around 1960 and a large peak in the mid 2000s.

![](../images/Year_Built_Hist.png)

I wanted to understand the relationship between 'Neighborhood' and 'Sales Price'. Given the large number of unique values in the 'Neighborhood' feature I subset the column on the Top 10 neighborhoods by Sales Volume and Average Sales Price.


![](../images/top_volume_saleprice.png)

* Most high volume neighborhoods showed minimal 'Sale Price' variability and had mean Sale Prices fairly close to the population mean.
* NridgHt was one outlier to this trend with a mean Sale Price over $300K.

![](../images/Top_Price_Sale_Price.png)

* 'NoRidge' has the highest average sale price of any neighborhood.
* Most of the top average sale price neighborhoods did not have a huge amount of variability in sale price. NridgHt and StoneBr were exceptions to this trend showing more variability.


![](../images/Year_Built_Hist.png)

* As with the high volume neighborhoods, the high average sale price neighborhoods showed a large degree of variability in year built.
![](../images/Year_Built_Avg_price.png)
High sales volume neighborhoods showed variability in terms of 'Year Built'. In some neighborhoods such as CollCr, Somerst, Gilbert, and NridgHt nearly all homes sold were built after 2000. Others like OldTown and Edwards had a much larger variance with a much older mean 'YearBuilt'.
