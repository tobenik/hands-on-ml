# Exercises for chapter 4 - Training models

1. **Which linear regression training algorithm can you use if you have a training set with millions of features?**

   _Gradient descent works well when there are a large number of features. If the sample size is large, then prefer stochastic or mini-batch gradient descent._

2. **Suppose the features in your training set have very different scales. Which algorithms might suffer from this, and how? What can you do about it?**

   _Gradient descent algorithms suffer from irregular coefficients on features (normal equation doesn't mind), so you should run the features through a scaler like sklearn's `StandardScaler()`_

3. **Can gradient descent get stuck in a local minimum when training a logistic regression model?**

   _No, because the cost function is convex (ie. the needle is at the bottom of the bowl)_

4. **Do all gradient descent algorithms lead to the same model, provided you let them run long enough?**

   _No, because the learning rate can be too high or too low, and the algorithm can get stuck in a local minimum_

5. **Suppose you use batch gradient descent and you plot the validation error at every epoch. If you notice that the validation error consistently goes up, what is likely going on? How can you fix this?**

   _Sounds like the learning rate is too high and the model won't converge. You should lower the learning rate._

6. **Is it a good idea to stop mini-batch gradient descent immediately when the validation error goes up?**

   _No because the model might be overfitting. A better way is to establish a threshold of epochs to pass since the last minimum before stopping training._

7. **Which gradient descent algorithm (among those we discussed) will reach the vicinity of the optimal solution the fastest? Which will actually converge? How can you make the others converge as well?**

   _Stochastic GD will reach the vicinity of the optimal solution the fastest, but it won't converge. Batch GD will converge, but it's slower. You can make the others (stochastic & mini-batch) converge by using a learning schedule (ie. decreasing the learning rate as epochs pass)._

8. **Suppose you are using polynomial regression. You plot the learning curves and you notice that there is a large gap between the training error and the validation error. What is happening? What are three ways to solve this?**

   _The model is overfitting. You can solve this by reducing the polynomial degree, regularizing the model, or increasing the size of the training set._

9. **Suppose you are using ridge regression and you notice that the training error and the validation error are almost equal and fairly high. Would you say that the model suffers from high bias or high variance? Should you increase the regularization hyperparameter α or reduce it?**

   _The model is underfitting, so it suffers from high bias. You should reduce the regularization hyperparameter α._

10. **Why would you want to use:**

    1. Ridge regression instead of plain linear regression (i.e., without any regularization)?
       1. Regularization helps prevent overfitting
    2. Lasso instead of ridge regression?
       1. Lasso drives some coefficients to zero so it can be used for feature selection
    3. Elastic net instead of lasso regression?
       1. Lasso can behave erraditacally when the number of features is greater than the number of samples, so elastic net is a good compromise between ridge and lasso

11. Suppose you want to classify pictures as outdoor/indoor and daytime/nighttime. Should you implement two logistic regression classifiers or one softmax regression classifier?

    _You should implement two logistic regression classifiers because softmax regression is used for multiclass classification. So softmax classifies something as belonging to class A from N classes, while two logistic regression classifiers give two different classes (eg. outdoor, night) which makes more sense here._
