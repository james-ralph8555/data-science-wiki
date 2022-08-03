- Data warehousing and SQL analytics platform
- Data is loaded from [[S3]], usually with COPY command
- Columnar datastore therefore efficient for queries
- Redshift spectrum can be used to directly query [[S3]] data
# Use Cases
- Online analytical processing (OLAP)
- Analyzing ad impressions and clicks
- Analyzing data across an S3 data lake and Redshift
# Anti-patterns
- Small datasets: for datasets less than 100GB, Redshift is overill and a [[Relational Database Service|RDS]] database is a better choice
- Online transaction processing (OLTP): If fast transactions are required, a traditional relational database or NoSQL database such as [[DynamoDB]] is a better choice
- Unstructured data: Redshift data must have a defined schema.  Data should be processed via and ETL service first
