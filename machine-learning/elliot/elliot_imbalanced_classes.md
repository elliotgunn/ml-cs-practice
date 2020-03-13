# Imbalanced Classes

These are my personal notes on dealing with severely imbalanced classes in machine learning. Note: much of it has been taken verbatim from the resources cited below.

Example job interview question from [here](https://www.reddit.com/r/MachineLearning/comments/c1vxoc/d_17_interviews_4_phone_screens_13_onsite_5/):
> Suppose you have a binary classifier (logistic regression, neural net, etc...), how do you handle imbalanced data sets in production?

The problem is that the distribution that you trained on and the distribution you are predicting on are different. This is a well-known cause of failure of ML methods in production.

First, know your data. Know what the model is used for, why there is imbalance in the data. Why is the model doing badly in production? Were there outliers that skewed your data (and/or bad data)? Is the training data from the same distribution as the data seen in production? Are the two classes easily separable? Is the chosen model/features correct? These will guide your methodological approach. For instance, if the imbalance comes from non-random missing values, then that requires a very different approach (see: [sample selection bias](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.92.170&rep=rep1&type=pdf)).

Adjust thresholds/cutoffs: most standard binary classification models (logistic regression, random forest, gbm etc.) output probabilities and default threshold is usually 0.5. By lowering this threshold you can make the model predict more from minority class and prevent the model putting everything into the majority class. You can do this with a model already in production and do not need to retrain. The easiest way to do this is with an ROC curve as it calculates sensitivity & specificity across a continuum of cutoffs.
- Example of adjusting prior probabilities: [thresholding with working code](https://mateuszbuda.github.io/2018/09/15/thresholding.html).
- How to choose a cutoff?
    - Finding a point on the ROC curve that is closest to the perfect model (100% sensitivity and specificity)
    - Using Youden's J index (measures the proportion of correctly predicted samples for both the event and nonevent groups)

Keep in mind the impact to the business value. Does this actually affect business metrics? That should orient the approach to everything above. What is the cost of false positives vs. false negatives? The optimization metric should not be accuracy. This is known as cost sensitivity training, as you want to optimize a cost or loss function that differentially weights specific types of errors.
- Use a confusion matrix to compare the predictive performances (especially useful for multi-class data)
- Use the [classification_report](http://scikit-learn.org/stable/modules/generated/sklearn.metrics.classification_report.html) to look at precision, recall, and f1-score.
- Use a precision-recall curve instead of ROC

If the issue is that the training data is skewed but not during production, then take steps to ensure that the training data reflects real-world distribution:
- resampling: downsampling/upsampling plus calibration to adjust the probability scores outputted by the model ([example with working code](https://jmetzen.github.io/2015-04-14/calibration.html))
- class weights: increase weights for the samples in the minority classes
- picking the right model: GBC (or boosting algorithms in general) directly address imbalance by sequentially training based on incorrectly classified examples

Questions to ask for more information:
- Why is the model doing badly in production? Outliers? Bad training data? Is the training data the same distribution as the one seen in production?
- Did you pick the right model for binary classification? SVM is more robust as not just fitting a single hyperplane but maximizing the margins. If the dataset is too small, try a Bayesian approach with a strong prior. Try [thresholding method (with code)](https://mateuszbuda.github.io/2018/09/15/thresholding.html).
- Feature engineering: did you pick the right features?

Answers taken from:
- [Reddit](https://www.reddit.com/r/MachineLearning/comments/c1vxoc/d_17_interviews_4_phone_screens_13_onsite_5/)
- [StackExchange](https://datascience.stackexchange.com/questions/1107/quick-guide-into-training-highly-imbalanced-data-sets)
- [Applied Predictive Modeling, chapter 16](http://appliedpredictivemodeling.com/)
- [Practical tips for class imbalance in binary classification](https://towardsdatascience.com/practical-tips-for-class-imbalance-in-binary-classification-6ee29bcdb8a7)
