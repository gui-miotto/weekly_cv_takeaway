---
layout: post
title:  "How to avoid machine learning pitfalls: a guide for academic researchers"
date:   2022-08-10 00:00:00 +0200
categories: ml best_practices
link: https://arxiv.org/abs/2108.02497
---

#### My remarks

- Excellent paper for beginners. But more experienced researchers may also profit from this reading, given how common some of those pitfalls are.

- Some of the recommended practices are difficult to apply to deep learning because they require training and evaluating multiple models. The computational costs may be prohibitive. Nevertheless, it is vital to understand the limitations of single evaluations.

#### Takeaways

- Before building the model:
    - Understand the data. Make some exploratory data analysis on the training set. If the dataset is described in a paper, read it.
    - But don't look into the test set.
    - Check if you have enough data. If not, you could generate more with data augmentation techniques and use cross-validation for a more efficient use of the existing data.
	- Talk with domain experts. It may prevent you from tackling the wrong questions or formulating your ML problem in the wrong way.
	- Review the literature. Someone else may have already solved your problem. Also, your method may have already been tried with a negative outcome.
	- Keep in mind how you want to deploy your model. Are there any time, memory, or energy constraints?

- Building the model:
	- Make sure the test data will not leak into the training process. The test dataset should be used just for the model's final evaluation. For things like hyperparameter optimization or learning curve monitoring (e.g. for early stopping) use a validation dataset (or cross-validation).
	- Try different models. This is easy to do with libraries like scikit-learn. There is no single best ML model for all problems.
	- But don't use inappropriate models. Models have assumptions. Check if your problem complies with these assumptions.
	- Tune the model's hyperparameters. There are many tools out there that do this automatically (AutoML).

- Evaluating the model:
	- Evaluate the models multiple times. ML models may be unstable. Train multiple models with different random seeds and cross-validation. Evaluate all of them and report results in terms of mean and standard deviation.
	- Carefully choose the evaluation metric. For instance, don't use accuracy with imbalanced data; other metrics, such as Cohen's kappa coefficient (k) and Matthews Correlation Coefficient (MCC) are better suited for this situation.
	- Consider using an ensemble of models. Ensemble learning techniques, such as boosting, bagging, and stacking, are known to perform well in many situations.

- Comparing models:
	- A higher accuracy does not necessarily mean a better model. When comparing two models, one has to evaluate both models many times and use statistical tests, such as McNemar's test, to compare their performance.
	- Use a correction factor when comparing multiple models. If you are comparing more than two models using a series of pair-wise statistical tests, you have to use a correction factor such as the Bonferroni correction to account for the multiplicity effect.
	- The results from community benchmarks may be misleading. There is no guarantee that the researchers used the test set just once. Also, small performance improvements may not be statically significant.
	- Even statistical tests may be misleading. Different tests may yield different conclusions. Also, given enough data, it is easier to make small performance differences seem statistically significant. It is beneficial to include a measure of effect size, such as Cohen's d or the Kolmogorov-Smirnov statistics.

- Reporting the results:
	- Be honest and transparent. It is good to share your code along with a script that runs all the experiments used in your paper. Write clean and well-documented code.
	- Report performance in many forms. Use multiple datasets and performance metrics.
	- Don't make claims not supported by the data. There are limits to what can be inferred from an experimental study. If a model performs well on a dataset it does not mean it will also do so in the real world or even on another dataset.
	- Look inside your model and try to understand how they reach their decisions. This will enrich the scientific contribution of your work. For deep learning, one could try explainable AI (XAI) techniques.
