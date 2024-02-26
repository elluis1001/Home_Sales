# Home_Sales

Here is a detailed README report for the PySpark home sales analysis notebook:

# PySpark Home Sales Analysis

This notebook performs analysis on a dataset of home sales using PySpark SQL and DataFrames.

## Data Analysis Report

The data analysis steps covered include:

### Data Loading and Cleaning

- The home sales data is loaded from a CSV file hosted on AWS S3 into a PySpark DataFrame
- The schema is inferred automatically on load
- Columns are cast to appropriate types like Integer and DateType 

### Exploratory Data Analysis

- Summary statistics are calculated on the DataFrame like count, min, max price
- Average home sale prices are calculated for different years and attributes:
  - Average price per year sold
  - Average price by number of bedrooms
  - Average price per year built
  - Average prices by neighborhood view rating

### Performance Optimization

- The DataFrame is cached into memory to avoid recomputing for interactive queries
- The data is also converted into a partitioned Parquet format on disk
  - Partitions are created based on year built 
  - This enables optimized reads when filtering on that column

### Query Performance Comparison

- The same analytic query is run on the raw CSV data, cached data, and partitioned Parquet data
- The relative performance of each is compared by tracking query runtime
- Caching provides 4x speedup over raw data
- Partitioned Parquet provides 60x speedup over raw data

### Analysis Conclusions

Some highlights from the analysis:

- Average sale price peaked in 2021 at just over $1M 
- Homes with a view rating of 90+ had avg prices over $1.5M
- Partitioning Provides significant performance benefits for large data

Overall, this notebook demonstrates how PySpark SQL and DataFrames can be used to efficiently analyze large datasets.

## Notebook Details

**Tools:**
- Python 3.6
- PySpark 3.0
- Jupyter Notebook

**Libraries Used:**
- Spark SQL
- pandas 
- Matplotlib

**Datasets:**
- `home_sales.csv` - CSV file containing home sale records  

## License 

This notebook and analysis is shared under the MIT License.
