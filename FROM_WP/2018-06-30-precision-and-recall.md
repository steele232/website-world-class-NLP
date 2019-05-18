Hello Everyone!

In this article, we will discuss how you can use Precision and Recall as a numerical evaluators to help you know if your machine learning classifier is performing well when your classes are “skewed”.

What do I mean by “skewed classes”? When I am creating a classifier to predict whether a given (random) person has cancer or not (hopefully they don’t),the odds are small that the person does have cancer because less than 99% of people have cancer (I don’t really know, this is just an example). The “classes” are referring to whether or not the person has cancer (1=has-cancer, 0=no-cancer) and so the classes are “skewed” because the is a HUGE difference between the number of people who actually have cancer (1) or have no cancer (0). Because of the “skewed classes”, it would be pretty easy for a classifier to gain 99% accuracy, by just predicting that the person that it’s classifying has NO cancer 100% of the time. That would give it 99% accuracy and 1% error. In many applications, that would be an AMAZING accuracy score for most classification applications, but isn’t valuable in this context; we need to beat that 99% accuracy and if we are measuring by accuracy, it’s hard to know whether the classifier model is making progress or if it’s just predicting 0 more often. This shows that accuracy as a single numerical evaluator is insufficient. That is why we are introducing **Precision** and **Recall**.

Let’s define Precision and Recall:

**Precision: (of all patients where we predicted y=1, what fraction *actually* have cancer?)**

True Positives / # we predicted positives

True Positives / True Positivies + False Positives

**Recall: (of all patients that actually have cancer, what fraction did we *correctly detect* as having cancer?)**

True Positives / # that were actually positive

True Positives / True Positives + False Negatives

## Conclusion.
If a model has high Precision and Recall, it’s probably going to do well. It’s better to use these as your numerical evaluators as you’re seeking to improve your classifier model.

***In the next article, we will talk about how you can take Precision and Recall and turn it into just one number that you can use as your single numeric evaluation metric.