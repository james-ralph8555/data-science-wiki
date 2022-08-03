- For running code without provisioning or managing servers
- Serverless
# Use Cases
- Real-time file processing
- Real-time stream processing with Kinesis Data Streams
- ETL
- Scheduling a function to run at regular intervals (like cron)
- Processing AWS events such as Cloudtrail evens
# Anti-patterns
- Long running applications: each lambda job must complete in 15 minutes
- High volume, highly dynamic websites: lambda does not provide the performance needed for this.  Using a service like [[EC2]] or [[Elastic Container Service|ECS]] is a better choice
- Stateful applications: any persistant data should be stored in [[S3]] or [[DynamoDB]]
