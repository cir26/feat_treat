# feat_treat
Docs related to the feat_treat() object class created for simplifying machine learning tasks, including tuning of hyperparameters for select ML algorithms.

*Currently supported algorithms include:*

***Classification -*** *Logistic, Random Forest, Extreme Gradient Boosting (XGB), Support Vector, and Multi-layer Perceptron Neural Network.*

Wraps other classes (e.g. sci-kit learn, skopts, imblearn, numpy, etc.) to reduce syntax and simplify redundant feature treatment tasks.
Stores and prints performance metrics as it goes and returns quick visual summary.


# Quick Start: Requirements
The following dependencies should be installed in your working environment before getting started (using pip install): 

pandas >= 0.24.2 

numpy >= 1.16.2

matplotlib >= 3.0.3

scipy >= 1.2.1

scikit-learn >= 0.21.2

imblearn == 0.5.0

scikit-optimize == 0.6.0

*If you installed python via Anaconda Navigator then you only require imblearn and scikit-optimize*


# Quick Start: Installing Feat_Treat Package
To install Feat_Treat use the following statement at the command line:

``` 
$ pip install git+https://github.com/cir26/feat_treat 
```


# Quick Start: Using Feat_Treat
Feat_Treat methods/functions are split up into multiple modules which can all be imported using the following statement:

``` 
from Feat_Treat.main import feat_treat
```

From here, a data object can be created by passing the feature dataframe and the target series as arguments to the function `feat_treat()`. Optionally, a random_state can be provided. For example,

``` 
data = feat_treat(X=feature_set, y=target_set, random_state=42) 
```

Now `data` is an object which can be operated on using methods defined in the Feat_Treat class. 
For example, the following `tune_test` method uses `data` to train a Random Forest classifier with bayes gradient boosted regression tree hyperparameter tuning optimization based on the area under the reciever operating characteristic curve with a 80/20 train/test split and 5-fold validation during tuning.

```
data.tune_test(model=RandomForestClassifier, tuning_iter=10, tuning_strategy='bayes:gbrt',  tuning_metric='roc_auc', test_size=0.2, kfold=5, n_jobs=-1)
```

