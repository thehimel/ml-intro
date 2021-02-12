# ml-intro

An introduction to machine learning.

## Motivation

I learn something better when I feel excited about it. And the save have happened for Machine Learning.
I'm pretty excited to learn Machine Learning.

To get introduced with ML, I have a known instructor who teaches things in a very easy manner. His name is Mosh Hamedani.
So, I found a tutorial on his YouTube channel and creating this repository as an exercise to this tutorial.
[Python Machine Learning Tutorial (Data Science)](https://youtu.be/7eh4d6sabA0)

## Software Versions

- Python 3.8.5

## Common ML Libraries

- Numpy
- Pandas
- MatPlotLib
- Scikit-Learn

## Notes

- Before running a ipynb file in the vscode, run the file on the browser mode of jupyter notebook at least once. Otherwise, it will now load the libraries properly.

## Installation

- Download and install Anaconda from [here](https://www.anaconda.com/products/individual). It will install all the required libraries for ML.
- In CMD, type `where conda`.
- If there is any miniconda installed in the system previously, delete the entries from the environment path variable. Only Anaconda3 must be set as conda.

## Virtual Environment

- `conda create mlintro`
- `conda activate mlintro`

## Open Jupyter Notebook

- `jupyter notebook`
- Go to your desired directory.
- New -> Python 3 Notebook.
- You can rename the file to anything.

## Importing a Data Set

- Go to [Kaggle](https://www.kaggle.com)
- Search for 'videogamesales'.
- Download the data set from [here](https://www.kaggle.com/gregorut/videogamesales)
- Keep the csv file inside 'src/data' directory.
- Create a Python 3 notebook with the following code:

```python
import pandas as pd
df = pd.read_csv('data/vgsales.csv')
df

# Shows the shape of the data set: (number_of_rows, number_of_columns)
df.shape

# Information regarding the data. Information regarding aggregation like count, mean, min, max, etc.
df.describe()

# Returns a 2D array with comma separated columns inside a sub-array.
df.values
```

## Jupyter Shortcuts

- There are basically 2 modes:
  - Edit Mode (Green sidebar)
  - Command Mode (Blue sidebar)
- Press 'Esc' to turn a segment to command mode.
- Press 'h' to see the keyboard shortcuts while being in the command mode.
- Useful shortcuts:
  - 'a': appends a cell *above* the current cell.
  - 'b': appends a cell *below* the current cell.
  - 'dd': to delete a cell.
  - Cell -> Run all
  - Press 'Tab' after a object to get the associated methods and attributes.
  - Press 'Shift + Tab' while keeping the cursor on any method or attribute to see the tool tip.
  - Press 'Ctrl + /' to comment or uncomment a line.
  - Press 'Ctrl + Enter' to run a cell without adding a new cell below the current cell.

## A Real Problem

### Problem Statement

Recommend music based on the user's age in a music app.

### Solution Steps

1. Import the data
2. Clean the data
3. Split the data intro training and test sets
4. Create a model
5. Train the model
6. Make predictions
7. Evaluate and improve

#### Import the data

- Download music.csv.zip from [here](https://programmingwithmosh.com/wp-content/uploads/2020/09/music.csv.zip)
- Extract and copy the music.csv to 'src/data'
- Run the following code to view the data set.

```python
# Importing the Data

import pandas as pd

music_data = pd.read_csv('data/music.csv')
music_data
```

#### Preparing the Data

- We don't have any repeated data, thus duplicate data removal is not needed.
- We need to divide our data set to input set and output set.

```python
# Preparing the Data

# Create a new data set by drop the specified column from a data set.
input_set = music_data.drop(columns=['genre'])
input_set

# Create a new data set with the specified column from a data set.
output_set = music_data['genre']
output_set
```

#### Learning and Predicting

- We are going to use Decision Tree algorithm from Scikit-Learn library to create the model.
- Scikit-Learn is the most popular ML library in Python.

```python
# Learning and Predicting

from sklearn.tree import DecisionTreeClassifier as DTC

# Instance of the DTC class which is an object.
model = DTC()

# Train the model
model.fit(input_set, output_set)

# Predict output for data that are not available in the input set
predictions = model.predict([
        # [age, gender] as in the input set.
        [21, 1],
        [22, 0]
    ]
)

predictions
```

#### Calculating the Accuracy

- Split the main data set into 2 sets: training set and testing set.
- Keep 70% to 80% data for training, and rest 20% to 30% data for testing.

```python
# Calculating the Accuracy
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# Splitting the data into training and testing sets with 20% data allocated for testing.
# Increasing the value of test_size will reduce the accuracy as less data will be there for training.
# For example for test_size = 0.2, score = 0.75 to 1.0. But for test_size = 0.8, score = 0.2 to 0.4.
# For test_size=0.1, score = 1.0. 1.0 means 100%, 0.2 means 20%, 0.33 means 33%, and so on.
# On each run train_test_split() picks data randomly for training. Thus, accuracy may defer on each run.
input_train, input_test, output_train, output_test = train_test_split(input_set, output_set, test_size=0.2)

model.fit(input_train, output_train)
predictions = model.predict(input_test)

score = accuracy_score(output_test, predictions)
score
```
