## INTRODUCTION TO PYTHON PROGRAMMING
# Experiment 3 - Pandas
URGEL, Hannah Pauleen A.      2ECE-B

# OVERVIEW
This experiment mainly introduces the Pandas library in Python, widely used to work and analyze structured data. Pandas provides tools to load datasets, exploit structures, and extract information through indexing, slicing, and filtering.

The following two problems are studied in this experiment:
Loading and displaying parts of a dataset.
Extracting specific data from the dataset using subsetting and indexing.
Work has been organized such that the problems presented show how through the use of Pandas it becomes easy working with tabular data like CSV files compared with raw Python lists or arrays. 

# PROBLEM 1:
Using knowledge obtained from the experiment and demonstrations:

a. Load the corresponding .csv file into a data frame named cars using pandas

b. Display the first five and last five rows of the resulting cars.

STEP 1: Import pandas and load the dataset:

## CODE:

```python
    import pandas as pd
    carfile = pd.read_csv("cars.csv")
    carfile
```

## OUTPUT:
<img width="988" height="946" alt="image" src="https://github.com/user-attachments/assets/b4c2b390-2423-4125-ab55-367a84b815d4" />

To get an initial look at the beginning of the dataset, I imported pandas as pd, which is the standard way of loading the pandas library in Python for easier use throughout the code. Pandas allows me to work with structured data, like CSV files, in an organized and efficient way. 

After that, I used pd.read_csv("cars.csv") to read the dataset and store it in a DataFrame called carfile. This DataFrame acts like a table where all the car data is stored and ready for analysis. 

Finally, I simply typed carfile to display the entire dataset, which let me check that the file was loaded correctly before performing any subsetting, slicing, or indexing. This step sets the foundation for all the operations that follow.

STEP 2: Display the first five rows:
## CODE:
```python
      carfile.head()
```
## OUTPUT:
<img width="1491" height="289" alt="image" src="https://github.com/user-attachments/assets/545dba9b-f46c-456f-a182-c5f9b43ac2d7" />
The head() function automatically displays the first five rows of the DataFrame, allowing me to confirm that the file was loaded correctly and to familiarize myself with the column names (Model, mpg, cyl, disp, hp, etc.). 

STEP 3: Display the last five rows:
## CODE:
```python
      carfile.tail()
```

## OUTPUT:
<img width="1490" height="300" alt="image" src="https://github.com/user-attachments/assets/f6bd3481-010d-438a-b687-cbf3f9f880a9" />
To check the dataset’s ending entries, I used carfile.tail(). The tail() function automatically shows the last five rows of the DataFrame, which helps ensure that the entire file was properly loaded and lets me spot any inconsistencies or anomalies at the bottom of the dataset.


# PROBLEM 2:
Using the dataframe cars in problem 1, extract the following information using subsetting, slicing and indexing operations.

a. Display the first five rows with odd-numbered columns (columns 1, 3, 5, 7…) of cars.

b. Display the row that contains the ‘Model’ of ‘Mazda RX4’.

c. How many cylinders (‘cyl’) does the car model ‘Camaro Z28’ have?

d. Determine how many cylinders (‘cyl’) and what gear type (‘gear’) do the car models ‘Mazda RX4 Wag’, ‘Ford Pantera L’ and ‘Honda Civic’ have.

STEP 1: Import pandas and load the dataset:
## CODE:
```python
    import pandas as pd
    carfile = pd.read_csv("cars.csv")
    carfile
```
## OUTPUT:
<img width="988" height="946" alt="image" src="https://github.com/user-attachments/assets/b4c2b390-2423-4125-ab55-367a84b815d4" />
Like with the first problem, I imported pandas as pd, which is the standard way of loading the pandas library in Python for easier use throughout the code. Pandas allows me to work with structured data, like CSV files, in an organized and efficient way. 

After that, I used pd.read_csv("cars.csv") to read the dataset and store it in a DataFrame called carfile. This DataFrame acts like a table where all the car data is stored and ready for analysis. 

Finally, I simply typed carfile to display the entire dataset, which let me check that the file was loaded correctly before performing any subsetting, slicing, or indexing. This step sets the foundation for all the operations that follow.

STEP 2: Display the first five rows with odd-numbered columns:
## CODE:
```python
      carfile[1:10:2]
 ```     
## OUTPUT:
<img width="1491" height="286" alt="image" src="https://github.com/user-attachments/assets/6b970f6d-deb9-41f2-a1bb-f4a17bb8658d" />
To display the first five rows with odd-numbered columns, I ran carfile[1:10:2], which uses Python slicing to select rows from index 1 up to (but not including) 10, stepping by 2. In practice this returns rows 1, 3, 5, 7, and 9. For me, this code is shorter and a more efficient method for callouts since there is already a table output

STEP 3: Display the row containing the model “Mazda RX4”:
## CODE:
```python
      carfile[0:1]
```

## OUTPUT:
<img width="1492" height="142" alt="image" src="https://github.com/user-attachments/assets/64a8202a-cedb-4d58-8583-2d5b8207273d" />
I looked through the dataset and identified that the model Mazda RX4 is located in row 0 of the DataFrame. After confirming its row index, I used carfile[0:1] to isolate and display just that row. This single-row slice shows the entire record for the Mazda RX4, including all of its fields such as mpg, cyl, hp, and gear, neatly arranged in a table.

STEP 4: Find how many cylinders “Camaro Z28” has:
## CODE:
```python
      carfile.loc[[23], ['Model', 'cyl']]
```
## OUTPUT:
<img width="1490" height="137" alt="image" src="https://github.com/user-attachments/assets/3ad93470-a1a6-4b0f-9a5a-5216684f9b4f" />
I first located the row where the model Camaro Z28 appears and confirmed that it is in row 23 of the DataFrame. After identifying the correct row index, I used carfile.loc[[23], ['Model', 'cyl']], which applies .loc (label-based indexing) to select row 23 and only the Model and cyl columns. This command neatly displays the Camaro Z28 model along with its cylinder count, confirming that it has 8 cylinders.

STEP 5: Get cylinders and gear type for three models:
## CODE:
```python
      carfile.loc[[1, 28, 18], ['Model', 'cyl', 'gear']]
```

## OUTPUT:
<img width="1494" height="200" alt="image" src="https://github.com/user-attachments/assets/6f2e845a-b32b-4c7a-a38b-f96c98babdfc" />
For this step, I first identified that Mazda RX4 Wag, Ford Pantera L, and Honda Civic are located in rows 1, 28, and 18, respectively. After confirming the correct rows, I used carfile.loc[[1, 28, 18], ['Model', 'cyl', 'gear']] to display only these three rows and the columns Model, cyl, and gear. This filters out any unrelated information and presents only the key details I need — the car model name, its number of cylinders, and gear type. This approach makes it easy to compare multiple models side by side in a clean and readable format.

