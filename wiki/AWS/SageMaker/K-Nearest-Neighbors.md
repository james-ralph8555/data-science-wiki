---
aliases: [KNN]
tags:
  - Classification
  - Regression
  - Clustering
---
- Simple classification or regression algorithm
- Classification works by finding the K closest points and returning the most frequent label
- Regression works by finding the K closest points and averaging their values
- Input format is recordIO-protobuf or CSV training, with first column as the label
- Uses file or pipe mode for both
- Sagemaker samples the data and performs dimensionality reduction to optimize algorithm
- Hyperparameters:
	- K - number of nearest neighbors to look at
	- Sample_size
- Trains on CPU or GPU instances