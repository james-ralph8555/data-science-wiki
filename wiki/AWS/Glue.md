---
tags:
  - ETL
  - Serverless
---
- For transforming, enriching, or cleaning data before analysis
- Can store data back in [[S3]], [[Redshift]], [[Relational Database Service|RDS]], or the [[Glue Data Catalog]]
- Fully managed
- Can be scheduled or run automatically
- Transformation type examples:
		DropFields, DropNullFields - remove (null fields)
		Filter - filter records
		Join - add other data to dataset
		Map - add/delete fields, perform extermal lookups
		Machine learning transform - FindMatchesML - for (fuzzy) data deduplication
		All Apache Spark transforms can be used
- Cannot write to recordIO-protobuf
- Performance can be modified by attaching more Data Processing Units (DPUs) to a glue job.  The default is 10 DPUs, and the minimum is 2 DPUs.
