---
tags:
  - AnomalyDetection
---
- Finds suspicious logins by IP address in web logs
- Input data is usernames or account IDs paired with an IP address paired with an IP address
- Works by using a neural network to learn latent vector representations of entities and IP addresses
- Automatically generates anomalous samples during training by randomly pairing usernames or account IDs with different IP addresses
- Hyperparameters:
	- Num_entitiy_vectors - controls hash size.  Values too large slow down algorithm, but values too small can cause hash collision issues.  Reccomended to set to 2x the number of unique usernames/account IDS
	- Vector_dim: size of embedding vectors - too large can result in overfitting
	- Standard neural net hyperparameters
- GPU reccomended for training since it is neural network based, but CPUs can be used too