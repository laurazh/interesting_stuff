# Way to handle categorical data

## Transform with count
- A simple transformation for a categorical data is to use its frequency as a feature

[see how to do it](https://stackoverflow.com/questions/22391433/count-the-frequency-that-a-value-occurs-in-a-dataframe-column)

df['a'].value_counts()


## Label encoding
- scikit learn library includes a method to label encode
- to includes pics
- [scikit learn label encode](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html)
- a dictionnary is also provided to retrieve the link between the original data and the label encoded one
- There are also different library providing label encoding method such as Keras



## One hot encoding
- The downside of the label encoding is that it gives a herarchy within the feature 
blue => 1
pink => 2
green => 3

inculde pics

However, it may not hold any meaning for some cases. That is why one_hot encoding is used.

Thaksfully scikit learn also has a method for this.
Another way to do it, is to use the get_dummy function

## Feature hashing
http://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.FeatureHasher.html
- If label encoding and one ot encoding where not satisfactory, the feature hashing method can also be used
- It transform a category to a vector
- the downside of this method is that once you transform your data, you will not be able to go back to the original one. There is no dictionary between the original/hashed data.
- the hashing method used is Murmurhash3

Another great libary for encoding is scikit-learn contrib, there is a special library for [categorical data](https://github.com/scikit-learn-contrib/categorical-encoding)

## Entity embedding
- Entity embedding is a new method that is more and more used in competition.
- It transforms a category to a vector
- paper [Entity Embeddings of Categorical Variables](https://arxiv.org/pdf/1604.06737.pdf) - Cheng  Guo and  Felix  Berkhahn
-  github link (https://github.com/entron/entity-embedding-rossmann)
- [example of implementation in kaggle](https://www.kaggle.com/aquatic/entity-embedding-neural-net)
- explanation detail _ https://medium.com/@satnalikamayank12/on-learning-embeddings-for-categorical-data-using-keras-165ff2773fc9
- 
