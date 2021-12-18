# Amazon_Vine_Analysis

## Overview
The purpose of this analysis was to Utilize PySpark determine if there was any bias in reviews for wireless products from the US Reviews Dataset in AWS (https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Wireless_v1_00.tsv.gz).  An analysis was performed using PySpark to make and filter dataframes from the US Reviews Dataset for information on paid and unpaid vine reviews.  Results of the analysis revealed that there does not appear to be any postivity bias towards paid vine reviews versus unpaid vine reviews.

## Results
Pyspark was used to import the reviews dataset and create a dataframe based on inferred schema.  The dataframe contained data on various aspects of Wireless products, custmer information, product information, and different variables on review information.  This dataframe contained all of the data from the US Reviews Dataset in AWS on Wireless products.
![image](https://user-images.githubusercontent.com/88444529/146654879-0447abb4-8c16-4f52-9f91-23e1631c1cea.png)
  - The dataframe was filtered to only contain information on reviews including the variables "review_id", "star_rating", "helpful_votes", "total_votes", "vine", and "verified_purchase".  
  - ![image](https://user-images.githubusercontent.com/88444529/146654930-121c349d-e9ca-4215-9237-8af62a87df33.png)
  - The dataframe was then filtered to only contain reviews that had more than 20 votes for the "total_votes" variable.  This ensured that reviews being analyzed had an appropriate sample size and would avoid bias and skew of the data.
  - ![image](https://user-images.githubusercontent.com/88444529/146654951-f8d0ac5b-1bb9-46b9-a794-1d67717e3fb5.png)
  - The dataframe was then filtered to find only the reviews that had greater than 50% "helpful_votes" compared to "total_votes".  This resulted in a dataframe with only reviews that had greater than 50% of helpful votes.
  - ![image](https://user-images.githubusercontent.com/88444529/146655010-4d4d2dfa-a54c-4951-a1bd-7a31403d6ef2.png)
  - Additional filters were put on the previous dataframe to make a dataframe with only paid vine and non-paid vine reviews.
  - ![image](https://user-images.githubusercontent.com/88444529/146655052-7625046e-211b-4f4b-9f1a-d2eb17381393.png)
  - ![image](https://user-images.githubusercontent.com/88444529/146655062-09b28a2c-dab1-453f-b207-b3165e171401.png)
  - Variables were genereated to calculate the number of total reviews in both the paid and nonpaid vine review dataframes.  The paid vine review count was 585 while the unpaid vine review count was 61139.  The number of five star reviews were then determined by filtering each of the paid and unpaid dataframes and performing a count.  The number of five star reviews in the unpaid vine review dataframe was 28839 while the number of five star reviews from the paid vine review dataframe was 213.  Finally, the percent of both paid and unpaid vine reviews of five star reviews compared to the total review count.  The percent of five star reviews in the unpaid vine reviews was 47.17 percent while the percent of five star reviews in the paid vine reviews was 36.41 percent.  

## Summary
Analysis of the Wireless products reviews dataset from the US Reviews Dataset in AWS revealed that there is positivity bias towards wireless products in the unpaid vine reviews.  The percent of five star reviews in the unpaid vine reviews was 47.17 percent while the percent of five star reviews in the paid vine reviews was only 36.31 percent.  This suggests that reviews are more positive in the unpaid vine reviews than the paid vine reviews.  The sample size was much larger for the unpaid vine reviews with 61139 total reviews while the paid vine reviews had a total of only 585.  It is unclear from our current analysis if this had any effect on the data.  It could be a good idea to run additional analysis involving sample and population level data.  Additional analysis should be performed using t-tests to compare the samples.
