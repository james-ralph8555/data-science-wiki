- Fully managed recommender engine - same one used by Amazon
- Fed in data from past purchases, ratings, impressions, cart adds, catalog, user demographics
- Explicted schema provided in Avro format
- Data can be provided with [[S3]] or in real time via API calls
- Will reccomend popular items for users with no data (new users)
- Can provide contextual reccomendations based on device type or time
- Hyperparameters:
	- hidden_dimension - automaticall optimized
	- back-propogation through time (bptt) - enabling gives higher weight to recent events via [[Recurrent Neural Networks|RNN]]
	- recency_mask - weights recent events more
	- min/max_user_history_length_percentile - filters out robots/webcrawlers
	- exploration_weight - controls relevance of items to uesrs
	- exploration_item_age_cut_off - controls how far to look back for reccomendations
- Security for user data (stored in [[S3]]) access is controlled via [[IAM]]
