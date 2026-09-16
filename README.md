# ECE-2112-PA-4

### Made by: Evan James G. Paciencia | 2ECE-C

This repository contains Programming Assignment 4 for the course Advanced Computer Programming** of S.Y. 2026-2027. This assignment covers **Data Wrangling and Data Visualization using Pandas and Matplotlib.

---

## A. VISAYAS COMMUNICATION DATAFRAME

Create a DataFrame named `VisComm` containing students whose **Hometown is Visayas** and whose **Track is Communication**.

The DataFrame should only contain the following columns:

- Name
- Gender
- Math
- Electronics
- Average

Both filtering conditions must be applied to the source dataset before selecting the columns. The resulting DataFrame and its row count should then be displayed.

### The following functions and methods were used:

`pd.read_excel()` – Reads an Excel file and loads its data into a Pandas DataFrame.

`.loc[]` – Selects rows and columns using their labels or names.

`.shape` – Gets the number of rows and columns of a DataFrame.

### Final Code:
```
import pandas as pd
import matplotlib.pyplot as plt

VisCom = pd.read_excel('board2.xlsx')

VisComm = VisCom.loc[
    (VisCom['Hometown'] == 'Visayas') &
    (VisCom['Track'] == 'Communication'),
    ['Name', 'Gender', 'Math', 'Electronics', 'Average']
]

VisComm

print("Number of rows:", VisComm.shape[0])
```

---

## B. VISAYAS FEMALE DATAFRAME

Create a DataFrame named `VisFemale` containing students whose **Hometown is Visayas** and whose **Gender is Female**.

The DataFrame should only contain:

* Name
* Track
* GEAS
* Electronics
* Average

After displaying `VisFemale`, display only the rows whose **Average is at least 60**. The second filtering operation should not overwrite `VisFemale`.

### The following functions and methods were used:

`.loc[]` – Selects rows and columns using their labels or names.

### Final Code:

```
VisFemale = VisCom.loc[
    (VisCom['Hometown'] == 'Visayas') &
    (VisCom['Gender'] == 'Female'),
    ['Name', 'Track', 'GEAS', 'Electronics', 'Average']
]

VisFemale

VisFemale.loc[VisFemale['Average'] >= 60]
```

### How the code works:

---

## C. CATEGORY-AVERAGE VISUALIZATION

Examine how the recorded **Average** differs across the three categorical features:

* Track
* Gender
* Hometown

For each feature, calculate the mean of `Average` for every category using Pandas. Display the three summary tables and create one figure containing three bar charts.

### The following functions and methods were used:

`.groupby()` – Groups the data based on a selected column.

`.mean()` – Calculates the average of the grouped data.

`.index` – Gets the labels or category names from the data.

`.values` – Gets the values from the data.

`plt.figure()` – Creates a figure for the plots.

`fig.add_subplot()` – Adds a subplot to the figure.

`.bar()` – Creates a bar chart.

`.set_title()` – Sets the title of a plot.

`.set_xlabel()` – Sets the label of the x-axis.

`.set_ylabel()` – Sets the label of the y-axis.

`plt.tight_layout()` – Adjusts the spacing between the plots.

`plt.show()` – Displays the plots.

### Final Code:
```
AvgHometown = VisCom.groupby('Hometown')['Average'].mean()
AvgGender = VisCom.groupby('Gender')['Average'].mean()
AvgTrack = VisCom.groupby('Track')['Average'].mean()

print("Average by Hometown:")
print(AvgHometown)

print("\nAverage by Gender:")
print(AvgGender)

print("\nAverage by Track:")
print(AvgTrack)

fig = plt.figure(figsize=(28, 6))

ax1 = fig.add_subplot(1, 3, 1)
ax1.bar(AvgHometown.index, AvgHometown.values)
ax1.set_title("Average by Hometown")
ax1.set_xlabel("Hometown")
ax1.set_ylabel("Average Score")

ax2 = fig.add_subplot(1, 3, 2)
ax2.bar(AvgGender.index, AvgGender.values)
ax2.set_title("Average by Gender")
ax2.set_xlabel("Gender")
ax2.set_ylabel("Average Score")

ax3 = fig.add_subplot(1, 3, 3)
ax3.bar(AvgTrack.index, AvgTrack.values)
ax3.set_title("Average by Track")
ax3.set_xlabel("Track")
ax3.set_ylabel("Average Score")

plt.tight_layout()
plt.show()
```

---

# Edit/History Log

Created: 9/10/2026
Last edited: 9/10/2026
Changes: 9/10/2026

* Added `board2.xlsx`

```
```
