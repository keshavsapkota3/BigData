# h1- BigData technology
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