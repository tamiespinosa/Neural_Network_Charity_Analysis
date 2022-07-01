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
 
  The first thing to tackle was the amount of epochs, the number of neurons and the functions used. We played around with those numbers. In the original data set the neurons were kept at 3 for one layer and 2 for the second one. We achieved a faily good accuracy with this model. 

 
 While optimizing one of the first desicions made was to follow the rule of thumb of of having at least 2 to 3 times the number of neurons as the number of inputs. We did this by setting up the neurons in the first layer as an equation. We then halfed the number of neurons assigned to the following layers.  We saw improvement in the model performance but only marginal improvement. It could be argued that although there was some improvement, it was not enough to justify the increase in parameters and memory consumed by the model. Yet since we were going for a certain accuracy, we decided to keep this set up for the final model.  
  
  The second desicion was to increase the number of hidden layers from 2 to 3. We again made marginal improvements to the model accuracy doing so. 
  
  The activation frunction we picked for our original model was relu for both hidden layers and then sigmoid for the output function. We picked this because relu having infinite numbers as output, we thought could learn the model faster. The sigmoid was picked because the output has a binary option, yes or no. 
  
  In the optimization design we found that introducing leaky-relu and liner functions tended to decrease the performance of the model. We then tested the tanh in all hidden layers and saw the first performance of all the combination of functions we had tried up to that point. 
  
  
  * Were you able to achieve the target model performance?
  
  We ultimately did achieve more than 75% accuracy. Reference the code and model to see the final numbers [[3]](#3)[[4]](#4).
  
  * What steps did you take to try and increase model performance?
 
 In the process of trying to increase the accuracy of the model, we went through several iterations and modifications of the code. After a few, we started keeping a log of the changes to see if it increased or decreased accuracy[[6]](#6). 
 
One of the first desicions was in regard to number of neurons, the second with regard to number of layers and the third in regards to optimization functions. We already described this desicion making process. 

The fourth desicion was to play with the count threshold set for the CLASSIFICATION column and for the APPLICATION_TYPE column to be categorized as 'Other'. 

Although these changes made minor progress towards improving the accuracy, they were not sufficient. 

We then went to doing a value count of the ASK_AMT and binning the values in it. This proved to improve the model, but only marginally. 

One thing that was noticed is the SPECIAL_CONSIDERATIONS_Y and SPECIAL_CONSIDERATIONS_N columns beasically have duplicate information from when the column was encoded, as one has 1s for yes and 0S for no, and the other one has the opposite. One of those columns is suffiecient to include all the information. Yet when we deleted the SPECIAL_CONSIDERATIONS_N column, the accuracy had a slight decrease. Ultimately we decided to delete to make the model more truthful.

The last desicion made was to not delete the EIN and NAME column and do a value count on them. The EIN column had one entry per EIN number, therefore it is a proper ID or index. This column needed to be deleted. Conversely the name showed that some organizations hard several grants given to them, therefore having some valuable information. We then proceeded to make different categories for the organizations that had less that 400 grants given to them. Of all the steps in the desicion making process this one prooved to be the one that game the most improvement to the model. We finally achieved over 75%. With more time I would've played with this category a little more to see if assigning more bins or less bins would make the model more or less accurate.  
 

## <a name="Summary"></a> Summary

  

## <a name="Resources"></a>Resources

<a name="1">[1]</a> [Original Alphabet Soup Charity Code](https://github.com/tamiespinosa/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity.ipynb)

<a name="2">[2]</a> [Original Alphabet Soup Model](https://github.com/tamiespinosa/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity.h5)

<a name="3">[3]</a> [Optimized Alphabet Soup Charity Code](https://github.com/tamiespinosa/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity_Optimzation.ipynb)

<a name="4">[4]</a> [Optimized Alphabet Soup Model](https://github.com/tamiespinosa/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity_Optimization.h5)


<a name="5">[5]</a> [Data Source](https://github.com/tamiespinosa/Neural_Network_Charity_Analysis/blob/main/Resources/charity_data.csv)

<a name="6">[6]</a> [Result Tracker](https://github.com/tamiespinosa/Neural_Network_Charity_Analysis/blob/main/Resources/Result_Tracker.xlsx)

[7] https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax
