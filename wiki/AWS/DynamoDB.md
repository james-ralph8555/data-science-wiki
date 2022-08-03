- NoSQL (not only SQL), serverless, provisioned read/write capacity, general purpose database
- Supports document stores such as JSON, XML, or HTML
- Tables do not have a fixed schema
- Low latency
# Anti-patterns
- SQL use cases: Use a [[Relational Database Service|RDS]] database for this
- Joins or complex transform: again, relational stores are better for this
- Large binary data: Binary data over 400KB should be stored in S3, but S3 can be used as a metadata store
- Large, infrequently accessed data: DynamoDB is optimized for workloads with a high ratio of I/O per GB of data stored.  S3 is a better choice for other use-cases.
