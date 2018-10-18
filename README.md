# PythonNotes
Pyspark, Pandas, Numpy and etc


Pyspark
---------------------
### 1. read csv file into dataframe, with separator

#### 1.
from pyspark.sql import SparkSession

spark = SparkSession \
    .builder \
    .appName("Python Spark SQL basic example") \
    .config("spark.some.config.option", "some-value") \
    .getOrCreate()

df = spark.read.csv("/home/stp/test1.csv",header=True);

#### 2.
https://www.analyticsvidhya.com/blog/2016/10/spark-dataframe-and-operations/

$ ./bin/pyspark --packages com.databricks:spark-csv_2.10:1.3.0

train = sqlContext.load(source="com.databricks.spark.csv", path = 'PATH/train.csv', header = True,inferSchema = True)

