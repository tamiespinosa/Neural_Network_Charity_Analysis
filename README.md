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
  
    - **IS_SUCCESSFUL**—Was the money used effectively

  
  * What variable(s) are considered to be the features for your model?

For our original model we used the following columns as features:  

    - **APPLICATION_TYPE**—Alphabet Soup application type
    
    - **AFFILIATION**—Affiliated sector of industry
    
    - **CLASSIFICATION**—Government organization classification
    
    - **USE_CASE**—Use case for funding
    
    - **ORGANIZATION**—Organization type
    
    - **STATUS**—Active status
    
    - **INCOME_AMT**—Income classification
    
    - **SPECIAL_CONSIDERATIONS**—Special consideration for application
    
    - **ASK_AMT**—Funding amount requested
    
Of those we reduced the number of unique entries by reclassifying some in a 'Other' category for the CLASSIFICATION column and for the APPLICATION_TYPE column.

For the optimized model we indluded the NAME column in addition to the features used for the original model. We reclassified the ASK_AMT and the NAME column. We played with the threshold used to determine the 'Other' category for the CLASSIFICATION column and for the APPLICATION_TYPE to get better accuracy. 
  
  * What variable(s) are neither targets nor features, and should be removed from the input data?
  
  In our original model we removed both the NAME and the EIN, as we considered them to be IDs. 
  
    - **EIN** and **NAME**—Identification columns
  
  In our optimized model we deleted the 'SPECIAL_CONSIDERATIONS_N' column as by having the 'SPECIAL_CONSIDERATIONS_Y' after the 'SPECIAL_CONSIDERATIONS' column was encoded, the data for special considerations is already covered. 
  
  In this model we also deleted the EIN column. When we looked further at the ID assumptions we made in the original model, we saw that some of the names of the organizations had been given a significant amount of grants, therefore making this valuable information to analyze. 
  
  Of the 34,299 data entries there were 19,568 NAME organizations. Of those, 18,776 only received one grant. We binned all those into one category, and then we organized some of the remaining ones based on buckets of number of grants they recived. We did this in order to reduce the 19,568 unique entries for the NAME column, into 13 unique names. We left all the organizations that received more than 400 grants as unique entries. 
  
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
