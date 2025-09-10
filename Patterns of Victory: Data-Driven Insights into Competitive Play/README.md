# Patterns of Victory: Data-Driven Insights into Competitive Play

Competitive gaming is defined by precision, strategy, and decision-making under pressure. This project explores **Counter-Strike: Global Offensive (CS:GO)** match data, specifically sourced from **ESEA competitive matches** — a third-party platform widely regarded as one of the highest levels of competitive play outside of professional tournaments. ESEA matches are typically played by the top few percent of the global player base, making this dataset an excellent lens for understanding how elite-level players approach maps, positioning, and tactics that lead to victory.

---

## 📝 Project Overview & Objective

The primary goal of this project is to determine what factors most influence **winning a round** in CS:GO at the high-competitive level. By analyzing player performance, map-specific trends, and situational dynamics, the project seeks to answer:

> Which elements of gameplay — such as map, timing, positioning, economy, and strategy — contribute the most to securing round victories?

**Key factors studied include:**

- **Map & Round Context:** Map type, round number, and round type (pistol, eco, buy, etc.).
- **Kill Data:** Timing of kills, weapon used, weapon type, attacker/victim positions.
- **Player/Team State:** Number of Terrorists vs. Counter-Terrorists alive, team economy value, and utility.
- **Bomb Status:** Whether the bomb is planted, site of plant, and bomb-timer pressure.
- **Outcome Data:** Which team ultimately secured the round.

By combining these features, the analysis highlights the drivers of victory in elite-level matches and demonstrates how data can capture patterns in tactical decision-making.

---

## ⚙️ Tools & Technologies

- **Python:** Core programming language  
- **Pandas / NumPy:** Data wrangling and cleaning  
- **Matplotlib / Seaborn:** Data visualization  
- **Scikit-learn:** Machine learning models  
- **Excel:** Initial data exploration and formatting  
- **Jupyter / Colab Notebook:** Interactive analysis and documentation   

---

## 📊 Data Cleaning & Preparation

The dataset consisted of **~2 million rows** of competitive CS:GO (ESEA) match events. Preparing such a large dataset for analysis required several structured steps:

- **Large-Scale Data Handling:** Processed millions of rows efficiently within memory constraints (~8GB RAM).  
- **Feature Selection & Standardization:** Filtered only relevant features for round outcomes, including:  
  - Match metadata (map, round number, round type, economy value)  
  - Player-level events (attacker/victim IDs, weapons, positions, alive counts)  
  - Objective-based events (bomb plant/defuse status, site location)  
- **Coordinate Transformation:** Designed a **vectorized coordinate conversion system** to map raw in-game world coordinates into radar map coordinates.  
  - Ensured accurate scaling across multiple maps (Dust2, Mirage, Inferno, etc.)  
  - Aligned kills and positions with CS:GO radar images for visualization  
- **Data Quality Improvements:** Addressed missing or inconsistent entries, normalized side labels (Terrorist vs. Counter-Terrorist), and ensured round-winner labels were reliable.

---

## 🔎 Exploratory Data Analysis (EDA)

The EDA phase focused on uncovering baseline game dynamics and identifying factors influencing round outcomes.

- **Win Rate Analysis:**  
  - Computed per-map win rates by side (Terrorist vs. Counter-Terrorist)  
  - Example: Dust2 is slightly T-sided (~53.6% T win rate), while Nuke strongly favors CTs (~55.6% CT win rate)  

- **Round Outcome Insights:**  
  - **Balanced maps:** Mirage displayed near parity between CT/T  
  - **Side-biased maps:** Train and Nuke heavily CT-sided, suggesting defensive strength  

- **Kill Distribution Trends:**  
  - Early-round aggression often shifts momentum but doesn’t guarantee victory  
  - Mid-round and late-round kills near choke points and bomb sites were more decisive  

- **Weapon Usage Patterns:**  
  - Rifles (AK-47, M4A1-S/M4A4) dominated kills in winning rounds  
  - Pistols and SMGs were more common in eco/force-buy rounds but correlated with lower win rates

---

## 🎨 Visualizations

Visualizations brought structure to the data, making patterns more tangible and strategic insights clearer.

- **Heatmaps of Kill Locations:**  
  - Created radar heatmaps of attacker kill positions across maps  
  - Results revealed hot zones (e.g., Dust2 mid doors, Mirage A ramp, Inferno banana), confirming that strategic choke points and bomb sites dominate round outcomes  
  - These zones correlate with high-level professional strategies around map control  

- **Win Rate Bar Charts:**  
  - Side-by-side bar charts comparing CT vs. T win rates per map  
  - Showed clear visual distinctions in balance (e.g., Mirage near-equal vs. Nuke heavily CT-favored)  

- **Temporal Analysis Plots:**  
  - Kill density plotted by round timer revealed “pressure points” where decisive engagements often occurred (early rushes vs. late executes)

---

## 🤖 Machine Learning Component

To move beyond descriptive insights, predictive modeling was applied to estimate **round outcomes** based on available features.

- **Objective:** Predict whether Terrorists or Counter-Terrorists would win a round  
- **Features Used:** Map, side, economy value, alive players, bomb status, weapon type, and positional data  
- **Models Implemented:**  
  - Logistic Regression (baseline classifier)  
  - Random Forest (non-linear, interpretable model)  

- **Feature Importance Analysis:**  
  - Economy value, number of players alive per side, and bomb status emerged as top predictors  
  - Positional data (map hot zones) contributed meaningfully, aligning with heatmap insights  

- **Performance:**  
  - Baseline models demonstrated reasonable predictive accuracy, proving that round outcomes are learnable from in-game features

---

## 📈 Key Insights / Analysis

- **Strategic Hotspots Define Engagements:**  
  - Players already know where the strongest positions are on each map to maximize kill potential  
  - Heatmaps confirmed hotspots such as window when holding B site on Dust2, or choke points on Nuke  
  - These locations consistently correlate with higher kill rates and round control  

- **Map-Specific Side Advantages:**  
  - **CT-favored maps:** Nuke (~55.6% CT win rate) and Train (~53% CT win rate)  
  - **T-favored maps:** Dust2 (~53.6% T win rate) and Inferno (~52.4% T win rate)  
  - **Balanced maps:** Mirage remains nearly even  

- **Round Timing Matters:**  
  - Decisive kills often occur mid-to-late round  
  - Early-round aggression can build momentum but does not always translate into consistent wins  

- **Weapon Dynamics:**  
  - Rifles dominate winning rounds due to power and versatility  
  - Pistols and SMGs appear frequently in eco or force-buy situations but correspond with lower win probabilities  

- **Economy as a Strong Predictor:**  
  - Team economy strongly affects round outcomes, influencing weapon, armor, and utility effectiveness  

- **Player Count is the Strongest Indicator:**  
  - Both ML models highlighted player count (man advantage) as the most reliable predictor of round success  

---

## 🔮 Future Work

- Expand machine learning models with advanced feature engineering, incorporating attacker and victim positions to better predict **round outcomes** and **duel success rates**  
- Deploy an **interactive dashboard** (Tableau, Power BI, or Streamlit) to allow users to explore heatmaps and win rates dynamically  
- Explore **time-based trends**, e.g., how strategies evolve across patches  

---

## 📌 Conclusion

This project demonstrates the full workflow of a data analyst: **cleaning messy data, performing analysis, creating compelling visualizations, and applying machine learning** for predictive insights.  

The CS:GO dataset functions much like sports performance analytics. Just as basketball analysts study shot charts and player rotations, or soccer analysts use heatmaps to evaluate passing lanes and goal opportunities, **esports analytics** reveals how strategy, positioning, and man advantage determine round outcomes.  

Esports analytics is a fast-growing field, with teams increasingly relying on data to refine strategies, scout opponents, and improve player performance — much like professional sports organizations.  

Ultimately, this project shows how data analytics can uncover actionable insights in any competitive arena — **whether in traditional sports, esports, or beyond**.

---

## 📂 Files Included

- `CS_GO_Competitive_Matchmaking_Data_Visualization_Analysis.ipynb` – This Colab notebook containing all code for data cleaning, analysis, visualization, and machine learning  
- `README.md` – This document provides a comprehensive overview of the project, including objectives, methodology, insights, and future work  

---

## 🔗 References

- **CS:GO Competitive Matchmaking Data (ESEA Matches)** – Kaggle: [https://www.kaggle.com/datasets/skihikingkevin/csgo-matchmaking-damage](https://www.kaggle.com/datasets/skihikingkevin/csgo-matchmaking-damage)  

---

## 🔗 Links

- **Portfolio:** [https://jordanho1006.github.io/portfolio/](https://jordanho1006.github.io/portfolio/)  
- **LinkedIn:** [https://www.linkedin.com/in/jordanho1006/](https://www.linkedin.com/in/jordanho1006/)
