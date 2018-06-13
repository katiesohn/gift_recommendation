# NYCDSC Capstone Project - Gift Recommendation

## Background

When trying to find the right gift, it can be difficult to have confidence in what we purchase. Outgift aims to solve this problem by making intelligent gift recommendations

## Challenge

Outgift is challenging you to create an algorithm which can recommend products to gifters, taking into account the relationship between gifter and recipient, the recipient's demographics, and their interests.

# Caveat

The data associating gift searches (surveys) and sales is not great, but we think it can be inferred by matching the Sale datetime and product with a Survey's datetime and product recommendations (the thinking goes if there was only one survey that recommended that product in a reasonable time window before the sale, we can assume the sale and survey match).

## Data

- [category_types.csv](//github.com/outgift/gift_recommendation/blob/master/data/category_types.csv) - Types of gift categories
  - `id` - Category Type id (unique identifier)
  - `name` - name of Category Type
  - `parent_id` - Parent Category Type id (foreign key)
- [categories.csv](//github.com/outgift/gift_recommendation/blob/master/data/categories.csv) - Gift categories
  - `id` - Category id (unique identifier)
  - `value` - description of Category
- [categories\_\_category_types.csv](//github.com/outgift/gift_recommendation/blob/master/data/categories__category_types.csv) - Associations between gift categories and gift category types (many-to-many relationship)
  - `category_type_id` - Category Type id (foreign key)
  - `category_id` - Category id (foreign key)
- [gifts.csv](//github.com/outgift/gift_recommendation/blob/master/data/gifts.csv) - List of Gifts
  - Because the gifts available are ever changing, the algorithm must determine the relationship between Surveys and Categories, then recommend gifts based on the relationship between those Categories and Gifts.
  - `id` - Gift id (unique identifier)
  - `name` - name of Gift
  - `brand_id` - Brand id (foreign key)
  - `retailer_id` - Retailer id (foreign key)
  - `feature_description` - Short description of product
  - `detailed_description` - Longer description of product (even longer description may be yielded from visiting product_link)
  - `product_link` - URL detailing product
  - `affiliate_link` - URL to purchase product from
  - `min_age` - Minimum age of recipient the product should be recommended to
  - `max_age` - Maximum age of recipient the product should be recommended to
  - `male` - Product is suitable for men
  - `female` - Product is suitable for women
  - `picture` - URL of image of product
  - `detail_picture` - URL of alternative image of product
  - `min_price` - Minimum price product is sold for
  - `max_price` - Maximum price product is sold for
- [brands.csv](//github.com/outgift/gift_recommendation/blob/master/data/brands.csv) - List of Brands, brands of products for gifts
  - `id` - Brand id (foreign key)
  - `name` - Name of brand
- [retailers.csv](//github.com/outgift/gift_recommendation/blob/master/data/retailers.csv) - List of Retailers, websites that sell the gifts
  - `id` - Brand id (foreign key)
  - `name` - Name of retailer
- [gifts\_\_categories.csv](//github.com/outgift/gift_recommendation/blob/master/data/gifts__categories.csv) - List of weighted associations between Gifts and Categories
  - `category_id` - Category id (foreign key)
  - `gift_id` - Gift id (foreign key)
  - `value` - Weighting, the higher the number the more application the category to the gift
- [sales.csv](//github.com/outgift/gift_recommendation/blob/master/data/sales.csv) - List of Sales (gift purchases)
  - Some affiliate sales are indirect, meaning the product was not recommended by Outgift so as will not found in `gifts.csv`.
    - `Retailer` - name of Retailer where sale was made (may determine foreign key)
    - `Product Name` - name of Gift (may determine foreign key)
    - `Date and time` - date and time of sale, may be used to match to surveys
    - `Indirect Sales` - whether sale was made from URL we sent the gifter to purchase from, may indicate whether the product is in `gifts.csv`
- [recipients.csv](//github.com/outgift/gift_recommendation/blob/master/data/recipients.csv) - List of Recipients, person who the gift is intended for
  - `id` - Recipient id (unique identifier)
  - `category_id` - Category id, the type will be "Relationship" (foreign key)
  - `gender` - Gender of recipient
  - `min_age` - Minimum of age range recipient is in
  - `max_age` - Maximum of age range recipient is in
- [surveys.csv](//github.com/outgift/gift_recommendation/blob/master/data/surveys.csv) - List of Surveys (gift searches)
  - `id` - Gift id (unique identifier)
  - `category_id` - Category id, the type will be "Occasion" (foreign key)
  - `date` - date and time of sale, may be used to match to surveys
  - `recipient_id`- Recipient id (foreign key)
  - `min_budget` - The minimum price the gifter wants to spend
  - `max_budget` - The maximum price the gifter wants to spend
- [surveys\_\_gifts.csv](//github.com/outgift/gift_recommendation/blob/master/data/surveys__gifts.csv) Associations between Surveys and Gifts (gift search results) (many-to-many relationship)
  - `survey_id` - Survey id (foreign key)
  - `gift_id` - Gift id (foreign key)
