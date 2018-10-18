# PythonNotes
Pyspark, Pandas, Numpy and etc


Pyspark
---------------------
### 1. read csv file into dataframe, with separator
from pyspark.sql import SparkSession

spark = SparkSession \
    .builder \
    .appName("Python Spark SQL basic example") \
    .config("spark.some.config.option", "some-value") \
    .getOrCreate()

df = spark.read.csv("/home/stp/test1.csv",header=True,separator="|");
