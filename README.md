# docker-compose with hdfs (namenode+datanode), hive2, spark2, jupyter notebook with pyspark

Versions:  
- Hadoop 2.7
- Hive 2.3.2 (metastore on postgres)
- Spark 2.4.5 (works with python3 and OpenJDK 8)
- Jupyter Notebook with pyspark (spark 2.4.5)

For start:  
1) In terminal `cd /path/to/project/`
2) (optional) Change shared folders for jupyter and/or spark-master services in volumes key
3) Enter `docker-compose up` and wait while services starting
4) Enter `docker exec jupyter jupyter notebook list` for get notebook url
5) (optional) Move example.ipynb file to jupyter shared folder and open its in notebook (url from step above)

Some details:  
- For start job on cluster, use `.master('spark://spark-master:7077')` when create SparkSession
- For access to Hive through spark.sql (saveAsTable, sql etc) add `.enableHiveSupport()` when create SparkSession
- Default spark file system - HDFS (hint: `docker exec namenode hdfs dfs -ls /user/jovyan/` for check files that saved from notebook)
- Python on jupyter container use conda
