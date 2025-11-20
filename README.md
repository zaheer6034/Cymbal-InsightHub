# 🚀 Cymbal Superstore Customer Segmentation (RFM + K-Means)

This project delivers an end-to-end customer segmentation workflow built in **BigQuery Studio**, using the **RFM (Recency, Frequency, Monetary)** framework and **K-Means clustering** to help identify actionable customer groups for targeted marketing at the Cymbal Superstore.

---

## 🎯 Project Objective

Identify, categorize, and analyze customer segments based on purchasing behavior, and outline practical marketing actions for each group.

---

## 🛠️ Methodology & Tools

### Environment
All work was completed in a **Colab Enterprise Notebook** running inside **BigQuery Studio**.

### Data Preparation (RFM)

A base table, `ecommerce.customer_stats`, was created using SQL in BigQuery from the public `thelook_ecommerce` dataset.

| Metric     | SQL Field                 | Description                                      |
|------------|---------------------------|--------------------------------------------------|
| Recency    | `days_since_last_order`   | Days since the customer’s most recent order     |
| Frequency  | `count_orders`            | Total number of orders placed                   |
| Monetary   | `average_spend`           | Average amount spent per order                  |

### Modeling & Analysis

- **BigQuery DataFrames (bigframes.pandas)**  
  RFM data was loaded directly into BigQuery DataFrames, enabling Python analysis without exporting data.

- **K-Means Clustering**  
  A K-Means model (`bigframes.ml.cluster.KMeans`) was trained with **k = 5** on the RFM features.

- **Visualization**  
  A scatterplot of `days_since_last_order` vs. `average_spend` (colored by cluster) was generated to verify cluster separation.

### Insight Summaries

Cluster centroids were used to generate:
- A segment title  
- A persona-style description  
- A recommended next marketing step  

---

## 📊 Customer Segments

| Cluster | Segment Name                  | Key RFM Traits                                           | Suggested Action                                                        |
|---------|--------------------------------|-----------------------------------------------------------|-------------------------------------------------------------------------|
| **1**   | The Lapsed Loyalists           | High recency, moderate frequency and spend               | Send personalized re-engagement incentives                              |
| **2**   | The Occasional Treaters        | High recency, low frequency, high spend                  | Promote premium items and limited-time bundles                          |
| **3**   | The One-and-Done Buyers        | Very high recency, low frequency, low spend              | Follow-up surveys + personalized product suggestions                    |
| **4**   | The Big Spenders               | High recency, low frequency, very high average spend     | Create a VIP program with exclusive benefits                            |
| **5**   | The Price-Conscious Shoppers   | Moderate recency, high frequency, low spend              | Highlight competitive pricing and value-focused offers                  |

---

## ⚙️ How to Run the Project

### Requirements
A Google Cloud project with:
- **BigQuery** enabled  
- **Vertex AI** enabled  
- IAM roles:
  - BigQuery Data Editor  
  - BigQuery Job User  
  - Vertex AI User  

