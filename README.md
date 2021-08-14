# Overview of the Project

Our client, SellBuy, has requested an analysis of Amazon review data.  The purpose of the analysis is to investigate and understand the benefits of the [Amazon Vine program](https://www.amazon.com/gp/vine/help).  The Vine program, administered through Amazon, allows companies to provide complementary products to Amazon customers.  In exchange for the product, the customer agrees to share honest feedback with Amazon customers by posting a review of new products.

In order to allow analyzation of the data, an ETL (Extract, Transform, Load) script was developed.  The project utilizes PySpark and PostgreSQL.  Various datasets were made available.  For the purposes of this analysis, the dataset for pet product was selected given SellBuy’s pet-focused offerings.  The dataset was extracted into a DataFrame.  The data was then transformed into various tables removing null and duplicate values.  Finally, the data was loaded into the database.


# Results

Once in the database, additional data wrangling was performed to meet the requirements of the project.  As requested, the reviews were filtered to only include those with at least 20 votes, at least half of which were helpful votes.  

Those were then split into reviews that were part of the Vine program and those that were not.  Finally, the 5-star reviews from both categories were captured.

## Vine vs. non-Vine reviews

Of the reviews with 20 or more votes, at least half of which were helpful:
* 170 were from the Vine program
* 37,840 were not from the Vine program

Of those that were 5-star reviews:
* 65 were from the Vine program (38% of the filtered Vine reviews)
* 20,612 were not from the Vine program (54% of the filtered non-Vine reviews)

Of the filtered 5-star reviews:
* 0.3% were from the Vine program
* 99.7% were not from the Vine program

See the appendix at the end of this summary for descriptive statistics from the appropriate DataFrames.

# Summary

It does not appear there is a positivity bias among Vine reviews.  Among the filtered reviews, a higher proportion of non-Vine reviews are 5-star than Vine reviews.

Based upon this quantitate analysis on this particular dataset, it does not appear that reviews in the Vine program provide a significant value.

The scripts developed for this analysis could be repurposed to analyze other product categories to see if this holds true or if other patterns emerge.

Additional investigation could be performed to see if there are other benefits to the Vine program.  Perhaps analyzing the helpful vote counts might reflect, for example, that Vine reviews are higher quality and thus help new products gain more momentum.  Also, analyzing all reviews (not just those with 20 or more votes, at least half of which were helpful), might provide additional insight to potential value from the Vine program.

Additionally, a more qualitative analysis could be performed.  Using Natural Language Processing (NLP), we could compare the quality of Vine vs. non-Vine reviews to see if there may appear to be more value to reviews from the Vine program.  However, the hypothesis is that any benefit would likely be marginal given that difference in votes seen above would not seem to indicate a significantly higher level of quality for Vine reviews.


# Appendix

## Number of Vine reviews after filtering for 20+ votes, >= 50% helpful

![Filtered_vine_reviews](https://user-images.githubusercontent.com/82730954/129459551-5f1c6197-af78-4f8f-964a-29ba3b1c5436.PNG)

## Number of non-Vine reviews after filtering for 20+ votes, >=50% helpful

![Filtered_nonvine_reviews](https://user-images.githubusercontent.com/82730954/129459556-fb29437b-5dc3-4dee-b49c-4cb432f03c35.PNG)

## Number of filtered Vine reviews that were 5-star reviews

![5_star_vine_reviews](https://user-images.githubusercontent.com/82730954/129459563-017d2bbf-4575-445f-bcd7-be353becfe9a.PNG)

## Number of filtered non-Vine reviews that were 5-star reviews

![5_star_nonvine_reviews](https://user-images.githubusercontent.com/82730954/129459566-93d438b3-9538-47af-b6af-6c240c423210.PNG)
