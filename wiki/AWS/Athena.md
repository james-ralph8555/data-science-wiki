---
tags:
  - Serverless
---
- For serverless [[SQL]] queries of [[S3]] data
- Supports CSV, JSON, ORC, Parquet, and Avro
- Columnar formats such as ORC and Parquet deliver superior performance and cost savings
- [[Glue Data Catalog]]s can inform Athena
- Security managed via [[IAM]] policies
- Much of Athena's security is governed by [[S3]] policies
## Use Cases
- Ad hoc queries
- Querying staged S3 data before processing and loading into [[Redshift]]
## Anti-patterns
- Enterprise Reporting and BI workloads: Redshift is better for storing and organizing data from many sources
- ETL Workloads: Use [[Elastic Map Reduce|EMR]] or [[Glue]] for this
- Relational database store: Athena is not a database and should not replace SQL engines like MySQL


[Full user guide](https://docs.aws.amazon.com/athena/latest/ug/athena-ug.pdf)
