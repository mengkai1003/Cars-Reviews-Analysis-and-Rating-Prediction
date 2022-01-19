## Cars Review Analysis and Rating Prediction 

The goal of this project was to determine the factors that car consumers care about most during the purchase process, the importance level of those factors and how they affect the overall rating of the car. Since we know that the car buying/selling market in the US is very big and important, and that the choice of getting one car over the other is not an easy one, we thought that this problem was worth solving, not only for the car buyers, but also for the manufacturers and dealerships. The insights driven from this project would help them understand what factors determine the customer decision and will provide them a centralized summary of these aspects. Furthermore, the project aimed to build a Rating Prediction System based on these factors and achieve a reliable performance in predicting the overall rating of a car.

We started by collecting the necessary data. There are many car review’s websites on the internet but one of the most complete and trustworthy is www.edmunds.com. We scraped a total of 27,647 car reviews from different models, years and manufacturers. Each observation consisted of the car type, make, model, year, an overall 5 star rating (outcome variable), a text review/verbatim and 7 car aspect 5 star rating including Safety, Technology, Performance, Interior, Comfort, Reliability and Value. After initial inspection of the dataset, we carried out some data cleaning and processing procedures, that included excluding the really long reviews (over 400 words of length), filtering out reviews that were not in english and removing duplicated reviews. The reason behind the first step is that we found that the majority of the reviews that were too long, were most of the times irrelevant, containing personal anecdotes and no objective review of the car. Since we considered that the amount of reviews was already sufficient and for the sake of simplicity and irrelevancy, we decided to exclude this subset of reviews. Thus we ended with 18,449 observations (a 33% size reduction) which we consider to be a reasonably good size.

CODE SCRIPTS

- 00 Web Scraping Edmunds.ipynb:
  - Script to collect the data from the website www.edmunds.com 
  - Data includes type, make, model, year of the car, as well as review (text), overall rating and aspects ratings

- 01 Data Processing & Cleaning.ipynb
  - Script to read in and clean the raw data scraped from Edmunds

- 02 Criteria Extraction.ipynb
  - Script extract the criteria/aspects from the text reviews 
    
    i) TF-IDF with K-Means Clustering method                                                                         
    ii) LDA analysis method

- 03 Classifiers.ipynb
  - Script to read in the manually labelled data and train classifications models to produce the aspects loadings for the whole dataset
  - Produces as output a dataset with aspect loadings for every text review that was scraped

- 04 Regression.ipynb
  - Script that takes as input the output of classifiers and fits regression models to predict the 5-star rating of the car based on the review

- 05 Evaluation.ipynb
  - Script that evaluates different regression models with different settings in terms of accuracy, precision, recall and f1 measure
  - Includes statistical significance testing for each of the models evaluated

DATASETS

- 01 initial_train_data_full_version.csv
  - Csv file containing the raw data that was scraped from www.edmunds.com. Csv file contains the columns type, make, model, year of the car, as well as total 5 star rating, the text review and the aspects 5 star rating

- 02 data_cleaned.csv
  - Csv file containing the output of the Data Processing & Cleaning script. From the original 22k rows, this csv file contains the 'cleaned' 18k rows

- 03 manual_labelling_data.xlsx
  - Excel file containing the 1000 rows sampled from the original data and the 9 discovered aspects with their manually labeled aspect loadings.

- 04 classifier_output_latest.csv
  - Csv file containing the output of the classification of the discovered outputs and the original dataset from edmunds. It is a sort of a 'full' dataset containing the original columns and the added columns from the classification. It is used for Regression and Models Evaluation
