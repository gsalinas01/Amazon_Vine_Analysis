# Amazon_Vine_Analysis
## Overview
In this project, I conducted a meta-analysis on reviews from the Amazon Vine Program. This challenge allowed me to learn about AWS's RDBs and S3 buckets and helped me understand the ETL process in a hands-on manner. 
The main goal of this analysis was to determine the level of bias, if any, between paid amazon reviews and unpaid amazon reviews in the Vine Program.

The analysis was drawn from a dataset of videogame reviews: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Video_Games_v1_00.tsv.gz

Technologies used: PySpark, Google Colab

## Process
After creating a Spark session in Google Colab, the Amazon videogame review data was loaded into a Spark DataFrame and subsequently cleaned and organized into a table as follows:
<img width="938" alt="Screen Shot 2021-11-08 at 11 24 47 PM" src="https://user-images.githubusercontent.com/60943801/140867476-230df054-2bff-4f2c-806c-622e151c7535.png">

This Dataframe was then filtered out for rows in which the total vote count was greater than or equal to 20 in order to avoid division by zero issues later. 

<img width="683" alt="Screen Shot 2021-11-08 at 11 27 33 PM" src="https://user-images.githubusercontent.com/60943801/140867691-dad72208-c9b1-453c-975e-b9cc391f5475.png">

Then, I created a new DataFrame to retrieve all the rows where the number of helpful votes divided by the number of total votes was equal to or greater than 50%.
This was done to create a cleaner dataset and establish a line of consistency. 

<img width="1095" alt="Screen Shot 2021-11-08 at 11 33 33 PM" src="https://user-images.githubusercontent.com/60943801/140868278-b9dd5014-7aab-4865-b73e-ab1609fec317.png">


The last step was to create a dataframe for paid and unpaid reviews

<img width="988" alt="Screen Shot 2021-11-08 at 11 33 26 PM" src="https://user-images.githubusercontent.com/60943801/140868267-350a4e99-a054-4a85-96e7-7022bad18d69.png">

## Results
The results of the analysis are as follows:
  * There were a total of 94 paid vine reviews for the videogame products in this dataframe and 40,471 unpaid reviews.
  * Of the 94 paid vine reviews, 48 were 5-star reviews. Of the 40,471 unpaid reviews, 15,663 were 5-star reviews.
  * 51% of paid vine reviews were 5-star reviews. 39% of unpaid reviews were 5-star reviews. 
 <img width="910" alt="Screen Shot 2021-11-08 at 11 35 07 PM" src="https://user-images.githubusercontent.com/60943801/140868823-ab1be3d7-af67-42b5-9982-e9128402725c.png">


## Summary
There seems to be bias with the paid vine reviews for this category of products. 51% of paid reviews had a 5-star rating, while only 39% of unpaid reviews had a 5-star rating. The small number of total paid vine reviews compared to the number of unpaid vine reviews yields a problem when comparing both dataframes, however due to the large volume of unpaid reviews, I am inclined to believe it's a more reliable source of analysis. To further analyze this data, we could normalize the data so as to have more similar total counts and compare the number of 5-star reviews then.
