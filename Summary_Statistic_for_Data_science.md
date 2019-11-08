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




```python

```
