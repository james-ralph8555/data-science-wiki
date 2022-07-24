---
aliases: [LDA]
tags:
  - NLP
  - TopicModelling
---
- Unsupervised topic modeling algorithm, not based on deep learning
- Works on other type of data other than documents
- Input format is recordIO-protobuf or CSV
- Each document has counts for every word in the vocabulary (in CSV format)
- Pipe mode only supported for recordIO
- Like [[Neural Topic Model]], the number of topics is specified
- Hyperparameters:
	- Num_topics
	- Alpha0 - initial guess for concentration parameter - smaller values produce sparser topic mixtures while larger values produce more uniform mixtures
- Single instance CPU only for training
