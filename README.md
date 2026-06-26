# 🌍 Global Food Price Analysis

> **A data-driven investigation into food price trends, commodity affordability, and market-level disparities across nations — powered by WFP market data.**

---

## 📌 Overview

Food price volatility is one of the most critical indicators of food insecurity and economic stress. This project analyzes the **World Food Programme (WFP) Global Food Prices** dataset to uncover price trends for essential staple commodities (Rice, Bread, Milk, Meat, Fish, Water) across multiple countries and time periods.

The project delivers:
- Standardized, comparable food price data across different currencies and units
- Country-level trend analysis for India, Mali, Ukraine, and Niger
- Market-level price dispersion analysis within countries
- USD-normalized cross-country rice price comparisons
- Linear regression forecasts of rice prices through 2024

---

## 📊 Dataset

| Attribute | Value |
|-----------|-------|
| **Source** | World Food Programme (WFP) |
| **Host** | [Kaggle — Global Food Prices](https://www.kaggle.com/datasets/jboysen/global-food-prices/data) |
| **File** | `wfp_market_food_prices.xlsx` |
| **Records** | 1M+ price observations |
| **Coverage** | 70+ countries, spanning multiple decades |

### Key Columns

| Column | Description |
|--------|-------------|
| `adm0_name` | Country name |
| `adm1_name` | Sub-national locality |
| `mkt_name` | Local market name |
| `cm_name` | Commodity / product name |
| `cur_name` | Currency name |
| `um_name` | Unit of measurement |
| `mp_month` / `mp_year` | Month and year of price record |
| `mp_price` | Price in local currency |
| `pt_name` | Market type (Retail/Wholesale/Producer/Farm Gate) |

---

## 🛠 Tech Stack

| Tool | Purpose |
|------|---------|
| `Python 3.x` | Core language |
| `pandas` | Data manipulation, pivot tables, groupby |
| `numpy` | Array operations, reshape for ML input |
| `matplotlib` | Line charts, bar charts, trend plots |
| `seaborn` | Statistical boxplots |
| `scikit-learn` | Linear regression forecasting |
| `Jupyter Notebook` | Interactive development environment |

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyter
```

### Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/global-food-price-analysis.git
   cd global-food-price-analysis
   ```

2. **Download the dataset**
   - Visit: [https://www.kaggle.com/datasets/jboysen/global-food-prices/data](https://www.kaggle.com/datasets/jboysen/global-food-prices/data)
   - Download `wfp_market_food_prices.xlsx`
   - Place it in the `/data` directory

3. **Update the file path**  
   In `Analysis_of_Global_food_price.ipynb`, update the data load cell:
   ```python
   df = pd.read_excel("data/wfp_market_food_prices.xlsx")
   ```

4. **Launch the notebook**
   ```bash
   jupyter notebook Analysis_of_Global_food_price.ipynb
   ```

---

## 🗂 Project Structure

```
global-food-price-analysis/
│
├── data/
│   └── wfp_market_food_prices.xlsx    # WFP dataset (download from Kaggle)
│
├── Analysis_of_Global_food_price.ipynb # Main analysis notebook
│
├── README.md                           # You are here!
└── requirements.txt                    # Python dependencies
```

---

## 📈 Analysis Pipeline

```
Raw Data (xlsx)
    │
    ▼
Data Loading & Exploration
    │  shape, dtypes, head, describe
    ▼
Data Cleaning
    │  Drop nulls (adm1_name), check duplicates
    ▼
Commodity Filtering
    │  Bread | Milk | Meat | Fish | Rice | Water | Exchange rate
    ▼
Name Standardization
    │  Strip parenthetical qualifiers from cm_name
    ▼
Unit Normalization
    │  Map 50+ units → KG-equivalent coefficient
    │  mp_price_un = mp_price / um_koef
    ▼
Pivot Table
    │  index: country × year × month × market
    │  columns: commodity
    ▼
Statistical Analysis
    │  Boxplots, Spearman correlation, descriptive stats
    ▼
Country Trend Analysis
    │  India, Mali, Ukraine, Niger — annual averages
    ▼
Market-Level Analysis
    │  Rice price ranking & volatility by local market
    ▼
USD Normalization
    │  Rice_USD = Rice / Exchange rate
    ▼
Multi-Country Comparison
    │  9 countries, year-over-year USD rice prices
    ▼
Linear Regression Forecasting
    │  Trend extrapolation through 2022–2024
```

---

## 🔍 Key Findings

### 1. Commodity Price Distributions
- **Meat and Fish** exhibit the widest price variance globally — affected by local production capacity, import dependency, and perishability.
- **Rice and Bread** show tighter distributions, reflecting their status as subsidized staple crops in many countries.

### 2. Country Trends
| Country | Key Observation |
|---------|----------------|
| **India** | Steady upward trend in Milk and Rice prices, accelerating post-2010 |
| **Mali** | Rice prices show cyclical volatility, likely linked to rainfall and harvest seasons |
| **Ukraine** | Sharp price spikes in Meat and Milk coinciding with geopolitical disruptions |
| **Niger** | Persistent high prices in a constrained market with limited supply chain |

### 3. Market-Level Disparity
- Within India alone, Rice prices vary by **200–300%** between the cheapest and most expensive local markets.
- The top 5 most volatile markets (by price range) are concentrated in landlocked or remote regions.

### 4. USD-Normalized Comparison (9 Countries)
- Countries like **Tajikistan** and **DRC** show the steepest upward trends in USD-equivalent rice costs.
- **Panama** and **Costa Rica** (already USD-based) display the most stable trajectories.

### 5. Price Forecasts (Linear Regression through 2024)
- Most countries show a **positive slope** (increasing rice prices in USD terms).
- **Afghanistan** and **Tajikistan** show the steepest predicted increases, suggesting growing food affordability challenges.

---

## 📉 Visualizations Produced

| Chart | Description |
|-------|-------------|
| Boxplot — All Commodities | Global price distribution per staple food |
| Bar — Year Correlation | Which commodities correlate most strongly with year (inflation signal) |
| Line — India (Milk, Rice) | Annual average price trend for India |
| Line — Mali (Rice) | Annual rice price trend for Mali |
| Line — Ukraine (Milk, Rice, Meat) | Multi-commodity trend for Ukraine |
| Line — Niger (Milk, Rice, Meat) | Multi-commodity trend for Niger |
| Bar — Market Rankings | Rice price ranking by local market (per country) |
| Line — Top 5 Volatile Markets | Price trajectory of India's 5 most volatile markets |
| Line — Multi-country USD | Rice price in USD across 9 countries |
| Trend + Scatter — Per Country | Linear regression forecast per country |


---

## 📚 References
- Kaggle Dataset: [https://www.kaggle.com/datasets/jboysen/global-food-prices/data](https://www.kaggle.com/datasets/jboysen/global-food-prices/data)

---

## 📝 License

This project is released under the [MIT License](LICENSE).

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/new-analysis`)
3. Commit your changes (`git commit -m 'Add new analysis'`)
4. Push to the branch (`git push origin feature/new-analysis`)
5. Open a Pull Request

---

*Built with ❤️ using Python and WFP open data*
