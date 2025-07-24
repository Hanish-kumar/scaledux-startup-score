# Startup Health Scoring Model – ScaleDux AI Internship Task

This project simulates a **Startup Evaluation Engine** that calculates a **composite health score** (out of 100) for fictional startups based on core business indicators — similar to a credit score. It was developed as part of the Artificial Intelligence Intern assignment by **ScaleDux Software Innovation Pvt. Ltd.**

---

## Objective

To evaluate the potential of 100 fictional startups by designing a custom scoring model using features such as:

- Team experience
- Market size
- Monthly active users
- Burn rate
- Funds raised
- Valuation

The goal is to identify top and bottom performers and provide meaningful business insights using Python, data analysis, and visualization techniques.

---

## Dataset Description

The dataset (`Startup_Scoring_Dataset.csv`) contains the following columns:

| Column                     | Description |
|---------------------------|-------------|
| `startup_id`              | Unique ID of each startup |
| `team_experience`         | Avg years of relevant team experience (scale 1–10) |
| `market_size_million_usd`| Total addressable market in million USD |
| `monthly_active_users`    | Monthly active users |
| `monthly_burn_rate_inr`   | Avg monthly expenses (INR) |
| `funds_raised_inr`        | Total funding raised (INR) |
| `valuation_inr`           | Current company valuation (INR) |

---

## Methodology

### 🔹 1. Data Preprocessing

- **Min-Max Normalization** was applied to all numeric features (scaled to [0, 1]).
- **Burn rate** was **inverted** post-normalization since a lower burn is more desirable.

### 🔹 2. Feature Weighting

Each feature was assigned a custom weight based on real-world startup evaluation logic:

| Feature                    | Weight (%) | Reasoning |
|---------------------------|------------|-----------|
| `monthly_active_users`    | 30%        | Most important — reflects traction and user engagement. |
| `market_size_million_usd`| 20%        | Larger TAM = greater growth potential. |
| `team_experience`         | 15%        | Strong teams build strong products. |
| `valuation_inr`           | 15%        | Market confidence proxy. |
| `funds_raised_inr`        | 10%        | Indicates past investor support. |
| `monthly_burn_rate_inr`   | 10%        | Penalized if too high (inverted). |

Final Score = Weighted Sum × 100

### 🔹 3. Ranking

- All startups were ranked based on their score.
- The **Top 10** and **Bottom 10** performers were identified and analyzed.

---

## Visualizations

- **Bar Chart**: Scores of all startups sorted by rank.
- **Heatmap**: Correlation between input features.
- **Histogram**: Distribution of final scores.

---

## Key Insights

- The **highest scoring startup** had a strong combination of high active users, large market size, and experienced team.
- The **lowest scoring startup** suffered from low traction, minimal market, and high burn rate.
- Burn rate showed **negative correlation** with overall scores — supporting its inversion.

---


## Tools Used

- Python (Pandas, NumPy, Seaborn, Matplotlib, scikit-learn)
- Jupyter Notebook (Google Colab)
- GitHub (for sharing)

---

## Future Improvements

- Apply regression or clustering models to validate scoring weights.
- Add time-series or trend data if available.
- Deploy as a scoring API using Flask/Streamlit for real-time evaluation.
