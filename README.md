# CORRAL_2ECEA_PA4
# ECE2112
# Programming_Assignment_4
This Proramming Assignment contains Python Code solution using Data Wrangling and Data Visualization technique with storytelling. It includes analization of data and presents different (i) data frames; and (ii) visuals using the given datasets. This is made by Marc Dominic C. Corral from 2-ECE-A as a programming assignment for ECE 2112 - Advance Computer Programming and Algorithms course.

# ECE BOARD EXAM PROBLEM
This problem involves creating data frames and visualizations that shows how the different features contributes to average grade. It also provides answer to the question "Does chosen track in college, gender, or hometown contributes to a higher average score?" using the bar graphs in Data Visualization.

# Python Code:
```python
import pandas as pd
import matplotlib.pyplot as plt

dataframe = pd.read_excel('board2.xlsx')
dataframe

Vis = dataframe[(dataframe['Hometown'] == 'Visayas') & (dataframe['Math']<70)][['Name', 'Gender', 'Track', 'Math']]
Vis

Instru = dataframe[(dataframe['Track'] == 'Instrumentation') & (dataframe['Hometown'] == 'Luzon') & (dataframe['Electronics']>70)][['Name', 'GEAS', 'Electronics']]
Instru

dataframe['Average'] = dataframe[['Math','Electronics','GEAS', 'Communication']].mean(axis=1)

Mindy = dataframe[(dataframe['Hometown'] == 'Mindanao') & (dataframe['Gender'] == 'Female') & (dataframe['Average'] >= 55)][['Name', 'Track', 'Electronics', 'Average']]
Mindy

plt.figure(figsize = (15, 10))

plt.subplot(2, 2, 1)
TrackAve = dataframe.groupby('Track')['Average'].mean()
plt.bar(TrackAve.index, TrackAve.values)
plt.title('Average Grade by Track')
plt.ylabel('Average Grade')
plt.xticks(rotation = 45)

plt.tight_layout()
plt.show()

plt.subplot(2, 2, 2)
GenderAve = dataframe.groupby('Gender')['Average'].mean()
plt.bar(GenderAve.index, GenderAve.values)
plt.title('Average Grade by Gender')
plt.ylabel('Average Grade')

plt.tight_layout()
plt.show()

plt.subplot(2, 2, 3)
HometownAve = dataframe.groupby('Hometown')['Average'].mean()
plt.bar(HometownAve.index, HometownAve.values)
plt.title('Average Grade by Hometown')
plt.ylabel('Average Grade')
plt.xticks(rotation = 45)

plt.tight_layout()
plt.show()

plt.subplot(2, 2, 4)
Subjects = ['Math', 'GEAS', 'Electronics', 'Communication']
SubjectMeans = [dataframe[subject].mean() for subject in Subjects]
plt.bar(Subjects, SubjectMeans)
plt.title('Average Scores by Subjects')
plt.ylabel('Averge Score')
plt.xticks(rotation = 45)

plt.tight_layout()
plt.show()
```

# Outputs:

Output for the dataframe:  Vis = [“Name”, “Gender”, “Track”, “Math<70”]; hometown is constant as Visayas

<img width="431" height="175" alt="image" src="https://github.com/user-attachments/assets/fdd88fe7-ebc1-4884-a073-bcaa5154c964" />

Output for the dataframe: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as
Instrumentation and hometown Luzon

<img width="330" height="159" alt="image" src="https://github.com/user-attachments/assets/88a0f7b0-9d8a-4227-9a47-0fdad4ec6d45" />

Output for the dataframe:  Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is
constant as Mindanao and gender Female

<img width="490" height="237" alt="image" src="https://github.com/user-attachments/assets/b39d5115-ec19-42b5-8916-b4d4aefc3dce" />

# Data Visualizations:

<img width="1000" height="710" alt="image" src="https://github.com/user-attachments/assets/8bbc52ab-07fb-4818-b6fa-6fe83e0332bf" />

<img width="474" height="333" alt="image" src="https://github.com/user-attachments/assets/27a559c8-bc7c-4cf9-a7dd-29fff0e5ddc8" />

<img width="454" height="360" alt="image" src="https://github.com/user-attachments/assets/71a68c88-e681-4e18-973f-b37905fa2fe2" />

<img width="445" height="383" alt="image" src="https://github.com/user-attachments/assets/4abab3dc-5b26-44e7-b039-f4d575070ad2" />

# Code Explanation:
```python
import pandas as pd  #This imports pandas into the Python code.
import matplotlib.pyplot as plt #This imports matplotlib.pyplot into the Python Code. 

dataframe = pd.read_excel('board2.xlsx').
dataframe  #This reads the excel file "board2.xlsx"

Vis = dataframe[(dataframe['Hometown'] == 'Visayas') & (dataframe['Math']<70)][['Name', 'Gender', 'Track', 'Math']]
Vis  #This locates the variables that apply to given condition inside the dataframe [] and outputs the specific column which was categorized when you input it.

Instru = dataframe[(dataframe['Track'] == 'Instrumentation') & (dataframe['Hometown'] == 'Luzon') & (dataframe['Electronics']>70)][['Name', 'GEAS', 'Electronics']] 
Instru #This locates the variables that apply to given condition inside the dataframe [] and outputs the specific column which was categorized when you input it.

dataframe['Average'] = dataframe[['Math','Electronics','GEAS', 'Communication']].mean(axis=1) #This gets the mean of all inside the dataframe [] and place it in columns or axis = 1.

Mindy = dataframe[(dataframe['Hometown'] == 'Mindanao') & (dataframe['Gender'] == 'Female') & (dataframe['Average'] >= 55)][['Name', 'Track', 'Electronics', 'Average']]  
Mindy #This locates the variables that apply to given condition inside the dataframe [] and outputs the specific column which was categorized when you input it.
#This also shows the average.
```

