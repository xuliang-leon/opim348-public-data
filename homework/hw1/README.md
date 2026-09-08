# Homework 1 data

Data files for OPIM348 Homework 1.

## Files

| File | Analysis | Contents |
| --- | --- | --- |
| `Candy Bars_Clustering.csv` | K-means clustering | 37 candy bars with calories, fat, protein, and carbohydrates |
| `fiesta-gifts-transactions.xlsx` | Supplier ABC analysis | 104,033 purchase transactions with supplier, SKU, quantity, price, and distribution fields |
| `Gym_KNN.csv` | KNN classification | 1,000 historical gym attendees with enrollment outcomes |
| `GymForecast_KNN.csv` | KNN prediction | 23 new attendees without observed enrollment outcomes |

## Direct data URLs

Use these URLs with pandas in a local notebook or Google Colab:

```python
import pandas as pd

base_url = "https://raw.githubusercontent.com/xuliang-leon/opim348-public-data/main/homework/hw1"

candy = pd.read_csv(f"{base_url}/Candy%20Bars_Clustering.csv")
fiesta = pd.read_excel(f"{base_url}/fiesta-gifts-transactions.xlsx")
gym = pd.read_csv(f"{base_url}/Gym_KNN.csv")
gym_forecast = pd.read_csv(f"{base_url}/GymForecast_KNN.csv")
```

The Fiesta Gifts workbook is also used in Week 2. Its copy in this folder keeps the Homework 1 data together in one stable location.
