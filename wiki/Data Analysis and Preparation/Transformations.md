# Transformations
- Applying functions to data may make models perform better on it
- For example, the logarithm of exponentially trending data will give a linear feature
- Categorical data which is originally represented with numbers should be one-hot encoded with some models e.g. neural networks
- Scaling to transform features to a certain mean and range is required with some models such as regressions
- This can be done with [[SciKitLearn]]'s standard scalar (scales to 0 mean/unit variance) or MinMaxScalar (scales to given range)
- Input data should always be shuffled
