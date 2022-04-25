# Experiments using Delta Lake

A simple notebook explaining some Delta Lake features (v. 1.2) and how to use them.

## How to install: 

1. Make sure to have an installed Spark distribution;
2. Define which Delta Lake you can use based on your Spark version ([check the compatibility list](https://docs.delta.io/latest/releases.html))
3. a) Start spark with Delta Lake "on-fly": 
```
pyspark --packages io.delta:delta-core_2.12:1.2.0 
        --conf "spark.sql.extensions=io.delta.sql.DeltaSparkSessionExtension" 
        --conf "spark.sql.catalog.spark_catalog=org.apache.spark.sql.delta.catalog.DeltaCatalog"
```
3. b) Or setup Delta Lake to be used in all Spark executions by adding the following configurations in `SPARK_HOME/conf/spark-defaults.conf`:

```
#---------------------
#       Delta Lake
#---------------------
spark.jars.packages io.delta:delta-core_2.12:1.2.0  
spark.sql.extensions io.delta.sql.DeltaSparkSessionExtension
spark.sql.catalog.spark_catalog org.apache.spark.sql.delta.catalog.DeltaCatalog
```