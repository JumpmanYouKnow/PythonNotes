# PythonNotes
Pyspark, Pandas, Numpy and etc


Pyspark
---------------------
### 1. initilaztion

#### 1. spark session
from pyspark.sql import SparkSession  
spark = SparkSession \
    .builder \
    .appName("name") \
    .config("spark.some.config.option", "some-value") \
    .getOrCreate()

#### 2. spark context
##### 1. from spark session
sc = spark.sparkContext
##### 2. from spark context
conf = SparkConf().setAppName("KMeans").setMaster("local[*]")  
sc = SparkContext(conf =conf)  
or  
sc = SparkContext.getOrCreate(conf)


### 2. paritition by index
.mapPartitionsWithIndex(lambda idx, it: islice(it, 1, None) if idx == 0 else it)\
this get rid of the first line(rdd) in the file. 

### 3. opeartions of spark dataframe
#### 1. read csv file into dataframe, with separator
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

# spark SQL has no concept of index
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
    .sort(desc("count"))\
OR\
.orderBy('Year', ascending=False)

#### 7. filter
In pyspark, filter on dataframe doesn't take functions that returns a boolean,\
it only takes SQL experssion that returns a boolean\
If you want it to take a boolean function, use udf, sample: 

@F.udf(returnType=BooleanType())\
def my_filter(col):\
&nbsp;&nbsp;&nbsp;&nbsp; func\
&nbsp;&nbsp;&nbsp;&nbsp; return Boolean
  
df.filter(my_filter('col')).show()\
Make sure includes:\
from pyspark.sql import functions as F\
from pyspark.sql.types import BooleanType

#### 8. Inferschema dependency:
NullType\
IntegerType\
LongType\
DecimalType\
DoubleType\
TimestampType\
BooleanType\
StringType

#### 9. Operation on column
 df.withColumn('new column', udf('old column')))

#### 10. Wide dependency and narrow dependency, 

Orgin we have M partitions, we repartiton to N partitions.  
narrow dependency, usually we have M > N, like Map, doesn't triger shuffle  
when M is greatly larger than N, it's better to manually triger shuffle, otherwise  
it affects parallelization and performance.  
  
Wide dependency, usually we have M < N, like Join, groupByKey, triger shuffle  


#### 11. coalesce and repartition
repartition(n) = coalesce(n, shuffle = true)

Pandas
---------------------
#### 1. Collect dataframe as dictionary
.set_index(['a','b']).T.to_dict('list')

#### 2. Read in csv file format 
https://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_csv.html


Other useful packages
---------------------
#### 1. track memory usage line by line
https://pypi.org/project/memory_profiler/

#### 2. track run time for each line
https://pypi.org/project/line_profiler/

#### 3.  
difference between list[0,1,2,3,4] and range(0,5) in python 3.0+
ie: difference between range(0,5) and xrange(0,5) in python before 3.0

the former one needs to allocate the actuall space on memory, the later one doesn't have to.
The later ones returns a object similar to iterator, (but allows random access), so allocate memory on demand.

Generic Python
---------------------

#### 1. Open file, read, write
Open: f = open(“hello.text”, flag), flag: 'r' = read, 'b' = binary, 'w' = write
read sing line:
f.readline() 
read a list of lines:
f.readlines()
read whole file as string:
f.read()

#### 2.  look up table of element, origin index -> the sorted index
idx = np.argsort()
lut = np.zeros_like(idx)  
lut[idx] = np.arange(len(origin_list))

lut[origin_index] = sorted_index

#### 3. load object and save object
def save_obj(obj, name ):
    with open('obj/'+ name + '.pkl', 'wb') as f:
        pickle.dump(obj, f, pickle.HIGHEST_PROTOCOL)

def load_obj(name ):
    with open('obj/' + name + '.pkl', 'rb') as f:
        return pickle.load(f)


