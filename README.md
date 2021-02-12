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

