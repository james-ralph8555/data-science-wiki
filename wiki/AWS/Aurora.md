---
tags:
    - Serverless
---
- A fully managed database that is compatible with MySQL and PostgreSQL
- Maximum storage size of 128 TiB
- Part of the [[Relational Database Service|RDS]]
- Security is managed via [[IAM]]
- Aurora DB clusters must be created in a [[Virtual Private Cloud|VPC]]
- VPC Entpoint and port connections can be secured using SSL/TLS
- Database can be encrypted at rest using a [[Key Management Service|KMS]] key
- Clusters can be encrypted with an AWS managed key or a customer managed key
- Aurora can lose access to a key for a cluster, such as when a key is disabled or access is revoked.  When access is lost, the cluster can be recovered within 7 days by reactivating the key.  After 7 days, the cluster can only be recovered from a backup
- Enabling backups is therefore strongly recomended
# Aurora Serverless
- An on-demand, autoscaling configuration for Aurora
- Great for variable workloads
