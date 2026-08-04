**Week-2 Module-3**

**Part-1:**



Introduction to pandas dataframes and series

Lesson visual

Embarking on Your Data Science Journey with Pandas: An Introduction

Welcome to Module 3 of our Machine Learning \& Data Science with Python course! In this foundational lesson, we will dive into the heart of data manipulation and analysis in Python: the Pandas library. As B-Tech students aspiring to excel in AI/ML, mastering Pandas is not just beneficial; it's essential. This module is designed to equip you with the core tools needed to handle real-world data effectively.



Pandas provides two primary data structures: Series and DataFrames. These structures are the workhorses for any data scientist, enabling efficient loading, cleaning, transformation, selection, filtering, and aggregation of structured data. Whether you're working with financial records, sensor readings, survey responses, or any other tabular data, Pandas will be your go-to library.



This lesson is structured to provide a comprehensive understanding, moving from fundamental concepts to practical implementation. We will explore what Series and DataFrames are, how to create them from various data sources like lists, dictionaries, and NumPy arrays, and how to navigate and inspect your data using powerful indexing and selection techniques. We'll also touch upon the crucial aspects of data types and basic data inspection methods that are vital for initial data understanding.



Learning Objectives for this Lesson:



Understand the fundamental concepts of Pandas Series and DataFrames.

Learn to create Series and DataFrames from common Python data structures.

Master indexing and selection techniques using loc and iloc.

Become familiar with essential DataFrame attributes and methods for data exploration.

Grasp the importance of data types in Pandas and how to interpret them.

Perform basic data inspection using methods like head, tail, info, and describe.

These objectives directly align with the module's overarching goals: to understand Pandas DataFrames and Series, load, clean, and transform structured data, perform data selection, filtering, and aggregation, and handle missing data and duplicate entries. While this lesson focuses on the introduction and basic manipulation, it lays the critical groundwork for the subsequent lesson on Data Loading and Cleaning, where we will apply these concepts to real-world datasets.



The real-world relevance of Pandas cannot be overstated. In virtually every data-driven field, from finance and healthcare to e-commerce and scientific research, data analysis is paramount. Companies rely on data scientists to extract insights, build predictive models, and make informed decisions. Pandas is the cornerstone of this process in Python, making it a highly sought-after skill in the job market. By the end of this lesson, you will be well on your way to becoming proficient in this indispensable tool.



Understanding the Building Blocks: Pandas Series and DataFrames Explained



At the core of the Pandas library are two fundamental data structures: the Series and the DataFrame. These structures are designed to handle tabular data efficiently and intuitively, making them indispensable tools for data analysis and manipulation in Python.



What is a Pandas Series?

A Pandas Series is a one-dimensional labeled array capable of holding any data type (integers, strings, floating-point numbers, Python objects, etc.). Think of it as a single column in a spreadsheet or a SQL table. Each element in a Series has an associated label, known as its index. This index allows for quick and easy access to individual elements.



Key Characteristics of a Series:



One-dimensional: It can only hold data in a single dimension.

Labeled Index: Each data point has a label (index) that can be an integer, a string, or any other hashable type. If no index is explicitly provided, a default integer index (starting from 0) is created.

Homogeneous Data Type: While a Series can hold any data type, all elements within a single Series are typically of the same type (e.g., all integers, all strings). This homogeneity allows for optimized operations.

Flexibility: Series can be created from various sources, including lists, NumPy arrays, and dictionaries.

Analogy: Imagine a single column in your favorite spreadsheet software, like Microsoft Excel or Google Sheets. This column contains a list of values (e.g., names of students, their ages, or their scores), and each value has a corresponding row number. In Pandas, the values are the data, and the row numbers (or custom labels) form the index.



Why are Series Important?

Series are the fundamental building blocks for more complex Pandas structures. They are used to represent individual features or variables in your dataset. Understanding Series is crucial because:



Data Representation: They provide a clear and efficient way to store and access one-dimensional data.

Foundation for DataFrames: A DataFrame is essentially a collection of Series that share the same index.

Vectorized Operations: Pandas leverages Series for fast, vectorized operations, meaning you can perform calculations on entire arrays of data without explicit loops, which significantly speeds up computation.

Data Alignment: The index of a Series plays a vital role in data alignment during operations, ensuring that data is combined correctly based on matching labels.

What is a Pandas DataFrame?

A Pandas DataFrame is a two-dimensional labeled data structure with columns of potentially different types. It is the most commonly used Pandas object and is analogous to a spreadsheet, a SQL table, or a dictionary of Series objects. A DataFrame has both a row index and a column index.



Key Characteristics of a DataFrame:



Two-dimensional: It has both rows and columns.

Labeled Axes: It has a row index (like a Series) and a column index, allowing for flexible data access and manipulation.

Heterogeneous Data Types: Columns in a DataFrame can have different data types (e.g., one column can be integers, another strings, another floats).

Size-Mutable: You can add or remove columns and rows.

Data Alignment: Operations between DataFrames are aligned by labels (both row and column indices).

Analogy: Think of a complete spreadsheet. It has rows (representing individual records or observations) and columns (representing different attributes or features of those records). Each cell in the spreadsheet contains a specific piece of data, identified by its row and column. A DataFrame mirrors this structure perfectly.



Why are DataFrames Important?

DataFrames are the workhorse of data analysis in Pandas. They are designed to handle structured data, which is data organized in a tabular format. Their importance stems from:



Comprehensive Data Handling: They can store and manage large datasets with diverse data types efficiently.

Intuitive Operations: Pandas provides a rich set of methods for data manipulation, cleaning, transformation, aggregation, and visualization directly on DataFrames.

Data Integration: They facilitate the integration of data from various sources (CSV, Excel, SQL databases, etc.).

Foundation for Machine Learning: Most machine learning algorithms in Python, especially those in Scikit-learn, expect data to be in a DataFrame or a similar array-like structure.

Readability and Maintainability: The labeled rows and columns make data easier to understand, inspect, and debug.

In summary, Series are like single columns, and DataFrames are like tables composed of multiple Series. Understanding these two structures is the first and most critical step in mastering Pandas for data science.



Constructing Your Data: Creating Pandas Series and DataFrames

Now that we understand what Series and DataFrames are, let's learn how to create them. Pandas offers flexible ways to construct these objects from various Python data structures, including lists, dictionaries, and NumPy arrays. This section will guide you through the most common creation methods, providing practical examples you can run in your Jupyter Notebook.



We'll start by importing the Pandas library, which is conventionally aliased as pd.



import pandas as pd

import numpy as np

Creating a Pandas Series from a List

A list is a fundamental Python data structure. You can easily convert a list into a Pandas Series. When you create a Series from a list without specifying an index, Pandas automatically assigns a default integer index starting from 0.



Hands-on Component 1: Create a Pandas Series from a list.



Let's create a Series representing the population of a few major cities.



Step 1: Define a Python list.



First, create a list containing the population figures.



population\_list = \[8600000, 3900000, 14000000, 2700000]

Step 2: Create the Pandas Series.



Use the pd.Series() constructor, passing your list as the argument.



population\_series = pd.Series(population\_list)

print(population\_series)

Expected Output:



0     8600000

1     3900000

2    14000000

3     2700000

dtype: int64

As you can see, Pandas has created a Series with a default integer index (0, 1, 2, 3) and the population figures as data. The dtype: int64 indicates that the data in this Series is of integer type.



Creating a Series with a Custom Index

Often, you'll want to associate meaningful labels with your data. You can provide a custom index when creating a Series by passing a list of labels to the index parameter.



Let's add city names as labels to our population Series.



Step 1: Define a list of labels (city names).



cities = \['New York', 'Los Angeles', 'Tokyo', 'London']

Step 2: Create the Series with a custom index.



Ensure the length of the cities list matches the length of the population\_list.



population\_series\_custom\_index = pd.Series(population\_list, index=cities)

print(population\_series\_custom\_index)

Expected Output:



New York       8600000

Los Angeles    3900000

Tokyo         14000000

London         2700000

dtype: int64

Now, each population figure is associated with a city name, making it much easier to reference specific data points.



Creating a Pandas DataFrame from a Dictionary

DataFrames are frequently created from dictionaries. In this scenario, the keys of the dictionary become the column names, and the values (which should be list-like or array-like) become the data for each column.



Hands-on Component 2: Create a Pandas DataFrame from a dictionary.



Let's create a DataFrame to store information about students, including their names, ages, and scores.



Step 1: Define a Python dictionary.



Each key represents a column name, and its corresponding value is a list of data for that column. Ensure all lists have the same length.



student\_data = {

&#x20;   'Name': \['Alice', 'Bob', 'Charlie', 'David'],

&#x20;   'Age': \[21, 22, 20, 23],

&#x20;   'Score': \[85, 90, 78, 92]

}

Step 2: Create the Pandas DataFrame.



Use the pd.DataFrame() constructor, passing your dictionary.



student\_df = pd.DataFrame(student\_data)

print(student\_df)

Expected Output:



Name  Age  Score

0    Alice   21     85

1      Bob   22     90

2  Charlie   20     78

3    David   23     92

Pandas automatically creates a default integer index for the rows (0, 1, 2, 3) and uses the dictionary keys ('Name', 'Age', 'Score') as column headers.



Creating a DataFrame with a Custom Row Index

Similar to Series, you can assign custom row labels (index) to a DataFrame using the index parameter.



Let's use student IDs as row labels.



Step 1: Define a list of student IDs.



student\_ids = \['S001', 'S002', 'S003', 'S004']

Step 2: Create the DataFrame with a custom index.



student\_df\_custom\_index = pd.DataFrame(student\_data, index=student\_ids)

print(student\_df\_custom\_index)

Expected Output:



Name  Age  Score

S001   Alice   21     85

S002     Bob   22     90

S003 Charlie   20     78

S004   David   23     92

This makes it easier to refer to specific students by their IDs.



Creating a DataFrame from NumPy Arrays

NumPy arrays are fundamental for numerical operations in Python, and Pandas integrates seamlessly with them. You can create both Series and DataFrames from NumPy arrays.



Creating a Series from a NumPy Array

This is very similar to creating a Series from a list.



numpy\_array = np.array(\[10, 20, 30, 40, 50])

series\_from\_numpy = pd.Series(numpy\_array)

print(series\_from\_numpy)

Expected Output:



0    10

1    20

2    30

3    40

4    50

dtype: int64

Creating a DataFrame from a 2D NumPy Array

When creating a DataFrame from a 2D NumPy array, you'll typically want to specify column names and row indices for clarity.



Let's create a DataFrame representing sensor readings.



Step 1: Create a 2D NumPy array.



sensor\_readings = np.array(\[

&#x20;   \[25.5, 60.2, 1012.5],

&#x20;   \[26.1, 61.5, 1011.8],

&#x20;   \[25.9, 60.8, 1012.1],

&#x20;   \[26.5, 62.0, 1011.5]

])

Step 2: Define column names and row indices.



sensor\_columns = \['Temperature', 'Humidity', 'Pressure']

sensor\_timestamps = \['T1', 'T2', 'T3', 'T4']

Step 3: Create the DataFrame.



sensor\_df = pd.DataFrame(sensor\_readings, index=sensor\_timestamps, columns=sensor\_columns)

print(sensor\_df)

Expected Output:



Temperature  Humidity  Pressure

T1         25.5      60.2    1012.5

T2         26.1      61.5    1011.8

T3         25.9      60.8    1012.1

T4         26.5      62.0    1011.5

This demonstrates how to construct DataFrames from NumPy arrays, providing meaningful labels for both rows and columns.



By mastering these creation methods, you gain the flexibility to start working with data from various sources and in different formats, setting the stage for more advanced data manipulation techniques.



Navigating Your Data: Indexing and Selecting with loc and iloc



Once you have created or loaded your data into Pandas Series and DataFrames, the next crucial step is to access specific pieces of information. Pandas provides powerful and flexible methods for indexing and selecting data, with loc and iloc being the primary tools for this purpose. Understanding how to use them effectively is key to data analysis.



We will continue using the student\_df DataFrame we created earlier, which has custom row indices (student IDs).



import pandas as pd

import numpy as np



student\_data = {

&#x20;   'Name': \['Alice', 'Bob', 'Charlie', 'David'],

&#x20;   'Age': \[21, 22, 20, 23],

&#x20;   'Score': \[85, 90, 78, 92]

}

student\_ids = \['S001', 'S002', 'S003', 'S004']

student\_df = pd.DataFrame(student\_data, index=student\_ids)



print("Our sample DataFrame:")

print(student\_df)

print("

" + "="\*30 + "

")

Sample DataFrame:



Our sample DataFrame:

&#x20;     Name  Age  Score

S001   Alice   21     85

S002     Bob   22     90

S003 Charlie   20     78

S004   David   23     92



==============================

Understanding loc: Label-Based Indexing

The loc accessor is primarily label-based. This means you use the actual labels of the rows and columns to select data. It's intuitive when your index has meaningful names (like strings or dates).



Selecting Rows with loc

You can select a single row by passing its index label.



\# Select the row with index 'S002'

bob\_data = student\_df.loc\['S002']

print("Data for Bob (S002):")

print(bob\_data)

print("

" + "="\*30 + "

")

Output:



Data for Bob (S002):

Name    Bob

Age      22

Score    90

Name: null, dtype: object



==============================

Notice that selecting a single row returns a Pandas Series, where the index is the column names and the values are the data from that row.



You can select multiple rows by passing a list of index labels.



\# Select rows for Alice and David

alice\_david\_data = student\_df.loc\[\['S001', 'S004']]

print("Data for Alice and David:")

print(alice\_david\_data)

print("

" + "="\*30 + "

")

Output:



Data for Alice and David:

&#x20;     Name  Age  Score

S001   Alice   21     85

S004   David   23     92



==============================

Selecting multiple rows returns a DataFrame.



Selecting Columns with loc

You can select a single column by passing its column label.



\# Select the 'Name' column

names = student\_df.loc\[:, 'Name'] # The ':' selects all rows

print("All student names:")

print(names)

print("

" + "="\*30 + "

")

Output:



All student names:

S001      Alice

S002        Bob

S003    Charlie

S004      David

Name: null, dtype: object



==============================

Selecting a single column returns a Series.



You can select multiple columns by passing a list of column labels.



\# Select 'Name' and 'Score' columns for all students

name\_score = student\_df.loc\[:, \['Name', 'Score']]

print("Names and Scores:")

print(name\_score)

print("

" + "="\*30 + "

")

Output:



Names and Scores:

&#x20;     Name  Score

S001   Alice     85

S002     Bob     90

S003 Charlie     78

S004   David     92



==============================

Selecting multiple columns returns a DataFrame.



Selecting Specific Rows and Columns with loc

The real power of loc comes when you combine row and column selection. The syntax is df.loc\[row\_labels, column\_labels].



\# Select 'Age' and 'Score' for Bob and Charlie

age\_score\_bob\_charlie = student\_df.loc\[\['S002', 'S003'], \['Age', 'Score']]

print("Age and Score for Bob and Charlie:")

print(age\_score\_bob\_charlie)

print("

" + "="\*30 + "

")

Output:



Age and Score for Bob and Charlie:

&#x20;     Age  Score

S002   22     90

S003   20     78



==============================

Slicing with loc

loc also supports slicing using labels. When slicing, the start and end labels are inclusive.



\# Select all columns for students from S002 to S004

students\_s002\_to\_s004 = student\_df.loc\['S002':'S004']

print("Students from S002 to S004:")

print(students\_s002\_to\_s004)

print("

" + "="\*30 + "

")

Output:



Students from S002 to S004:

&#x20;     Name  Age  Score

S002     Bob   22     90

S003 Charlie   20     78

S004   David   23     92



==============================

\# Select 'Name' column for students from S001 to S003

names\_s001\_to\_s003 = student\_df.loc\['S001':'S003', 'Name']

print("Names from S001 to S003:")

print(names\_s001\_to\_s003)

print("

" + "="\*30 + "

")

Output:



Names from S001 to S003:

S001      Alice

S002        Bob

S003    Charlie

Name: null, dtype: object



==============================

Understanding iloc: Integer-Location Based Indexing

The iloc accessor is strictly integer-location based. This means you use the integer positions of rows and columns (starting from 0) to select data, regardless of the labels.



Selecting Rows with iloc

Select a single row by its integer position.



\# Select the first row (position 0)

first\_row = student\_df.iloc\[0]

print("First row (position 0):")

print(first\_row)

print("

" + "="\*30 + "

")

Output:



First row (position 0):

Name    Alice

Age        21

Score      85

Name: null, dtype: object



==============================

Selecting a single row returns a Series.



Select multiple rows by passing a list of integer positions.



\# Select the second and fourth rows (positions 1 and 3)

rows\_1\_and\_3 = student\_df.iloc\[\[1, 3]]

print("Rows at positions 1 and 3:")

print(rows\_1\_and\_3)

print("

" + "="\*30 + "

")

Output:



Rows at positions 1 and 3:

&#x20;   Name  Age  Score

S002   Bob   22     90

S004 David   23     92



==============================

Selecting multiple rows returns a DataFrame.



Selecting Columns with iloc

Select a single column by its integer position.



\# Select the second column (position 1, which is 'Age')

ages = student\_df.iloc\[:, 1] # The ':' selects all rows

print("All student ages:")

print(ages)

print("

" + "="\*30 + "

")

Output:



All student ages:

S001    21

S002    22

S003    20

S004    23

Name: null, dtype: int64



==============================

Selecting a single column returns a Series.



Select multiple columns by passing a list of integer positions.



\# Select the first and third columns (positions 0 and 2, 'Name' and 'Score')

name\_score\_cols = student\_df.iloc\[:, \[0, 2]]

print("Names and Scores (using iloc):")

print(name\_score\_cols)

print("

" + "="\*30 + "

")

Output:



Names and Scores (using iloc):

&#x20;     Name  Score

S001   Alice     85

S002     Bob     90

S003 Charlie     78

S004   David     92



==============================

Selecting multiple columns returns a DataFrame.



Selecting Specific Rows and Columns with iloc

Combine row and column integer positions: df.iloc\[row\_positions, column\_positions].



\# Select 'Age' and 'Score' (columns 1 and 2) for the first and third students (rows 0 and 2)

age\_score\_0\_and\_2 = student\_df.iloc\[\[0, 2], \[1, 2]]

print("Age and Score for students at positions 0 and 2:")

print(age\_score\_0\_and\_2)

print("

" + "="\*30 + "

")

Output:



Age and Score for students at positions 0 and 2:

&#x20;     Age  Score

S001   21     85

S003   20     78



==============================

Slicing with iloc

iloc supports slicing using integer positions. When slicing, the start position is inclusive, and the end position is exclusive (just like standard Python list slicing).



\# Select all columns for students from position 1 up to (but not including) position 4

students\_1\_to\_3 = student\_df.iloc\[1:4]

print("Students from position 1 to 3:")

print(students\_1\_to\_3)

print("

" + "="\*30 + "

")

Output:



Students from position 1 to 3:

&#x20;     Name  Age  Score

S002     Bob   22     90

S003 Charlie   20     78

S004   David   23     92



==============================

\# Select 'Name' column (position 0) for students from position 0 up to (but not including) position 3

names\_0\_to\_2 = student\_df.iloc\[0:3, 0]

print("Names for students at positions 0 to 2:")

print(names\_0\_to\_2)

print("

" + "="\*30 + "

")

Output:



Names for students at positions 0 to 2:

S001    Alice

S002      Bob

S003  Charlie

Name: null, dtype: object



==============================

loc vs. iloc: Key Differences

The choice between loc and iloc depends on whether you want to use labels or integer positions:



loc: Label-based. Use when you know the names of rows/columns. Slicing is inclusive of the end label.

iloc: Integer-location based. Use when you know the numerical position of rows/columns. Slicing is exclusive of the end position (standard Python slicing).

Hands-on Component 3: Select specific columns and rows from a DataFrame.



Using the student\_df, select the 'Name' and 'Age' columns for the student with ID 'S003' and the student at position 1 (which is 'S002').



Using loc:



\# Select 'Name' and 'Age' for 'S003' and 'S002'

selected\_data\_loc = student\_df.loc\[\['S003', 'S002'], \['Name', 'Age']]

print("Selection using loc:")

print(selected\_data\_loc)

print("

" + "="\*30 + "

")

Using iloc:



First, determine the integer positions for 'S003' and 'S002'. 'S003' is at position 2, and 'S002' is at position 1. The 'Name' column is at position 0, and 'Age' is at position 1.



\# Select 'Name' (pos 0) and 'Age' (pos 1) for students at positions 2 and 1

selected\_data\_iloc = student\_df.iloc\[\[2, 1], \[0, 1]]

print("Selection using iloc:")

print(selected\_data\_iloc)

print("

" + "="\*30 + "

")

Expected Output for both:



Selection using loc:

&#x20;     Name  Age

S003 Charlie   20

S002     Bob   22



==============================

Selection using iloc:

&#x20;     Name  Age

S003 Charlie   20

S002     Bob   22



==============================

Mastering loc and iloc is fundamental for efficient data manipulation in Pandas. They allow you to precisely target and extract the data you need for analysis.



Exploring Your Data's Structure: DataFrame Attributes and Methods

Once you have your data in a Pandas DataFrame, you'll want to understand its structure, contents, and characteristics. Pandas provides a rich set of attributes and methods that allow you to quickly inspect and get a feel for your dataset. These tools are invaluable for initial data exploration and understanding.



Let's continue working with our student\_df DataFrame.



import pandas as pd

import numpy as np



student\_data = {

&#x20;   'Name': \['Alice', 'Bob', 'Charlie', 'David', 'Eve'],

&#x20;   'Age': \[21, 22, 20, 23, 21],

&#x20;   'Score': \[85, 90, 78, 92, 88],

&#x20;   'Major': \['CS', 'EE', 'CS', 'ME', 'CS']

}

student\_ids = \['S001', 'S002', 'S003', 'S004', 'S005']

student\_df = pd.DataFrame(student\_data, index=student\_ids)



print("Our enhanced sample DataFrame:")

print(student\_df)

print("

" + "="\*40 + "

")

Sample DataFrame:



Our enhanced sample DataFrame:

&#x20;     Name  Age  Score Major

S001   Alice   21     85    CS

S002     Bob   22     90    EE

S003 Charlie   20     78    CS

S004   David   23     92    ME

S005     Eve   21     88    CS



========================================

Essential DataFrame Attributes

Attributes are properties of the DataFrame that you can access directly without calling a function (i.e., no parentheses () are needed).



DataFrame.index

This attribute returns the row index (labels) of the DataFrame.



print("DataFrame Index:")

print(student\_df.index)

print("

" + "="\*40 + "

")

Output:



DataFrame Index:

Index(\['S001', 'S002', 'S003', 'S004', 'S005'], dtype='object')



========================================

DataFrame.columns

This attribute returns the column labels of the DataFrame.



print("DataFrame Columns:")

print(student\_df.columns)

print("

" + "="\*40 + "

")

Output:



DataFrame Columns:

Index(\['Name', 'Age', 'Score', 'Major'], dtype='object')



========================================

DataFrame.values

This attribute returns the data in the DataFrame as a NumPy ndarray. It's useful for interoperability with other libraries that expect NumPy arrays.



print("DataFrame Values (as NumPy array):")

print(student\_df.values)

print("

" + "="\*40 + "

")

Output:



DataFrame Values (as NumPy array):

\[\['Alice' 21 85 'CS']

&#x20;\['Bob' 22 90 'EE']

&#x20;\['Charlie' 20 78 'CS']

&#x20;\['David' 23 92 'ME']

&#x20;\['Eve' 21 88 'CS']]



========================================

DataFrame.shape

This attribute returns a tuple representing the dimensions of the DataFrame (number of rows, number of columns).



print("DataFrame Shape (rows, columns):")

print(student\_df.shape)

print("

" + "="\*40 + "

")

Output:



DataFrame Shape (rows, columns):

(5, 4)



========================================

This tells us we have 5 rows and 4 columns.



DataFrame.dtypes

This attribute returns the data type of each column.



print("DataFrame Data Types:")

print(student\_df.dtypes)

print("

" + "="\*40 + "

")

Output:



DataFrame Data Types:

Name     object

Age       int64

Score     int64

Major    object

dtype: object



========================================

Understanding data types is crucial for performing correct operations and identifying potential issues.



Essential DataFrame Methods

Methods are functions associated with the DataFrame that perform operations and often return new DataFrames or Series (or modify the DataFrame in place if specified).



DataFrame.head(n=5)

Returns the first n rows of the DataFrame. By default, it returns the first 5 rows.



print("First 3 rows (using head(3)):")

print(student\_df.head(3))

print("

" + "="\*40 + "

")

Output:



First 3 rows (using head(3)):

&#x20;     Name  Age  Score Major

S001   Alice   21     85    CS

S002     Bob   22     90    EE

S003 Charlie   20     78    CS



========================================

DataFrame.tail(n=5)

Returns the last n rows of the DataFrame. By default, it returns the last 5 rows.



print("Last 2 rows (using tail(2)):")

print(student\_df.tail(2))

print("

" + "="\*40 + "

")

Output:



Last 2 rows (using tail(2)):

&#x20;     Name  Age  Score Major

S004   David   23     92    ME

S005     Eve   21     88    CS



========================================

DataFrame.info(verbose=None, show\_counts=None)

Provides a concise summary of the DataFrame, including the index dtype and column dtypes, non-null values, and memory usage. This is one of the most useful methods for initial data inspection.



print("DataFrame Info:")

student\_df.info()

print("

" + "="\*40 + "

")

Output:



DataFrame Info:



Index: 5 entries, S001 to S005

Data columns (total 4 columns):

&#x20;#   Column  Non-Null Count  Dtype 

\---  ------  --------------  ----- 

&#x20;0   Name    5 non-null      object

&#x20;1   Age     5 non-null      int64 

&#x20;2   Score   5 non-null      int64 

&#x20;3   Major   5 non-null      object

dtypes: int64(2), object(2)

memory usage: 200.0+ bytes



========================================

The info() method is excellent for quickly checking for missing values (indicated by non-null counts less than the total number of entries) and understanding the data types.



DataFrame.describe()

Generates descriptive statistics of the DataFrame's numerical columns. This includes count, mean, standard deviation, minimum, maximum, and quartiles.



print("Descriptive Statistics:")

print(student\_df.describe())

print("

" + "="\*40 + "

")

Output:



Descriptive Statistics:

&#x20;            Age      Score

count   5.000000   5.000000

mean   21.400000  87.000000

std     1.140175   5.700877

min    20.000000  78.000000

25%    21.000000  85.000000

50%    21.000000  88.000000

75%    22.000000  90.000000

max    23.000000  92.000000



========================================

By default, describe() only includes numerical columns. You can include other types using the include parameter (e.g., include='all' or include=\['object']).



print("Descriptive Statistics (including object types):")

print(student\_df.describe(include='all'))

print("

" + "="\*40 + "

")

Output:



Descriptive Statistics (including object types):

&#x20;     Name        Age  Score Major

count    5   5.000000    5.0     5

unique   5        NaN    NaN     3

top  Alice        NaN    NaN    CS

freq     1        NaN    NaN     3

mean   NaN  21.400000   87.0   NaN

std    NaN   1.140175    5.7   NaN

min    NaN  20.000000   78.0   NaN

25%    NaN  21.000000   85.0   NaN

50%    NaN  21.000000   88.0   NaN

75%    NaN  22.000000   90.0   NaN

max    NaN  23.000000   92.0   NaN



========================================

When include='all' is used, describe() provides statistics relevant to each data type: null, unique values, top occurring value, and its frequency for object types, and standard numerical statistics for numerical types.



DataFrame.T (Transpose)

This attribute returns the transpose of the DataFrame, swapping rows and columns.



print("Transposed DataFrame:")

print(student\_df.T)

print("

" + "="\*40 + "

")

Output:



Transposed DataFrame:

&#x20;         S001   S002   S003   S004   S005

Name     Alice    Bob Charlie  David    Eve

Age         21     22      20     23     21

Score       85     90      78     92     88

Major       CS     EE      CS     ME     CS



========================================

These attributes and methods provide a quick and efficient way to understand the basic characteristics of your data, which is essential before diving into more complex analysis or cleaning tasks.



Introduction to pandas dataframes and series

Lesson visual

Understanding Data Types in Pandas

Data types are fundamental to how data is stored, processed, and interpreted. In Pandas, each column in a DataFrame (and each element in a Series) has an associated data type, often referred to as its dtype. Understanding these types is crucial for performing correct operations, avoiding errors, and optimizing performance.



Pandas leverages NumPy's data types, but also introduces its own specific types for handling missing data and categorical information.



Common Pandas Data Types (dtypes)

Here are some of the most common data types you'll encounter:



object: This is a generic type that can hold any Python object. It's often used for strings, but can also contain mixed types. When Pandas cannot infer a more specific type, it defaults to object.

int64: 64-bit signed integers. This is the standard integer type in Pandas and NumPy.

float64: 64-bit floating-point numbers. This is the standard type for decimal numbers.

bool: Boolean values (True or False).

datetime64\[ns]: Date and time values. Pandas has sophisticated support for time series data.

timedelta\[ns]: Represents the difference between two datetime values.

category: A special type for categorical data. This is very efficient for columns with a limited number of unique values (e.g., 'Male'/'Female', 'Yes'/'No', product categories).

You can inspect the data types of a DataFrame using the .dtypes attribute, as we saw in the previous section.



import pandas as pd



data = {

&#x20;   'IntegerColumn': \[1, 2, 3, 4, 5],

&#x20;   'FloatColumn': \[1.1, 2.2, 3.3, 4.4, 5.5],

&#x20;   'StringColumn': \['apple', 'banana', 'cherry', 'date', 'elderberry'],

&#x20;   'BooleanColumn': \[True, False, True, False, True],

&#x20;   'MixedColumn': \[1, 'two', 3.0, True, None]

}

df\_types = pd.DataFrame(data)



print("DataFrame with various data types:")

print(df\_types)

print("

" + "="\*40 + "

")



print("Data types of the DataFrame:")

print(df\_types.dtypes)

print("

" + "="\*40 + "

")

Output:



DataFrame with various data types:

&#x20;  IntegerColumn  FloatColumn StringColumn  BooleanColumn MixedColumn

0              1          1.1        apple           True             1

1              2          2.2       banana          False           two

2              3          3.3       cherry           True           3.0

3              4          4.4         date          False          True

4              5          5.5   elderberry           True          None



========================================

Data types of the DataFrame:

IntegerColumn      int64

FloatColumn      float64

StringColumn    object

BooleanColumn     bool

MixedColumn     object

dtype: object



========================================

Understanding `object` dtype

The object dtype is a catch-all. While convenient, it can sometimes lead to performance issues because Pandas cannot perform vectorized operations as efficiently on objects as it can on specific numerical or boolean types. It's also important to note that None values in a column that would otherwise be numeric will often cause that column to be cast to object dtype.



Pandas has introduced nullable integer and float types (e.g., Int64, Float64 - note the capital 'I' and 'F') that can handle missing values (pd.NA) while retaining their numeric type. This is a more modern approach than relying solely on the object dtype for numeric columns with missing data.



The Importance of Data Types

Memory Usage: Different data types consume different amounts of memory. Using the most appropriate and efficient type can significantly reduce the memory footprint of your DataFrames, especially for large datasets. For example, a category dtype is much more memory-efficient than an object dtype for columns with repeated string values.

Performance: Vectorized operations on numerical types (int64, float64) are much faster than operations on object types.

Correctness of Operations: Performing mathematical operations on strings will result in errors, while operations on numbers are expected. Pandas enforces type consistency to ensure operations are valid.

Data Integrity: Understanding data types helps in identifying potential data quality issues. For instance, if a column expected to be numeric is of object type, it might contain non-numeric entries that need cleaning.

Function Compatibility: Many libraries and functions (especially in machine learning) expect specific data types. For example, Scikit-learn models typically require numerical input.

Type Conversion

You can explicitly convert data types using the astype() method. This is a common operation during data cleaning and preparation.



\# Convert 'IntegerColumn' to float

df\_types\['IntegerColumn'] = df\_types\['IntegerColumn'].astype('float64')

print("After converting IntegerColumn to float:")

print(df\_types.dtypes)

print("

" + "="\*40 + "

")



\# Convert 'StringColumn' to category

df\_types\['StringColumn'] = df\_types\['StringColumn'].astype('category')

print("After converting StringColumn to category:")

print(df\_types.dtypes)

print("

" + "="\*40 + "

")

Output:



After converting IntegerColumn to float:

IntegerColumn    float64

FloatColumn      float64

StringColumn      object

BooleanColumn       bool

MixedColumn       object

dtype: object



========================================

After converting StringColumn to category:

IntegerColumn    float64

FloatColumn      float64

StringColumn    category

BooleanColumn       bool

MixedColumn     object

dtype: object



========================================

The astype() method is a powerful tool for ensuring your data is in the correct format for analysis and modeling. We will explore type conversion in more detail in the next lesson on Data Loading and Cleaning.



Initial Data Exploration: Essential Inspection Methods

Before diving deep into analysis or cleaning, it's crucial to get a quick overview of your dataset. Pandas provides several intuitive methods for initial data inspection, allowing you to understand the structure, content, and basic statistics of your DataFrame. These methods are your first line of defense in comprehending your data.



We will use a slightly larger and more diverse DataFrame for this section to better illustrate the methods.



import pandas as pd

import numpy as np



data = {

&#x20;   'ProductID': \['A101', 'B202', 'C303', 'A101', 'D404', 'B202', 'E505', 'C303', 'A101', 'F606'],

&#x20;   'Category': \['Electronics', 'Clothing', 'Home Goods', 'Electronics', 'Electronics', 'Clothing', 'Home Goods', 'Home Goods', 'Electronics', 'Clothing'],

&#x20;   'Price': \[1200.50, 45.99, 150.75, 1150.00, 800.25, 55.00, 210.50, 165.00, 1250.75, 39.99],

&#x20;   'Quantity': \[10, 50, 20, 12, 8, 45, 15, 22, 11, 55],

&#x20;   'InStock': \[True, True, False, True, True, True, False, True, True, True],

&#x20;   'Rating': \[4.5, 4.0, 3.8, 4.6, 4.2, 4.1, 3.5, 3.9, 4.4, 4.0]

}

order\_ids = \[f'ORD{i:03d}' for i in range(1, 11)]

sales\_df = pd.DataFrame(data, index=order\_ids)



print("Sample Sales DataFrame:")

print(sales\_df)

print("

" + "="\*50 + "

")

Sample Sales DataFrame:



Sample Sales DataFrame:

&#x20;     ProductID     Category    Price  Quantity  InStock  Rating

ORD001      A101  Electronics  1200.50        10     True     4.5

ORD002      B202     Clothing    45.99        50     True     4.0

ORD003      C303   Home Goods   150.75        20    False     3.8

ORD004      A101  Electronics  1150.00        12     True     4.6

ORD005      D404  Electronics   800.25         8     True     4.2

ORD006      B202     Clothing    55.00        45     True     4.1

ORD007      E505   Home Goods   210.50        15    False     3.5

ORD008      C303   Home Goods   165.00        22     True     3.9

ORD009      A101  Electronics  1250.75        11     True     4.4

ORD010      F606     Clothing    39.99        55     True     4.0



==================================================

DataFrame.head(n=5): Peeking at the Beginning

As discussed earlier, head() displays the first n rows. It's excellent for quickly seeing the structure and the first few data points.



print("First 5 rows (default head):")

print(sales\_df.head())

print("

" + "="\*50 + "

")



print("First 3 rows:")

print(sales\_df.head(3))

print("

" + "="\*50 + "

")

Output:



First 5 rows (default head):

&#x20;     ProductID     Category    Price  Quantity  InStock  Rating

ORD001      A101  Electronics  1200.50        10     True     4.5

ORD002      B202     Clothing    45.99        50     True     4.0

ORD003      C303   Home Goods   150.75        20    False     3.8

ORD004      A101  Electronics  1150.00        12     True     4.6

ORD005      D404  Electronics   800.25         8     True     4.2



==================================================

First 3 rows:

&#x20;     ProductID     Category    Price  Quantity  InStock  Rating

ORD001      A101  Electronics  1200.50        10     True     4.5

ORD002      B202     Clothing    45.99        50     True     4.0

ORD003      C303   Home Goods   150.75        20    False     3.8



==================================================

DataFrame.tail(n=5): Checking the End

tail() displays the last n rows. This is useful for verifying data loading, especially if there are summary rows or footers in your source file.



print("Last 5 rows (default tail):")

print(sales\_df.tail())

print("

" + "="\*50 + "

")



print("Last 2 rows:")

print(sales\_df.tail(2))

print("

" + "="\*50 + "

")

Output:



Last 5 rows (default tail):

&#x20;     ProductID     Category    Price  Quantity  InStock  Rating

ORD006      B202     Clothing    55.00        45     True     4.1

ORD007      E505   Home Goods   210.50        15    False     3.5

ORD008      C303   Home Goods   165.00        22     True     3.9

ORD009      A101  Electronics  1250.75        11     True     4.4

ORD010      F606     Clothing    39.99        55     True     4.0



==================================================

Last 2 rows:

&#x20;     ProductID  Category   Price  Quantity  InStock  Rating

ORD009      A101 Electronics 1250.75        11     True     4.4

ORD010      F606  Clothing    39.99        55     True     4.0



==================================================

DataFrame.info(): The Comprehensive Overview

info() is arguably the most important method for initial inspection. It provides a summary of the DataFrame's structure, including:



The DataFrame's class and memory usage.

The index type and range.

For each column: its name, the number of non-null values, and its data type (dtype).

This method is invaluable for quickly identifying missing data and understanding the types of information you're working with.



print("DataFrame Info:")

sales\_df.info()

print("

" + "="\*50 + "

")

Output:



DataFrame Info:



Index: 10 entries, ORD001 to ORD010

Data columns (total 6 columns):

&#x20;#   Column     Non-Null Count  Dtype  

\---  ------     --------------  -----  

&#x20;0   ProductID  10 non-null     object 

&#x20;1   Category   10 non-null     object 

&#x20;2   Price      10 non-null     float64

&#x20;3   Quantity   10 non-null     int64  

&#x20;4   InStock    10 non-null     bool   

&#x20;5   Rating     10 non-null     float64

dtypes: bool(1), float64(2), int64(1), object(2)

memory usage: 480.0+ bytes



==================================================

Notice how info() clearly shows that all columns have 10 non-null values, meaning there are no missing values in this particular DataFrame. It also confirms the data types we expect.



DataFrame.describe(): Statistical Insights

describe() provides summary statistics for numerical columns. It's a quick way to understand the distribution and range of your numerical data.



print("Descriptive Statistics for numerical columns:")

print(sales\_df.describe())

print("

" + "="\*50 + "

")

Output:



Descriptive Statistics for numerical columns:

&#x20;           Price    Quantity    Rating

count   10.000000   10.000000  10.00000

mean   325.424000   23.800000   4.05000

std    445.485814   17.644765   0.37556

min     39.990000    8.000000   3.50000

25%     52.490000   11.250000   3.92500

50%    157.875000   17.500000   4.05000

75%   1162.750000   47.500000   4.27500

max   1250.750000   55.000000   4.60000



==================================================

This output gives us insights like:



The average price is $325.42, but the median (50%) is much lower at $157.88, indicating a right-skewed distribution (likely due to high-priced electronics).

The quantity sold ranges from 8 to 55.

Ratings are generally high, between 3.5 and 4.6.

Using describe(include='all') provides similar statistics for non-numerical columns as well, such as the count of unique values and the most frequent one.



print("Descriptive Statistics (including all types):")

print(sales\_df.describe(include='all'))

print("

" + "="\*50 + "

")

Output:



Descriptive Statistics (including all types):

&#x20;     ProductID     Category        Price    Quantity  InStock    Rating

count          10           10    10.000000   10.000000       10  10.00000

unique          6            3          NaN         NaN      NaN       NaN

top          A101  Electronics         NaN         NaN      NaN       NaN

freq            3            4          NaN         NaN      NaN       NaN

mean          NaN          NaN   325.424000   23.800000      NaN  4.05000

std           NaN          NaN   445.485814   17.644765      NaN  0.37556

min           NaN          NaN    39.990000    8.000000      NaN  3.50000

25%           NaN          NaN    52.490000   11.250000      NaN  3.92500

50%           NaN          NaN   157.875000   17.500000      NaN  4.05000

75%           NaN          NaN   1162.750000   47.500000      NaN  4.27500

max           NaN          NaN   1250.750000   55.000000      NaN  4.60000



==================================================

These initial inspection methods are your first step in understanding any dataset. They provide a quick, high-level view that guides your subsequent analysis and cleaning efforts.



Putting It All Together: Practical Application and Hands-on Exercises

In this section, we'll consolidate our learning by applying the concepts of creating, indexing, and inspecting Pandas Series and DataFrames through practical exercises. This hands-on approach is crucial for solidifying your understanding and building confidence.



We will use the Jupyter Notebook environment for these exercises. Ensure you have Pandas and NumPy installed and imported.



import pandas as pd

import numpy as np

Exercise 1: Creating and Inspecting a Series of Temperatures

Objective: Create a Pandas Series from a list of daily temperatures and perform basic inspection.



Scenario: You have recorded the maximum temperature for five consecutive days.



Steps:



Create a Python list named daily\_temperatures containing the following temperature values: \[25.5, 27.0, 26.8, 28.2, 27.5].

Create a Pandas Series named temp\_series from this list.

Assign custom index labels representing the days of the week: \['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday'].

Print the created temp\_series to verify its contents.

Use the .index attribute to display the index.

Use the .values attribute to display the data as a NumPy array.

Use the .dtype attribute to check the data type.

Expected Code Snippet:



\# Step 1: Create the list

daily\_temperatures = \[25.5, 27.0, 26.8, 28.2, 27.5]



\# Step 2 \& 3: Create the Series with custom index

days\_of\_week = \['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']

temp\_series = pd.Series(daily\_temperatures, index=days\_of\_week)



\# Step 4: Print the Series

print("Temperature Series:")

print(temp\_series)

print("

" + "="\*30 + "

")



\# Step 5: Display the index

print("Index of the Temperature Series:")

print(temp\_series.index)

print("

" + "="\*30 + "

")



\# Step 6: Display the values

print("Values of the Temperature Series:")

print(temp\_series.values)

print("

" + "="\*30 + "

")



\# Step 7: Check the data type

print("Data type of the Temperature Series:")

print(temp\_series.dtype)

print("

" + "="\*30 + "

")

Expected Output:



Temperature Series:

Monday       25.5

Tuesday      27.0

Wednesday    26.8

Thursday     28.2

Friday       27.5

dtype: float64



==============================

Index of the Temperature Series:

Index(\['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday'], dtype='object')



==============================

Values of the Temperature Series:

\[25.5 27.  26.8 28.2 27.5]



==============================

Data type of the Temperature Series:

float64



==============================

Exercise 2: Creating and Inspecting a DataFrame of Product Inventory

Objective: Create a Pandas DataFrame from a dictionary and perform initial inspection.



Scenario: You are managing inventory for a small online store. You have data on product names, quantities in stock, and their prices.



Steps:



Create a Python dictionary named inventory\_data with the following structure:

Key 'ProductName' with values: \['Laptop', 'Keyboard', 'Mouse', 'Monitor', 'Webcam']

Key 'Quantity' with values: \[15, 50, 75, 20, 30]

Key 'Price' with values: \[1200.00, 75.50, 25.00, 300.75, 60.00]

Create a Pandas DataFrame named inventory\_df from this dictionary.

Assign custom row index labels representing product SKUs: \['SKU001', 'SKU002', 'SKU003', 'SKU004', 'SKU005'].

Print the entire inventory\_df.

Use the .shape attribute to find the number of rows and columns.

Use the .columns attribute to list the column names.

Use the .dtypes attribute to check the data types of each column.

Use the .head(2) method to display the first two rows.

Use the .tail(1) method to display the last row.

Use the .info() method to get a summary of the DataFrame.

Use the .describe() method to get descriptive statistics for numerical columns.

Expected Code Snippet:



\# Step 1: Create the dictionary

inventory\_data = {

&#x20;   'ProductName': \['Laptop', 'Keyboard', 'Mouse', 'Monitor', 'Webcam'],

&#x20;   'Quantity': \[15, 50, 75, 20, 30],

&#x20;   'Price': \[1200.00, 75.50, 25.00, 300.75, 60.00]

}



\# Step 2 \& 3: Create the DataFrame with custom index

product\_skus = \['SKU001', 'SKU002', 'SKU003', 'SKU004', 'SKU005']

inventory\_df = pd.DataFrame(inventory\_data, index=product\_skus)



\# Step 4: Print the DataFrame

print("Inventory DataFrame:")

print(inventory\_df)

print("

" + "="\*30 + "

")



\# Step 5: Display shape

print("Shape of the Inventory DataFrame (rows, columns):")

print(inventory\_df.shape)

print("

" + "="\*30 + "

")



\# Step 6: Display columns

print("Column names:")

print(inventory\_df.columns)

print("

" + "="\*30 + "

")



\# Step 7: Display data types

print("Data types of Inventory DataFrame columns:")

print(inventory\_df.dtypes)

print("

" + "="\*30 + "

")



\# Step 8: Display first 2 rows

print("First 2 rows (head(2)):")

print(inventory\_df.head(2))

print("

" + "="\*30 + "

")



\# Step 9: Display last row

print("Last row (tail(1)):")

print(inventory\_df.tail(1))

print("

" + "="\*30 + "

")



\# Step 10: Display DataFrame info

print("Inventory DataFrame Info:")

inventory\_df.info()

print("

" + "="\*30 + "

")



\# Step 11: Display descriptive statistics

print("Descriptive Statistics for Inventory DataFrame:")

print(inventory\_df.describe())

print("

" + "="\*30 + "

")

Expected Output:



Inventory DataFrame:

&#x20;       ProductName  Quantity    Price

SKU001       Laptop        15  1200.00

SKU002     Keyboard        50    75.50

SKU003        Mouse        75    25.00

SKU004      Monitor        20   300.75

SKU005       Webcam        30    60.00



==============================

Shape of the Inventory DataFrame (rows, columns):

(5, 3)



==============================

Column names:

Index(\['ProductName', 'Quantity', 'Price'], dtype='object')



==============================

Data types of Inventory DataFrame columns:

ProductName     object

Quantity         int64

Price          float64

dtype: object



==============================

First 2 rows (head(2)):

&#x20;       ProductName  Quantity    Price

SKU001       Laptop        15  1200.00

SKU002     Keyboard        50    75.50



==============================

Last row (tail(1)):

&#x20;     ProductName  Quantity  Price

SKU005       Webcam        30  60.00



==============================

Inventory DataFrame Info:



Index: 5 entries, SKU001 to SKU005

Data columns (total 3 columns):

&#x20;#   Column       Non-Null Count  Dtype  

\---  ------       --------------  -----  

&#x20;0   ProductName  5 non-null      object 

&#x20;1   Quantity     5 non-null      int64  

&#x20;2   Price        5 non-null      float64

dtypes: float64(1), int64(1), object(1)

memory usage: 160.0+ bytes



==============================

Descriptive Statistics for Inventory DataFrame:

&#x20;        Quantity      Price

count    5.000000   5.000000

mean    36.000000  330.250000

std     23.853717  453.589139

min     15.000000   25.000000

25%     20.000000   60.000000

50%     30.000000   75.500000

75%     50.000000  300.750000

max     75.000000 1200.000000



==============================

Exercise 3: Selecting Specific Data from the Inventory DataFrame

Objective: Use loc and iloc to select specific rows and columns from the inventory\_df.



Scenario: You need to extract specific pieces of information from the inventory data.



Tasks:



Select and print the Price and Quantity for the Monitor (SKU004).

Select and print the ProductName for all items using loc.

Select and print the ProductName for the first three items (SKU001, SKU002, SKU003) using iloc.

Select and print the Price for the Keyboard (SKU002) and Webcam (SKU005).

Expected Code Snippet:



\# Task 1: Select Price and Quantity for Monitor (SKU004)

\# Using loc:

monitor\_price\_qty\_loc = inventory\_df.loc\['SKU004', \['Price', 'Quantity']]

print("Task 1 (loc): Price and Quantity for Monitor:")

print(monitor\_price\_qty\_loc)

print("

" + "="\*30 + "

")



\# Task 2: Select ProductName for all items using loc

all\_product\_names\_loc = inventory\_df.loc\[:, 'ProductName']

print("Task 2 (loc): All Product Names:")

print(all\_product\_names\_loc)

print("

" + "="\*30 + "

")



\# Task 3: Select ProductName for first three items (SKU001, SKU002, SKU003) using iloc

\# SKU001 is at pos 0, SKU002 at pos 1, SKU003 at pos 2. ProductName is at col pos 0.

first\_three\_names\_iloc = inventory\_df.iloc\[0:3, 0] # Slicing 0:3 includes 0, 1, 2

print("Task 3 (iloc): Product Names for first three items:")

print(first\_three\_names\_iloc)

print("

" + "="\*30 + "

")



\# Task 4: Select Price for Keyboard (SKU002) and Webcam (SKU005)

\# Using loc:

keyboard\_webcam\_price\_loc = inventory\_df.loc\[\['SKU002', 'SKU005'], 'Price']

print("Task 4 (loc): Price for Keyboard and Webcam:")

print(keyboard\_webcam\_price\_loc)

print("

" + "="\*30 + "

")

Expected Output:



Task 1 (loc): Price and Quantity for Monitor:

Quantity    20.00

Price      300.75

Name: null, dtype: object



==============================

Task 2 (loc): All Product Names:

SKU001       Laptop

SKU002     Keyboard

SKU003        Mouse

SKU004      Monitor

SKU005       Webcam

Name: null, dtype: object



==============================

Task 3 (iloc): Product Names for first three items:

SKU001    Laptop

SKU002  Keyboard

SKU003     Mouse

Name: null, dtype: object



==============================

Task 4 (loc): Price for Keyboard and Webcam:

SKU002    75.50

SKU005    60.00

Name: null, dtype: float64



==============================

These exercises provide a practical foundation for working with Pandas Series and DataFrames. Remember to experiment with different combinations of indexing and methods to become more comfortable.



Summary, Best Practices, and Preparing for Data Loading

Congratulations on completing the introduction to Pandas Series and DataFrames! You've covered the fundamental concepts and practical skills necessary to begin your data analysis journey.



Key Takeaways from this Lesson:

Pandas Series: A one-dimensional labeled array, like a single column.

Pandas DataFrame: A two-dimensional labeled data structure with columns of potentially different types, like a table.

Creation: Series and DataFrames can be created from Python lists, dictionaries, and NumPy arrays using pd.Series() and pd.DataFrame(). Custom indices can be provided.

Indexing and Selection:

.loc\[] is label-based (uses row/column names). Slicing is inclusive.

.iloc\[] is integer-location based (uses row/column positions). Slicing is exclusive (standard Python slicing).

Attributes: Properties like .index, .columns, .values, .shape, and .dtypes provide structural information.

Methods: Functions like .head(), .tail(), .info(), and .describe() offer quick ways to inspect and summarize data.

Data Types (dtypes): Understanding types like int64, float64, object, and bool is crucial for memory efficiency, performance, and correctness. The .astype() method allows for type conversion.

Best Practices and Pro Tips:

Import Convention: Always import Pandas as pd: import pandas as pd.

Descriptive Indexing: Use meaningful labels for your indices (e.g., dates, IDs) whenever possible. This makes your code more readable and your data easier to work with using .loc.

Prefer .loc and .iloc: While direct indexing (e.g., df\['column']) works, using .loc and .iloc is generally recommended for clarity and to avoid potential ambiguity, especially when chaining operations.

Use .info() Early and Often: This is your go-to method for a quick understanding of your data's structure, types, and missing values.

Understand Data Types: Pay close attention to dtypes. If a numerical column is showing as object, investigate why (often due to non-numeric entries or None values). Consider using nullable dtypes (e.g., pd.Int64Dtype()) for columns that might contain missing numerical data.

.describe() for Numerical Insights: Use this to quickly grasp the central tendency, dispersion, and shape of your numerical data.

Check for Duplicates (Later): While not covered in depth here, remember that identifying and handling duplicate rows is a critical step in data cleaning.

Readability: Write clear, concise code. Use meaningful variable names. Add comments where necessary.

Additional Resources:

Official Pandas Documentation: pandas.pydata.org/docs/ - The definitive source for all Pandas information.

Pandas Cookbook: Search for "Pandas Cookbook" online for practical recipes and examples.

Online Courses and Tutorials: Platforms like Coursera, edX, DataCamp, and YouTube offer numerous resources for further learning.

Preparation for the Next Lesson: Data Loading and Cleaning

In our next lesson, we will build directly upon the foundation laid today. We will focus on the practical aspects of getting data into Pandas and preparing it for analysis.



Topics to Prepare For:



Reading Data: We will learn how to load data from common file formats like CSV (Comma Separated Values), Excel spreadsheets, and basic SQL queries.

Handling Missing Values: This is a critical step. We'll explore methods like isnull(), notnull(), dropna(), and fillna() to identify and manage missing data.

Identifying and Removing Duplicates: We'll learn how to find and eliminate redundant rows using duplicated() and drop\_duplicates().

Renaming Columns and Resetting Indices: Making your DataFrame's structure more intuitive.

Data Type Conversion: Using astype() to ensure columns have the correct data types.

Basic String Manipulation: Performing simple operations on text data within columns.

Hands-on Components for Next Lesson:



Load a dataset from a CSV file.

Identify and fill missing values in a DataFrame.

Remove duplicate rows from a dataset.

To prepare, try to find a simple CSV file online (e.g., from Kaggle or government open data portals) and try to load it into a Pandas DataFrame using pd.read\_csv(). This will give you a head start for our next session.



Keep practicing, and you'll become proficient with Pandas in no time!



**Part-2:**



Data Loading and Cleaning

Lesson visual

Introduction: Laying the Foundation for Data Science with Pandas

Welcome to the essential module on data loading and cleaning! In the world of Data Science and Machine Learning, the adage 'Garbage in, garbage out' holds profoundly true. Before any sophisticated model can be built or insightful analysis performed, the data must be in a usable, reliable, and consistent format. This lesson is your gateway to mastering the foundational skills of data ingestion and preparation using Python's powerful Pandas library.



Throughout this lesson, we will delve into the critical processes of reading data from various common sources, identifying and rectifying imperfections within datasets, and ensuring the data is ready for subsequent analytical steps. Our focus will be on practical application, equipping you with the hands-on experience needed to tackle real-world data challenges.



Learning Objectives for this Lesson:



Understand how to load structured data from CSV, Excel, and basic SQL sources into Pandas DataFrames.

Master techniques for identifying and handling missing values using Pandas functions like isnull(), notnull(), dropna(), and fillna().

Learn to detect and remove duplicate rows to ensure data integrity.

Gain proficiency in renaming columns and resetting DataFrame indices for clarity and consistency.

Understand the importance of and practice converting data types for accurate analysis.

Develop skills in basic string manipulation on DataFrame columns.

These objectives directly contribute to the module's overarching goals: 'Understand Pandas DataFrames and Series,' 'Load, clean, and transform structured data,' 'Perform data selection, filtering, and aggregation,' and 'Handle missing data and duplicate entries.'



The ability to load and clean data is not just a technical skill; it's a fundamental prerequisite for any data-driven decision-making process. Whether you're building a predictive model, performing exploratory data analysis, or creating a business intelligence dashboard, the quality of your insights is directly proportional to the quality of your data. This lesson will provide you with the essential toolkit to ensure that quality.



Ingesting Data: Bringing Information into Pandas

The first step in any data science workflow is to get your data into a format that can be easily manipulated and analyzed. Pandas provides highly efficient and user-friendly functions for reading data from a variety of common file formats and databases. We will focus on three primary sources: CSV files, Excel spreadsheets, and basic SQL queries.



Reading Data from CSV Files

Reading Data from Excel Files

Reading Data from SQL Databases (Basic)

Comma Separated Values (CSV) files are one of the most ubiquitous data formats. They are plain text files where data values are separated by commas. Pandas offers the read\_csv() function, which is incredibly versatile.



Why CSV? CSVs are simple, human-readable, and widely supported by almost all data-handling software. They are excellent for data exchange.



How to Implement:



To use read\_csv(), you simply provide the path to your CSV file. Pandas will automatically infer the delimiter (usually a comma) and attempt to correctly parse the data into a DataFrame.



Let's assume you have a file named sales\_data.csv in the same directory as your Jupyter Notebook.



import pandas as pd



\# Load data from a CSV file

df\_csv = pd.read\_csv('sales\_data.csv')



\# Display the first 5 rows of the DataFrame

print(df\_csv.head())



\# Display information about the DataFrame (columns, data types, non-null counts)

print(df\_csv.info())

Key Parameters for read\_csv():



filepath\_or\_buffer: The path to the file.

sep: The delimiter to use (e.g., ',' for comma, ';' for semicolon, ' ' for tab). Defaults to ','.

header: Row number to use as the column names. Defaults to 0 (the first row). Set to None if the file has no header.

index\_col: Column to use as the row labels (index). Can be an integer or column name.

names: A list of column names to use. Useful if the file has no header.

dtype: A dictionary mapping column names to data types (e.g., {'column\_name': null}).

parse\_dates: A list of column names or indices to parse as dates.

na\_values: Additional strings to recognize as NaN (Not a Number).

Real-world Scenario: Imagine you've downloaded a dataset of customer transactions from an e-commerce platform. This data is typically provided in CSV format. You would use pd.read\_csv() to load it into Pandas for analysis, perhaps to identify top-selling products or customer purchasing patterns.



Mastering Missing Values: The isnull(), notnull(), dropna(), and fillna() Toolkit

Real-world data is rarely perfect. Missing values, often represented as NaN (Not a Number) in Pandas, are a common issue. These can arise from various reasons: data entry errors, sensor malfunctions, or simply data that was not collected. Ignoring missing values can lead to biased analyses and inaccurate model predictions. Pandas provides a robust set of tools to identify, understand, and handle them.



Identifying Missing Values with <code>isnull()</code> and <code>notnull()</code>

Removing Missing Values with <code>dropna()</code>

Imputing Missing Values with <code>fillna()</code>

The first step in handling missing data is to detect its presence. Pandas offers two straightforward boolean methods for this:



isnull(): Returns a DataFrame of the same shape, where True indicates a missing value (NaN) and False indicates a present value.

notnull(): The inverse of isnull(), returning True for present values and False for missing values.

Why is this important? Before you can decide how to handle missing data, you need to know where it is and how much of it there is. This step is crucial for understanding the completeness of your dataset.



How to Implement:



Let's create a sample DataFrame with some missing values to demonstrate.



import pandas as pd

import numpy as np



\# Create a sample DataFrame with missing values

data = {

&#x20;   'Name': \['Alice', 'Bob', 'Charlie', 'David', 'Eve'],

&#x20;   'Age': \[25, 30, np.nan, 22, 28],

&#x20;   'City': \['New York', np.nan, 'Los Angeles', 'Chicago', 'New York'],

&#x20;   'Salary': \[70000, 80000, 65000, np.nan, 72000]

}

df = pd.DataFrame(data)



print('Original DataFrame:')

print(df)



\# Identify missing values using isnull()

is\_null\_df = df.isnull()

print('

DataFrame showing missing values (True indicates NaN):')

print(is\_null\_df)



\# Identify non-missing values using notnull()

is\_not\_null\_df = df.notnull()

print('

DataFrame showing non-missing values (True indicates not NaN):')

print(is\_not\_null\_df)



\# Count missing values per column

missing\_counts = df.isnull().sum()

print('

Number of missing values per column:')

print(missing\_counts)



\# Calculate the percentage of missing values per column

missing\_percentage = (df.isnull().sum() / len(df)) \* 100

print('

Percentage of missing values per column:')

print(missing\_percentage)

Real-world Scenario: You're analyzing survey responses, and some participants skipped certain questions. Using df.isnull().sum(), you can quickly see how many responses are missing for each question, helping you decide if a question needs to be removed or if the missing responses can be imputed.



Ensuring Data Integrity: Identifying and Removing Duplicate Rows

Duplicate records in a dataset can skew analysis results, leading to overcounting of certain observations and potentially flawed conclusions. For instance, if a customer record appears twice, any analysis based on customer counts or average purchase value would be inaccurate. Pandas provides straightforward methods to detect and remove these duplicates.



Identifying Duplicate Rows with <code>duplicated()</code>

Removing Duplicate Rows with <code>drop\_duplicates()</code>

The duplicated() method returns a boolean Series indicating which rows in a DataFrame are duplicates. By default, it considers a row a duplicate if it is identical to a previous row.



Why identify duplicates? Before removing them, it's good practice to understand how many duplicates exist and where they are located. This helps in deciding the best course of action.



How to Implement:



Let's create a DataFrame with duplicate entries.



import pandas as pd



\# Create a sample DataFrame with duplicate rows

data\_dup = {

&#x20;   'ID': \[1, 2, 3, 1, 4, 2, 5],

&#x20;   'Name': \['Alice', 'Bob', 'Charlie', 'Alice', 'David', 'Bob', 'Eve'],

&#x20;   'Value': \[100, 200, 150, 100, 300, 200, 250]

}

df\_dup = pd.DataFrame(data\_dup)



print('Original DataFrame with duplicates:')

print(df\_dup)



\# Identify duplicate rows (marks subsequent occurrences as True)

duplicate\_rows = df\_dup.duplicated()

print('

Boolean Series indicating duplicate rows:')

print(duplicate\_rows)



\# Show the actual duplicate rows

duplicate\_data = df\_dup\[df\_dup.duplicated()]

print('

Rows identified as duplicates:')

print(duplicate\_data)



\# Count the number of duplicate rows

num\_duplicates = df\_dup.duplicated().sum()

print(f'

Number of duplicate rows: {num\_duplicates}')

Key Parameters for duplicated():



subset: A list of column labels to consider for identifying duplicates. If not specified, all columns are used.

keep: Determines which duplicates (if any) to mark.

'first' (default): Marks duplicates except for the first occurrence.

'last': Marks duplicates except for the last occurrence.

False: Marks all duplicates.

Real-world Scenario: In a customer database, a customer might accidentally be entered twice with the exact same details. Using df.duplicated() helps you find these redundant entries.



Structuring Your Data: Renaming Columns and Resetting Indices

A well-structured DataFrame is easier to understand and work with. Column names should be descriptive and consistent, and the index should serve a clear purpose. Pandas provides simple yet powerful methods to rename columns and manage the DataFrame index.



Renaming Columns with <code>rename()</code>

Managing Indices with <code>reset\_index()</code>

Column names are crucial for readability. Often, data sources have cryptic or inconsistent column names (e.g., 'col1', 'cust\_id', 'SALES\_AMT'). The rename() method allows you to change these names systematically.



Why rename columns? Clear, descriptive column names make your code more readable, your analysis easier to follow, and your DataFrames more self-explanatory. It's a fundamental step in data wrangling.



How to Implement:



The rename() method typically uses a dictionary to map old names to new names. You can rename specific columns or all columns.



import pandas as pd



\# Sample DataFrame with less-than-ideal column names

data\_rename = {

&#x20;   'cust\_id': \[101, 102, 103],

&#x20;   'ord\_dt': \['2023-01-15', '2023-01-16', '2023-01-17'],

&#x20;   'prod\_nm': \['Widget A', 'Gadget B', 'Thingamajig C'],

&#x20;   'amt': \[50.50, 75.25, 120.00]

}

df\_rename = pd.DataFrame(data\_rename)



print('Original DataFrame with cryptic column names:')

print(df\_rename)



\# Rename specific columns using a dictionary

new\_column\_names = {

&#x20;   'cust\_id': 'CustomerID',

&#x20;   'ord\_dt': 'OrderDate',

&#x20;   'prod\_nm': 'ProductName',

&#x20;   'amt': 'Amount'

}

df\_renamed = df\_rename.rename(columns=new\_column\_names)

print('

DataFrame after renaming columns:')

print(df\_renamed)



\# You can also rename columns using a lambda function (less common for direct mapping)

\# df\_renamed\_lambda = df\_rename.rename(columns=lambda x: x.upper())



\# To modify the DataFrame in place, use inplace=True

\# df\_rename.rename(columns=new\_column\_names, inplace=True)

Best Practices for Column Names:



Use descriptive names (e.g., 'CustomerAge' instead of 'Age' if context is needed).

Use snake\_case (e.g., 'order\_date') or camelCase (e.g., 'orderDate') consistently. Avoid spaces and special characters.

Keep names concise but informative.

Real-world Scenario: When merging data from different sources, column names might conflict or be ambiguous. Renaming them to a standardized format before merging is crucial for clarity and preventing errors.



Data Loading and Cleaning

Lesson visual

Ensuring Data Consistency: Data Type Conversion

Data types are fundamental to how data is stored and processed. Pandas DataFrames have columns with specific data types (e.g., integer, float, string, boolean, datetime). Incorrect data types can lead to errors during calculations, incorrect aggregations, and inefficient memory usage. Converting data types is a critical cleaning step.



Understanding and Converting Data Types with <code>astype()</code>

Pandas infers data types when reading data, but these inferences are not always correct. For example, numerical IDs might be read as integers but should perhaps be strings, or dates might be read as strings and need to be converted to datetime objects.



Why convert data types?



Accuracy: Performing mathematical operations on strings will fail or produce unexpected results. Dates need to be in datetime format for time-based analysis.

Efficiency: Using appropriate data types (e.g., smaller integer types like int8 or int16 if values are within range) can significantly reduce memory usage, especially for large datasets.

Functionality: Certain Pandas functions or methods only work with specific data types (e.g., datetime methods for datetime objects).

How to Implement:



The astype() method is the primary way to convert data types. You can convert a single column or multiple columns.



import pandas as pd

import numpy as np



\# Sample DataFrame with mixed/incorrect data types

data\_types = {

&#x20;   'ProductID': \['101', '102', '103', '104'],

&#x20;   'Quantity': \['5', '10', '7', '12'],

&#x20;   'Price': \[25.50, 10.00, 30.75, 15.20],

&#x20;   'OrderDate': \['2023-03-10', '2023-03-11', '2023-03-10', '2023-03-12'],

&#x20;   'IsShipped': \['True', 'False', 'True', 'True']

}

df\_types = pd.DataFrame(data\_types)



print('Original DataFrame with potentially incorrect types:')

print(df\_types)

print('

Original Data Types:')

print(df\_types.dtypes)



\# Convert 'ProductID' from string to integer

df\_types\['ProductID'] = df\_types\['ProductID'].astype(int)



\# Convert 'Quantity' from string to integer

df\_types\['Quantity'] = df\_types\['Quantity'].astype(int)



\# Convert 'OrderDate' from string to datetime objects

df\_types\['OrderDate'] = pd.to\_datetime(df\_types\['OrderDate'])



\# Convert 'IsShipped' from string to boolean

df\_types\['IsShipped'] = df\_types\['IsShipped'].astype(bool)



print('

DataFrame after type conversions:')

print(df\_types)

print('

Data Types after conversion:')

print(df\_types.dtypes)



\# Converting multiple columns at once using a dictionary

df\_types\_multi = pd.DataFrame(data\_types)

conversion\_dict = {

&#x20;   'ProductID': null,

&#x20;   'Quantity': null,

&#x20;   'OrderDate': 'datetime64\[ns]',

&#x20;   'IsShipped': bool

}

df\_types\_multi = df\_types\_multi.astype(conversion\_dict)

print('

DataFrame after multi-column type conversion:')

print(df\_types\_multi)

print('

Data Types after multi-column conversion:')

print(df\_types\_multi.dtypes)

Common Data Types in Pandas:



object: Typically strings, but can also hold mixed types.

int64: 64-bit integers.

float64: 64-bit floating-point numbers.

bool: Boolean (True/False).

datetime64\[ns]: Datetime objects.

category: For categorical data, efficient for columns with a limited number of unique values.

Handling Errors during Conversion:



If a value cannot be converted (e.g., trying to convert 'abc' to an integer), astype() will raise an error. You can use pd.to\_numeric(), pd.to\_datetime(), etc., with the errors parameter:



errors='raise' (default): Raise an exception if conversion fails.

errors='coerce': Replace unconvertible values with NaN.

errors='ignore': Return the original input if conversion fails.

Real-world Scenario: You receive a dataset where a column representing 'Revenue' is stored as strings (e.g., '$1,200.50'). To perform calculations, you first need to remove the '$' and ',' characters and then convert the column to a float type using pd.to\_numeric(df\['Revenue'].str.replace('\[$,]', '', regex=True)).



Manipulating Text Data: Basic String Operations on Columns

Text data is prevalent in datasets, and often it needs to be cleaned, standardized, or extracted. Pandas provides a powerful string manipulation API accessible via the .str accessor on Series (columns) of string type.



Accessing String Methods with the <code>.str</code> Accessor

The .str accessor allows you to apply string processing methods to each element in a Pandas Series. This is incredibly useful for tasks like changing case, splitting strings, removing whitespace, or extracting patterns.



Why manipulate strings? Text data often contains inconsistencies (e.g., 'New York', 'new york', ' NY'). Standardizing this text is crucial for accurate grouping, filtering, and analysis. You might also need to extract specific information, like domain names from email addresses.



How to Implement:



Let's use a DataFrame with some text data that needs cleaning.



import pandas as pd



\# Sample DataFrame with text data

data\_strings = {

&#x20;   'Email': \['  alice@example.com  ', 'bob@DOMAIN.COM', 'charlie@example.com', 'david@EXAMPLE.COM '],

&#x20;   'ProductName': \['  Super Widget  ', 'Mega Gadget', '  Ultra Thingamajig', 'Super Widget']

}

df\_strings = pd.DataFrame(data\_strings)



print('Original DataFrame with messy strings:')

print(df\_strings)



\# 1. Removing leading/trailing whitespace with .str.strip()

df\_strings\['Email'] = df\_strings\['Email'].str.strip()

df\_strings\['ProductName'] = df\_strings\['ProductName'].str.strip()

print('

DataFrame after stripping whitespace:')

print(df\_strings)



\# 2. Converting to lowercase with .str.lower()

df\_strings\['Email'] = df\_strings\['Email'].str.lower()

df\_strings\['ProductName'] = df\_strings\['ProductName'].str.lower()

print('

DataFrame after converting to lowercase:')

print(df\_strings)



\# 3. Splitting strings with .str.split()

\# Let's split the email into username and domain

email\_parts = df\_strings\['Email'].str.split('@', expand=True)

email\_parts.columns = \['Username', 'Domain'] # Rename columns for clarity

df\_strings = pd.concat(\[df\_strings, email\_parts], axis=1) # Add new columns to DataFrame

print('

DataFrame after splitting Email:')

print(df\_strings)



\# 4. Extracting substrings or patterns with .str.extract() (using regex)

\# Extracting the domain again, this time using regex for practice

df\_strings\['ExtractedDomain'] = df\_strings\['Email'].str.extract(r'@(.\*)')

print('

DataFrame after extracting domain using regex:')

print(df\_strings)



\# 5. Replacing substrings with .str.replace()

df\_strings\['ProductName'] = df\_strings\['ProductName'].str.replace('super', 'premium', regex=False) # Case-sensitive replacement

print('

DataFrame after replacing "super" with "premium":')

print(df\_strings)

Commonly Used .str Methods:



.str.contains(pattern): Checks if a pattern exists in each string.

.str.startswith(prefix) / .str.endswith(suffix): Checks for string prefixes/suffixes.

.str.len(): Returns the length of each string.

.str.slice(start, stop): Extracts a slice of the string.

.str.get(i): Equivalent to slicing, but can be more readable.

.str.findall(pattern): Finds all occurrences of a pattern.

Regular Expressions (Regex): For more complex pattern matching and extraction, understanding regular expressions is highly beneficial. Pandas' string methods often leverage regex capabilities.



Real-world Scenario: You have a dataset of addresses, and you need to extract the city name from each address string. You could use .str.extract() with a carefully crafted regular expression to isolate the city component.



Hands-On Practice: Loading and Cleaning a Sample Dataset



Now, let's put our knowledge into practice by performing a comprehensive data loading and cleaning exercise. We will simulate a common scenario where you receive a dataset with missing values, potential duplicates, and inconsistent formatting.



Step-by-Step Implementation Guide

We will use a hypothetical dataset representing customer orders. First, let's create a dummy CSV file to work with.



import pandas as pd

import numpy as np

import os



\# --- Create a dummy CSV file for practice ---

csv\_data = {

&#x20;   'OrderID': \[1001, 1002, 1003, 1004, 1005, 1001, 1006, 1007, 1008, 1009, 1010, 1003],

&#x20;   'CustomerID': \[1, 2, 3, 4, 5, 1, 6, 7, 8, 9, 10, 3],

&#x20;   'OrderDate': \['2023-01-15', '2023-01-16', '2023-01-17', '2023-01-18', '2023-01-19', '2023-01-15', '2023-01-20', np.nan, '2023-01-22', '2023-01-23', '2023-01-24', '2023-01-17'],

&#x20;   'ProductName': \['Laptop', 'Keyboard', 'Mouse', 'Monitor', 'Webcam', 'Laptop', 'Desk', 'Chair', 'Printer', 'Scanner', 'External HDD', 'Mouse'],

&#x20;   'Quantity': \[1, 2, 3, 1, 1, 1, 1, 1, 1, 1, 1, 3],

&#x20;   'Price': \[1200.50, 75.00, 25.00, 300.00, 50.00, 1200.50, 150.00, 250.00, np.nan, 180.00, 90.00, 25.00],

&#x20;   'Status': \['Shipped', 'Processing', 'Shipped', 'Processing', 'Shipped', 'Shipped', 'Processing', 'Shipped', 'Processing', 'Shipped', 'Processing', 'Shipped']

}

df\_practice = pd.DataFrame(csv\_data)

df\_practice.to\_csv('customer\_orders.csv', index=False)

print('Dummy CSV file "customer\_orders.csv" created.')

\# --- End of CSV creation ---



\# 1. Load the dataset from the CSV file

print('

\--- Step 1: Loading Data ---')

df = pd.read\_csv('customer\_orders.csv')

print('Dataset loaded successfully.')

print('Original DataFrame shape:', df.shape)

print('First 5 rows of the loaded data:')

print(df.head())

print('

Data types before cleaning:')

print(df.dtypes)



\# 2. Handle Missing Values

print('

\--- Step 2: Handling Missing Values ---')

print('Missing values before imputation:')

print(df.isnull().sum())



\# Impute missing 'OrderDate' with the mode (most frequent date)

\# Note: For dates, imputing with mode might not always be ideal, but for demonstration purposes...

mode\_order\_date = df\['OrderDate'].mode()\[0]

df\['OrderDate'].fillna(mode\_order\_date, inplace=True)

print(f'

Filled missing OrderDate with mode: {mode\_order\_date}')



\# Impute missing 'Price' with the median price

median\_price = df\['Price'].median()

df\['Price'].fillna(median\_price, inplace=True)

print(f'Filled missing Price with median: {median\_price:.2f}')



print('

Missing values after imputation:')

print(df.isnull().sum())



\# 3. Identify and Remove Duplicate Rows

print('

\--- Step 3: Identifying and Removing Duplicate Rows ---')

print('Number of duplicate rows before removal:', df.duplicated().sum())



\# Remove duplicate rows, keeping the first occurrence

df.drop\_duplicates(inplace=True)

print('Number of duplicate rows after removal:', df.duplicated().sum())

print('DataFrame shape after removing duplicates:', df.shape)



\# 4. Renaming Columns and Resetting Indices

print('

\--- Step 4: Renaming Columns and Resetting Indices ---')

\# Rename columns for better readability

new\_names = {

&#x20;   'OrderID': 'Order\_ID',

&#x20;   'CustomerID': 'Customer\_ID',

&#x20;   'OrderDate': 'Order\_Date',

&#x20;   'ProductName': 'Product\_Name',

&#x20;   'Quantity': 'Quantity\_Ordered',

&#x20;   'Price': 'Unit\_Price',

&#x20;   'Status': 'Order\_Status'

}

df.rename(columns=new\_names, inplace=True)

print('Columns renamed.')



\# Reset the index after dropping duplicates

df.reset\_index(drop=True, inplace=True)

print('Index reset.')



\# 5. Data Type Conversion

print('

\--- Step 5: Data Type Conversion ---')

print('Data types before conversion:')

print(df.dtypes)



\# Convert Order\_Date to datetime objects

df\['Order\_Date'] = pd.to\_datetime(df\['Order\_Date'])



\# Convert relevant IDs to string type (often good practice for IDs)

df\['Order\_ID'] = df\['Order\_ID'].astype(str)

df\['Customer\_ID'] = df\['Customer\_ID'].astype(str)



\# Ensure Quantity\_Ordered is integer

df\['Quantity\_Ordered'] = df\['Quantity\_Ordered'].astype(int)



print('

Data types after conversion:')

print(df.dtypes)



\# 6. Basic String Manipulation on Columns

print('

\--- Step 6: Basic String Manipulation ---')

\# Standardize 'Order\_Status' to lowercase and strip whitespace

df\['Order\_Status'] = df\['Order\_Status'].str.lower().str.strip()

print('Order\_Status standardized to lowercase and stripped.')



\# Example: Extracting the first 3 characters of ProductName (if needed)

\# df\['Product\_Prefix'] = df\['Product\_Name'].str.slice(0, 3)



print('

\--- Cleaning Complete ---')

print('Final cleaned DataFrame head:')

print(df.head())

print('

Final DataFrame info:')

df.info()



\# Clean up the dummy CSV file

os.remove('customer\_orders.csv')

print('

Dummy CSV file "customer\_orders.csv" removed.')

Explanation of Steps:



Loading Data: We use pd.read\_csv() to load our prepared data into a DataFrame. We then inspect its initial state using .head() and .dtypes.

Handling Missing Values: We identify missing values using .isnull().sum(). We then impute the missing OrderDate with its mode and the missing Price with its median.

Removing Duplicates: We check for duplicate rows using .duplicated().sum() and then remove them using .drop\_duplicates(inplace=True).

Renaming and Resetting: We use .rename() with a dictionary to give columns more descriptive names and .reset\_index(drop=True, inplace=True) to ensure a clean, sequential index.

Data Type Conversion: We convert OrderDate to datetime objects and ensure Quantity\_Ordered is an integer. IDs are converted to strings for robustness.

String Manipulation: We standardize the Order\_Status column by converting it to lowercase and stripping whitespace using .str.lower().str.strip().

This hands-on exercise demonstrates the practical application of the concepts covered in this lesson, resulting in a clean, well-structured DataFrame ready for further analysis.



Summary, Best Practices, and Preparation for Next Steps

Congratulations on completing the Data Loading and Cleaning lesson! You've acquired essential skills that form the bedrock of any successful data science project. Let's recap the key takeaways and prepare for our next module.



Key Takeaways and Best Practices

Preparation for Next Lesson: Data Transformation and Aggregation

Key Takeaways:



Data Ingestion: Pandas provides versatile functions like pd.read\_csv(), pd.read\_excel(), and pd.read\_sql\_query() to load data from various sources.

Handling Missing Values: Understanding and addressing missing data is crucial. We learned to identify them with isnull() and notnull(), and handle them using dropna() (removal) and fillna() (imputation with strategies like mean, median, mode, ffill, bfill).

Data Integrity: Ensuring data uniqueness is vital. duplicated() helps identify duplicate rows, and drop\_duplicates() removes them.

Data Structuring: Clear column names and a clean index improve readability and usability. rename() and reset\_index() are key tools for this.

Data Type Consistency: Correct data types are essential for accurate analysis. astype(), pd.to\_numeric(), and pd.to\_datetime() are used for type conversion.

String Manipulation: The .str accessor provides powerful methods (.strip(), .lower(), .split(), .replace(), .extract()) for cleaning and transforming text data.

Best Practices:



Understand Your Data: Before cleaning, explore your data thoroughly. Understand the meaning of each column and the potential sources of errors.

Document Your Cleaning Steps: Keep a record of all cleaning operations performed. This ensures reproducibility and helps others understand your process.

Prioritize Imputation over Deletion: Whenever possible, impute missing values rather than deleting rows or columns, as deletion can lead to significant data loss. Choose imputation methods appropriate for your data.

Standardize Naming Conventions: Adopt consistent naming for columns (e.g., snake\_case) and stick to it throughout your project.

Validate Data Types: Always check data types after loading and after cleaning to ensure they are appropriate for subsequent analysis.

Use `inplace=True` with Caution: While convenient, using inplace=True modifies the DataFrame directly. It's often safer to create new DataFrames or use explicit assignments (e.g., df = df.dropna()) for better control and debugging.

Iterative Process: Data cleaning is often an iterative process. You might discover new issues as you proceed with analysis, requiring further cleaning steps.

Pro Tip: Create a dedicated script or notebook for your data cleaning process. This makes it easy to re-run the cleaning steps on updated data or for different projects.



**Part-3:**



Data Transformation and Aggregation

Lesson visual

Introduction: Mastering Data Manipulation with Pandas

Welcome to this crucial lesson on Data Transformation and Aggregation, a cornerstone of effective data science and machine learning workflows. In this session, we will dive deep into the powerful capabilities of the Pandas library in Python, equipping you with the skills to reshape, refine, and summarize your data. As B-Tech students embarking on your AI/ML journey, understanding how to manipulate data is as fundamental as understanding algorithms themselves. This lesson directly supports the module's learning objectives: 'Understand Pandas DataFrames and Series,' 'Load, clean, and transform structured data,' 'Perform data selection, filtering, and aggregation,' and 'Handle missing data and duplicate entries.'



The ability to transform and aggregate data is not merely an academic exercise; it is the engine that drives insightful analysis and robust model building in the real world. Whether you are preparing data for a predictive model, generating reports for business stakeholders, or exploring complex datasets to uncover hidden patterns, the techniques we will cover today are indispensable. Imagine a scenario where you need to analyze sales performance across different regions, identify the top-performing products, or calculate the average customer spending. These tasks, and countless others, rely heavily on efficient data transformation and aggregation.



Throughout this lesson, we will focus on practical application, using Python, Pandas, and Jupyter Notebooks to demonstrate these concepts. We will move from basic filtering and sorting to more advanced grouping, merging, and function application. By the end of this session, you will be proficient in manipulating your data to extract meaningful information and prepare it for further analysis or machine learning tasks. Let's begin by understanding how to selectively extract information from your datasets.



Precise Data Selection: Filtering Records Based on Conditions

Data rarely comes in a perfectly pre-processed state. Often, you need to isolate specific subsets of your data that meet certain criteria. This process, known as filtering, is fundamental to exploratory data analysis and data preparation. Pandas provides intuitive and efficient ways to filter DataFrames based on various conditions, allowing you to focus on the most relevant information.



What is Data Filtering?

Data filtering involves selecting rows from a DataFrame that satisfy one or more specified conditions. These conditions can be based on the values in one or more columns. For instance, you might want to select all customers from a specific city, all transactions above a certain amount, or all products belonging to a particular category.



Why is Filtering Important?

Focus on Relevant Data: It allows you to narrow down large datasets to the specific observations that are of interest for your analysis.

Data Cleaning and Validation: Filtering can help identify and isolate erroneous or outlier data points that do not meet expected criteria.

Feature Engineering: Creating new features often involves filtering data to create subsets for specific calculations or transformations.

Reporting and Visualization: Generating reports or visualizations often requires presenting specific segments of data.

How to Implement Data Filtering in Pandas

Pandas offers several powerful methods for filtering, primarily through boolean indexing. This involves creating a boolean Series (a Series of True/False values) that indicates which rows to keep.



Let's assume we have a DataFrame named df. The general syntax for filtering is:



filtered\_df = df\[condition]

Where condition is a boolean expression that evaluates to True for rows you want to keep and False for rows you want to discard.



1\. Filtering with a Single Condition

You can filter based on the value of a single column. For example, to select rows where the 'Age' column is greater than 30:



\# Assuming df is your DataFrame and it has an 'Age' column

older\_than\_30 = df\[df\['Age'] > 30]

Similarly, for string comparisons:



\# Assuming df has a 'City' column

from\_london = df\[df\['City'] == 'London']

2\. Filtering with Multiple Conditions

You can combine multiple conditions using logical operators:



AND: Use the ampersand (\&). Both conditions must be True.

OR: Use the pipe symbol (|). At least one condition must be True.

NOT: Use the tilde symbol (\~). Negates the condition.

Important Note: When combining conditions, each individual condition must be enclosed in parentheses due to Python's operator precedence rules.



Example: Select customers from 'New York' who are older than 25:



ny\_and\_older\_25 = df\[(df\['City'] == 'New York') \& (df\['Age'] > 25)]

Example: Select customers who are either from 'Paris' OR have an 'Age' less than 20:



paris\_or\_young = df\[(df\['City'] == 'Paris') | (df\['Age'] < 20)]

Example: Select customers NOT from 'Tokyo':



not\_tokyo = df\[\~(df\['City'] == 'Tokyo')]

3\. Using the .isin() Method

For checking if a column's value is present in a list of values, .isin() is very efficient:



\# Select customers from 'London', 'Paris', or 'Berlin'

selected\_cities = \['London', 'Paris', 'Berlin']

customers\_in\_cities = df\[df\['City'].isin(selected\_cities)]

4\. Using the .str Accessor for String Operations

Pandas provides a .str accessor for Series containing strings, enabling powerful string manipulation and filtering:



Example: Select customers whose names start with 'A':



starts\_with\_a = df\[df\['Name'].str.startswith('A')]

Example: Select customers whose email addresses contain 'example.com':



example\_emails = df\[df\['Email'].str.contains('example.com')]

Real-World Scenario: Analyzing E-commerce Orders

Imagine an e-commerce dataset with columns like OrderID, CustomerID, Product, Category, Price, Quantity, and OrderDate. You might need to:



Find all orders for a specific product, say 'Laptop'.

Identify orders placed within a particular date range.

Filter for orders where the total value (Price \* Quantity) exceeds $1000.

Select all orders from a specific customer.

Each of these tasks is accomplished using the filtering techniques discussed above.



Let's set up a sample DataFrame to practice this.



Hands-On: Filtering Customer Data by Location and Purchase Amount

Now, let's put filtering into practice. We'll create a sample DataFrame representing customer data and then apply various filtering conditions.



Step 1: Setting up the Environment and Sample Data

First, ensure you have Pandas installed. Open your Jupyter Notebook or JupyterLab and import the Pandas library. We'll create a DataFrame with customer information, including their city and the amount they spent on their last purchase.



import pandas as pd

import numpy as np



\# Create a sample DataFrame

data = {

&#x20;   'CustomerID': \[101, 102, 103, 104, 105, 106, 107, 108, 109, 110, 111, 112],

&#x20;   'City': \['New York', 'Los Angeles', 'Chicago', 'New York', 'Los Angeles', 'Chicago', 'New York', 'Los Angeles', 'Chicago', 'New York', 'Los Angeles', 'Chicago'],

&#x20;   'PurchaseAmount': \[150.50, 220.75, 95.00, 310.20, 180.00, 450.50, 75.90, 290.00, 120.00, 550.00, 210.00, 300.00],

&#x20;   'Category': \['Electronics', 'Clothing', 'Home Goods', 'Electronics', 'Clothing', 'Home Goods', 'Electronics', 'Clothing', 'Home Goods', 'Electronics', 'Clothing', 'Home Goods']

}

df\_customers = pd.DataFrame(data)



print("Original DataFrame:")

print(df\_customers)

Step 2: Filtering for Customers in 'New York'

Let's find all customers located in 'New York'.



\# Filter for customers in 'New York'

ny\_customers = df\_customers\[df\_customers\['City'] == 'New York']



print("

Customers in New York:")

print(ny\_customers)

Step 3: Filtering for Purchases Above a Certain Amount

Now, let's identify customers whose purchase amount was greater than $200.



\# Filter for purchases greater than $200

high\_value\_purchases = df\_customers\[df\_customers\['PurchaseAmount'] > 200]



print("

Purchases greater than $200:")

print(high\_value\_purchases)

Step 4: Combining Filters - Customers in 'Los Angeles' with Purchases > $200

Let's combine two conditions: customers in 'Los Angeles' AND whose purchase amount is greater than $200.



\# Filter for customers in 'Los Angeles' AND purchase amount > $200

la\_high\_value = df\_customers\[(df\_customers\['City'] == 'Los Angeles') \& (df\_customers\['PurchaseAmount'] > 200)]



print("

Customers in Los Angeles with purchases > $200:")

print(la\_high\_value)

Step 5: Using .isin() to Filter by Multiple Cities

Let's find customers who are either in 'Chicago' or 'Los Angeles'.



\# Filter for customers in 'Chicago' OR 'Los Angeles'

chicago\_or\_la = df\_customers\[df\_customers\['City'].isin(\['Chicago', 'Los Angeles'])]



print("

Customers in Chicago or Los Angeles:")

print(chicago\_or\_la)

This hands-on exercise demonstrates the flexibility and power of Pandas for selecting specific subsets of data based on defined criteria. These filtered datasets can then be used for further analysis, visualization, or as input for subsequent transformation steps.



Organizing Your Data: Sorting DataFrames for Better Insights

Once you have filtered your data, the next logical step is often to organize it in a meaningful way. Sorting DataFrames is a fundamental operation that arranges rows based on the values in one or more columns. This can reveal trends, identify extremes, and make data easier to interpret.



What is Sorting?

Sorting involves arranging the rows of a DataFrame in ascending or descending order based on the values in specified columns. You can sort by a single column or by multiple columns, defining a hierarchy for the sorting order.



Why is Sorting Important?

Identifying Extremes: Easily find the highest or lowest values in a dataset (e.g., top-selling products, lowest temperatures).

Trend Analysis: Sorting by date or time is crucial for understanding temporal patterns.

Data Presentation: Presenting data in a sorted order often makes it more readable and understandable for reports and visualizations.

Preparation for Other Operations: Some algorithms or data processing steps may require data to be sorted beforehand.

How to Implement Sorting in Pandas

Pandas DataFrames have a built-in method called .sort\_values() for this purpose.



The basic syntax is:



sorted\_df = df.sort\_values(by='column\_name')

1\. Sorting by a Single Column (Ascending Order)

By default, .sort\_values() sorts in ascending order.



\# Sort the customer DataFrame by PurchaseAmount in ascending order

sorted\_by\_amount\_asc = df\_customers.sort\_values(by='PurchaseAmount')



print("

Customers sorted by PurchaseAmount (Ascending):")

print(sorted\_by\_amount\_asc)

2\. Sorting by a Single Column (Descending Order)

To sort in descending order, use the ascending=False parameter.



\# Sort the customer DataFrame by PurchaseAmount in descending order

sorted\_by\_amount\_desc = df\_customers.sort\_values(by='PurchaseAmount', ascending=False)



print("

Customers sorted by PurchaseAmount (Descending):")

print(sorted\_by\_amount\_desc)

3\. Sorting by Multiple Columns

You can sort by multiple columns by passing a list of column names to the by parameter. The sorting will be applied sequentially based on the order of columns in the list.



Example: Sort first by 'City' (ascending) and then by 'PurchaseAmount' (descending) within each city.



\# Sort by City (ascending) then PurchaseAmount (descending)

sorted\_multi = df\_customers.sort\_values(by=\['City', 'PurchaseAmount'], ascending=\[True, False])



print("

Customers sorted by City (Asc) then PurchaseAmount (Desc):")

print(sorted\_multi)

In this example, all 'Chicago' customers will appear first, sorted by their purchase amount from highest to lowest. Then, 'Los Angeles' customers will appear, also sorted by purchase amount descending, and so on.



4\. Handling Missing Values during Sorting

By default, NaN (Not a Number) values are placed at the end when sorting in ascending order and at the beginning when sorting in descending order. You can control this behavior using the na\_position parameter ('first' or 'last').



\# Example with NaN values (let's add one for demonstration)

df\_with\_nan = df\_customers.copy()

df\_with\_nan.loc\[2, 'PurchaseAmount'] = np.nan # Add a NaN value



\# Sort with NaN at the beginning

sorted\_nan\_first = df\_with\_nan.sort\_values(by='PurchaseAmount', na\_position='first')

print("

DataFrame sorted with NaN first:")

print(sorted\_nan\_first)



\# Sort with NaN at the end (default behavior)

sorted\_nan\_last = df\_with\_nan.sort\_values(by='PurchaseAmount', na\_position='last')

print("

DataFrame sorted with NaN last:")

print(sorted\_nan\_last)

Real-World Scenario: Analyzing Stock Prices

Consider a DataFrame of stock prices with columns like Date, StockSymbol, Open, High, Low, and Close. To analyze performance:



You might sort by Date to see the price movement over time.

You could sort by Close price (descending) to find the highest closing prices on a given day.

Sorting by StockSymbol and then Date would allow you to view the history of each stock individually.

Sorting is a simple yet powerful tool for making your data more interpretable and for preparing it for more complex analytical tasks.



Unlocking Insights: Grouping Data with groupby()

One of the most powerful operations in data analysis is the ability to group data based on certain categories and then perform calculations on those groups. This is precisely what Pandas' groupby() method enables. It's the foundation for many aggregation tasks and is essential for understanding how different segments of your data behave.



What is Grouping Data?

Grouping, often referred to as the "split-apply-combine" strategy, involves:



Splitting: Dividing the DataFrame into smaller groups based on the unique values in one or more columns (the 'keys').

Applying: Performing a function (like aggregation, transformation, or filtering) independently on each of these smaller groups.

Combining: Merging the results of these operations back into a new DataFrame or Series.

Why is Grouping Important?

Summarizing Categorical Data: Calculate statistics (like sum, mean, count) for each category within your dataset. For example, average sales per region, total revenue per product category.

Comparative Analysis: Understand how different groups compare against each other.

Identifying Patterns within Subsets: Discover trends or anomalies that are specific to certain groups.

Data Transformation: Apply transformations that are specific to the context of each group (e.g., normalizing data within each category).

How to Implement Grouping with groupby()

The groupby() method is called on a DataFrame, and it takes the column(s) to group by as an argument. It returns a GroupBy object, which is not yet a DataFrame but an intermediate object that holds the grouped information.



The general workflow is:



grouped\_data = df.groupby('column\_to\_group\_by')

Once you have the GroupBy object, you can then apply aggregation functions to it.



1\. Grouping by a Single Column

Let's use our df\_customers DataFrame. We can group by the 'City' column to see how customers are distributed across different cities.



\# Group by 'City'

grouped\_by\_city = df\_customers.groupby('City')



\# The grouped\_by\_city object now holds the groups.

\# We can inspect the groups (though this is usually done with aggregation)

\# print(grouped\_by\_city.groups) # This shows the indices for each group



\# To see the actual data for each group, you can iterate:

\# for name, group in grouped\_by\_city:

\#     print(f"

Group: {name}")

\#     print(group)

2\. Grouping by Multiple Columns

You can group by more than one column by passing a list of column names.



Example: Group by both 'City' and 'Category' to see the distribution of customers across cities and product categories.



grouped\_by\_city\_category = df\_customers.groupby(\['City', 'Category'])



\# print(grouped\_by\_city\_category.groups) # Inspecting groups

3\. Accessing Groups

You can access individual groups using the .get\_group() method:



\# Get the group for 'New York'

ny\_group = grouped\_by\_city.get\_group('New York')

print("

Data for 'New York' group:")

print(ny\_group)

Real-World Scenario: Analyzing Website Traffic

Imagine a DataFrame containing website traffic data with columns like Date, Source (e.g., 'Google', 'Facebook', 'Direct'), PageVisited, and TimeOnPage. To understand traffic patterns:



You could group by Source to analyze the average time spent on the site from each traffic source.

Grouping by Date and Source could reveal daily traffic trends from different channels.

Grouping by PageVisited could show which pages are most popular and how long users stay on them.

The groupby() method is the gateway to performing these kinds of segmented analyses. In the next section, we will explore how to apply aggregation functions to these groups.



Data Transformation and Aggregation

Lesson visual

Quantifying Insights: Applying Aggregation Functions to Groups

Once data is grouped using groupby(), the real power emerges when we apply aggregation functions. Aggregation condenses the data within each group into a single summary value. Pandas provides a rich set of built-in aggregation functions that can be applied directly to a GroupBy object.



What are Aggregation Functions?

Aggregation functions are operations that take a collection of values (typically from a group) and return a single scalar value. Common aggregation functions include:



sum(): Calculates the sum of values.

mean(): Calculates the average of values.

count(): Counts the number of non-null values.

size(): Counts the total number of rows (including nulls).

min(): Finds the minimum value.

max(): Finds the maximum value.

std(): Calculates the standard deviation.

var(): Calculates the variance.

median(): Calculates the median.

first(): Returns the first value in the group.

last(): Returns the last value in the group.

Why are Aggregation Functions Important?

Data Summarization: They reduce large datasets into concise summaries, making them easier to understand and report on.

Performance Metrics: Calculate key performance indicators (KPIs) for different segments (e.g., average revenue per customer, total sales per product).

Feature Engineering: Create aggregated features for machine learning models (e.g., average purchase amount per customer).

Identifying Key Trends: Spotting patterns by comparing aggregated metrics across groups.

How to Apply Aggregation Functions

After creating a GroupBy object, you can chain aggregation methods directly onto it. You can apply these functions to specific columns or to all applicable columns.



1\. Applying a Single Aggregation Function to a Specific Column

Let's continue with our df\_customers DataFrame, grouped by 'City'. We want to calculate the average PurchaseAmount for each city.



\# Group by 'City' and calculate the mean of 'PurchaseAmount'

average\_purchase\_by\_city = df\_customers.groupby('City')\['PurchaseAmount'].mean()



print("

Average Purchase Amount by City:")

print(average\_purchase\_by\_city)

Notice that the result is a Pandas Series, where the index is the grouping key ('City') and the values are the calculated means.



2\. Applying Multiple Aggregation Functions to a Specific Column

You can apply multiple aggregation functions to a single column using the .agg() method. This is highly efficient.



Example: For each city, calculate the total purchase amount (sum) and the number of customers (count).



\# Group by 'City' and apply multiple aggregations to 'PurchaseAmount'

city\_summary = df\_customers.groupby('City')\['PurchaseAmount'].agg(\['sum', 'mean', 'count', 'min', 'max'])



print("

Summary Statistics for Purchase Amount by City:")

print(city\_summary)

3\. Applying Different Aggregations to Different Columns

The .agg() method is even more powerful when you want to apply different aggregations to different columns simultaneously. You pass a dictionary where keys are the column names and values are the aggregation functions (or lists of functions) to apply.



Example: For each city, calculate the sum of PurchaseAmount and the count of CustomerID.



\# Group by 'City' and apply different aggregations to different columns

multi\_column\_agg = df\_customers.groupby('City').agg(

&#x20;   TotalPurchaseAmount=('PurchaseAmount', 'sum'),

&#x20;   NumberOfCustomers=('CustomerID', 'count'),

&#x20;   AveragePurchase=('PurchaseAmount', 'mean')

)



print("

Multi-column Aggregation by City:")

print(multi\_column\_agg)

In this example, we've also used named aggregation (e.g., TotalPurchaseAmount=('PurchaseAmount', 'sum')) to give more descriptive names to the resulting columns.



4\. Applying Aggregations After Grouping by Multiple Columns

You can extend these aggregation techniques to DataFrames grouped by multiple columns.



Example: Group by both 'City' and 'Category' and calculate the total purchase amount for each combination.



\# Group by 'City' and 'Category', then sum 'PurchaseAmount'

city\_category\_sales = df\_customers.groupby(\['City', 'Category'])\['PurchaseAmount'].sum()



print("

Total Purchase Amount by City and Category:")

print(city\_category\_sales)

The result here is a Series with a MultiIndex (City and Category). You can convert this back to a DataFrame using .reset\_index() if needed.



Real-World Scenario: Analyzing Sales Performance

Consider a sales dataset with columns like Region, Product, SalesAmount, and Quantity. Using grouping and aggregation:



Calculate the total sales for each Region.

Find the average Quantity sold per Product.

Determine the maximum SalesAmount for each Region and Product combination.

Count the number of sales transactions in each Region.

These aggregated results provide high-level insights into business performance, enabling informed decision-making.



Hands-On: Calculating Average Purchase Amount per Category within Each City

Let's combine grouping and aggregation to answer a specific business question: What is the average purchase amount for each product category within each city?



Step 1: Ensure DataFrame is Ready

We'll use the same df\_customers DataFrame created earlier. If you've closed your notebook, recreate it.



import pandas as pd

import numpy as np



data = {

&#x20;   'CustomerID': \[101, 102, 103, 104, 105, 106, 107, 108, 109, 110, 111, 112],

&#x20;   'City': \['New York', 'Los Angeles', 'Chicago', 'New York', 'Los Angeles', 'Chicago', 'New York', 'Los Angeles', 'Chicago', 'New York', 'Los Angeles', 'Chicago'],

&#x20;   'PurchaseAmount': \[150.50, 220.75, 95.00, 310.20, 180.00, 450.50, 75.90, 290.00, 120.00, 550.00, 210.00, 300.00],

&#x20;   'Category': \['Electronics', 'Clothing', 'Home Goods', 'Electronics', 'Clothing', 'Home Goods', 'Electronics', 'Clothing', 'Home Goods', 'Electronics', 'Clothing', 'Home Goods']

}

df\_customers = pd.DataFrame(data)



print("Original DataFrame:")

print(df\_customers)

Step 2: Group by City and Category

We need to group by both 'City' and 'Category' to get the desired breakdown.



\# Group by 'City' and 'Category'

grouped\_data = df\_customers.groupby(\['City', 'Category'])

Step 3: Apply the Mean Aggregation to PurchaseAmount

Now, we'll select the 'PurchaseAmount' column from the grouped object and apply the mean() aggregation function.



\# Calculate the average PurchaseAmount for each City-Category combination

average\_purchase\_per\_category\_in\_city = grouped\_data\['PurchaseAmount'].mean()



print("

Average Purchase Amount per Category within each City:")

print(average\_purchase\_per\_category\_in\_city)

Step 4: Resetting the Index for a Flat DataFrame (Optional but Recommended)

The output is a Series with a MultiIndex. Often, it's more convenient to have this as a regular DataFrame with columns for 'City', 'Category', and 'AveragePurchaseAmount'. We can achieve this using .reset\_index().



\# Reset the index to convert the Series back into a DataFrame

average\_purchase\_df = average\_purchase\_per\_category\_in\_city.reset\_index()



\# Rename the aggregated column for clarity

average\_purchase\_df = average\_purchase\_df.rename(columns={'PurchaseAmount': 'AveragePurchaseAmount'})



print("

Average Purchase Amount per Category within each City (as DataFrame):")

print(average\_purchase\_df)

This hands-on exercise demonstrates how to effectively use groupby() in conjunction with aggregation functions to derive meaningful insights from your data. You've successfully calculated a key metric (average purchase amount) broken down by two important dimensions (city and category).



Combining Datasets: Merging and Joining DataFrames

In real-world data science, you rarely work with a single, monolithic dataset. More often, your data is spread across multiple tables or files, each containing different pieces of information. Merging and joining are techniques used to combine these disparate datasets into a single, unified DataFrame, allowing for more comprehensive analysis.



What are Merging and Joining?

Merging and joining are operations that combine two or more DataFrames based on one or more common columns (keys). While often used interchangeably, they stem from SQL's join operations and have slightly different nuances:



Merge: A more general term in Pandas, often used for combining DataFrames based on common columns or indices. It's highly flexible and can perform various types of joins.

Join: Typically refers to combining DataFrames based on their indices, although it can also be used with columns.

Concatenate: Stacks DataFrames together either vertically (along rows) or horizontally (along columns). This is different from merging/joining as it does not rely on common keys for alignment.

Why are Merging and Joining Important?

Data Integration: Combine related information from different sources (e.g., customer demographics from one table and their order history from another).

Enriching Data: Add new attributes or context to an existing dataset.

Creating Comprehensive Views: Build a single view of data that spans multiple entities.

Relational Data Analysis: Essential for working with data that has inherent relationships between different entities.

How to Implement Merging and Joining in Pandas

Pandas provides several functions for these operations:



pd.merge(): The most versatile function for combining DataFrames based on columns.

DataFrame.join(): Primarily used for combining based on indices, but can also join on columns.

pd.concat(): Used for stacking DataFrames.

1\. Using pd.merge()

pd.merge() is the workhorse for combining DataFrames based on common columns. It mimics SQL's JOIN operations.



The basic syntax is:



merged\_df = pd.merge(left\_df, right\_df, on='key\_column', how='join\_type')

Key parameters:



left\_df, right\_df: The DataFrames to merge.

on: The column name(s) to join on. If column names are different in the two DataFrames, use left\_on and right\_on.

how: Specifies the type of join. Common options are:

'inner' (default): Returns only rows where the key exists in \*both\* DataFrames.

'left': Returns all rows from the left DataFrame and matching rows from the right. If no match, NaN is used for right DataFrame columns.

'right': Returns all rows from the right DataFrame and matching rows from the left. If no match, NaN is used for left DataFrame columns.

'outer': Returns all rows from \*both\* DataFrames. If no match, NaN is used.

Example: Merging Customer Demographics with Order Details

Let's create two sample DataFrames:



\# DataFrame 1: Customer Demographics

data\_customers = {

&#x20;   'CustomerID': \[101, 102, 103, 104, 105],

&#x20;   'Name': \['Alice', 'Bob', 'Charlie', 'David', 'Eve'],

&#x20;   'City': \['New York', 'Los Angeles', 'Chicago', 'New York', 'Los Angeles']

}

df\_demographics = pd.DataFrame(data\_customers)



\# DataFrame 2: Order Information

data\_orders = {

&#x20;   'OrderID': \[1, 2, 3, 4, 5, 6],

&#x20;   'CustomerID': \[101, 102, 101, 103, 104, 106], # Customer 106 is not in demographics

&#x20;   'Product': \['Laptop', 'Keyboard', 'Mouse', 'Monitor', 'Webcam', 'Desk'],

&#x20;   'Amount': \[1200, 75, 25, 300, 50, 150]

}

df\_orders = pd.DataFrame(data\_orders)



print("

Customer Demographics DataFrame:")

print(df\_demographics)

print("

Order Information DataFrame:")

print(df\_orders)

Inner Join: Combine customers and their orders. Only customers who have placed orders AND exist in the demographics table will be included.



inner\_merged = pd.merge(df\_demographics, df\_orders, on='CustomerID', how='inner')

print("

Inner Merge (Customers with Orders):")

print(inner\_merged)

Left Join: Keep all customers from the demographics table and add their order information. If a customer has no orders, their order details will be NaN.



left\_merged = pd.merge(df\_demographics, df\_orders, on='CustomerID', how='left')

print("

Left Merge (All Customers, their Orders if any):")

print(left\_merged)

Right Join: Keep all orders from the orders table and add customer demographics. If an order belongs to a customer not in the demographics table, their demographic details will be NaN.



right\_merged = pd.merge(df\_demographics, df\_orders, on='CustomerID', how='right')

print("

Right Merge (All Orders, their Customer Info if any):")

print(right\_merged)

Outer Join: Keep all records from both tables. If a customer has no orders, or an order belongs to a customer not in demographics, NaN values will fill the missing parts.



outer\_merged = pd.merge(df\_demographics, df\_orders, on='CustomerID', how='outer')

print("

Outer Merge (All Records from Both):")

print(outer\_merged)

2\. Using DataFrame.join()

.join() is convenient when you want to join based on the index of one DataFrame and a column of another, or when joining two DataFrames on their indices.



\# Example: Join df\_orders (indexed by OrderID) with df\_demographics (on CustomerID)

\# This requires setting an index first. Let's re-index df\_orders by CustomerID for demonstration.

df\_orders\_indexed = df\_orders.set\_index('CustomerID')

print("

Order DataFrame indexed by CustomerID:")

print(df\_orders\_indexed)



\# Join df\_demographics (on CustomerID column) with df\_orders\_indexed (on its index)

\# Note: .join() defaults to a left join

joined\_df = df\_demographics.join(df\_orders\_indexed, on='CustomerID', how='left')

print("

DataFrame joined using .join():")

print(joined\_df)

3\. Using pd.concat()

pd.concat() is used to append DataFrames either row-wise (axis=0, default) or column-wise (axis=1). It does not align based on keys like merge/join.



Example: Concatenating two DataFrames vertically.



\# Create another small DataFrame

data\_more\_customers = {

&#x20;   'CustomerID': \[106, 107],

&#x20;   'Name': \['Frank', 'Grace'],

&#x20;   'City': \['Boston', 'Seattle']

}

df\_more\_customers = pd.DataFrame(data\_more\_customers)



\# Concatenate df\_demographics and df\_more\_customers vertically

concatenated\_df = pd.concat(\[df\_demographics, df\_more\_customers], ignore\_index=True)

print("

Concatenated DataFrame (Vertical):")

print(concatenated\_df)

Example: Concatenating two DataFrames horizontally (requires matching indices or careful alignment).



\# Create two DataFrames with the same index

df\_part1 = pd.DataFrame({'A': \['A0', 'A1'], 'B': \['B0', 'B1']}, index=\[0, 1])

df\_part2 = pd.DataFrame({'C': \['C0', 'C1'], 'D': \['D0', 'D1']}, index=\[0, 1])



\# Concatenate horizontally

concatenated\_horizontal = pd.concat(\[df\_part1, df\_part2], axis=1)

print("

Concatenated DataFrame (Horizontal):")

print(concatenated\_horizontal)

Real-World Scenario: Customer 360 View

Imagine you have three datasets:



customers.csv: Contains customer ID, name, address, signup date.

orders.csv: Contains order ID, customer ID, order date, total amount.

support\_tickets.csv: Contains ticket ID, customer ID, issue date, resolution status.

To create a comprehensive 'Customer 360' view, you would:



Merge customers.csv with orders.csv on CustomerID (likely a left join from customers to orders).

Merge the result with support\_tickets.csv on CustomerID (again, likely a left join).

This process allows you to see all information related to a customer in one place, enabling better customer service and targeted marketing.



Hands-On: Merging Customer Demographics with Their Order Totals

Let's practice merging two DataFrames. We'll create a DataFrame with customer demographics and another with their order summaries, then merge them to see which customers have placed orders and their total spending.



Step 1: Create Sample DataFrames

We'll define two DataFrames: one for customer information and another for aggregated order totals per customer.



import pandas as pd

import numpy as np



\# DataFrame 1: Customer Demographics

data\_customers = {

&#x20;   'CustomerID': \[101, 102, 103, 104, 105, 106],

&#x20;   'Name': \['Alice', 'Bob', 'Charlie', 'David', 'Eve', 'Frank'],

&#x20;   'City': \['New York', 'Los Angeles', 'Chicago', 'New York', 'Los Angeles', 'Boston']

}

df\_demographics = pd.DataFrame(data\_customers)



\# DataFrame 2: Aggregated Order Totals per Customer

\# Let's assume this was derived from a larger orders table using groupby and sum

data\_order\_totals = {

&#x20;   'CustomerID': \[101, 102, 101, 103, 104, 107], # Customer 107 has an order but no demographic entry

&#x20;   'TotalOrderAmount': \[1225.00, 75.00, 1225.00, 300.00, 50.00, 200.00] # Note: Customer 101 appears twice in raw orders, sum aggregates it. Let's simulate a pre-aggregated table.

}

\# To make it a pre-aggregated table, we'd typically do:

\# df\_raw\_orders = pd.DataFrame({'CustomerID': \[101, 102, 101, 103, 104, 107], 'Amount': \[1200, 75, 25, 300, 50, 200]})

\# df\_order\_totals = df\_raw\_orders.groupby('CustomerID')\['Amount'].sum().reset\_index()

\# df\_order\_totals = df\_order\_totals.rename(columns={'Amount': 'TotalOrderAmount'})



\# For simplicity, let's use a pre-defined aggregated table that might have duplicates if not careful

\# A better pre-aggregated table would look like this:

data\_order\_totals\_unique = {

&#x20;   'CustomerID': \[101, 102, 103, 104, 107],

&#x20;   'TotalOrderAmount': \[1225.00, 75.00, 300.00, 50.00, 200.00]

}

df\_order\_totals = pd.DataFrame(data\_order\_totals\_unique)





print("Customer Demographics DataFrame:")

print(df\_demographics)

print("

Order Totals DataFrame:")

print(df\_order\_totals)

Step 2: Perform a Left Merge

We want to see all customers from our demographics table and, if they have placed orders, show their total order amount. This calls for a left merge, where df\_demographics is the left DataFrame.



\# Perform a left merge on 'CustomerID'

customer\_order\_summary = pd.merge(

&#x20;   df\_demographics,

&#x20;   df\_order\_totals,

&#x20;   on='CustomerID',

&#x20;   how='left'

)



print("

Customer Order Summary (Left Merge):")

print(customer\_order\_summary)

Observation: Notice that 'Frank' (CustomerID 106) has NaN in the TotalOrderAmount column because he exists in df\_demographics but not in df\_order\_totals. Customer 107, who exists in df\_order\_totals but not df\_demographics, is not included because it was a left merge.



Step 3: Perform an Outer Merge

Now, let's perform an outer merge to see all customers from both tables, filling in NaN where data is missing.



\# Perform an outer merge on 'CustomerID'

all\_customer\_and\_order\_data = pd.merge(

&#x20;   df\_demographics,

&#x20;   df\_order\_totals,

&#x20;   on='CustomerID',

&#x20;   how='outer'

)



print("

All Customer and Order Data (Outer Merge):")

print(all\_customer\_and\_order\_data)

Observation: Now, both 'Frank' (CustomerID 106) and Customer 107 are included. 'Frank' has NaN for TotalOrderAmount, and Customer 107 has NaN for 'Name' and 'City'.



This hands-on exercise highlights how different merge types allow you to control which records are kept and how missing data is handled when combining datasets. This is a critical step in building a unified view of your data.



Customizing Operations: Applying Functions to DataFrames

While Pandas offers a vast array of built-in functions for data manipulation, there are times when you need to perform custom operations that are not directly available. The .apply() method in Pandas is a versatile tool that allows you to apply a custom function along an axis of a DataFrame (either row-wise or column-wise).



What is Applying Functions?

The .apply() method takes a function as an argument and applies it to each row or column of a DataFrame. This function can be a built-in Python function, a lambda function, or a user-defined function.



Why is Applying Functions Important?

Custom Transformations: Perform complex calculations or data transformations that are specific to your needs.

Data Cleaning: Implement custom logic for handling missing values, standardizing formats, or correcting data errors.

Feature Engineering: Create new features based on intricate logic involving multiple columns.

Flexibility: Extends the capabilities of Pandas beyond its predefined methods.

How to Implement Applying Functions

The syntax for .apply() is:



df.apply(func, axis=0, ...)

Key parameters:



func: The function to apply. This can be a function name, a lambda function, or a callable object.

axis: Specifies whether to apply the function to rows (axis=1) or columns (axis=0, default).

1\. Applying a Function to Columns (axis=0)

When axis=0 (the default), the function is applied to each column. The function receives a Series (representing a column) as input.



Example: Calculate the range (max - min) for numerical columns in our df\_customers DataFrame.



\# Define a function to calculate range

def calculate\_range(series):

&#x20;   # Ensure the series is numeric and handle potential NaNs

&#x20;   numeric\_series = pd.to\_numeric(series, errors='coerce')

&#x20;   if numeric\_series.isnull().all():

&#x20;       return np.nan

&#x20;   return numeric\_series.max() - numeric\_series.min()



\# Apply the function to each column

column\_ranges = df\_customers.apply(calculate\_range, axis=0)



print("

Range (Max - Min) for each column:")

print(column\_ranges)

2\. Applying a Function to Rows (axis=1)

When axis=1, the function is applied to each row. The function receives a Series (representing a row) as input, where the index of the Series corresponds to the column names.



Example: Create a new column 'PurchaseCategory' based on the 'PurchaseAmount'.



\# Define a function to categorize purchase amounts

def categorize\_purchase(row):

&#x20;   if row\['PurchaseAmount'] > 300:

&#x20;       return 'High Value'

&#x20;   elif row\['PurchaseAmount'] > 100:

&#x20;       return 'Medium Value'

&#x20;   else:

&#x20;       return 'Low Value'



\# Apply the function row-wise

df\_customers\['PurchaseCategory'] = df\_customers.apply(categorize\_purchase, axis=1)



print("

DataFrame with new 'PurchaseCategory' column:")

print(df\_customers)

3\. Using Lambda Functions with .apply()

Lambda functions are often used with .apply() for concise, one-off operations.



Example: Convert all string columns to uppercase.



\# Apply a lambda function to convert string columns to uppercase

for col in df\_customers.columns:

&#x20;   if df\_customers\[col].dtype == 'object': # Check if column is of object type (often strings)

&#x20;       df\_customers\[col] = df\_customers\[col].apply(lambda x: x.upper() if isinstance(x, str) else x)



print("

DataFrame with string columns converted to uppercase:")

print(df\_customers)

4\. Applying Functions to Specific Columns

You can also select specific columns and then apply a function.



\# Apply a function only to the 'PurchaseAmount' column

\# Example: Add a 10% tax to PurchaseAmount

df\_customers\['PurchaseAmountWithTax'] = df\_customers\['PurchaseAmount'].apply(lambda x: x \* 1.10)



print("

DataFrame with 'PurchaseAmountWithTax' column:")

print(df\_customers)

Performance Considerations

While .apply() is very flexible, it can sometimes be slower than vectorized Pandas operations (operations that work on entire Series or DataFrames at once, like df\['col'] + 5 or df.groupby('col').sum()). If a vectorized solution exists for your problem, it is generally preferred for performance reasons. However, for complex custom logic, .apply() is an invaluable tool.



Real-World Scenario: Calculating BMI

Suppose you have a DataFrame with columns 'Height' (in meters) and 'Weight' (in kilograms). You can use .apply() with a lambda function to calculate the Body Mass Index (BMI) for each person:



\# Assume df\_people has 'Height' and 'Weight' columns

\# df\_people\['BMI'] = df\_people.apply(lambda row: row\['Weight'] / (row\['Height']\*\*2), axis=1)

This demonstrates how .apply() can be used to create new derived features based on existing data.



Data Transformation and Aggregation

Lesson visual

Practical Application: Comprehensive Data Transformation and Aggregation Scenario

In this section, we will synthesize the concepts learned throughout the lesson by working through a more comprehensive scenario. We will load a dataset, perform filtering, sorting, grouping, aggregation, and merging to derive meaningful insights.



Scenario: Analyzing E-commerce Sales Data

Imagine you are given two CSV files:



customers.csv: Contains customer demographic information.

orders.csv: Contains individual order details.

Your goal is to:



Understand the total sales generated by each customer.

Identify the top 5 customers by total spending.

Calculate the average order value per customer.

Determine the most popular product category for customers in 'New York'.

Step 1: Setup and Data Loading

First, let's create dummy CSV files for our scenario and then load them into Pandas DataFrames.



import pandas as pd

import numpy as np

import os



\# --- Create dummy CSV files ---

\# customers.csv

customer\_data = {

&#x20;   'CustomerID': \[101, 102, 103, 104, 105, 106, 107, 108, 109, 110],

&#x20;   'Name': \['Alice', 'Bob', 'Charlie', 'David', 'Eve', 'Frank', 'Grace', 'Heidi', 'Ivan', 'Judy'],

&#x20;   'City': \['New York', 'Los Angeles', 'Chicago', 'New York', 'Los Angeles', 'Boston', 'New York', 'Chicago', 'New York', 'Los Angeles'],

&#x20;   'SignupDate': pd.to\_datetime(\['2022-01-15', '2022-02-20', '2022-03-10', '2022-01-25', '2022-04-05', '2022-05-12', '2022-02-01', '2022-03-22', '2022-01-30', '2022-04-18'])

}

df\_customers\_csv = pd.DataFrame(customer\_data)

df\_customers\_csv.to\_csv('customers.csv', index=False)



\# orders.csv

order\_data = {

&#x20;   'OrderID': range(1, 16),

&#x20;   'CustomerID': \[101, 102, 101, 103, 104, 105, 101, 106, 107, 108, 103, 109, 110, 102, 107],

&#x20;   'Product': \['Laptop', 'Keyboard', 'Mouse', 'Monitor', 'Webcam', 'Desk', 'Charger', 'Chair', 'Lamp', 'Notebook', 'Pen', 'Tablet', 'Phone', 'Mousepad', 'Stapler'],

&#x20;   'Category': \['Electronics', 'Electronics', 'Electronics', 'Electronics', 'Electronics', 'Furniture', 'Electronics', 'Furniture', 'Home Goods', 'Office Supplies', 'Office Supplies', 'Electronics', 'Electronics', 'Electronics', 'Office Supplies'],

&#x20;   'Price': \[1200, 75, 25, 300, 50, 150, 30, 200, 40, 10, 5, 400, 800, 15, 8],

&#x20;   'Quantity': \[1, 2, 3, 1, 1, 1, 2, 1, 5, 10, 20, 1, 1, 1, 5]

}

df\_orders\_csv = pd.DataFrame(order\_data)

df\_orders\_csv.to\_csv('orders.csv', index=False)



print("Dummy CSV files created: customers.csv, orders.csv")



\# Load the datasets

df\_customers = pd.read\_csv('customers.csv')

df\_orders = pd.read\_csv('orders.csv')



\# Calculate Total Amount for each order

df\_orders\['TotalAmount'] = df\_orders\['Price'] \* df\_orders\['Quantity']



print("

Loaded Customer DataFrame:")

print(df\_customers.head())

print("

Loaded Orders DataFrame (with TotalAmount):")

print(df\_orders.head())

Step 2: Calculate Total Sales per Customer

We need to aggregate the TotalAmount from the df\_orders DataFrame by CustomerID.



\# Group orders by CustomerID and sum the TotalAmount

customer\_total\_sales = df\_orders.groupby('CustomerID')\['TotalAmount'].sum().reset\_index()

customer\_total\_sales = customer\_total\_sales.rename(columns={'TotalAmount': 'TotalSpending'})



print("

Total Spending per Customer:")

print(customer\_total\_sales.head())

Step 3: Merge Customer Demographics with Total Sales

Now, let's merge this aggregated sales data with the customer demographics to get a complete view.



\# Merge customer demographics with their total spending

\# Use a left merge to keep all customers, even if they have not ordered yet

customer\_spending\_details = pd.merge(

&#x20;   df\_customers,

&#x20;   customer\_total\_sales,

&#x20;   on='CustomerID',

&#x20;   how='left'

)



\# Fill NaN TotalSpending with 0 for customers who have not ordered

customer\_spending\_details\['TotalSpending'] = customer\_spending\_details\['TotalSpending'].fillna(0)



print("

Customer Spending Details (Demographics + Total Spending):")

print(customer\_spending\_details.head())

Step 4: Identify Top 5 Customers by Total Spending

We can now sort the merged DataFrame by TotalSpending in descending order and select the top 5.



\# Sort by TotalSpending in descending order

top\_customers = customer\_spending\_details.sort\_values(by='TotalSpending', ascending=False)



\# Select the top 5 customers

top\_5\_customers = top\_customers.head(5)



print("

Top 5 Customers by Total Spending:")

print(top\_5\_customers)

Step 5: Calculate Average Order Value per Customer

To find the average order value, we need the total spending and the count of orders for each customer. We can achieve this by grouping the original df\_orders DataFrame again.



\# Group orders by CustomerID and calculate count and sum

customer\_order\_stats = df\_orders.groupby('CustomerID').agg(

&#x20;   NumberOfOrders=('OrderID', 'count'),

&#x20;   TotalSpending=('TotalAmount', 'sum')

).reset\_index()



\# Calculate Average Order Value

customer\_order\_stats\['AverageOrderValue'] = customer\_order\_stats\['TotalSpending'] / customer\_order\_stats\['NumberOfOrders']



print("

Customer Order Statistics (Count, Total, Average):")

print(customer\_order\_stats.head())

Step 6: Determine Most Popular Category for Customers in 'New York'

This requires filtering customers to 'New York', then looking at their orders, and finally grouping those orders by category.



\# 1. Filter customers from 'New York'

ny\_customers\_df = df\_customers\[df\_customers\['City'] == 'New York']

ny\_customer\_ids = ny\_customers\_df\['CustomerID'].tolist()



\# 2. Filter orders placed by these 'New York' customers

ny\_orders = df\_orders\[df\_orders\['CustomerID'].isin(ny\_customer\_ids)]



\# 3. Group these orders by 'Category' and count them

ny\_category\_counts = ny\_orders.groupby('Category').size().reset\_index(name='Count')



\# 4. Find the category with the maximum count

most\_popular\_ny\_category = ny\_category\_counts.sort\_values(by='Count', ascending=False).iloc\[0]



print("

Order Counts by Category for Customers in New York:")

print(ny\_category\_counts)

print(f"

Most Popular Category for New York Customers: {most\_popular\_ny\_category\['Category']} (with {most\_popular\_ny\_category\['Count']} orders)")

This comprehensive exercise demonstrates how to chain together filtering, grouping, aggregation, and merging to answer complex business questions. You've successfully transformed raw data into actionable insights.



Summary, Best Practices, and Next Steps

Congratulations on completing the lesson on Data Transformation and Aggregation! You've gained a solid understanding of essential Pandas techniques that are fundamental to any data science workflow.



Key Takeaways:

Filtering: Precisely select subsets of data using boolean indexing, logical operators (\&, |, \~), and methods like .isin() and string operations via the .str accessor.

Sorting: Organize your data for better readability and analysis using .sort\_values(), with options for single or multiple columns and ascending/descending order.

Grouping (groupby()): The powerful "split-apply-combine" strategy allows you to segment your data based on categories.

Aggregation: Condense grouped data into meaningful summaries using functions like .sum(), .mean(), .count(), .size(), and especially the versatile .agg() method.

Merging and Joining: Combine data from multiple sources using pd.merge() (for column-based joins) and DataFrame.join() (often for index-based joins), understanding the different `how` parameters ('inner', 'left', 'right', 'outer').

Applying Functions (.apply()): Execute custom logic on rows or columns when built-in methods are insufficient, using either defined functions or lambda expressions. Remember to consider performance implications.

Best Practices and Pro Tips:

Vectorization First: Whenever possible, leverage Pandas' built-in vectorized operations (like direct arithmetic on Series, .isin(), .str methods, and aggregation functions on grouped objects) before resorting to .apply() for performance gains.

Descriptive Column Names: Use clear and concise names for your columns, especially after aggregation or merging, to make your DataFrames self-explanatory. Use named aggregation with .agg().

Understand Your Joins: Carefully choose the `how` parameter in pd.merge() based on whether you need all records from one table, both tables, or only matching records.

Handle Missing Data: Be mindful of NaN values during filtering, sorting, and aggregation. Use methods like .fillna() appropriately.

Iterate and Inspect: do not hesitate to print intermediate results or inspect groups during complex operations to understand what's happening at each step.

Readability: Break down complex operations into smaller, manageable steps. Use comments to explain your logic.

Additional Resources:

Pandas Merge, Join, Concatenate documentation



Pandas Group By documentation



Pandas Applying Functions documentation



Preparation for Module 3 Assessment:

The upcoming Module 3 Assessment will test your practical ability to apply the concepts covered in this module. You can expect exercises that require you to:



Load data from a file (e.g., CSV).

Clean the data by handling missing values or duplicates.

Filter the data based on specific criteria.

Sort the data to identify trends or extremes.

Group data by one or more columns and perform aggregations (e.g., calculate sums, averages, counts).

Merge two related datasets to create a unified view.

Apply custom functions for data transformation.

Practice Tip: Revisit the hands-on exercises in this lesson and try to modify them or create new scenarios. Experiment with different filtering conditions, aggregation functions, and join types. The more you practice, the more comfortable you will become with these essential data manipulation techniques.





