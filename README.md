# Egypt Real Estate Market Analysis

## Why this project?
I picked the Egyptian real estate market mostly because it's messy and local. No English-first pricing conventions, mixed units, compound values, and a real gap in missing data. It felt like a better test of actual data cleaning skills than another polished tutorial dataset.

## The Data
I used the [Egyptian Real Estate Listings](https://www.kaggle.com/datasets/hassankhaled21/egyptian-real-estate-listings) dataset from Kaggle (Hassan Khaled21), which contains ~20,000 property listings originally collected from PropertyFinder Egypt. I cleaned it to practice a full pandas cleaning and EDA workflow on real, messy data.

- **Stats**: 19,924 listings going in, 19,917 after cleaning.
- **Key challenges**: mixed units in the size column (sqft and sqm in the same field, split with regex), and the `down_payment` column missing in ~73% of rows. Too much to drop, so I filled it with the mean.

## Key Insights
- **Price distribution**: mean price is 16.4M EGP, median is 10.66M EGP. The gap means there's a long tail of high-end listings pulling the average up. Median is the more honest "typical" number here.
- **Typical unit**: ~3 bedrooms, 3 bathrooms, average size 215 sqm.
- **Market activity**: 9 property types account for most of the listings; the rest are long-tail niche types.
- **Size barely correlates with price** (~0 in the correlation matrix). Surprising, since bedrooms (0.47) and bathrooms (0.51) correlate with price far more. My best guess: Pearson correlation is very sensitive to outliers, and both price (up to 840M EGP) and size (up to 9,500 sqm) have a handful of extreme values that could be pulling the coefficient toward zero. Worth re-checking with Spearman or on log-transformed values before trusting this number at face value.

## Visualizations
![Correlation Matrix](the%20correlation%20between%20the%20columns.png)
![Price Distribution](Distribution%20of%20Real%20Estate%20Prices%20%26%20Outliers%20Detection%20%28Cleaned%20Data%29.png)
![Average Price by Type](Average%20Price%20by%20real%20estate%20type.png)
![Price Trend Over Time](Average%20Real%20Estate%20Price%20Trend%20Over%20Time.png)
![Property Type Distribution](The%20Pie%20Charts%20to%20Show%20the%20Top%209%20Real%20Estate%20and%20Others.png)
![Price vs Size](Real%20Estate%20Price%20vs%20Size%20%28Detecting%20Patterns%20%26%20Outliers%29.png)

## Technical Stack
- **Python**: Pandas, NumPy, Regex
- **Visualization**: Matplotlib, Seaborn
- **Environment**: Jupyter Notebooks

## Future Improvements
- Apply IQR or Z-score filtering for more robust outlier handling. Right now outliers are only flagged visually via boxplot.
- Location-aware imputation for missing down payment values instead of a simple mean.
- Re-check the size–price correlation with Spearman or log-transformed values to see if it's a real weak relationship or an outlier artifact.

---
**Author**: Kurollos Talat · [LinkedIn](https://linkedin.com/in/kurollos-talat-49409520a) · kurollostalat@gmail.com
