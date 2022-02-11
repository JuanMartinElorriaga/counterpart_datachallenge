## Profiling report and KNN Imputation for status and value features

## Challenge

_Please evaluate the data sets provided in python and provide a brief report (ideally with imagery) outlining statistics of note within the provided data. Your goal is to use the training set (training.csv) to fill in the missing data in the testing set (testing.csv). Try to cap the time spent on the actual problem around 60 minutes._

### Objectives

- Evaluate your capabilities and comfort level in managing abstract data in Python
- Assess your analytical abilities when it come to somewhat vague and undirected data related problems
- Showcase your ability to tell a story with data
- Collaborate with the team on a fun little problem

### Suggestions

The correctness of the submission is not of primary importance. Rather, we are looking for a small representative code sample of your experience and comfort in python, as well as an understanding of how you approach challenges of this nature when only partially directed.

### Dataset
#### Training dataset

- city
- website
- employees
- _status_ (IPO Status: public, private, unlisted)
- _value_ (1: 'risky'; 0: 'safe')


#### Testing dataset

- city
- website
- employees (groups)

## KNN Imputation
### What is imputation
*Imputation* is a technique used for replacing the missing data with some substitute value to retain most of the data/information of the dataset. These techniques are used because removing the data from the dataset every time is not feasible and can lead to a reduction in the size of the dataset to a large extend, which not only raises concerns for biasing the dataset but also leads to incorrect analysis.

### Effects of Missing Values
Having missing values in our datasets can have various detrimental effects:

- Missing data can limit our ability to perform important data science tasks such as converting data types or visualizing data.

- Missing data can reduce the statistical power of our models which in turn increases the probability of Type II error. Type II error is the failure to reject a false null hypothesis.

- Missing data can reduce the representativeness of the samples in the dataset.

- Missing data can distort the validity of the scientific trials and can lead to invalid conclusions.


### KNN Imputation
*K-nearest neighbors (KNN)* algorithm is a type of supervised ML algorithm which can be used for both classification as well as regression predictive problems. It has two main properties:

- _Lazy learning algorithm_: KNN is a lazy learning algorithm because it does not have a specialized training phase and _uses all the data_ for training while classification.

- _Non-parametric learning algorithm_: KNN is also a non-parametric learning algorithm because it doesn’t assume anything about the underlying data.

K-nearest neighbors (KNN) algorithm uses _‘feature similarity’_ to predict the values of new datapoints which further means that the new data point will be assigned a value based on how closely it matches the points in the training set.

#### Notes
- By default, it uses a Euclidean distance metric to impute the missing values.

- The KNN Imputer does not recognize text data values.

- A good way to modify the text data is to perform one-hot encoding or create “dummy variables”. The idea is to convert each category into a binary data column by assigning a 1 or 0.

- KNN Imputer is a distance-based imputation method and it requires us to normalize our data. 

#### Pros and Cons

#### Pros
- It is very simple algorithm to understand and interpret.

- It is very useful for nonlinear data because there is no assumption about data in this algorithm.

- It is a versatile algorithm as we can use it for classification as well as regression.

- It has relatively high accuracy but there are much better supervised learning models than KNN.

#### Cons
- It is computationally a bit expensive algorithm because it stores all the training data.

- High memory storage required as compared to other supervised learning algorithms.

- Prediction is slow in case of big N.

- It is very sensitive to the scale of data as well as irrelevant features.



### Alternative ways to solve this problem

- Mean, median and most frequent value imputation

- _"Probability approach imputation"_: take each city, grouped by number of employees and ponderate the probability of having a specific value and/or status. The result is that for each group, you will have a specific probability of ocurrence, which could be used for a ponderated imputation.

- API approach: use *Crunchbase API* to recollect financial information from each company
    - For status: there is a flag called _'IPO status'_ that could be extracted and apllied directly to retrieve the company's status.
    - For value: a ponderated formula could be calculated, taking financial metrics as proxy estimators.


## Project Structure


├── data       <- The original data (training and testing csv's) 

├── scripts    <- The python code (notebook.ipynb)

├── processed  <- Files exported as final results

│   ├── Profiling_report.html <- Statistical analysis in html style
│   ├── testing_filled.csv    <- Testing csv but filled with the missing columns
