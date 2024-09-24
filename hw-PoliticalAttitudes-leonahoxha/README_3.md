# Exercise on Logistic Regression

In this task we want to use people's attitudes on political topics to predict their voting decisions. 

We start by simply predicting whether they will vote for a "left" party (SPD, Die Linke (Left), Die Grünen (Green)) or a "right" party (CDU/CSU, FDP, AfD).

### Wrangling and preprocessing

1. Remove all participants with `NaN` values on any political attitudes and remove all participants that did not vote for any of the six parties above.  

2. Create a dummy variable, `left_vote`, in the dataframe, which is `1` if a participant voted for one of the left parties and `0` otherwise.  

> Tip: Look at the variable `prtvfde2` and look up how the parties are coded. You may want to use the `isin()` function of a pandas DataFrame.

3. We will need our input matrix `X` which contains peoples' attitudes on several political attitudes (`["imueclt", "euftf", "lrscale", "wrclmch", "gincdif", "freehms", "impcntr"]`) and our target data `left_vote`

4. Scale the data on political attitudes, `X`, using `sklearn`'s `StandardScaler`.


### Regression model and understanding the model

5. Split your data into a test and training sample, using `sklearn`'s `train_test_split`.

6. Do a logistic regression using the political attitudes (`["imueclt", "euftf", "lrscale", "wrclmch", "gincdif", "freehms", "impcntr"]`) to predict the `left_vote` variable. Remember that we only use the training sample! 

> Tip: use `sklearn`'s `LogisticRegression` to define a regression classifier (`log_reg=LogisticRegression()`) and use its functions `log_reg.fit(...)` and `log_reg.predict_proba(...)`. Note that `predict_proba(...)` returns two probabilities per observation, one for `0` and one for `1`! Which is the one that we care about? You may want to save this as `y_pred_proba_test`.

7. Create a variable, `y_pred_proba`, in the dataframe, which stores the predicted probability to vote for a left party for each respondent (both test and training data).

8. Using a boxplot, visualise the probability to vote for a left party predicted by our model on the y-axis over the actual vote of the respondents on the x-axis (both test and training data combined).  

9. What are the three most important predictor variables in your model? Is a high score in these predictor attitudes correlated or anti-correlated with voting a left party? Look at what the questions actually are and think about whether this matches your expectations?

    > Tip: Look at the `coef_` attribute of your regression object. What are these coefficients? What does the sign of the coefficient mean? Select the most important ones and determine which of the attitudes this coefficient corresponds to.

    - Optional (but nice) task: Visualise how the predicted probability to vote for a left party depends on the response for each of these three variables. Again use boxplots to visualise this and use subplots for each of the three variable. Briefly interpret your plots. Does it match your expectations? It should!


### Prediction and decision-making.

10. Predict the `left_vote` variable of your test sample. You may want to do a sanity check by comparing the actual `left_vote` vs. your predicted `left_vote`. They should match often but not necessarily always. 

> Note: the logistic regression prediction `log_reg.predict(...)` uses a threshold of `0.5`, i.e. all observations with probability to vote left higher than 0.5 are classified as left voters. To change that default behaviour you actually need to predict by hand: `y_pred_threshold90 = (y_pred_proba >= 0.9).astype(int) `, where `y_pred_proba` is the the predicted probability of each participant to vote a left party.

11. Print the confusion matrix (using `sklearn.metric`'s `confusion_matrix(y_target, y_predicted)`) of the actual and predicted labels in the test sample using different thresholds (0.1, 0.25, 0.5 (default), 0.75, 0.9). See the note above if you need a tip on how to perform this prediction. What do the values in the confusion matrix correspond to? Think: specificity and sensitivity. Come up with a use case for your model (e.g. you are a right-wing think tank that wants to target the left voters with an advertisement campaign) and choose a threshold that would be suitable to obtain a good sensivity/specificity ratio for your case (see "Making decisions" in the Concepts Lecture). 

12. Plot the ROC-curve using the actual votes and the corresponding predicted probabilities for the test sample. Interpret this in terms of specificity and sensitivity.

> Tip: Look up `sklearn.metric`'s `roc_curve`. What are the outputs? The ROC curve plots the true-positive-rate (i.e. participants that were correctly classified as voters of a left party) over the false-positive-rate (i.e. participants that were classified as voters of a right party but actually voted left). 

13. Determine the AUC metric (using `sklearn.metric`'s `roc_auc_score()` function). 

> Note: there's also a `auc` function, that returns the area under a general curve. Here `roc_auc_score` is probably more straightforward.

## Optional Tasks

Feel encouraged to do the same analysis for predicting whether people vote for a particular party or not (rather than whether they vote a left or a right party).

Perhaps, to reduce plot overkill, focus on one particular question that interests you.For example, one interesting question could be whether a logistic prediction model works better for a small, ideological party (such as the 'Die Grünen (Green)' or 'AfD') than for large parties such as ('CDU/CSU' or 'SPD'). You may want to compare the AUC-score (see 13.) for this.



