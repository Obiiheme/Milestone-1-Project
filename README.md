# \# Milestone 1: Business Analytics Project-Ready Dataset

# 

# \## 📌 Project Context

# This project is part of a larger Business Analytics initiative focused on \*\*Retail Pricing Optimization\*\*.  

# The goal is to create a \*\*project-ready dataset\*\* that can be used for demand modeling, elasticity estimation, and price optimization.

# 

# This work follows from the \*\*Business Requirements Document (BRD)\*\* prepared earlier in the course.

# 

# ---

# 

# \## 📊 Data Sources

# \- \*\*Primary Dataset:\*\* Retail Price Optimization dataset (Suddharshan S., Kaggle, 2023).  

# &nbsp; Includes product IDs, categories, historical prices, units sold, freight charges, and promotional indicators.  

# \- \*\*Supplementary Dataset:\*\* Synthetic data created for `brand` and `category\_level2` attributes.  

# &nbsp; Provides richer metadata for downstream analysis and feature engineering.

# 

# ---

# 

# \## ⚙️ Data Preparation Steps

# 

# \### 1. Data Cleaning

# \- Removed duplicate records.  

# \- Handled missing values using:

# &nbsp; - \*\*Median imputation\*\* for numeric variables.  

# &nbsp; - \*\*Mode substitution\*\* for categorical variables.  

# \- Standardized formats (currency, date).  

# \- Converted inconsistent numeric fields with `pd.to\_numeric`.  

# 

# \### 2. Supplementary Data Creation

# \- Created a synthetic metadata file (`brand`, `category\_level2`) joined on `product\_id`.  

# \- Ensured referential integrity for merging.  

# \- This step improves interpretability and enriches feature engineering.

# 

# \### 3. Data Transformation

# \- \*\*Feature Engineering:\*\*  

# &nbsp; - `revenue = unit\_price × qty`  

# &nbsp; - `price\_gap = unit\_price – competitor\_price`  

# &nbsp; - `is\_discounted` flag from promotion indicator  

# &nbsp; - `avg\_weight\_per\_unit`, `price\_per\_gram`  

# \- \*\*Seasonality Variables:\*\*  

# &nbsp; - Extracted `month`, `quarter`, `is\_holiday\_season` (Nov/Dec).  

# \- \*\*Scaling/Normalization:\*\*  

# &nbsp; - Min–max scaling applied to `unit\_price` and `qty`.  

# \- \*\*Elasticity Variables:\*\*  

# &nbsp; - `log\_price` and `log\_qty` to support econometric elasticity modeling.

# 

# \### 4. Encoding (applied after EDA)

# \- One-hot encoding of categorical variables: `brand`, `category\_level2`.  

# \- Produces ML-ready dataset with ~50 engineered features.

# 

# ---

# 

# \## 📂 Dataset Versions

# Two dataset versions are explicitly maintained:

# 1\. \*\*EDA-friendly dataset\*\*  

# &nbsp;  - Retains categorical columns (not encoded).  

# &nbsp;  - Best for exploratory plots and descriptive statistics.  

# 

# 2\. \*\*ML-ready dataset\*\*  

# &nbsp;  - Includes scaling, log transforms, and one-hot encoding.  

# &nbsp;  - Ready for econometric models and ML pipelines.  

# 

# Both versions are exported as CSV and Parquet formats for flexibility.

# 

# ---

# 

# \## 📈 Exploratory Data Analysis (EDA)

# Key insights observed:

# \- \*\*Price distribution\*\* shows wide variance; elasticity visible in scatterplot.  

# \- \*\*Promotions\*\* create sharp short-term demand spikes.  

# \- \*\*Revenue analysis by brand\*\* and \*\*price gap by category\*\* provide insights into competitive positioning.  

# 

# Plots are saved in `/notebook\_plots`.

# 

# ---

# 

# \## ✅ Dataset Readiness

# \- \*\*EDA dataset:\*\* ~48,500 rows × 30 features.  

# \- \*\*ML-ready dataset:\*\* ~48,500 rows × 50 features (after encoding \& transformations).  

# \- Stored in `/data/processed`.  

# \- Supplementary files stored in `/supplementary`.  

# 

# ---

# 

# \## 📂 Repository Structure

# 

# The project repository is organized as follows:

# 

# ```

# Milestone-1-Project/

# │

# ├── archive\_contents/              ← Original raw dataset

# │   └── retail\_price.csv

# │

# ├── data/

# │   └── processed/                 ← Cleaned and transformed datasets

# │       ├── retail\_pricing\_EDA.csv

# │       └── retail\_pricing\_ML.csv

# │

# ├── supplementary/                 ← Supplementary metadata files

# │   ├── competitor\_prices.csv

# │   ├── product\_info.csv

# │   └── promotions.csv

# │

# ├── notebook\_plots/                ← Visualizations generated during EDA

# │

# ├── notebooks/

# │   └── Milestone1\_project.ipynb   ← End-to-end data preparation notebook

# │

# ├── milestone\_1\_Project Assignment.pptx

# │   

# │

# ├── README.md                      ← Project documentation

# └── requirements.txt               ← Python dependencies (if needed)

# ```

# 

# ---

# 

# \## 🔒 Ethics \& Bias Considerations

# \- Dataset reflects retail sales but excludes customer demographics.  

# \- Pricing models risk \*\*unfair pricing\*\* if optimized without ethical guardrails.  

# \- Safeguard: recommendations should balance profitability with customer value.

# 

# ---

# 

# \## 📚 References

# \- Suddharshan, S., 2023. \*Retail Price Optimization Dataset\*. Kaggle. Available at: <https://www.kaggle.com/datasets/suddharshan/retail-price-optimization> \[Accessed 23 September 2025].  

# \- Shmueli, G., Bruce, P.C., Gedeck, P. and Patel, N.R., 2020. \*Data mining for business analytics\*. Hoboken, NJ: Wiley.  

# \- Nagle, T.T. and Müller, G., 2018. \*The strategy and tactics of pricing\*. 6th ed. New York: Routledge.  

# \- Kotler, P., Keller, K.L. and Chernev, A., 2022. \*Marketing management\*. 16th ed. Harlow: Pearson.  

# \- Phillips, R., 2021. \*Pricing and revenue optimization\*. Stanford, CA: Stanford University Press.  

# \- Doan, A., Halevy, A.Y. and Ives, Z.G., 2012. \*Principles of data integration\*. Amsterdam: Elsevier.  

# \- Batini, C. and Scannapieco, M., 2016. \*Data and information quality: Dimensions, principles and techniques\*. Cham: Springer.  

# \- Jordon, J. et al., 2024. \*Synthetic data survey\*. London: The Royal Society.  

# \- Bauer, A. et al., 2024. \*Comprehensive exploration of synthetic data generation: A survey\*. arXiv preprint arXiv:2401.02524.  

# \- IBM Institute for Business Value, 2020. \*Pricing in a digital world\*. Armonk, NY: IBM.  

# \- PwC, 2022. \*The power of pricing: Unlocking growth through analytics\*. London: PricewaterhouseCoopers.  

# \- McKinsey \& Company, 2021. \*The future of pricing\*. McKinsey Insights.  



