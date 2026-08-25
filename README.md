# OPIM348 public classroom data

Public data files used by the OPIM348 Supply Chain Analytics Colab exercises.

## Week 3

- `week03/hm_ladieswear_dinov2_768_embeddings.csv` contains 2,000 H&M Ladieswear product IDs, image filenames, and 768 instructor-computed DINOv2 image-embedding values.
- `week03/hm_ladieswear_dinov2_product_weekly_sales.csv` contains weekly aggregate units for the embedded products with recorded transactions.

The visual clusters in the course notebook are constructed from image embeddings only. Sales are joined afterward to evaluate descriptive associations with total observed product sales.

## Source and limitations

The files are derived for classroom use from the [H&M Personalized Fashion Recommendations](https://www.kaggle.com/competitions/h-and-m-personalized-fashion-recommendations/data) competition data. Use is subject to the competition rules.

Recorded transactions do not reveal complete inventory, availability, stockouts, promotion, or verified product launch dates. The classroom analysis must not interpret cluster-level sales differences as causal effects of visual style.
