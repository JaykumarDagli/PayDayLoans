This is a min project in which we learn non linear supervised modelling techniques - Decision trees, Random forest and Extra trees

# PayDayLoans

## Decision Trees

- Decision tree is one of the machine learning algorithms used in regression as well as classification problems. The way this algo works is that it contains multiple nodes [a binary question] according to which each record is verified and classified into different buckets. The last node which does not have any further classification is called terminal node [leaf node].
- After the buckets are formed, for classification we can check the majority and decided which class will represent the specific bucket and in case of regression we can just take avg of different values
- How are the questions formed? Questions are formed on how data is present in the dataframe
    - For categorical [which are converted to dummies in cleaning] we ask if specific value exists or not
    - For numerical we choose a range and qts are formed accordingly
    - None of this is manual, all is in the backend
- But sometimes, there is no clear majority when solving a classification problem i.e. which classes are correctly predicted by the algorithm and thus we choose a metric → gini or entropy
    - These are both based on the concept of homogenity i.e. one bucket should have one specific class majority

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a51a9bf0-3368-49f5-bdad-73aa5d7d89b7/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a51a9bf0-3368-49f5-bdad-73aa5d7d89b7/Untitled.png)

    Formula [p is prob of a single class]

    - Among these, which can choose any one as per convinience
    - Just that the value should be as low as possible for a better classification. Based on who provided better homogenity, a rule is chosen that gives least value of gini/entropy whichever is chosen
    - In Regression problem, we choose the rule that gives least value of sum of square
- Hyper parameters:
    1. Criterion: Gini or Entropy 
    2. Max depth: if none, the tree will expand until all nodes are terminal nodes i.e. all nodes are pure OR until all leaves contain less than min samples split 
    3. Max leaf nodes does the same thing i.e. we can give the number of leaf/terminal nodes that we will accept. Choose one → either max depth or max leaf nodes!
    4. Min sample split: minimum number of samples required to split an **internal node** [can be between 5-10 as it may lead to overfitting]
    5. Min sample leaf:  minimum number of samples required to split a **leaf** node

## Random Forest and Extra trees

- The best thing about decision tree is that it can capture non linear patterns unlike linear/logistic regression but this only is the issue, that it will overfit the model i.e. it captures niche patterns which is opposite of what we want i.e. we want generalised patterns which does not happen, Thus we use Random Forest
- RF: Build multiple decision trees on random subset of data to cut out the noise/niche patterns, at each node a random subset is chosen and rules which give the best result are taken to build the trees.
- Hyperparameters: **Number of estimators**: number of trees to be used to build a forest, **max features**: number of festures to be selected at a node and **bootstrap**: if we need to select features with replacement or without it, value is either True/False
- Decsion tree as well as Random forest are essentially 'black box' i.e. no one know which parameters are selected, which are not, what rule is applied and if the performance can still be improved. To make sense of these models, **feature importance** parameter is very important,
- **rf.feature_importances_** will share how important each feature is, using which we can select the best features and build another model like a linear/logistic regression where contribution of each feature can be checked
- **Extra trees [Extreme random forest]** is same as random forest, just that at every split in random forest, the **best splitter** is used [meaning rule which results in best gini/entropy is chosen in RF] but in ET, random splitter is chosen and the prediction is made. It is simply faster than random forest.
