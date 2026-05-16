# 🔍 Customer Funnel & Subscription Analysis | Python EDA

> End-to-end exploratory data analysis across 5 datasets covering customer activity, demographics, subscriptions, and orders — with a full conversion funnel, stage-wise drop-off rates, and average transition days between funnel stages.

---

## 🛠️ Tools & Technologies

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=flat)
![Plotly](https://img.shields.io/badge/Plotly-3F4F75?style=flat&logo=plotly&logoColor=white)

---

## 🎯 Objective

To analyse a customer journey dataset spanning 478 customers and understand:
- **Where do customers drop off** in the conversion funnel?
- **How long does it take** to transition from one stage to the next?
- Which cities and age groups represent the most customers?
- Which subscription plans generate the most revenue?

---

## 📁 Dataset Overview

The project uses **5 separate CSV datasets**, joined and analysed together:

| Dataset | Rows | Columns | Description |
|---------|------|---------|-------------|
| `cust_activity.csv` | 7,500 | 3 | Customer activity log: Browse, Sign_Up, Add_to_Cart, Checkout, Review, Return/Refund |
| `cust_bio.csv` | 478 | 3 | Customer demographics: City, Age |
| `cust_sub.csv` | 51 | 3 | Subscription purchases: Plan, Purchase Date |
| `sp.csv` | 6 | 5 | Subscription plan master: Plan name, Price, Duration |
| `orders.csv` | 127 | 4 | Order data: Amount, Payment mode |

**Key stats:**
- 478 unique customers across 5 Indian cities
- 7,500 total activity records
- 51 subscribers (Silver / Gold / Diamond plans)
- 127 completed orders

**Cities:** Chennai, Delhi, Kolkata, Noida, Mumbai  
**Age range:** 20–37 years (mean: 28.7)  
**Subscription Plans:** Silver (₹720–₹1,200), Gold (₹1,440–₹2,400), Diamond (₹2,880–₹4,800)

---

## 🔍 Analysis Performed

### Part 1 — Preliminary EDA
- Null value and duplicate checks across all 5 datasets (✅ zero nulls, zero duplicates)
- Customer count by city (bar chart)
- Age-range distribution using binning — `pd.cut()` (pie chart)
- Activity frequency count across all funnel stages (bar chart)
- Month-wise total order amount via merge + groupby (line chart)
- Subscription plan–wise revenue using merge on Plan_Var_ID (bar chart)

### Part 2 — Funnel Analysis
- Full 6-stage conversion funnel with stage counts and % conversion
- Pivot table to find each customer's earliest date at each funnel stage
- Date-diff calculation between consecutive funnel stages per customer
- Average transition days between each funnel stage

---

## 📊 Key Insights

### Conversion Funnel

| Funnel Stage | Customers | % Conversion from Previous Stage |
|---|---|---|
| Browse | 681 | — (top of funnel) |
| Sign_Up | 478 | **70.19%** |
| Add_to_Cart | 287 | **60.04%** |
| Checkout | 127 | **44.25%** |
| Review | 40 | **31.50%** |
| Return/Refund | 20 | **15.75%** |

> ⚠️ **Biggest drop-off: Add_to_Cart → Checkout (44.25%)** — only 127 of 287 customers who added items actually checked out. This is the highest-priority stage to optimise.

### Avg. Days to Transition Between Stages

| Stage Transition | Avg. Days |
|---|---|
| Sign_Up → Browse | 2.52 days |
| Browse → Add_to_Cart | 0.86 days |
| **Add_to_Cart → Checkout** | **14.43 days** ← longest gap |
| Checkout → Review | 2.63 days |
| Checkout → Return/Refund | 3.40 days |

> 💡 The **14.4-day gap** between Add_to_Cart and Checkout suggests customers are sitting on pending carts. A cart-abandonment email nudge could significantly improve checkout conversion.

### Revenue by Subscription Plan
| Plan | Revenue |
|---|---|
| Diamond (1 Year) | ₹28,800 |
| Diamond (6 Months) | ₹25,920 |
| Gold (1 Year) | ₹24,000 |
| Silver (1 Year) | ₹16,800 |
| Gold (6 Months) | ₹7,200 |
| Silver (6 Months) | ₹5,040 |

### City-wise Customer Distribution
Chennai leads with 109 customers, followed by Delhi (106), Kolkata (94), Noida (92), Mumbai (77).

---

## 📸 Output Screenshots
<img width="1897" height="909" alt="Funnel_chart" src="https://github.com/user-attachments/assets/d848c8e7-68fb-453d-8cf0-24279fb1d5e1" />

<img width="1907" height="903" alt="City_bar_chart" src="https://github.com/user-attachments/assets/7ccc7143-70c2-446a-80d7-be638378c043" />

<img width="1903" height="906" alt="Age_Range_pie_chart" src="https://github.com/user-attachments/assets/6f77a00a-8f68-44f6-b4cf-7f4f48685c6c" />

<img width="1897" height="912" alt="Activity_bar_chart" src="https://github.com/user-attachments/assets/8270db2f-b6cb-4957-9ffc-803951c66399" />

<img width="1897" height="913" alt="Order_month_line_chart" src="https://github.com/user-attachments/assets/20b8bca2-a2ad-4a60-aefa-b161dae22359" />

<img width="1899" height="913" alt="Plan_var_id_bar_chart" src="https://github.com/user-attachments/assets/5980502d-e7ef-46c1-a252-4b14e2fafee3" />

<img width="1903" height="909" alt="Funnel table with conversion % and avg transition days" src="https://github.com/user-attachments/assets/b68cb1eb-0458-440d-b171-5f8a58c68514" />

---

## 🚀 How to Run

### 1. Clone the repository
```bash
git clone https://github.com/abhishekjain2004/customer-funnel-analysis.git
cd customer-funnel-analysis
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the notebook
```bash
jupyter notebook Funnel_Analysis_Project.ipynb
```

> ⚠️ Make sure all 5 CSV files (`cust_activity.csv`, `cust_bio.csv`, `cust_sub.csv`, `sp.csv`, `orders.csv`) are in the **same folder** as the notebook before running.

---

## 📂 Project Structure

```
customer-funnel-analysis/
├── Funnel_Analysis_Project.ipynb   ← Main analysis notebook
├── cust_activity.csv               ← Customer activity log (7,500 rows)
├── cust_bio.csv                    ← Customer demographics (478 rows)
├── cust_sub.csv                    ← Subscription data (51 rows)
├── sp.csv                          ← Subscription plan master (6 rows)
├── orders.csv                      ← Orders data (127 rows)
├── requirements.txt                ← Python dependencies
├── images/
│   ├── funnel_chart.png
│   └── city_distribution.png
└── README.md
```

---

## 📦 Requirements

Create a `requirements.txt` file with the following:

```
pandas
numpy
seaborn
matplotlib
plotly
jupyter
```

---

## 💡 What I Learned

- Merging and joining multiple real-world datasets using `pd.merge()`
- Using `pd.pivot_table()` to reshape activity data into per-customer funnel stages
- Calculating date differences between funnel stages using `.dt.days`
- Building interactive funnel charts with `plotly.express.funnel()`
- Binning continuous age data into categories with `pd.cut()`
- Identifying cart abandonment patterns through transition-time analysis

---

## 🙋 About Me

Made by **[Abhishek Jain](https://github.com/abhishekjain2004)**  
Aspiring Data Analyst | PG in Data Science & Analytics with Gen AI @ Imarticus Learning  
📧 abhishek2004.jain@gmail.com · [LinkedIn]www.linkedin.com/in/abhishek-jain-297014277
