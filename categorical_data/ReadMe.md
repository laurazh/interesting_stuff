# Way to handle categorical data

https://blog.myyellowroad.com/using-categorical-data-in-machine-learning-with-python-from-dummy-variables-to-deep-category-42fd0a43b009

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


--------------------------------
example of code n°1

    model = Sequential()
    no_of_unique_cat  = df_train[categorical_var].nunique()
    embedding_size = min(np.ceil((no_of_unique_cat)/2), 50 )
    embedding_size = int(embedding_size)
    vocab  = no_of_unique_cat+1
    model.add( Embedding(vocab ,embedding_size, input_length = 1 ))
    model.add(Reshape(target_shape=(embedding_size,)))
    models.append( model )
    
example of code n°2

    input_ps_car_11_cat = Input(shape=(1,))
    embedding = Embedding(104, 10, input_length=1)(input_ps_car_11_cat)
    embedding = Reshape(target_shape=(10,))(embedding)
    inputs.append(input_ps_car_11_cat)
    embeddings.append(embedding)
    
for each category/entity
- create an input of shape 1
- create an embedding layer
- reshape to embedding_size


here: 
- vocab=input_dim             => the unique count of the category
- embeding_size= output_dim   => user should define this value 
    - best practice : embedding_size = min(np.ceil((no_of_unique_cat)/2), 50 )

--------------------------------
example of code  n°1:

    model_rest = Sequential()
    model_rest.add(Dense(16, input_dim= 1 ))
    models.append(model_rest)

for the rest of the column/not entiy
- create an input shape (number of columns)
- dense(units) the input => just activation layer
- reshape

At the end 
concatenate the embeddings
