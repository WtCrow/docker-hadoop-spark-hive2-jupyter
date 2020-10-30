# docker-compose with hdfs (namenode+datanode), hive2, spark 2.4.5, jupyter notebook with pyspark


Versions:  
- Hadoop 2.7
- Hive 2.3.2 (metastore on postgres)
- Spark 2.4.5 (works with python3.7)
- Jupyter Notebook with pyspark (spark 2.4.5)
- OpenJDK 8

For start:  
1) (optional) Change shared folders for jupyter and/or spark-master services in volumes key
2) In new terminal: `cd /path/to/docker-compose/`
3) Enter `docker-compose up` and wait while services starting
4) In new terminal enter: `docker ps` and find jupyter container id
5) Enter `docker exec <jupyter_id> jupyter notebook list` for get notebook url
6) (optional) Move example.ipynb file to jupyter shared folder and open its in notebook (url from step above)

Some details:  
- For start job on cluster, use `.master('spark://spark-master:7077')` whene create SparkSession
- For access to Hive through spark.sql (saveAsTable, sql etc) add `.enableHiveSupport()` whene create SparkSession
- Default spark file system - HDFS (hint: `docker exec <namenode_id> hdfs dfs -ls /`)
- Python on jupyter container use conda
