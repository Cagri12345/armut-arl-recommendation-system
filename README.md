# Armut Service Platform - Product Recommendation System

This project aims to develop a service recommendation system for Armut, Turkey’s largest online service platform, using **Association Rule Learning (ARL)** based on user-service interaction history.

---

## 🔍 Project Objective

Analyzes users' past services and discovers relationships between services to recommend new services that users might be interested in.

---

## 📦 Dataset

The dataset contains the service history of users on the Armut platform. Sample data is as follows:

| UserId | ServiceId | CategoryId | CreateDate           |
|--------|-----------|------------|----------------------|
| 25446  | 4         | 5          | 2017-08-06 16:11:00  |
| 22948  | 48        | 5          | 2017-08-06 16:12:00  |
| 10618  | 0         | 8          | 2017-08-06 16:13:00  |
| 7256   | 9         | 4          | 2017-08-06 16:14:00  |
| 25446  | 48        | 5          | 2017-08-06 16:16:00  |

- **UserId**: Unique identifier of the user who received the service  
- **ServiceId**: Unique identifier of the service received  
- **CategoryId**: Category identifier of the service  
- **CreateDate**: Date and time when the service was received  

---

## 🧠 Methodology

This project treats the services users receive within the same month as a “basket” and applies the **Apriori algorithm** to find frequently co-occurring services and their association rules.  
Based on the derived rules, it recommends services that users might be interested in.

---

## 🛠 Libraries Used

- `pandas`  
- `mlxtend.frequent_patterns` (Apriori and association_rules)  

---

## 🚀 Functions

### `arl_recommender(rules_df, product_id, rec_count=1)`

Given a service ID (e.g., `"2_0"`), returns the top `rec_count` recommendations based on association rules.

**Parameters:**  
- `rules_df`: DataFrame output from association_rules  
- `product_id`: Service ID for which recommendations are requested  
- `rec_count`: Number of recommendations to return (default is 1)

**Returns:**  
- List of recommended service IDs

---

## 📊 Example Usage

```python
# Recommend 1 service for a user who took service '2_0'
arl_recommender(rules, "2_0", rec_count=1)
