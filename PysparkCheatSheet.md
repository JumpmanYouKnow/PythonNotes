---
title: "Pyspark"
date: 2019-09-08
---
---------------------
### 1. initilaztion

#### 1. spark session
```Python
from pyspark.sql import SparkSession  
spark = SparkSession \
    .builder \
    .appName("name") \
    .config("spark.some.config.option", "some-value") \
    .getOrCreate()
```

#### 2. spark context
##### 1. from spark session
```Python
sc = spark.sparkContext
```
##### 2. from spark context
```Python
conf = SparkConf().setAppName("KMeans").setMaster("local[*]")  
sc = SparkContext(conf =conf)  
or  
sc = SparkContext.getOrCreate(conf)
```

### 2. paritition by index
```Python
.mapPartitionsWithIndex(lambda idx, it: islice(it, 1, None) if idx == 0 else it)\
this get rid of the first line(rdd) in the file. 
```

### 3. opeartions of spark dataframe
#### 1. read csv file into dataframe, with separator
```Python
from pyspark.sql import SparkSession

spark = SparkSession \
    .builder \
    .appName("Python Spark SQL basic example") \
    .config("spark.some.config.option", "some-value") \
    .getOrCreate()

  df_demand = spark.read\
        .format("com.databricks.spark.csv")\
        .option("header", "true")\
        .option("inferSchema", "true")\
        .option("mode", "DROPMALFORMED")\
        .option("delimiter", "|")\
        .load(demand_data)
```
#### 2. Basic Operations
https://www.analyticsvidhya.com/blog/2016/10/spark-dataframe-and-operations/

#### 3. read dictionary into spark dataframe
1. dict -> pandas.df -> spark.df  
https://stackoverflow.com/questions/43751509/how-to-create-new-dataframe-with-dict?rq=1  
2.  dict -> spark.rdd (json rdd) -> json parser -> spark.df  
https://stackoverflow.com/questions/51774796/how-to-convert-dictionary-to-data-frame-in-pyspark  


Note:
when use pandas df to create spark df, if you want to perserve indices,  
use: spark_df = spark.createDataFrame(pandasdf.reset_index(drop=False))  
must have reset_index(drop=False) to preserve indices, as spark SQL has no concept of index  

#### 3. Unique value of a column
select("col name").distinct()
.drop("col name")
#### 4. drop col
.drop("col name")

#### 5. spark df to pandas df
.toPandas() # cost is expensive, try to minimum use it! it's an action, collect all the data to the driver

#### 6.sort by col, (descending)
from pyspark.sql.functions import desc

(group_by_dataframe
    .count()
    .filter("`count` >= 10")
    .sort(desc("count"))\
OR\
.orderBy('Year', ascending=False)

#### 7. filter
In pyspark, filter on dataframe doesn't take functions that returns a boolean,\
it only takes SQL experssion that returns a boolean\
If you want it to take a boolean function, use udf, sample: 
```Python
@F.udf(returnType=BooleanType())
def my_filter(col):
    func
    return Boolean
  
df.filter(my_filter('col')).show()
Make sure includes:
from pyspark.sql import functions as F
from pyspark.sql.types import BooleanType
```
#### 8. map on column
 df.withColumn('new column', udf('old column')))

#### 9. coalesce and repartition
repartition(n) = coalesce(n, shuffle = true)

### 4. Wide dependency and narrow dependency, 

Orgin we have M partitions, we repartiton to N partitions.  
narrow dependency, usually we have M > N, like Map, doesn't triger shuffle  
when M is greatly larger than N, it's better to manually triger shuffle, otherwise  
it affects parallelization and performance.  
  
Wide dependency, usually we have M < N, like Join, groupByKey, triger shuffle  

### 5. Inferschema dependency:
NullType\
IntegerType\
LongType\
DecimalType\
DoubleType\
TimestampType\
BooleanType\
StringType
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTk0MTMxMzM1LDEzMDcyODA4NzZdfQ==
-->