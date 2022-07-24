• How to detect: training loss keeps decreasing, validation loss stays the same or goes up
• Causes: Model structure too complicated/large for data
• Increase regularization with
	- Dropout
	- Batch Normalization
	- Decreasing model size - network width/depth for NN
	- L1/L2 regularization
	- Early stopping
	- More training data
• Can adjust model specific hyperparameters tuning:
	- max_depth and min_samples_leaf for random forest/decision tree
	- K for [[K-Nearest-Neighbors|KNN]]
	- Regularization and Eta/Subsample parameters for [[XGBoost]]