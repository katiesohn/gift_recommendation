# NYCDSC Capstone Project - Gift Recommendation

## Background
When trying to find the right gift, it can be difficult to have confidence in what we purchase. Outgift aims to solve this problem by making intelligent gift recommendations

## Challenge
Outgift is challenging you to create an algorithm which can recommend products to gifters, taking into account the relationship between gifter and recipient, the recipient's demographics, and their interests.

## Data
- List of Surveys (gift searches)
  - includes gift recommendations
  - includes datetime the Survey was input
- [List of Sales](//github.com/outgift/gift_recommendation/blob/master/sales.csv) (gift purchases)
  - Can be associated with Surveys using gift recommendations and datetime to determine what which gift recommendations were successful
- List of Categories
- List of Gifts
  - Because the gifts available are ever changing, the algorithm must first determine the relationship between a Gift search and categories, and then recommend gifts based on the relationship between Categories and Gifts
- List of weighted associations between Gifts and Categories


