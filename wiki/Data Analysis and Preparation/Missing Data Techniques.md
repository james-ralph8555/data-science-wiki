# Mean replacement
- Fast and easy
- Works well when outliers are not present
- Major drawback: does not take into account correlations between columns
# Median replacement
- Similar to mean replacement but works better when outliers are present
# Dropping data
- Generally bad choice
- Can bias dataset (potential reason why data is missing)
# Replacing data with other columns
- Situational e.g. a dataset with missing full text reviews can have missing values filled with the review summary
# Machine learning
- K Nearest Neighbors ([[K-Nearest-Neighbors|KNN]]) can be used to find similar rows and average their values - good for numerical data
- Deep learning models work well for filling in missing categorical data
- Regression techniques can be used for numerical data (MICE is a good algorithm for missing data)