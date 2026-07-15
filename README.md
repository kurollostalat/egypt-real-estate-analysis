# Egypt Real Estate Market Analysis

## Why this project?
I picked the Egyptian real estate market mostly because it's messy and local — no clean Kaggle dataset, no English-first pricing conventions, just raw listings I had to scrape and wrangle myself. It felt like a better test of actual data cleaning skills than another polished tutorial dataset.

## The Data
I scraped and cleaned ~20,000 property listings from PropertyFinder Egypt to practice a full pandas cleaning + EDA workflow on real, messy data.

- **Stats**: 19,924 listings going in, 19,917 after cleaning.
- **Key challenges**: mixed units in the size column (sqft and sqm in the same field, split with regex), and the `down_payment` column missing in ~73% of rows — too much to drop, so I filled it with the mean.

## Key Insights
- **Price distribution**: mean price is 16.4M EGP, median is 10.66M EGP. The gap means there's a long tail of high-end listings pulling the average up — median is the more honest "typical" number here.
- **Typical unit**: ~3 bedrooms, 3 bathrooms, average size 215 sqm.
- **Market activity**: 9 property types account for most of the listings; the rest are long-tail niche types.
- **Size barely correlates with price** (~0 in the correlation matrix) — surprising, since bedrooms (0.47) and bathrooms (0.51) correlate with price far more. My best guess: Pearson correlation is very sensitive to outliers, and both price (up to 840M EGP) and size (up to 9,500 sqm) have a handful of extreme values that could be pulling the coefficient toward zero. Worth re-checking with Spearman or on log-transformed values before trusting this number at face value.

## Visualizations
![Correlation Matrix](The%20Correlation%20Between%20Numeric%20Columns.png)
![Price Distribution](Distribution%20of%20Real%20Estate%20Prices%20%26%20Outliers%20Detection%20%28Cleaned%20Data%29.png)
![Average Price by Type](Average%20Price%20by%20real%20estate%20type.png)
![Price Trend Over Time](Average%20Real%20Estate%20Price%20Trend%20Over%20Time.png)
![Property Type Distribution](The%20Pie%20Charts%20to%20Show%20the%20Top%209%20Real%20Estate%20and%20Others.png)

## Technical Stack
- **Python**: Pandas, NumPy, Regex
- **Visualization**: Matplotlib, Seaborn
- **Environment**: Jupyter Notebooks

## Future Improvements
- Apply IQR or Z-score filtering for more robust outlier handling — right now outliers are only flagged visually via boxplot.
- Location-aware imputation for missing down payment values instead of a simple mean.
- Re-check the size–price correlation with Spearman or log-transformed values to see if it's a real weak relationship or an outlier artifact.

---
**Author**: Kurollos Talat · [LinkedIn](https://linkedin.com/in/kurollos-talat-49409520a) · kurollostalat@gmail.com
