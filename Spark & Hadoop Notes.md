# DistributedComputingNotes
Mostly Hadoop, Spark
As well as concepts, ------------- think at scale!

Spark
---------------------
### 1. Code Optimization

#### 1. avoid creating duplicate rdds


#### 2. avoid re-calcualtion, reuse same rdd as much as you can, 
- use cache() to prevent re calculation, (cache rdd in memory)
- use persist() to manually set different level of cache, 
- ex.StorageLevel.MEMORY_AND_DISK_SER
- others:  
MEMORY_ONLY  
MEMORY_AND_DISK  
MEMORY_ONLY_SER  
MEMORY_AND_DISK_SER: cache to memory first, if memory is not enough, write to disk  
DISK_ONLY  
MEMORY_ONLY_2  
MEMORY_AND_DISK_2  
  
_SER meaning seralize  
_2 make a replicate on other node  
choose Memory_only when avaiable,   
disk_only and _2 are bad on performance, usually worse than re-calcualtion  

#### 3. avoid using shuffle
ex. reduceByKey, join, distinct, repartition  
when rdd is small, consider using Broadcast+ map(similar to hash join)

#### 4. using map-side join
it has some prerequiste though, but performance is much better than reducer-side join  
use reduceByKey and aggregateByKey rather than groupByKey (no combiners)  

#### 4. broadcast variable when you need to

#### 5. when serializtion, use kryo

### 2. Parameter & cluster configuration Optimization
#### 1.
https://stackoverflow.com/questions/37871194/how-to-tune-spark-executor-number-cores-and-executor-memory
http://blog.cloudera.com/blog/2015/03/how-to-tune-your-apache-spark-jobs-part-1/
http://blog.cloudera.com/blog/2015/03/how-to-tune-your-apache-spark-jobs-part-2/

### 3. SparkSession and SparkContext
For Spark 2.0+  
SparkSession is a combination of SQLContext, HiveContext, SparkContext and StreamingContext  
You can use SparkContext by directly initilaztion or use SparkSession.sparkContext  (lower case s captial C)


### 4.spark get single output file

When working with a larger dataset:  

rdd.collect() should not be used in this case as it will collect all data as an Array in the driver, which is the easiest way to get out of memory.  

rdd.coalesce(1).saveAsTextFile() should also not be used as the parallelism of upstream stages will be lost to be performed on a single node, where data will be stored from.  

rdd.coalesce(1, shuffle = true).saveAsTextFile() is the best simple option as it will keep the processing of upstream tasks parallel and then only perform the shuffle to one node (rdd.repartition(1).saveAsTextFile() is an exact synonym).  

rdd.saveAsSingleTextFile() as provided bellow additionally allows one to store the rdd in a single file with a specific name while keeping the parallelism properties of rdd.coalesce(1, shuffle = true).saveAsTextFile().
https://stackoverflow.com/questions/24371259/how-to-make-saveastextfile-not-split-output-into-multiple-file

MapReduce
---------------------
### 1. Downside
https://homes.cs.washington.edu/~billhowe/mapreduce_a_major_step_backwards.html



> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ2ODcwNjQxNF19
-->