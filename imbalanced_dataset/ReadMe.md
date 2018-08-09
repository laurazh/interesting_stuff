# Strategy to imbalanced
https://machinelearningmastery.com/tactics-to-combat-imbalanced-classes-in-your-machine-learning-dataset/

For a given dataset and its label, if one label is in majority, it is called an imbalanced dataset.
To better train an algo, it is better to have a balanced dataset as it will give a more general algo.



## use different metric
For example, if 90% of my label is "A", if i always predict "A", I will have an accuracy of 90%.
The accuracy has no meaning in my case.
One of the metrics that is "imbalanced data" resilient is to use:
- ROC/AUC
- recall
- F1 score
- confusion matrix

## upsampling/downsampling
if you like your metrics and don't want to touch it, you can still upsampling or downsampling methods.
Meaning that you either downsample the majority class or upsample the minority one.
You can do it randomly, or use other methods as described in the [scikit_learn contib package](https://github.com/scikit-learn-contrib/imbalanced-learn)
to add notebook to see benchmarks

## Outlyer detection
If your dataset have a really high ajority class like 90%, maybe you could also check it the remaining 10% are not just outlyers.
If you have some busness knowledge, it will be easier, but some algo can also do some checks for you:

LSH

Isolation forest
 
 to add notebook
