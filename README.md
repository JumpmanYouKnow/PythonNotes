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

  df_demand = spark.read\
        .format("com.databricks.spark.csv")\
        .option("header", "true")\
        .option("mode", "DROPMALFORMED")\
        .option("delimiter", "|")\
        .load(demand_data)

#### 2.
https://www.analyticsvidhya.com/blog/2016/10/spark-dataframe-and-operations/

$ ./bin/pyspark --packages com.databricks:spark-csv_2.10:1.3.0

train = sqlContext.load(source="com.databricks.spark.csv", path = 'PATH/train.csv', header = True,inferSchema = True)

#### 3. Unique value of a column
select("col name").distinct()

#### 4. drop value
.drop("col name")

#### 5. spark df to pandas df
.toPandas() # cost is expensive, try to minimum use it! it's an action, collect all the data to the driver

#### 6.sort by col, (descending)
from pyspark.sql.functions import desc

(group_by_dataframe
    .count()
    .filter("`count` >= 10")
    .sort(desc("count"))
OR
.orderBy('Year', ascending=False)

#### 7. filter
In pyspark, filter on dataframe doesn't take functions that returns a boolean,\
it only takes SQL experssion that returns a boolean\
If you want it to take a boolean function, use udf, sample: 

@F.udf(returnType=BooleanType())\
def my_filter(col):\
&npspfunc\
&npspreturn Boolean
  
df.filter(my_filter('col')).show()\
Make sure includes:\
from pyspark.sql import functions as F\
from pyspark.sql.types import BooleanType



Pandas
---------------------
#### 1. Collect dataframe as dictionary
.set_index(['a','b']).T.to_dict('list')
