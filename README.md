# OPIM348 public classroom data

Public data files used by the OPIM348 Supply Chain Analytics Colab exercises.

## Homework

- [`homework/hw1`](homework/hw1) contains the four datasets used in Homework 1: candy-bar clustering, Fiesta Gifts supplier ABC analysis, gym-enrollment KNN modeling, and gym forecast scoring. The folder README provides direct raw-file URLs for Python and Colab.

## Week 2

- `week02/fiesta-gifts-transactions.xlsx` contains 104,033 Fiesta Gifts transaction records and 20 fields covering purchase dates, invoices, SKUs, item types, quantities, prices, customers, suppliers, distribution centres, and transport distances. It supports the Week 2 pandas exercises in inspection, filtering, aggregation, joining, and visualization.

## Week 3

- `week03/hm_ladieswear_articles_sample.csv` contains 2,000 H&M Ladieswear product records with product names, product and garment groups, visual attributes, colours, descriptions, image filenames, observed sales-week bounds, and observed units. `article_id` is stored as a zero-padded 10-digit key so it joins directly to the embedding and weekly-sales files.
- `week03/hm_ladieswear_dinov2_768_embeddings.csv` contains 2,000 H&M Ladieswear product IDs, image filenames, and 768 instructor-computed DINOv2 image-embedding values.
- `week03/hm_ladieswear_dinov2_product_weekly_sales.csv` contains weekly aggregate units for the embedded products with recorded transactions.

The visual clusters in the course notebook are constructed from image embeddings only. Sales are joined afterward to evaluate descriptive associations with total observed product sales.

### Week 3 source and limitations

The files are derived for classroom use from the [H&M Personalized Fashion Recommendations](https://www.kaggle.com/competitions/h-and-m-personalized-fashion-recommendations/data) competition data. Use is subject to the competition rules.

Recorded transactions do not reveal complete inventory, availability, stockouts, promotion, or verified product launch dates. The classroom analysis must not interpret cluster-level sales differences as causal effects of visual style.

## Week 7

- [`week07/sales_store_729.csv`](week07/sales_store_729.csv) contains daily sales records for store 729 across multiple items.
- [`week07/sales_store_729_item.csv`](week07/sales_store_729_item.csv) contains the daily records for item 2004092 used in the forecasting and replenishment lecture.

These files record sales rather than uncensored customer demand. A stockout may hide demand that could not be fulfilled.
