# CORRAL_2ECEA_PA4
# ECE2112
# Programming_Assignment_4
This Proramming Assignment contains Python Code solution using Data Wrangling and Data Visualization technique with storytelling. It includes analization of data and presents different (i) data frames; and (ii) visuals using the given datasets. This is made by Marc Dominic C. Corral from 2-ECE-A as a programming assignment for ECE 2112 - Advance Computer Programming and Algorithms course.

# ECE BOARD EXAM PROBLEM
<h6>This problem involves creating data frames and visualizations that shows how the different features contributes to average grade. It also provides answer to the question "Does chosen track in college, gender, or hometown contributes to a higher average score?" using the bar graphs in Data Visualization.</h6>

---
1.) A Python script/code where by using data wrangling and visualization techniques, we make dataframes on the file 'board2.csv' based on the given conditions:
```python
import pandas as pd #This imports Pandas Library into the Python Code.

dataframe = pd.read_excel('board2.xlsx')
dataframe  #This reads the excel file "board2.xlsx"
```
---
FIRST CONDITION:

<h6>Using the filename INSTRU, we will construct a dataframe where the displayed values are "Track" set as "Instrumentation", "Hometown" set as "Luzon", and their "Electronics" score must be greater than 70. Then the values that are qualified in the previous conditions, will displays the values of the columns "Name", "GEAS", and "Electronics".</h6> 

```python
Instru = dataframe[(dataframe['Track'] == 'Instrumentation') & #This locates all the values with "Instrumrntation" in the "Hometown" column.
        (dataframe['Hometown'] == 'Luzon') & #This locates all the values with "Luzon" in the "Hometown" column.
        (dataframe['Electronics']>70)] #This locates all the values located in the "Electronics" column higher than 70.
        [['Name', 'GEAS', 'Electronics']] #This displays only the columns inside the [], which fits the conditions above.
Instru
```

<h6>The output for this condition should look like this with these values:</h6>
<img width="261" height="179" alt="image" src="https://github.com/user-attachments/assets/75671ce2-5cd6-48e3-94d1-edad9a471059" />

---
SECOND CONDITION:

<h6>Using the filename MINDY, we will create a dataframe where the values displayed has their "Gender" set as 'Female', "Hometown" set as 'Mindanao', and their "Average" score is greater or equal to 55. The values that are qualified with the previous conditions displays the values of the columns "Name", "Track", "Electronics", and "Average".</h6> 

```python
#First we must make a new column called "Average" which displays the Average scores of all the subjects in the dataframe.

dataframe['Average'] = dataframe[['Math','Electronics','GEAS', 'Communication']].mean(axis=1) #This gets the mean of all inside the dataframe [] and place it in columns or axis = 1.

Mindy = dataframe[(dataframe['Hometown'] == 'Mindanao') & #This locates all the values with "Mindanao" in the "Hometown" column.
        (dataframe['Gender'] == 'Female') & #This loactes all the values with "Female" in the "Gender" column.
        (dataframe['Average'] >= 55)] #This locates all the values that are greater than or equal to 55 in the "Average" column, which is the new column we make.
        [['Name', 'Track', 'Electronics', 'Average']] #This displays only the columns inside the [], which fits the conditions above.
Mindy
```

<h6>The output for this condition should look like this with these values:</h6>
<img width="418" height="239" alt="image" src="https://github.com/user-attachments/assets/389d6b17-44d6-4ee1-b62a-54598f251bfb" />

---
2.) A Python script/code that creates a data visualization that shows how the different features contributes to average grade. Does chosen track in college, gender, or hometown contributes to a higher average score?

```python
import matplotlib.pyplot as plt #This imports MatPlot Library into the Python Code for Data Visualization. 
```

---
The Average Grade by the students by "Track" 
```python
plt.figure(figsize = (15, 10)) #This inputs the size of the graph.

plt.subplot(2, 2, 1) #This prepares the subplot inside the figure.
TrackAve = dataframe.groupby('Track')['Average'].mean() #This groups the dataframe by the values in the "Track" column and calculates its mean.
plt.bar(TrackAve.index, TrackAve.values) #This creates a Bar Graph, the x-axis is TrackAve.index (Track names) and the height of each bar is TrackAve.values (The computed mean grades).
plt.title('Average Grade by Track') #This places "Average Grade by Track" as the title of the graph.
plt.ylabel('Average Grade') #This places "Average Grade" as the label on the y axis.
plt.xlabel('Track') #This places "Track" as the label on the x axis.
plt.xticks(rotation = 45) #This rotates the tick labels on the x-axis by 45 degrees so the names won’t overlap.

plt.show() #This shows the Bar Graph.
```
<h6>With the Python Script/Codes above, the Bar Graph for the Average Grade by the students by "Track" will be like this:</h6>
<img width="756" height="646" alt="image" src="https://github.com/user-attachments/assets/053fca3a-30d0-4ac5-ac19-db57d448ed8c" />

---
The Average Grade by the students by "Gender" 
```python
plt.subplot(2, 2, 2) #This prepares the subplot inside the figure.
GenderAve = dataframe.groupby('Gender')['Average'].mean() #This groups the dataframe by the values in the "Gender" column and calculates its mean.
plt.bar(GenderAve.index, GenderAve.values) #This creates a Bar Graph, the x-axis is GenderAve.index (Male and Female) and the height of each bar is GenderAve.values (The computed mean grades).
plt.title('Average Grade by Gender') #This places "Average Grade by Gender" as the title of the graph.
plt.ylabel('Average Grade') #This places "Average Grade" as the label on the y axis.
plt.xlabel('Gender') #This places "Gender" as the label on the x axis.

plt.show() #This shows the Bar Graph.
```
<h6>With the Python Script/Codes above, the Bar Graph for the Average Grade by the students by "Gender" will be like this:</h6>
<img width="371" height="319" alt="image" src="https://github.com/user-attachments/assets/3c341c7d-01fb-45f0-a15c-0fff209459ca" />

---
The Average Grade by the students by "Hometown" 
```python
plt.subplot(2, 2, 3) #This prepares the subplot inside the figure.
HometownAve = dataframe.groupby('Hometown')['Average'].mean() #This groups the dataframe by the values in the "Hometown" column and calculates its mean.
plt.bar(HometownAve.index, HometownAve.values) #This creates a Bar Graph, the x-axis is HometownAve.index (Hometown names) and the height of each bar is HometownAve.values (The computed mean grades).
plt.title('Average Grade by Hometown') #This places "Average Grade by Hometown" as the title of the graph.
plt.ylabel('Average Grade') #This places "Average Grade" as the label on the y axis.
plt.xlabel('Hometown') #This places "Hometown" as the label on the x axis.
plt.xticks(rotation = 45) #This rotates the tick labels on the x-axis by 45 degrees so the names won’t overlap.

plt.show() #This shows the Bar Graph.
```
<h6>With the Python Script/Codes above, the Bar Graph for the Average Grade by the students by "Hometown" will be like this:</h6>
<img width="383" height="376" alt="image" src="https://github.com/user-attachments/assets/d4735846-0898-41d3-ba23-d9af9fc29b9a" />

---
The Average Grade by the students by "Subjects" 
```python
plt.subplot(2, 2, 4) #This prepares the subplot inside the figure.
Subjects = ['Math', 'GEAS', 'Electronics', 'Communication'] #This creates a list of column names from the datarame.
SubjectMeans = [dataframe[subject].mean() for subject in Subjects] #This uses a list comprehension to calculate the mean value for each subject column.
plt.bar(Subjects, SubjectMeans) #This creates a Bar Graph, the x-axis is the Subjetcs and the height of each bar is the mean grades from SubjectMeans.
plt.title('Average Grade by Subjects') #This places "Average Grade by Subjects" as the title of the graph.
plt.ylabel('Averge Grade') #This places "Average Grade" as the label on the y axis.
plt.xlabel('Subjects') #This places "Subjects" as the label on the x axis.
plt.xticks(rotation = 45) #This rotates the tick labels on the x-axis by 45 degrees so the names won’t overlap.

plt.show() #This shows the Bar Graph.
```
<h6>With the Python Script/Codes above, the Bar Graph for the Average Grade by the students by "Subjects" will be like this:</h6>
<img width="390" height="415" alt="image" src="https://github.com/user-attachments/assets/c9b914d2-daa2-4603-a8b3-aaa7e51a42db" />
