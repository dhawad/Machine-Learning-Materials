 - ## Materials
 
    - [Machine Learning](#Machine Learning)
    - [Python](#Python)
    - [Github Link](#Github)

 ## Machine Learning

This repository includes materials on different topics of machine learning algorithms.

- [ ] [Adaptive Boosting](http://www.cs.princeton.edu/courses/archive/spr07/cos424/papers/boosting-survey.pdf)
- [ ] [XGBoost](http://proceedings.mlr.press/v42/chen14.pdf)
- [ ] [Random Forest](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) 
- [ ] [NLP with Deep Learning](http://web.stanford.edu/class/cs224n/syllabus.html)
- [ ] [Word Embedding - Analytics Vidhya](https://www.analyticsvidhya.com/blog/2017/06/word-embeddings-count-word2veec/)
- [ ] [Word Embedding - Xin Rong](https://www.youtube.com/watch?v=D-ekE-Wlcds)
- [ ] [CNN](http://brohrer.github.io/how_convolutional_neural_networks_work.html)
- [ ] [Information Value](https://medium.com/@sundarstyles89/weight-of-evidence-and-information-value-using-python-6f05072e83eb)
- [ ] [Kmeans for Beginners](https://www.youtube.com/watch?v=YWgcKSa_2ag)
- [ ] [AdaBoost - Special Case of Gradient Boost](https://www.youtube.com/watch?v=ErDgauqnTHk)
- [ ] [Gradient Boost](https://www.youtube.com/watch?v=sRktKszFmSk)
- [ ] [Gradient Boost and XGBoost](https://www.analyticsvidhya.com/blog/2018/09/an-end-to-end-guide-to-understand-the-math-behind-xgboost/)


 ## Python
- [ ] [Pydata](https://www.youtube.com/user/PyDataTV)
- [ ] [Enthought](https://www.youtube.com/user/EnthoughtMedia) 

 ## Github 

- [ ] [Analytics Vidhya Github References](https://www.analyticsvidhya.com/blog/2018/08/best-machine-learning-github-repositories-reddit-threads-july-2018/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+AnalyticsVidhya+%28Analytics+Vidhya%29)

### Machine Learning Questions

This section contains notes/summaries/questions on some of Machine Learning topics.
 
 
## Decision Trees and Random Forest

### How does the basic decision tree algorithm work ?
The decision tree algorithm tries to unmix the data at each node by asking questions that makes the two separated datasets most homogenous. The homogenity of the data is quantified using GINI impurity and at each node questions are asked such that the decrease in the Gini impurity is the maxiumum. This decrease in the impurity is called information gain. GINI impurity is basically the chance of being incorrect if we randomly assign a label to an example in the same set. 

### Parameter Tuning in Decision Trees.
criterion : This parameter determines how the impurity of a split will be measured. The default value is “gini” but you can also use “entropy” as a metric for impurity.
max_depth: This determines the maximum depth of the tree. The default value is set to none. This will often result in over-fitted decision trees. The depth parameter is one of the ways in which we can regularize the tree, or limit the way it grows to prevent over-fitting.
min_samples_split: The minimum number of samples a node must contain in order to consider splitting. The default value is two. You can use this parameter to regularize your tree.
min_samples_leaf: The minimum number of samples needed to be considered a leaf node. The default value is set to one. Use this parameter to limit the growth of the tree.
max_features: The number of features to consider when looking for the best split. If this value is not set, the decision tree will consider all features available to make the best split. Depending on your application, it’s often a good idea to tune this parameter
splitter: This is how the decision tree searches the features for a split. The default value is set to “best”. That is, for each node, the algorithm considers all the features and chooses the best split. If you decide to set the splitter parameter to “random,” then a random subset of features will be considered. The split will then be made by the best feature within the random subset.

### How does the random forest overcome the short-comings of a decision tree ?
Building decision trees require algorithms capable of determining an optimal choice at each node. One popular algorithm is the Hunt’s algorithm. This is a greedy model, meaning it makes the most optimal decision at each step, but does not take into account the global optimum. What does this mean? At each step the algorithm chooses the best result. However, choosing the best result at a given step does not ensure you will be headed down the route that will lead to the optimal decision when you make it to the final node of the tree, called the leaf node.
Decision trees are prone to overfitting, especially when a tree is particularly deep. This is due to the amount of specificity we look at leading to smaller sample of events that meet the previous assumptions. This small sample could lead to unsound conclusions.One way to combat this issue is by setting a max depth. This will limit our risk of overfitting; but as always, this will be at the expense of error due to bias.This is a simpler model with less variance sample to sample but ultimately will not be a strong predictive model.

Ideally, we would like to minimize both error due to bias and error due to variance. Enter random forests. Random forests mitigate this problem well. A random forest is simply a collection of decision trees whose results are aggregated into one final result. Their ability to limit overfitting without substantially increasing error due to bias is why they are such powerful models.
One way Random Forests reduce variance is by training on different samples of the data. A second way is by using a random subset of features. This techique is known as bagging.

### Does Random Forest overfit ?

No. It uses bagging technique which generates several decision trees in parallel also known as base learners. Data sampled with replacement is fed to these learners for training. The final prediction is the averaged output from all the learners. Individual tress might have high variance, but the bagging method eventually reduces variance.


### Decorrelating Trees

In Ensemble Technique (RF, GBM, GRB) , trees are decorrelated to reduce variance. Random Forest uses bagging in which number of features are selected at random and then from those features splitting criteria is decided. In this way , every tree is pretty much different from each other. 

In Boosting technique , same is done by giving weights to misclassified rows. 

### Shallow and Bushy trees

In Boosting trees, depending on problem statement one might get shallow tress as compared to those in RF. Boosting trees grow shallow trees because it can wait for later trees to grow in depth where it has not done well in terms of predictions. In Random Forest trees are independent and identically distributed , so each trees have to grow at much larger depth to identify patterns. This causes high variance which is reduced by averaging out. 

Source : https://www.youtube.com/watch?v=wPqtzj5VZus @42:05 


  
## Boosting Techniques
### Adaboost
Adaboost works by giving higher weightage to misclassification and lower weightage to correct classification. 
For eg. 
Lets say total number of rows = 1000
initial weightage to each rows = 1/1000
correct classification =  200
misclassification = 800
learning rate = 0.1
weightage to rows of correct classification = (e^-0.1)/sum of numerator = 720
weightage to rows of incorrect classifcation = (e^0.1)/sum of numerator = 220
Hence , 20 rows from 200 misclassfied is duplicated to get 220 rows. This might results in overfitting.
The next model is built. 
At the end of n trees, weighted sum of predictions is taken into account. 
More is the error rate, less is the weightage given to trees.

### Gradient Boost
This algorithm boost weak classifer in different ways. It uses gradient descent of loss function to reduce its misclassification.   
An initial prediction is made. Its residual(Actual - Predcition) is calculated. Residual is nothing but a gradient of loss function. For the next model, this residual will be target variable. The way it differs from another algorithm like logistic is , GBM uses gradient descent for every rows rather than gradient descent at the end of each iterations. This makes the algorithm prone to outliers.
Gradient Boost works well if there is good differences between classes. However, if data is noisy it might look to fit each pattern and might overfit.

### Extreme Gradient Boost
Regularization , Penalise model for its complexity eg for number of trees or leaves by giving weights 
Works well on sparse data (eg tfidf)
Also GBM and XGB works on greedy search to decide  splitting criteria.
 
### How to see relationship of features with target variable.

  <img src="https://github.com/Adi1729/Machine-Learning-Materials/blob/master/model_interpretation_ensemble.png" width = 80%,  height = 80%>

## K-Means Clustering

### How does K-Means Clustering Work?
Imagine a bunch of random points on a X-Y plane. Suppose if we try to find 3 clusters within this data, the algorithm would first choose 3 random points as 3 centroids from the data and calculate the eucledian distances between the each centroid. Based on these distances, 3 clusters would be formed such that all the points within that cluster is closer to the centroid. Finally the algorithm would calculate the centroids once again by taking the mean of all the points within the cluster. The process is repeated iteratively until the centroids stop changing. 

### How to determine the number of clusters ?
As the number of clusters increase, variation (sum of squares criterion) in data decreases. Variation is zero when the number of clusters is equal to number of data points. If we plot the reduction in variation vs number of clusters, we see that at certain point increasing the number of clusters decreases the variation the maximum. This plot is called the "elbow curve".
[link](https://www.youtube.com/watch?v=4b5d3muPQmA)

### Drawbacks of sum of Squares Criterion in K-means clustering.
  Inertia, or the within-cluster sum of squares criterion, can be recognized as a measure of how internally coherent clusters are. It suffers from various drawbacks:

   1. Inertia makes the assumption that clusters are convex and isotropic, which is not always the case. It responds poorly to elongated clusters, or manifolds with irregular shapes.                                                                            
   2. Inertia is not a normalized metric: we just know that lower values are better and zero is optimal. But in very high-dimensional spaces, Euclidean distances tend to become inflated (this is an instance of the so-called “curse of dimensionality”). Running a dimensionality reduction algorithm such as PCA prior to k-means clustering can alleviate this problem and speed up the computations.
   
   <img src="https://github.com/Adi1729/Machine-Learning-Materials/blob/master/kmeans.png">
   
### LDA
-> K-Means is going to partition the n documents into k disjoint clusters whereas LDA tries to assign a document to a mixture of k different topics.
[link](https://www.youtube.com/watch?v=DWJYZq_fQ2A)


### Word2Vec Models
-> Captures the semantic sense of the document. For similar words, dot product would be on the higher side.
-> CBOW : Continous Bag of Words : Use the context word to predict the middle word.
   Skipgram: Use the middle word to predict the context.
-> Basically is a one layer neural network. In CBOW method the sentence like "My name is Aniket" is such that words "my","is","Aniket" would be used as input and "name" would be kept as output and the neural network is trained like this. One Hot encoding is used to train the model. Finally we would get an embedding matrix as a word embedding for every word in the corpus as the hidden layer of the neural network.





## Logistic Regression

### Is logistic regression a linear or a non-linear model ?
Logistic regression is considered a linear model as the decision boundary would be a linear function of x i.e. the predictions can be written as linear combination of x.

if p=1/(1+ e^(-z)) and if p=0.5 is the threshold then z=0 is the decision boundary.
[link1](https://stats.stackexchange.com/questions/93569/why-is-logistic-regression-a-linear-classifier)
[link2](https://www.quora.com/Why-is-logistic-regression-considered-a-linear-model)


### Why can't we use the cost function of Linear Regression in Logistic Regression?
If we try to use the cost function of the linear regression in ‘Logistic Regression’ then it would be of no use as it would end up being a non-convex function with many local minimums, in which it would be very difficult to minimize the cost value and find the global minimum. So we define the log cost function for logistic regression which is quite convex in nature.
Below is short explaination for it.
"In case y=1, the output (i.e. the cost to pay) approaches to 0 as y_pred approaches to 1. Conversely, the cost to pay grows to infinity as y_pred approaches to 0. This is a desirable property: we want a bigger penalty as the algorithm predicts something far away from the actual value. If the label is y=1 but the algorithm predicts y_pred=0, the outcome is completely wrong."
[link1](https://www.internalpointers.com/post/cost-function-logistic-regression)
[link2](https://towardsdatascience.com/introduction-to-logistic-regression-66248243c148)

### Can Logistic Regression be used for multiclass classification ?
Yes, using one-vs-all classification. Suppose there are 3 different classes we want to predict. We would train 3 different classifiers for each class i to predict the probability that y=i and then finally take the class that has the max probabilty while prediction.


### Is standardization required in logistic regression?
Standardization isn't required for logistic regression. The main goal of standardizing features is to help convergence of the technique used for optimization. It's just that standardizing the features makes the convergence faster.


### AIC ?
[link](https://www.methodology.psu.edu/resources/aic-vs-bic/)

### What is L1(Ridge), L2(LASSO) regularization ?
Regularization is a technique to discourage the complexity of the model. It does this by penalizing the loss function. This helps to solve the overfitting problem.
In L1 regularization we change the loss function to this:

L1 regularization does feature selection. It does this by assigning insignificant input features with zero weight and useful features with a non zero weight.

L2 regularization forces the weights to be small but does not make them zero and does non sparse solution. L2 is not robust to outliers as square terms blows up the error differences of the outliers and the regularization term tries to fix it by penalizing the weights.

[link](https://medium.com/datadriveninvestor/l1-l2-regularization-7f1b4fe948f2)



## Things to be added.
1. Complete workflow of a data science project.
2. Doc to vec models
3. Precision, Recall, lift charts, ROC curves.
4. When to use a particular model.




 
  
  
  
  
