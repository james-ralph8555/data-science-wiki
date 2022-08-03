---
aliases: [EMR]
tags:
  - ETL
---
- Includes Spark (like [[Glue]]), Presto (like [[Athena]]), Flink, Hive (data warehouse)
- EMR Clusters have a main node on a single [[EC2]] instance which manages the cluster
- Core nodes contain the Hadoop distributed file system (HDFS) and can run tasks
- Task nodes do not store data and can be added/removed from cluster as needed
- HDFS is emphemeral and is lost when the cluster is removed
- EMRFS works like HDFS but contains [[S3]] data
- Apache Spark MLLib can perform machine learning tasks
- EMR can be managed from an EMR notebook (Jupyter notebook)
- EMR security is managed with [[IAM]] policies and [[IAM]] roles
# Anti-patterns
- Small datasets: EMR is built for massive parallel processing, and small jobs should be run on a single machine with less overhead
