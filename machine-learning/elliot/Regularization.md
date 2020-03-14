Why Regularization?

1. Dealing with multicollinearity (when X variables are linearly related):
Consider why we regularize in a regression context: We need to constrict the model from being too flexible. Applying the correct amount of regularization will slightly increase the bias for a larger reduction in variance. The classic example of this is adding polynomial terms and interaction effects to a regression: In the degenerate case, the prediction equation will interpolate data points, but probably be terrible when attempting to predict the values of unseen data points. Shrinking those coefficients will likely minimize or entirely eliminate some of those coefficients and improve generalization.





Sources:
[Stack Exchange](https://stats.stackexchange.com/questions/168622/why-is-multicollinearity-not-checked-in-modern-statistics-machine-learning)

[When is collinearity a problem?](http://www.biom.uni-freiburg.de/Dateien/PDF/collinearity-a-review-of-methods-to-deal-with-it-and-a-simulation-study-evaluating-and-their-performance)
