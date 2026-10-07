# 🛒 E-Commerce Retail Data Analytics & Machine Learning Portfolio

## 📖 Overview
This project presents an **integrated Data Science and Business Intelligence (DS-BI) framework** for performing large-scale e-commerce sales analytics and predictive modeling. Built around real-world transnational transaction datasets—such as the formidable **UCI Online Retail II dataset spanning over 1 million transactions**—it demonstrates how online retailers can uncover product performance, regional demand, customer purchasing behaviors, and future revenue streams *without requiring expensive enterprise infrastructure*.

Through comprehensive automation, SQL-based data aggregation, and advanced machine learning modeling, this framework bridges the gap between raw unstructured transaction logs and actionable business insights.

---

## ⚡ Core Modules & Capabilities

### 1️⃣ High-Performance Ingestion & Feature Engineering
When dealing with hundreds of thousands of rows, traditional approaches hit Memory constraints. This framework optimizes ingestion and processing:
- **In-Memory SQL Processing:** Primarily utilizing embedded in-process OLAP database querying (such as DuckDB or SQLite) to run zero-copy SQL transformations directly within host process memory. This paradigm achieves exceptional speed (e.g., average query speeds of 11.46 ms on over 800,000 clean records).
- **Data Hygiene Integration:** Cleans raw transactional logs by filtering out missing customer identifiers, negative pricing/quantities, and cancellations (e.g., invoices with a 'C' prefix).
- **Feature Engineering:** Computes derived financial features like line-item revenue (`Quantity × Unit Price`), time-elapsed recencies, and extracts intelligent chronological vectors (months, days, hours, cyclic sine/cosine variables) to power time-series forecasting.

### 2️⃣ Sales Analytics: Products, Regions & Temporal Trends
Interactive Visualizations are designed for executive dashboards to provide real-time strategic intelligence:
- **Top Sellers Identification:** Identifies leading revenue-generating inventory items (such as the REGENCY CAKESTAND 3 TIER and WHITE HANGING HEART T-LIGHT HOLDER).
- **Geographic Distribution:** Evaluates market concentration, highlighting primary domestic markets (e.g., the United Kingdom contributing ~79% of total revenue) alongside secondary European wholesale channels.
- **Peak Trading Profiles:** Maps critical surges, such as the massive Q4 Holiday Season (pre-Christmas) surges (£100K–£250K/week above baseline) and intra-day purchasing spikes (peaking between 10:00 and 13:00 hours on Thursdays and Fridays). 

### 3️⃣ Customer Segmentation & Market Basket Mining
- **RFM Scoring:** Categorizes buyers strictly via Recency, Frequency, and Monetary metrics. It reveals fundamental business statistics, such as "Champions" (22.2% of customers) generating ~68% of total revenue (£12M of £17.7M) in perfect accordance with the Pareto principle.
- **K-Means VIP Clustering:** We algorithmically standardize behavioral features to segment users. Achieving a Silhouette Score of 0.9164 at K=2 cleanly separates high-value B2B wholesale accounts (the VIP "Whales") from ordinary retail shoppers.
- **Cross-Selling (Association Rules):** Applies the Apriori algorithm to discover high-lift product bundles—such as `STRAWBERRY CERAMIC TRINKET BOX ↔ SWEETHEART CERAMIC TRINKET BOX` (Lift = 13.95).

### 4️⃣ Predictive Modeling & Revenue Forecasting
Using historical vectors (Jan-Oct) to forecast the future behavior of clients (Nov-Dec target labels):
- **Revenue Modeling:** Compares Linear and Polynomial Regression baselines against powerful Gradient Boosting Regressors (R² = 0.6982 / advanced predictability) to forecast numerical customer spend by capturing non-linear interactions natively.
- **Churn & Return Prediction:** Trains Logistic Regression and Random Forest classifiers (up to AUC-ROC = 1.0000 on deep profiles) to flag dormant accounts preemptively (Recency accounts for ~82% of feature importance). Furthermore, it theoretically uses multimodal ensembles (AutoGluon/ELECTRA) on textual product descriptions to classify return likelihood and underlying causes.
- **Time-Series Demand Forecasting:** Combines additive seasonal decomposition (STL) with autoregressive pipelines (ARIMA) and holiday indicator variables to accurately predict when massive inventory stockups will be demanded by the consumer base.

---

## 🛠️ Technology Stack
* **Language:** Python
* **Data Ingestion & SQL:**  SQLite (In-Process)
* **Data Manipulation:** Pandas, NumPy
* **Data Visualization:** Matplotlib, Seaborn
* **Machine Learning:** Scikit-Learn (KMeans, Linear/Logistic Regression, Polynomial Features, Random Forest), AutoGluon

---

## 🚀 How to Run
1. Ensure the `online_retail.csv` file is downloaded and placed in the primary directory.
2. Ensure you have installed the required dependencies from the Python ecosystem:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn sqlite3
   ```
3. Execute the `Amazon_Flipkart_Data_Analysis_Portfolio.ipynb` Jupyter Notebook sequentially. 

## 🎯 Conclusion
This pipeline successfully demonstrates how to ingest massive e-commerce datasets, clean severe anomalies, extract real-world business intelligence visualization dashboards, segment VIP customers through strict clustering, and scientifically forecast future revenue metrics for optimal supply-chain and marketing management.
