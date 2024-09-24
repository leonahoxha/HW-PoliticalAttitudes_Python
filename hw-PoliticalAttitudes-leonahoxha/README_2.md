# Exercises Part 2


## Principle Component Analysis

We could do the above exercise for each pair of variables, but typically we want to have more effective and meaningful visualisisation. One big part of this is principle component analysis. 

In this exercise, we will do a PCA of the political attitude space in the European Social Survey. We consider the following political attitudes: `["imueclt", "euftf", "lrscale", "wrclmch", "gincdif", "freehms", "impcntr"]`

- First, remove all the observations containing `NaN` in any of the political attitudes or the variable `prtvfde2`, e.g. using `dropna` with the parameters `subset`, `how`, and `axis`.
- Add a new column to the dataframe that contains the colour of each respondent indicating the party that he/she voted for in the last election. Use the following colour scheme: `{"CDU/CSU": "black", "SPD": "red", "FDP": "yellow", "Bündnis 90/Die Grünen": "green", "Die Linke": "purple", "AfD": "blue", "Andere Partei": "grey"}`.
- Use standard scaling (e.g. using `sklearn`'s `scaler = StandardScaler().fit(X)` and `X_scaled = scaler.transform(X)`) to the data of the political attitudes, such that the transformed data is centred at the mean and scaled by the standard deviation.
- Do the PCA!
- (1) Produce a scatter plot of the first and second PCA component (on the x- and y-axis, respectively) and colour each transformed data point according to the party that the respondent voted for in the last election. 
	- Optional: you can add arrows showing the directions of each of the political attitudes in the PC1-PC2-space.
	- Indicate the explained variance of the principle component in the axis labels (e.g. the xlabel should look something like this: "PC1 (explained variance: XXX)")
- (2) Produce a plot that shows the explained variance by each PC component. Using this plot, how many PC components are sufficient to roughly represent the respondents' political attitudes in your opinion?
- (3) Visualise the vectors of the principle components 1 to 3 (see e.g. the figure on slide "Variable loadings" in the Concepts lecture on PCA). Describe qualitatively what PC1 represents. 
