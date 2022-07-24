---
aliases: [PCA]
tags:
  - "DimensionalityReduction"
---
- Unsupervised dimensionality reduction - projects features into lower dimensional space with minimal information (variance) loss
- Components in lower dimensional space are meaningless to humans but retain information so they are useful for statistical algorithms
- Input is recordIO-protobuf or CSV in pipe or filemode
- Works by computing covariance matrix and reducing it with singular value decomposition
- Can work in regular mode which uses all data, or randomized mode for large datasets which approximates data
- Hyperparameters:
	- Algorithm_mode - regular or randomized
	- Subtract_mean - unbiases data
- Can use GPU or CPU