# NYCDSC Capstone Project - Gift Recommendation

## Background

When trying to find the right gift, it can be difficult to have confidence in what we purchase. Outgift aims to solve this problem by making intelligent gift recommendations

## Challenge

Outgift is challenging you to create an algorithm which can recommend products to gifters, taking into account the relationship between gifter and recipient, the recipient's demographics, and their interests.

## Data

- [List of Categories Types](//github.com/outgift/gift_recommendation/blob/master/data/category_types.csv)
- [List of Categories](//github.com/outgift/gift_recommendation/blob/master/data/categories.csv)
- [Associations between Categories and Category Types](//github.com/outgift/gift_recommendation/blob/master/data/categories__category_types.csv)
- [List of Gifts](//github.com/outgift/gift_recommendation/blob/master/data/gifts.csv)
  - Because the gifts available are ever changing, the algorithm must first determine the relationship between a Surveys and Categories, and then recommend gifts based on the relationship between those Categories and Gifts
- [List of weighted associations between Gifts and Categories](//github.com/outgift/gift_recommendation/blob/master/data/gifts__categories.csv)
- [List of Surveys (gift searches)](//github.com/outgift/gift_recommendation/blob/master/data/surveys.csv)
- [Associations between Surveys and Gifts (gift search results)](//github.com/outgift/gift_recommendation/blob/master/data/surveys__gifts.csv)
- [List of Sales (gift purchases)](//github.com/outgift/gift_recommendation/blob/master/data/sales.csv)
  - Possibly can be associated by matching the Sale datetime and product with a Survey's datetime and gift recommendations (if there was only one survey that recommended that product in a reasonable time window before the sale, we can infer a positive correlation between that gift search and that gift)
