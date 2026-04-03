# Series-to-DataFrame
# Pandas DataFrame Operations

This notebook provides an introduction to fundamental operations with Pandas DataFrames, a powerful data structure for data manipulation and analysis in Python. It covers common tasks such as DataFrame creation, data selection, inspection, and basic modifications.

## Table of Contents
- [Introduction](#introduction)
- [Setup](#setup)
- [Creating DataFrames](#creating-dataframes)
- [DataFrame Inspection](#dataframe-inspection)
- [Data Selection and Indexing](#data-selection-and-indexing)
- [DataFrame Modification](#dataframe-modification)
- [Filtering DataFrames](#filtering-dataframes)
- [Additional Examples](#additional-examples)

## Introduction
This notebook demonstrates various functionalities of the Pandas library, focusing on DataFrames. You'll learn how to:
- Initialize DataFrames from different data sources (Series, dictionaries, NumPy arrays).
- Access and manipulate data using `loc`, `iloc`, and column indexing.
- Get descriptive statistics and information about DataFrame properties.
- Add, delete, and modify columns.
- Filter data based on conditions.

## Setup
Before running the code, ensure you have Pandas installed:

```python
import pandas as pd
import numpy as np
```

## Creating DataFrames
DataFrames can be created from various sources. This notebook shows examples of creating DataFrames from a list of Series and from 2D dictionaries and NumPy arrays.

### From Series
```python
purchase_1=pd.Series({'Name':'Chris','Item Purchased':'Dog Food','Cost':22.50})
purchase_2=pd.Series({'Name':'Kevyn','Item Purchased':'Kitty Litter','Cost':2.50})
purchase_3=pd.Series({'Name':'Vinod','Item Purchased':'Bird Seed','Cost':5.00})
df=pd.DataFrame([purchase_1,purchase_2,purchase_3],index=['Store 1','Store 1','Store 2'])
print(df)
```

### From 2D Dictionary
```python
data={
    'Activity1':{'Blue House':98,'Red House':87,'Green House':59,'Yellow House':78},
    'Activity2':{'Blue House':85,'Red House':76,'Green House':67,'Yellow House':99},
    'Activity3':{'Blue House':88,'Red House':80,'Green House':91,'Yellow House':55}
}
df_dict=pd.DataFrame(data)
print(df_dict)
```

### From NumPy Array
```python
data_np=np.array([['A', 98,56,87],
              ['B', 32,76,65],
              ['C', 55,99,88]])
df_np=pd.DataFrame(data_np,columns=['Name','A','B','C'],index=['1','2','3'])
print(df_np)
```

## DataFrame Inspection
Methods to get insights into your DataFrame:

- `df.describe()`: Generates descriptive statistics.
- `df.shape`: Returns a tuple representing the dimensionality of the DataFrame.
- `df.isnull()`: Detects missing values.
- `df.dtypes`: Returns the data type of each column.
- `df.count()`: Counts non-NA cells for each column or row.

```python
print(df.describe())
print(df.shape)
print(df.isnull().sum())
print(df.dtypes)
print(df.count())
```

## Data Selection and Indexing
Access data using row and column labels (`loc`) or integer-location based indexing (`iloc`).

- **Selecting by label (`.loc`)**: 
  ```python
df.loc['Store 1'] # Selects rows with index 'Store 1'
df.loc["Store 1",'Cost'] # Selects 'Cost' column for 'Store 1'
df.loc[:,["Name","Cost"]] # Selects 'Name' and 'Cost' columns for all rows
  ```
- **Selecting by position (`.iloc`)**: 
  ```python
df.iloc[0:2,0:2] # Selects rows 0-1 and columns 0-1
  ```
- **Selecting single column**: 
  ```python
df['Name'] # Returns a Series
  ```
- **Transposing DataFrame**: 
  ```python
df.T # Transposes rows and columns
  ```

## DataFrame Modification

- **Dropping rows/columns**: `df.drop("Store 1")` (does not modify in-place by default).
- **Adding new columns**: `df["location"] = ['Asansol','Kolkata','Bihar']`
- **Modifying existing column values**: `df['Cost'] += 2`
- **Adding new rows**: 
  ```python
df.loc["Store 3"] = pd.Series({'Cost':12.5,'Item Purchased':'Dog Food','Name':'Random','location':'None'})
  ```

## Filtering DataFrames
Select data based on conditional logic.

```python
# Example: Display furniture with a price greater than 25000
df_furniture[df_furniture['Price'] > 25000]

# Example: Display furniture with a price under 10000
df_furniture[df_furniture['Price'] < 10000]
```

## Additional Examples

The notebook also includes examples of selecting alternative rows using slicing `df.iloc[::2]`.
