# BigData
First of all we imported essential modules like:
* SparkSession – the entry point to use DataFrame and SQL APIs in PySpark.
* SparkConf – used to customize Spark configurations.
Then wenconfigured Spark to allocate 4 GB of memory to each executor, which helps when working with large datasets.
Then we gave the Spark application a name.
And connected Spark to a local MongoDB database:
This enabled us to read from and write to MongoDB collections using Spark DataFrames.
Applied the custom executor memory configuration we created earlier.
Created a new Spark session or reused an existing one.

## Then we imported following: 
   MongoClient: Connects to local MongoDB  
   requests: Downloads raw CSV file from GitHub  
   pandas: Loads and processes the CSV
   StringIO: Treats string like a file for pandas to read

Then connected  to a MongoDB database called ‘Project’ and  
created a collection called ‘Online_Retails’.
Downloaded the CSV file from GitHub’s raw link.

Then we treated the CSV string as a file and 
loaded it into a pandas DataFrame.

We converted the DataFrame into a list of dictionaries, where each dictionary = one row. Then 
added all records to MongoDB collection in one go.

1. Environment Setup
PySpark Version: 3.5.5

Spark session created with:

4GB executor memory

MongoDB integration via spark.mongodb.read/write.connection.uri

🧱 2. MongoDB Data Ingestion
MongoDB DB & Collection: Project.Online_Retails

Source Data: CSV from GitHub (Online Retail dataset)

Pandas used to:

Read the CSV

Clean and preprocess data

Insert ~541,909 records into MongoDB

🧹 3. Data Cleaning (Pandas)
Total records after load: 2,167,636

Missing Values:

Description: 5,816 missing

CustomerID: 540,320 missing → Dropped

Dropped nulls → Remaining rows: 1,627,316

Removed duplicates → Final clean rows: 1,627,316

📊 4. Feature Engineering
Converted InvoiceDate to datetime

Extracted YearMonth (period)

Created new column: TotalSale = Quantity * UnitPrice

📈 5. Sales Aggregation
✅ Monthly Sales
YearMonth	TotalSale
2010-12	552,372.86
2011-01	473,731.90
...	...
2011-12	341,539.43
✅ Sales by Country
Country	TotalSale
United Kingdom	6,747,156.15
Netherlands	284,661.54
EIRE (Ireland)	250,001.78
France	196,626.05
...	...
📥 6. Store Aggregated Results in MongoDB
Collection: Project.sales_data

Inserted: 50 records (Monthly + Country-wise summaries)

⚡ 7. PySpark Integration
Converted Pandas DataFrame to PySpark DataFrame

Registered as SQL View sales_view

Ran SQL query to re-aggregate monthly sales

Schema verified

Repartitioned data by Country

Cached df1_spark for performance

🔍 8. Indexing
Created an index on InvoiceDate in MongoDB to speed up queries.

📊 9. Visualizations
Monthly Sales Trend → Line chart (Seaborn)

Sales by Country → Bar chart

✅ Key Takeaways
Cleaned and processed over 1.6 million rows of retail data

Integrated MongoDB, Pandas, PySpark, Seaborn, and Matplotlib

Performed insightful aggregation by month and country

Stored clean and enriched data in MongoDB

Optimized PySpark operations with caching and repartitioning


