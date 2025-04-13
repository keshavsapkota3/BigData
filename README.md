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