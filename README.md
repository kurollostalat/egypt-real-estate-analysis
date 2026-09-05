# Egypt Real Estate Analysis
## Why this project?
I picked the Egyptian real estate market mostly because it's messy and local. No English-first pricing conventions, mixed units, compound values, and a real gap in missing data. It felt like a better test of actual data cleaning skills than another polished tutorial dataset.

## The Data
I used the [Egyptian Real Estate Listings](https://www.kaggle.com/datasets/hassankhaled21/egyptian-real-estate-listings) dataset from Kaggle (Hassan Khaled21), which contains ~20,000 property listings originally collected from PropertyFinder Egypt. I cleaned it to practice a full pandas cleaning and EDA workflow on real, messy data.
- **Stats**: 19,924 listings going in, [FILL: X] after cleaning (includes IQR-based outlier removal on price, not just the size filter).
- **Key challenges**: mixed units in the size column (sqft and sqm in the same field, split with regex), compound bedroom values like "3+maid" that needed parsing before summing, and the `down_payment` column missing in ~73% of rows. Too much to drop, so I filled it with the mean after fixing a scale bug in the normalization step.

## Key Insights
- **Price distribution**: mean price is [FILL: X]M EGP, median is [FILL: X]M EGP. The gap means there's a long tail of high-end listings pulling the average up. Median is the more honest "typical" number here.
- **Typical unit**: ~3 bedrooms, 3 bathrooms, average size [FILL: X] sqm.
- **Market activity**: 9 property types account for most of the listings; the rest are long-tail niche types.
- **Weak correlations with price overall**: size ([FILL: X]), bedrooms ([FILL: X]), and bathrooms ([FILL: X]) all correlate weakly with price. Down payment correlates even more weakly ([FILL: X]) — but with 73% of that column missing and mean-imputed, this number reflects that weakness more than it reflects a true absence of relationship.
- **Bedrooms and bathrooms move together**: the strongest relationship in the matrix isn't with price at all, it's between bedrooms and bathrooms ([FILL: X]), which makes sense since larger units tend to scale both together.

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

## Data Limitations
- The `down_payment` column has 73% missing values. Mean imputation was used as a practical compromise, but any conclusion drawn from this column should be treated with caution.
- A few extreme size values (well above typical unit sizes for their property type) were flagged manually but not automatically removed — worth a closer look before drawing size-based conclusions.

## Future Improvements
- Location-aware imputation for missing down payment values instead of a simple mean.
- Re-check price correlations with Spearman or log-transformed values, since the weak Pearson correlations across the board could partly be an artifact of remaining outliers or non-linear relationships.
- Automated outlier detection for size relative to property type (e.g. flagging a 6,800 sqm "Apartment" automatically instead of manual review).

---
**Author**: Kurollos Talat · [LinkedIn](https://linkedin.com/in/kurollos-talat-49409520a) · kurollostalat@gmail.com
