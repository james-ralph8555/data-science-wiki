- Low latency streaming ingest at scale
- Streams are partitioned by shards
		Shards can be provisioned manually or with an API call
		Each provisioned shard gets 1MB/s in and 2 MB/s out
		On-demand mode can be used to have capacity automatically managed by AWS based on throughput peak in last 30 days
- Data retention is 24 hours by default, allows for up to 365 days
- Can have multiple consumers for same stream
- Each record inserted into stream can be up to 1MB
- Use Kinesis Client Library (KCL) to handle distributed consumption and computation on kinesis data streams
- The KCL differs from the Kinesis Data Stream API in the AWS SDK by providing a layer of abstraction to make common tasks easier
- Use Kinesis Producer Library (KPL) to help with writing to a kinesis data stream
# Use Cases
- Log and data feed intake and processing: prevents log data from being lost if server fails and also reduced local log storage use
- Real time metrics and reporting to power real-time dashboards
# Anti-patterns
- Small scale consistent throughput: Kinesis data streams is designed for streams over 200KB/s
- Long term data storage and analytics
