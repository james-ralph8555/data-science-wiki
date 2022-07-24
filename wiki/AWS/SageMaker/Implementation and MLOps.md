## Sagemaker/Docker integration
- All sagemaker models are hosted in docker containers registed with the [[Elastic Container Registry]] (ECR)
- Allows any script or algorithm within [[SageMaker]] as long as the docker container follows a certain file structure
- Containres must be able to respond to both /invocations and /ping on port 8080, and accept socket connection requests within 250ms
- The file structure for a training container:
- The file structure for a deployment container:
- Docker image must contain:
	- nginx.conf - config for nginx web gateway/frontend
	- predictor.py - config for flask webserver to serve model and make predictions
	- serve/ directory - deployment model directory, launches gunicorn server to launch multiple flask webservers
	- train/ directory - used for training
	- wsgi.py - wrapper for invoking flask application
- Can have different training/inference images or they can be combined into the above image
- Environment variables in the dockerfile can define where sagemaker can find programs in the container, checkpoint directories, etc
- e.g. include "ENV SAGEMAKER_PROGRAM train.py" in the docker file to set /opt/ml/code/train.py as the training entrypoint - SageMaker does not do this automatically
- Hyperparameters can be set via environment variables for hyperparameter tuning
- Multiple variants of a model can be deployed at once
- Variant weights determine how often each model is used
- Useful for A/B testing where the existing model gets the most traffic and the new model gets a higher share of users as its effectiveness is proven
## Edge Deployment: Neo and IoT Greengrass
- Neo provides a way to deploy trained models to edge devices e.g. NVIDIA Jetson
- Code is compiled and optimized for chosen device
- Good for very-low latency applications e.g. embedded applications or applications where internet is not available
- IoT greengrass delivers Neo compiled modeleds to an actual edge device
## Security
- General best practices:
	- Use IAM service to set up accounts by the principal of least access
	- Use MFA
	- Use encrption in transit (SSL/TLS)
	- Use Cloudtrail to log API and user activity
	- Use encryption at rest
- AWS Key Management Service ([[Key Management Service|KMS]]) is accepted by notebooks and all SageMaker jobs to encrypt data at rest
- S3 buckets can be encrypted for training data and hosting models, potentially with [[Key Management Service|KMS]]
- All sagemaker traffic supports SSL/TLS
- IAM roles are assigned to SageMaker to give it permissions to access resources
- When doing distributed training, communications between nodes can be encrypted but this will increase training time
- Sagemaker does not support resource based policies, but supports authorization based on resource tags
- Granular [[IAM]] Permissions:
	- CreateTrainingJob
	- CreateModel
	- CreateEndpointConfig
	- CreateTransformJob
	- CreateHyperParameterTuningJob
	- CreateNotebookInstance
	- UpdateNotebookInstance
- Predefined policies:
	- AmazonSageMakerReadOnly
	- AmazonSageMakerFullAccess
	- AdministratorAccess
	- DataScientist
- [[Cloudwatch]] can log, monitor, and alarm endpoints and their latency/health
- Cloudwatch can monitor number of human workers on Ground Truth
- Cloudwatch metrics are available at a 1-minute frequency
- [[CloudTrail]] records actions of users, roles, and services within SageMaker
- CloudTrail does not monitor calls to InvokeEndpoint
- For further reading, reference the "Infrastructure Security" in the SageMaker developer guide
### Virtual Private Cloud (VPC)
- All training jobs run in a [[Virtual Private Cloud]]
- Private VPCs can be setup for a training job
- To connect a private VPC to S3 data, S3 VPC endpoints must be setup
- These VPC endpoints are secured with their own policies and S3 bucket policies
- SageMaker Notebooks are internet-enabled by default
- If internet access is disabled for [[SageMaker Notebooks|notebook]]s, and interface endpoint ([[PrivateLink]]) or NAT Gateway and configure this to allow outbound connections
- Training and inference containers are also internet-enabled - these can be isolated from the network but this prevents S3 access
## Managing Resources
- In general, use GPUs for deep learning training
- Inference is less demanding an can be run on CPU instances
- Managed spot training can use EC2 spot instances for training for large cost savings
- Checkpoints should be used so training can be resumed if/when spot instances are interrupted
- Automatic scaling can dynamically adjust resources used according to current load
### Elastic Inference (EI)
- Used to accelerate deep learning inference
- EI accelerator is coupled with CPU instance
- This gives benefits of a GPU but for cheaper
- Can be applied to notebooks, Tensorflow/MXNet containers
- Works with Image Classification and ObjectDetection built-in algorithms
### Availability Zones
- When using multiple instances in production, sagemaker automatically attempts to distribute these accross availability zones
- VPC's should have a subnet for each availibility zone
## Serverless Inference
- Fully managed inference service
- Container, memory requirement, and concurrency are specified
- Capacity is automatically provisioned and scaled
- Can be monitored from cloud watch
## Inference reccomender
- Reccomends best instance type & config for models
- Benchmarks different instance types on a given model
- Can perform custom load tests to guarantee performance
## Inference Pipelines
- Can deploy inference via a sequence of 2-15 containers
- Any combination of pre-trained built in algorithms or custom containerized algorithms work
- Can handle real-time inference and for batch transforms
## SageMaker Notebooks
[[SageMaker Notebooks]]
- Only files and data saved within the /home/ec2-user/SageMaker folder persist between notebook instance sessions. Files and data that are saved outside this directory are overwritten when the notebook instance stops and restarts.
- Notebook access any s3 bucket with "sagemaker" in its name with default [[IAM]] permissions
## Distributed training
- Two modes - fully replicated and sharded by S3 - set in "S3DataSource/S3DataDistributionType" in sagemaker config
- Fully replicated - full dataset given to all nodes
	- Increased model stability
	- Scaling resource usage
	- Good for smaller data amounts
- Sharded by S3 - data chunked into smaller keys by S3 key
	- Good for larger data amounts
	- Faster training
	- Each model exposed to only a subset of data
- Use Horovod to distibute training
