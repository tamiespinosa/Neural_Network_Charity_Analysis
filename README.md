# Neural_Network_Charity_Analysis

## Table of Contents
- [Overview of Project](#OverviewProject)
- [Results](#Results)
  * [Data Processing](#DataProcessing)
  * [Compiling, Training and Evaluating the Model](#Compiling)
- [Summary](#Summary)
- [Resources](#Resources)

## <a name="OverviewProject"></a>Overview of Project

Alphabet Soup, a fictional company that funds different charities, has data of  grants they have given in the past to different charities [[5]](#5). They would like to be able to predict which charities will use their grants successfully in the future. For this project we will use neural networks to build the needed model. Our first model we used predicted the success of the test data with around 72% accuracy [[1]](#1)[[2]](#2). Since we were looking for 75% accuracy or higher, we optimized the model to improve its accuracy [[3]](#3)[[4]](#4). 

## <a name="Results"></a>Results

### <a name="DataProcessing"></a>Data Processing

  * What variable(s) are considered the target(s) for your model?
  
  The column "IS_SUCCESSFUL" was considered to be the target for our model. A value of 1 is assumed to mean the grant was used successfully and a value of 0 is assumed to have not. 
  
  * What variable(s) are considered to be the features for your model?
  
  
  * What variable(s) are neither targets nor features, and should be removed from the input data?
  
  In our original model we removed both the NAME and the EIN, as we considered them to be IDs. Yet, as we looked into the data further we saw that some of the names of the organizations had been given a significant amount of grants, therefore making this valuable information to analyze. 
  
  Of the 34,299 data entries there were 19,568 organizations. Of those, 18,776 only received one grant. We binned all those into one category, and then we organized some of the remaining ones based on buckets of number of grants they recived. We did this in order to reduce the 19,568 unique entries for the NAME column, into 13 unique names. We left all the organizations that received more than 400 grants as unique entries. 
  
### <a name="Compiling"></a>Compiling, Training and Evaluating the Model

  * How many neurons, layers, and activation functions did you select for your neural network model, and why?
  * Were you able to achieve the target model performance?
  * What steps did you take to try and increase model performance?

## <a name="Summary"></a> Summary

  

## <a name="Resources"></a>Resources

<a name="1">[1]</a> [Original Alphabet Soup Charity Code](https://github.com/tamiespinosa/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity.ipynb)

<a name="2">[2]</a> [Original Alphabet Soup Model](https://github.com/tamiespinosa/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity.h5)

<a name="3">[3]</a> [Optimized Alphabet Soup Charity Code](https://github.com/tamiespinosa/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity_Optimzation.ipynb)

<a name="4">[4]</a> [Optimized Alphabet Soup Model](https://github.com/tamiespinosa/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity_Optimization.h5)


<a name="5">[5]</a> [Data Source](https://github.com/tamiespinosa/Neural_Network_Charity_Analysis/blob/main/Resources/charity_data.csv)

[6] https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax
