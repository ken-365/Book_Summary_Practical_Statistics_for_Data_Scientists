Disclaimer: this book summary purpose is only for personal use for education and research. Not for commercial.

# 1. Exploratory Data Analysis
This chapter focuses on the first step in any data science project: exploring the
data. Exploratory data analysis

## Elements of Structured Data

Much of the data is unstructured, such as images are a collection of pixels with each pixel containing RGB (red, green, blue) color information. Texts are sequences of words and nonword characters, and Clickstreams are sequences of actions by a user interacting with an app or web page.  

### Identify type of data
**Continuous**  

- Data that can take on any value in an interval.  

**Discrete**  

- Data that can take on only integer values, such as counts.  

**Categorical**  

- Data that can take on only a specific set of values representing a set of possible categories.  

**Binary**

- A special case of categorical data with just two categories of values (0/1, true/false).  

**Ordinal**  
- Categorical data that has an explicit ordering.  

**and much more**

There are two basic types of structured data: numeric and categorical. Numeric
data comes in two forms: continuous, such as wind speed or time duration, and
discrete, such as the count of the occurrence of an event. Categorical data takes
only a fixed set of values, such as a type of TV screen (plasma, LCD, LED, etc.)
or a state name (Alabama, Alaska, etc.). Binary data is an important special case
of categorical data that takes on only one of two values, such as 0/1, yes/no, or
true/false. Another useful type of categorical data is ordinal data in which the
categories are ordered; an example of this is a numerical rating (1, 2, 3, 4, or 5).  

### Rectangular Data (widely use in software package R, etc)
The typical frame of reference for an analysis in data science is a rectangular
data object, like a spreadsheet or database table.

Data frame
Rectangular data (like a spreadsheet) is the basic data structure for statistical and machine
learning models.

**Feature** (attribute, input, predictor, variable)

- A column in the table is commonly referred to as a feature.

**Outcome** (dependent variable, response, target, output)

- Many data science projects involve predicting an outcome — often a yes/no outcome (in Table 1-1, it is “auction was competitive or not”). The features are sometimes used to predict the outcome in an experiment or study.

**Records** (case, example, instance, observation, pattern, sample)
- A row in the table is commonly referred to as a record.

## Estimates of Location (Central tendency)

**Mean**  

- The sum of all values divided by the number of values.

**Median**

- The value such that one-half of the data lies above and below.

**Robust** (resistant to outliers)  

- Not sensitive to extreme values. (transfrom data to more intepret pattern)

**Outlier**

- A data value that is very different from most of the data.

### Median and Robust Estimates

Compared to the mean, which uses all observations, the median
depends only on the values in the center of the sorted data. While this might seem
to be a disadvantage, since the mean is much more sensitive to the data, there are
many instances in which the median is a better metric for location. Let’s say we
want to look at typical household incomes in neighborhoods around Lake
Washington in Seattle. In comparing the Medina neighborhood to the Windermere
neighborhood, using the mean would produce very different results because Bill
Gates lives in Medina. If we use the median, it won’t matter how rich Bill Gates
is — the position of the middle observation will remain the same.

### Outliers

The median is referred to as a robust estimate of location since it is not influenced
by outliers (extreme cases) that could skew the results. An outlier is any value
that is very distant from the other values in a data set.

## Estimates of Variability

Location is just one dimension in summarizing a feature. A second dimension,
variability, also referred to as dispersion, measures whether the data values are
tightly clustered or spread out. At the heart of statistics lies variability: measuring
it, reducing it, distinguishing random from real variability, identifying the various
sources of real variability, and making decisions in the presence of it.  

**Resudials** (errors,deviation)

- The difference between the observed values and the estimate of location (eg, mean).

**Variance**

- The sum of squared deviations(residuals) from the mean divided by n – 1 where n is the number of data values.
- $s^{2} = \sum \frac{{(x-\bar{x})}^{2}}{n-1}$

**Standard deviation** (2-norm)

- The square root of the variance. 
- $s = \sqrt{Variance}$

**Percentile**

- The value such that P percent of the values take on this value or less and (100–P) percent take on this value or more.

## Correlation
Exploratory data analysis in many modeling projects (whether in data science or
in research) involves examining correlation among predictors, and between
predictors and a target variable.

**Correlation coefficient**
- A metric that measures the extent to which numeric variables are associated with one another (ranges from –1 to +1).

**Correlation matrix**
- A table where the variables are shown on both rows and columns, and the cell values are the correlations between the variables.

'''library(corrplot)
corrplot(cor(etfs), method = "ellipse")'''

**Scatterplot**
- A plot in which the x-axis is the value of one variable, and the y-axis the value of another.

# Chapter 2. Data and Sampling Distributions

### Random Sampling and Sample Bias

Random sampling is a process in which each available member of the population
being sampled has an equal chance of being chosen for the sample at each draw  

Data quality often matters more than data quantity when making an estimate or a
model based on a sample. Data quality in data science involves completeness,
consistency of format, cleanliness, and accuracy of individual data points.
Statistics adds the notion of representativeness.

#### Regression to the Mean

Regression to the mean refers to a phenomenon involving successive
measurements on a given variable  
The phenomenon was first identified by Francis Galton in 1886 [Galton-1886], who
wrote of it in connection with genetic tendencies; for example, the children of
extremely tall men tend not to be as tall as their father  

### Sampling Distribution of a Statistic
The term sampling distribution of a statistic refers to the distribution of some
sample statistic, over many samples drawn from the same population

**Sample statistic**
- A metric calculated for a sample of data drawn from a larger population.

**Central limit theorem**
- The tendency of the sampling distribution to take on a normal shape as sample size rises.

**Standard error**
- The variability (standard deviation) of a sample statistic over many samples (not to be confused with standard deviation, which, by itself, refers to variability of individual data values).

#### Central Limit Theorem

It says that the means drawn from multiple samples will resemble the “Normal Distribution”, even if the source population is not normally distributed,
provided that the sample size is large enough and the departure of the data from
normality is not too great.  

The benefit is that its allow us to use nice properties of normal distribution such as confidence intervals and hypothesis tests.

### The Bootstrap 

One easy and effective way to estimate the sampling distribution of a statistic, or
of model parameters, is to draw additional samples, with replacement, from the
sample itself and recalculate the statistic or model for each resample. This
procedure is called the bootstrap, and it does not necessarily involve any
assumptions about the data or the sample statistic being normally distributed.  

The algorithm for a bootstrap resampling of the mean is as follows, for a
sample of size n:
1. Draw a sample value, record, replace it.
2. Repeat n times.
3. Record the mean of the n resampled values.
4. Repeat steps 1–3 R times.
5. Use the R results to:
 - Calculate their standard deviation (this estimates sample mean standard error).
 - Produce a histogram or boxplot.
 - Find a confidence interval.
 
### Confidence Intervals

The percentage of confidence intervals, constructed in the same way from the same population,
expected to contain the statistic of interest.  
Presenting an estimate not as a single number
but as a range is one way to counteract this tendency. Confidence intervals do this
in a manner grounded in statistical sampling principles.  

### Normal Distribution

Error
- The difference between a data point and a predicted or average value.

Standardize
- Subtract the mean and divide by the standard deviation.

z-score
- The result of standardizing an individual data point.

Standard normal
- A normal distribution with mean = 0 and standard deviation = 1.

QQ-Plot
- A plot to visualize how close a sample distribution is to a normal distribution.

68% of the data lies within one standard
deviation of the mean, and 95% lies within two standard deviations  

### Student’s t-Distribution

The t-distribution is a normally shaped distribution, but a bit thicker and longer
on the tails. It is used extensively in depicting distributions of sample statistics

### Binomial Distribution

Yes/no (binomial) outcomes lie at the heart of analytics since they are often the
culmination of a decision or other process; buy/don’t buy, click/don’t click,
survive/die, and so on.  
The binomial distribution would answer a question like:  
If the probability of a click converting to a sale is 0.02, what is the probability
of observing 0 sales in 200 clicks?  
The R function dbinom calculates binomial probabilities. For example:  
$dbinom(x=2, n=5, p=0.1)$  
would return 0.0729, the probability of observing exactly x = 2 successes in n = 5
trials, where the probability of success for each trial is p = 0.1.
Often we are interested in determining the probability of x or fewer successes in n
trials. In this case, we use the function pbinom:  
$pbinom(2, 5, 0.1)$  
This would return 0.9914, the probability of observing two or fewer successes in
five trials, where the probability of success for each trial is 0.1.
The mean of a binomial distribution is $n*p$ ; you can also think of this as the
expected number of successes in n trials, for success probability = p.
The variance is $n*p(1-p)$. With a large enough number of trials
### Poisson and Related Distributions

Many processes produce events randomly at a given overall rate — visitors
arriving at a website, cars arriving at a toll plaza (events spread over time),
imperfections in a square meter of fabric, or typos per 100 lines of code (events
spread over space).  

Lambda
- The rate (per unit of time or space) at which events occur.

Poisson distribution
- The frequency distribution of the number of events in sampled units of time or space.

Exponential distribution
- The frequency distribution of the time or distance from one event to the next event.

## Statistical Experiments and Significance Testing

Whenever you see references to statistical significance, t-tests, or p-values, it is
typically in the context of the classical statistical inference “pipeline”  
  
*Formulate hypothesis -> Design experiment -> Collect Data -> Inference/Conclusion*  
  
This process starts with a hypothesis (“drug A is better than the
existing standard drug,” “price A is more profitable than the existing price B”).
An experiment (it might be an A/B test) is designed to test the hypothesis —
designed in such a way that, hopefully, will deliver conclusive results. The data is
collected and analyzed, and then a conclusion is drawn. The term inference
reflects the intention to apply the experiment results, which involve a limited set
of data, to a larger process or population.

### A/B Testing
 
 An A/B test is an experiment with two groups to establish which of two
treatments, products, procedures, or the like is superior. Often one of the two
treatments is the standard existing treatment, or no treatment. If a standard (or no)
treatment is used, it is called the control. A typical hypothesis is that treatment is
better than control.

Treatment
- Something (drug, price, web headline) to which a subject is exposed.

Treatment group
- A group of subjects exposed to a specific treatment.

Control group
- A group of subjects exposed to no (or standard) treatment.

### Hypothesis Tests

Null hypothesis
- The hypothesis that chance is to blame.
- assumption that the treatments are equivalent, and any difference between the groups is due to chance.

Alternative hypothesis
- Counterpoint to the null (what you hope to prove).

One-way test
- Hypothesis test that counts chance results only in one direction.

Two-way test
- Hypothesis test that counts chance results in two directions.

### Resampling

repeatedly sample values from observed data,
with a general goal of assessing random variability in a statistic. It can also be
used to assess and improve the accuracy of some machine-learning models (e.g.,
the predictions from decision tree models)  

#### Permutation Test
The first step in a permutation test of a hypothesis is to combine the
results from groups A and B (and, if used, C, D, …) together. We then test that hypothesis by randomly drawing groups from this combined set, and seeing how much they differ from one another. The
permutation procedure is as follows:  
1. Combine the results from the different groups in a single data set.
2. Shuffle the combined data, then randomly draw (without replacing) a resample of the same size as group A.
3. From the remaining data, randomly draw (without replacing) a resample of the same size as group B.
4. Do the same for groups C, D, and so on.
5. Whatever statistic or estimate was calculated for the original samples (e.g., difference in group proportions), calculate it now for the resamples, and record; this constitutes one permutation iteration.
6. Repeat the previous steps R times to yield a permutation distribution of the test statistic.

*perm_fun <- function(x, n1, n2)  
{  
n <- n1 + n2  
idx_b <- sample(1:n, n1)  
idx_a <- setdiff(1:n, idx_b)  
mean_diff <- mean(x[idx_b]) - mean(x[idx_a])  
return(mean_diff)  
}*  

### Statistical Significance and P-Values
Statistical significance is how statisticians measure whether an experiment (or
even a study of existing data) yields a result more extreme than what chance might
produce. If the result is beyond the realm of chance variation, it is said to be
statistically significant.

**Alpha**
- The probability threshold of “unusualness” that chance results must surpass, for actual outcomes to be deemed statistically significant.

**Type 1 error**
- Mistakenly concluding an effect is real (when it is due to chance).

**Type 2 error**
- Mistakenly concluding an effect is due to chance (when it is real).

### Overfitting 

The more variables you add, or the more models you run, the
greater the probability that something will emerge as “significant” just by chance.  
This related to a Type 1 error. Lets say you run a .95 significant test 20 times on 20 randomly predicted value then the prebability of  all 20 will correctly reject is $0.95^{20} = 0.36$ which mean the prob of not correct is $1-0.36 = 0.64$  

Oneway to avoid is that, In supervised learning tasks, a train set is tested data that the model has not seen before mitigates this risk.  

Another way is try to remove redundant variables. Use something like anova.

### Degree of Freedom

refers to the number of values free to vary. For example, if you
know the mean for a sample of 10 values, and you also know 9 of the values, you
also know the 10th value. Only 9 are free to vary.  

### ANOVA

The statistical procedure that tests for a
statistically significant difference among the groups is called analysis of
variance, or ANOVA.

Pairwise comparison
- A hypothesis test (e.g., of means) between two groups among multiple groups.

Omnibus test
- A single hypothesis test of the overall variance among multiple group means.

Decomposition of variance
- Separation of components. contributing to an individual value (e.g., from the overall average, from a treatment mean, and from a residual error).

F-statistic
- A standardized statistic that measures the extent to which differences among group means exceeds what might be expected in a chance model.

SS
- “Sum of squares,” referring to deviations from some average value.

### F-Statistic
The F-statistic is based on the ratio of the variance across group means (i.e., the
treatment effect) to the variance due to residual error. The higher this ratio, the
more statistically significant the result. If the data follows a normal distribution,
then statistical theory dictates that the statistic should have a certain distribution.
Based on this, it is possible to compute a p-value

### Chi-Square Test

A measure of the extent to which some observed data departs from expectation

### Multi-Arm Bandit Algorithm

Multi-arm bandits offer an approach to testing, especially web testing, that allows
explicit optimization and more rapid decision making than the traditional
statistical approach to designing experiments.


```python

```
