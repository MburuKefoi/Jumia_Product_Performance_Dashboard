
# Jumia_Product_Performance
## Project Overview
The following project is about Jumia products where we are analysing data to enable Jumia and its sellers understand how price,promotions and customerfeedback influence product performance

## Project Objectives
To determine whether large discounts are associated with reviews
To understand if higher ratings attracts strong engagements
To determine if price and ratings are correlated
Which are the best performing products
Which products may need different pricing

## Jumia Dataset
Our Jumia dataset had six fields namely;Product,Current Price,Old Price,Discount,Review,Ratings.The data had 116 rows.We enriched our data to include Calculated Discount,Check Prices,Check Ratings and Check Discount.
We then calculated high discount and low rating,high discount and low engagement,many reviews and average rating and strong engagement and excellent rating.


## Data Cleaning
We did some cleaning on our data to enable easier formatting and faster understanding of our data.But even before doing any cleaning we pasted our raw data into a new sheet called Cleaned data and we did make an excel table called 'tblproducts'
Below are some of the cleaning we did in each field.
 - Product - Trimmed the columns product and removed extra spaces.There were also 3 exact duplicates that we removed 
 - Current Price - This field had text as its data types.We removed Ksh,commas and exta spaces and set it to the right currency.For the price range present we did average to find a midpoint.
 - Old Price - Had the same issue as Current Price so we cleaned just as Current Price
 - Discount - Had general as its data type,we then formatted it as a percentage
 - Review - All rows in this field had negative reviews.We figured that must have been data entry error and conerted it to absolute values.Missing reviews were left blank because assuming it as zero would have given
vague results
 - Ratings - Missing rows were also left blank just as reviews.We also removed 'out of 5' and changed our numbers to decimal places 

## Formulas
Used the following formulas to check our discount and ratings
     =IF(OR(ISBLANK[@Rating],[@Rating]<0,[@Rating]>5),"Check Rating","Ok")
     =IF(OR(ISBLANK[@Discount],[@Discount]<0,[@Discount]>5),"Check Rating","Ok")
 To check prices we first had to have a threshhold that we created using this formulae
     =IF(OR([Current Price]>[Old Price]),"Check Prices","Ok")
We then grouped ratings,prices and discount into categories of three
     =QUARTILE.INC(tblproducts[Current Price],1)
     =QUARTILE.INC(tblproducts[Current Price],3)
The above formulas will give you the first quarter of price that will we use as threshhold for low price and the second quarter will give the threshhold for high prices.To get our price category we will reference the above formulas
Having formulae one as PriceQ1 and formulae two as PriceQ3,we catogorise price as follows
     =IF([@Current Price]<Priceq1,"Low Prices",IF([@Current Price<PriceQ3,"Medium Price,High Price))
For ratings and discount categories use the following formulas
     =IF([@Ratings]<3,"Poor",IF([@Ratings]<4,"Average","Excellent"))
     =IF([@Discount]<20%,"Low Discount",IF([@Discount}<40%,"Medium Discount","High Discount"))
We also had different formulas we used to find engagement and performance flags as shown in our workbook 

## Analysis
In our Analysis worksheet,we found;
 - Total Products
 - Average Current Price
 - Average Old Price
 - Average discount
 - Average rating
 - Total review
 - Most expensive price
 - Least expensive price
 - Most expensive product
 - Least expensive product
We checked for correlation between discount versus reviews,rating versus review and current price versus rating.None had a regression coeficient of above 7 so all had very weak correlation.Infact we can say they were not correlated.
The pearson analysis always found the variables to have weak/insignificant relationships.

## Findings
 - A lot of products have ratings as missing
 - Most products have been rated excellent then average then lastly poor
 - Most products had  high discount of above 40%
 - Most highly rated products are products with high prices
 - Products with medium discount received the most reviews of 351, products with high discount received 334 reviews and products with low discount received 38

## Recommendations
 - Give more discount because clearly discount attracts more sales
 - Maintain the good quality,good customer services for the highly rated products
 - We also need to know the kind of reviews our customer gives back to be able to enrich what we know about our data


























