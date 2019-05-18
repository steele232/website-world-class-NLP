If you’re working in a company on a Machine Learning project, you know that there are often pressures coming from a few different directions that help to shape the project’s objectives.

If you make a change to you machine learning and it seems to help achieve 2 of the 5 project objectives but creates decreases in 1 or more other project objectives, how do you decide whether or not to keep the change. How do you know what “progress” is?

One great practice for this is to create a Single Numeric Evaluation Metric. Often this is the % of correct classifications on a test or cross-validation set. That could be summed up as the % accuracy. That works well for many applications, but not for ***applications with Skewed Classes.

With Skewed Classes, we learned that Precision and Recall are valuable metrics for understanding if the model is progressing, but ***F Scores make it possible to take both the Precision and Recall values and create a Single Numeric Evaluation Metric.