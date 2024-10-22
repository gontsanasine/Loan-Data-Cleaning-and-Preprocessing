# Loan Data Cleaning and Preprocessing

## Introduction

This project focuses on cleaning and preprocessing a loan dataset to prepare it for analysis. Using NumPy,I address common data quality issues such as missing values, inconsistencies, and formatting errors. This process is crucial for ensuring the dataset's integrity and usability in subsequent analysis.

## Dataset Overview

The dataset used in this project contains the following columns:
	
![image](https://github.com/user-attachments/assets/6d6b6f80-ca50-4a92-8017-9ef59fc19329)

### Tools Used
NumPy: Utilized for data manipulation and preprocessing tasks.

Python: The programming language used for the project.

CSV: The data format for the loan dataset.
## Objectives

The main objectives of this project are to:
- Identify and handle missing values
- Normalize and standardize numerical data
- Encode categorical variables
- Validate data integrity

## Data Cleaning and Preprocessing Process

The following steps outline the data cleaning and preprocessing tasks performed using NumPy:

### 1. Loading the Data

Load the CSV dataset into a NumPy array for manipulation.

```python
import numpy as np

# Load the dataset
raw_data_np = np.genfromtxt("loan-data.csv",
                         delimiter = ";",
                           skip_header = 1,
                           autostrip = True)
```
## Data Manipulations

In this project, various manipulations were performed on multiple columns to prepare the dataset for analysis. The following summarizes the key operations:

### Seperating into strings and numeric columns
```python
header_full = np.genfromtxt("loan-data.csv",
                                  delimiter = ';',
                                  skip_footer = raw_data_np.shape[0],
                                  autostrip = True, 
                                  dtype = "str")

header_strings, header_numeric = header_full[columns_strings], header_full[columns_numeric]
```

### Numerical Columns
#### Loaned Amount, Iterest Rate, Total Payment, Installement
```python
for i in [1,3,4,5]:
    loan_data_numeric[:,i] = np.where(loan_data_numeric[:,i] == temporary_fill,
                                      temporary_stats[2, columns_numeric[i]],
                                      loan_data_numeric[:,i])

```
#### Currency Change
```python
EUR_USD = np.genfromtxt("EUR-USD.csv", delimiter = ',', autostrip = True, skip_header = 1, usecols = 3)
EUR_USD

exchange_rate = loan_data_strings[:,0] 

for i in range(1,13):
    exchange_rate = np.where(exchange_rate == i,
                             EUR_USD[i-1],
                             exchange_rate) 

exchange_rate = np.where(exchange_rate == 0,
                         np.mean(EUR_USD),
                         exchange_rate) 

exchange_rate
```
### Categorical Columns

- **Loan Status**: Encoded as binary values (1 for Approved, 0 for Rejected).
- **Issue Date**: Change from strings to the months represented in numbers:
  ```python
  for i in range(13):
        loan_data_strings[:,0] = np.where(loan_data_strings[:,0] == months[i],
                                          i,
                                          loan_data_strings[:,0])
  ```
For detailed implementations of each manipulation, please refer to the [Data Cleaning and Preprocessing Notebook](https://github.com/gontsanasine/Loan-Data-Cleaning-and-Preprocessing/blob/main/Loan%20data%20-%20cleaning%20and%20preprocessing.ipynb)


Sure! Here’s a section for “What I Learned” and “Challenges” that you can include in your README:

## What I Learned
Through this project, I gained valuable insights and skills in data cleaning and preprocessing, including:

Data Integrity Importance: I learned that maintaining data integrity is crucial for accurate analysis. Addressing issues such as missing values and inconsistencies significantly enhances the quality of the dataset.

Proficiency with NumPy: Working with NumPy improved my ability to perform efficient data manipulations and mathematical operations, allowing me to handle large datasets effectively.

Handling Diverse Data Types: I developed skills in managing different types of data, such as numerical, and categorical, and learned how to apply appropriate preprocessing techniques for each type.

Data Normalization Techniques: I gained experience in normalizing and standardizing numerical data, which is essential for ensuring that various features contribute equally to analysis.

Encoding Categorical Variables: I learned how to effectively encode categorical data, transforming it into a format suitable for modeling while preserving the meaning of the original data.

## Challenges
During the project, I encountered several challenges that helped deepen my understanding:

Dealing with Missing Values: Determining the best approach to handle missing values required careful consideration. I had to balance between removing data and imputing values, which could affect the dataset's integrity.

Data Type Conversion: Ensuring that all columns were in the correct format presented challenges, especially when dealing with mixed data types. This required thorough checks and adjustments to avoid errors in analysis.

Scalability of Operations: Working with a large dataset posed performance challenges. I had to optimize my use of NumPy functions to ensure that data manipulations were efficient and did not lead to excessive computation times.

Maintaining Documentation: Keeping track of all the transformations and cleaning steps I applied was crucial. Ensuring that my documentation was clear and comprehensive was a challenge that I learned to prioritize.

These experiences not only improved my technical skills but also reinforced the importance of careful planning and documentation in data projects.

## Results
After performing the above cleaning and preprocessing tasks, the dataset is now free of missing values and inconsistencies, with standardized and encoded features, making it ready for further analysis.

## Conclusion
Data cleaning and preprocessing are essential steps in preparing datasets for analysis. This project demonstrated how to effectively utilize NumPy for handling missing values, normalizing data, and encoding categorical variables. The cleaned dataset can now support reliable insights into loan approval trends and applicant profiles.
