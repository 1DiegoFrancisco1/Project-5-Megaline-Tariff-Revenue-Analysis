# 📞 Project 5 — Megaline Tariff Revenue Analysis

### 🏢 Project Context
You work as a data analyst for the telecommunications operator **Megaline**, which offers two prepaid plans — **Surf** and **Ultimate**.  
The commercial department wants to identify which plan generates higher **average revenue**, so they can optimize **marketing and advertising budgets**.

This project uses data from **500 customers** throughout **2018**, including details about their **calls, messages, internet usage,** and **subscription plans**.  
Your goal is to analyze customer behavior, compute total revenues per user, and use **statistical hypothesis testing** to determine which plan is more profitable.

---

## 📂 Data Overview

The dataset contains **five interconnected tables**:

| Table | Description |
|--------|-------------|
| `users` | User information — `user_id`, name, age, city, plan, subscription and churn dates |
| `calls` | Each user’s call records — `id`, `call_date`, `duration`, `user_id` |
| `messages` | SMS records — `id`, `message_date`, `user_id` |
| `internet` | Web session data — `id`, `mb_used`, `session_date`, `user_id` |
| `plans` | Plan details — `plan_name`, monthly fee, included minutes, messages, and data, plus overage prices |

---

## 💰 Tariff Plans Description

| Feature | Surf | Ultimate |
|----------|-------|-----------|
| Monthly fee | \$20 | \$70 |
| Minutes included | 500 | 3,000 |
| SMS included | 50 | 1,000 |
| Internet included | 15 GB | 30 GB |
| Extra minute | \$0.03 | \$0.01 |
| Extra SMS | \$0.03 | \$0.01 |
| Extra 1 GB | \$10 | \$7 |

**Important business rule:**  
- Call durations are rounded **up to the next minute** per call.  
- Internet usage is rounded **up to the next GB per month** (1 GB = 1024 MB).

---

## 🧹 Step 1 — Data Preparation

- Verified and corrected **data types**, mostly converting date fields to `datetime`.
- Created new calculated columns for billing:
  - `gb_used` → total monthly data rounded to GB.
- Merged multiple sources into a **single DataFrame per user and month**, combining calls, messages, and internet usage.
- Defined **overages**:

---

## 📊 Step 2 — Usage and Consumption Analysis

### 🔸 Calls
- Average call duration varied slightly between tariffs.  
- **Ultimate** users made slightly **longer calls**, while **Surf** users grew in number throughout the year.

### 🔸 SMS
- **Ultimate** users sent **more messages** per month on average with **lower variance**,  
whereas **Surf** users showed more **heterogeneity** and fewer messages overall.

### 🔸 Internet
- Average monthly usage (in GB) was **similar in both plans** (≈17 GB mean),  
but **Surf users** exceeded their limits more frequently and had **more outliers**.
- Since Surf overage costs are higher, this behavior actually **benefits Megaline’s revenue**.

---

## 💵 Step 3 — Revenue Comparison

- **Annual revenue totals:**  
The **Surf plan generated more total income** in 2018 due to its **larger user base**.
- **Average monthly revenue per user:**  
The **Ultimate plan** yielded **higher revenue per subscriber**,  
though **Surf’s rapid customer growth** explains its higher total income.

---

## 📈 Step 4 — Hypothesis Testing

### 🎯 Hypothesis 1
**H₀:** Average monthly revenue from Surf and Ultimate is equal.  
**H₁:** They differ.

- Used an **independent two-sample t-test** assuming unequal variances.
- **p-value ≈ 0.03 < 0.05 → Reject H₀**  
✅ Conclusion: *Average revenue differs — Ultimate users generate higher mean income.*

### 🎯 Hypothesis 2
**H₀:** The average monthly revenue from users in the NY–NJ region equals that of other regions.  
**H₁:** The means differ.

- **p-value ≈ 0.0335 < 0.05 → Reject H₀**  
✅ Conclusion: *The NY–NJ region shows a statistically significant difference in average revenue.*

---

## 🧭 Business Rules and Key Assumptions
- Applied billing logic strictly:
- Each call = 1 full minute minimum.
- Total monthly data rounded **up to GB**.
- These transformations were **essential** to avoid underestimating revenue and reflect real billing processes.

---

## 💡 Step 5 — Key Insights and Recommendations

1. **Focus marketing efforts on the Surf plan.**  
 - Although its base fee is lower, it’s rapidly expanding and contributes more **total revenue**.  
 - Offer **loyalty incentives** (free months, referral bonuses, extra data for retention).

2. **Promote upgrades to Ultimate.**  
 - Target **Surf users** who frequently exceed their limits with personalized **upgrade offers**.

3. **Regional marketing strategy.**  
 - Since **NY–NJ** differs in revenue behavior, consider **localized promotions**  
   (geo-targeted discounts, in-store partnerships, regional ads).

---

## 🧰 Tools and Libraries
- **Python** 🐍  
- **Pandas**, **NumPy**, **Matplotlib**, **Seaborn**  
- **SciPy** for hypothesis testing (`ttest_ind`)

---

## 🧾 Deliverables
- Cleaned and merged multi-source telecom dataset.  
- Comprehensive exploratory analysis of usage patterns.  
- Statistical testing to support data-driven business decisions.  
- Actionable recommendations for marketing and pricing strategies.

---

## 🧠 Summary
From cleaning to hypothesis testing, this project simulated a real data analytics workflow for a telecom company — combining **data engineering**, **exploratory analysis**, and **business reasoning**.  
It demonstrates how even simple usage metrics can drive **marketing strategy**, **revenue optimization**, and **data-driven decision-making**.

---

### 👨‍💻 Author
**Diego Francisco Domínguez Aguilar**  
_Data Science Bootcamp – TripleTen (2025)_  
