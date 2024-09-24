# Political Attitudes

In this homework you will explore the Political Attitudes of the German population based on data from the European Social Survey. 

The dataset is provided in this repository. 

**Create a quarto document** and write your solutions into that document such that the rendered html-file is **"human-readable"**. That means meaningful headlines, well-prepared graphics, code folded, no clutter of code output, and some short text introducing and concluding the different exercises. 

Find the first exercises below.   

**Watch out:** More exercises will appear here later in new README-files! You will extend your analysis in the same quarto document. 
Finally, you have one html-file with all analyses. 

# Datat

This repo contains a subset of the [European Social Survey (ESS)](https://www.europeansocialsurvey.org/) data. The ESS tracks the behaviours, attitudes, and beliefs of individuals across European countries. By now, there are 10 survey waves covering a period from 2002 to 2020. We will work only with the latest wave and restrict ourselves to a subset of the questions concerning some political attitudes among German citizens. 

In particular, we consider the following items 

| Item | Question |
|---|---|
| `freehms` | Gays and lesbians free to live life as they wish | 
| `euftf` | European unification go further or gone too far |
| `wrclmch` | How worried about climate change | 
| `gincdif` | Government should reduce differences in income levels |
| `imueclt` | Country's cultural life undermined or enriched by immigrants |
| `lrscale` | Placement on left right scale | 
| `impcntr` | Allow many/few immigrants from poorer countries outside Europe |
| `prtvfde2` | Party voted for in last national election 2, Germany |

The questions are typically answered via Likert-type scale. 
For example, `lrscale` contains numbers 0 to 10 that encode the individual's self-placement from left (0) to right (10). The variable `prtvfde2` contains numbers that encode the relevant parties in the german political landscape. See
https://ess-search.nsd.no/variable/query/prtvfde2/1

The instructions below focus on `python` but the exercises can be solved in `R` as well, of course.

# Exercises

## Preparation

- Clone this repository to your local machine
- Create a quarto document to write your report in
- Load the data
- Define the missing data (look up the corresponding numbers used for "No Answer", "Refuse Answer", ... in the documentation of each variable!). For now, we do not need to filter out missing data.

## Exploration

In this first task we want to explore the dataset and create some visualisations.

### Task 1a: Characterising voters

Create a boxplot of the `lrscale` variable grouped by party that the individuals voted for (`prtvfde2`).

Try adjusting the colours of the boxplot to match the typical colours of the parties:

| party | colour | 
| --- | --- |
| CDU/CSU (conservative) | black | 
| SPD (social democrat) | red |
| Linke (Left) | purple | 
| Grünen (Green) | green |
| FDP (Liberals) | yellow |
| AfD (right-wing populist) | blue | 

> Tip: This can be done quite neatly in seaborn's `sns.boxplot(...)` by providing the `palette` argument with a dictionary containing the responses and the corresponding colours `{1: "black", ...}`. Also, adjust the tick labels!

Do the same exploratory analysis with a different variable and explain your observations to someone who is unfamiliar with the political landscape in Germany.

### Task 1b: Exploration and visualisation of two variables.

#### Scatterplot 

This analysis aims to explore the variables and their dependencies in the dataset. Let's focus on two variables, say `imueclt` and `impcntr`.

First, produce a scatter plot where each point corresponds to a data point in the `impcntr` - `imueclt` plane. This probably looks pretty uninformative. Why? Explain!
Also try setting the transparency of the data points to a very small value, e.g. `alpha=0.01`. 

#### Heatmap

Let's do a better job by creating a heatmap of the data (or a 2D histogram). 
First, create a nice (pivoted) table which contains the number of responses for each set of values in `imueclt` (index/rows) and `impcntr` (columns). Include this table in your report.

> Tip: you can use pandas' `pivot_table` or a combination of grouping and pivoting (unstacking).

Now, plot this table as a heatmap, using for example, `sns.heatmap(...)`.

Describe your observations! 

#### Correlation

Finally, report the correlation coefficient of the two variables and briefly interpret it.


