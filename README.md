# Amazon_Vine_Analysis

## Overview

This project analyzes Amazon Vine program and analyzes the Amazon reviews written by members of the paid Amazon Vine program. The goal was to determine if there were any bias towards favorable reviews from Vine members in the dataset, and if having a paid Vine review made a difference in the percentage of 5-start reviews.
The analysis uses PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, load the transformed data into pgAdmin and calculate different metrics.
Various Natural Language Processing(NLP) skills were explored to prepare a customer review analysis for a client interested in digital video games.

## Resources

* Data Source [Amazon Review datasets](https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt)
* Software: Google Colab Notebook, PostgreSQL 11.9, pgAdmin 4, AWS

## Topics Explored

1. Define big data and describe the challenges associated with it.
2. Define Hadoop and name the main elements of its ecosystem.
3. Explain how MapReduce processes data.
4. Define Spark and explain how it processes data.
5. Describe how NLP collects and analyzes text data.
6. Explain how to use AWS Simple Storage Service (S3) and relational databases for basic cloud storage.
7. Complete an analysis of an Amazon customer review.

## Results

For this analysis PySpark was used to perform the ETL process and to connect the data to an AWS RDS instance. After the data was transformed, it was loaded into pgAdmin.
Below is the database "amazondb" created in the AWS RDS.

<img width="1440" alt="RDS DB" src="https://user-images.githubusercontent.com/88418201/145653422-49fb01d8-5bfb-4027-b196-da2e3a006240.png">

The data after being transformed was loaded into the PgAdmin into 4 tables into your database: customers_table, products_table, review_id_table, and vine_table.

<img width="400" alt="query" src="https://user-images.githubusercontent.com/88418201/145655699-ea17b592-d60d-412b-9a46-63f8335ad65b.png">

**1. How many Vine reviews and non-Vine reviews were there?**

The dataset contains 145,431 reviews. Only reviews with 20 or more votes where considered for the rest of the analysis leaving behind 3,342 reviews. Helpful votes were defined as being 50% or greater than the total votes narrowing the list to 1,685 reviews.

Unfortunately, due to the applied criteria, it significantly diminished the sample size. There were no reviews that were paid for the Vine program and there were 1,685 non-Vine reviews.

<img width="1700" alt="1-1" src="https://user-images.githubusercontent.com/88418201/145656285-30490cc8-316f-4b69-a6c7-3342656a2d39.png">

<img width="372" alt="1-2" src="https://user-images.githubusercontent.com/88418201/145656288-f72674d8-226e-4267-bdbe-76a555fc05a5.png">

<img width="372" alt="1-3" src="https://user-images.githubusercontent.com/88418201/145656333-20d3d2f9-1c7f-4d3a-93e4-1bd5b28db5fe.png">

**2. How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?**

As for 5-star unpaid Vine reviews, there were 631 reviews. Since there were 0 paid Vine reviews so attempting to divide by zero, the code would result in a zero division error. Therefore, there are also 0 paid Vine with 5-star reviews.

<img width="638" alt="2-1" src="https://user-images.githubusercontent.com/88418201/145656435-5303553d-be67-4b2f-9819-ef5807509632.png">

<img width="672" alt="2-2" src="https://user-images.githubusercontent.com/88418201/145656436-353fa582-a128-40d0-8253-4046f49dd012.png">

**3. What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?**

The percentage of unpaid 5-star Vine reviews resulted in 37.4%, while the percentage of paid 5-star Vine reviews is 0%.

<img width="1118" alt="3-1" src="https://user-images.githubusercontent.com/88418201/145656524-bb145650-c833-44e0-9fb5-3638dface50d.png">

<img width="812" alt="3-2" src="https://user-images.githubusercontent.com/88418201/145656528-73c8f046-9b69-4952-b775-a2e64417f0bd.png">

## Summary

As the sample size was constricted to a degree that it was impossible to compare paid and unpaid Vine reviews, the analysis is biased towards unpaid Vine reviews. Another indicator is comparing 37% of unpaid 5-star Vine reviews to 0% paid 5-star Vine reviews also shows that the unpaid Vine are biased as well.

The starting criteria of 20 likes or the 50% helpful criteria may have been too high, which made the data set too small. Adjustments to these criteria is a first step to reconsidering using this data set. Additionally we could analyse the statistical distribution (mean, median and mode) of the star rating for the Vine and non-Vine reviews.
