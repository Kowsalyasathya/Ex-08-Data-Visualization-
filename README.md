# Ex-07-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.
# CODE
Name : Kowsalya M
Register No : 212222230069
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sbn
df=pd.read_csv("/content/Superstore(1).csv",encoding='windows-1252')
df.head()

df.info()
df.isnull().sum()
1.Which Segment has Highest sales?
sbn.barplot(x=df['Segment'],y=df['Sales'])
plt.title("Highest Sales of the segment")

2.Which City has Highest profit?
sbn.barplot(x=df['City'],y=df['Profit'])
plt.title("Highest Profit of cities")

City=df.loc[:,["City","Profit"]]
df.head(5)
City=City.groupby(by=["City"]).sum().sort_values(by="Profit")
plt.figure(figsize=(10,10))
sbn.barplot(x=City.index,y="Profit",data=City)
plt.xticks(rotation = 90)
plt.xlabel=("City")
plt.ylabel=("Profit")
plt.show()

3.Which ship mode is profitable?
sbn.barplot(x=df['Ship Mode'],y=df['Profit'])
plt.title("Profitable Ship Mode")

4.Sales of the product based on region.
sbn.barplot(x=df['Sales'], y=df['Region'])
plt.title("Sales of Product based on Region")

5.Find the relation between sales and profit.
sbn.lineplot(x=df['Sales'], y=df['Profit'])
plt.title("Relation between Sales and Profit")

6.Find the relation between sales and profit based on the following category. i) Segment ii)City iii)States iv)Segment and Ship Mode
v)Segment, Ship mode and Region 
i) Segment
grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
ax.legend()
plt.title("Sales and Profit based on Segment")
plt.show()

2.City
grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('City')
ax.set_ylabel('Value')
ax.legend()
plt.title("Sales and Profit based on City")
plt.show()

3.states
grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.title("Sales and Profit based on States")

4.Segment and Ship Mode
grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.legend(loc="best")
plt.title("Sales and Profit based on Segment and Ship mode")
plt.show()

5.Segment, Ship mode and Region
grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])
sbn.set_style("whitegrid")
sbn.set_palette("Set1")
pivot_data.plot(kind='bar', stacked=True, figsize=(8, 5))
plt.legend(title='Region')
plt.legend(loc='best')
plt.title("Sales and Profit based on Segment,Ship mode and Region")

# OUPUT :

![8 1](https://github.com/Kowsalyasathya/Ex-08-Data-Visualization-/assets/118671457/a6345c6e-1661-4a05-9079-e276265f0846)
![8 2](https://github.com/Kowsalyasathya/Ex-08-Data-Visualization-/assets/118671457/30f733aa-61e1-4a61-9c39-30fc94ed8efd)
![8 3](https://github.com/Kowsalyasathya/Ex-08-Data-Visualization-/assets/118671457/39e7d850-da67-48e0-843a-e3a1838041b8)
![8 4](https://github.com/Kowsalyasathya/Ex-08-Data-Visualization-/assets/118671457/b8cfd082-9158-4d87-be00-ee1c9cdcbd6c)
![8 5](https://github.com/Kowsalyasathya/Ex-08-Data-Visualization-/assets/118671457/e5fbb457-ec62-4326-8222-050f96b51fba)

![8 6](https://github.com/Kowsalyasathya/Ex-08-Data-Visualization-/assets/118671457/b9a6644d-6f85-4cdf-809b-758dec201e2c)
![8 7](https://github.com/Kowsalyasathya/Ex-08-Data-Visualization-/assets/118671457/365162e2-0619-4ee9-b795-0187ca54a0e2)

![8 8](https://github.com/Kowsalyasathya/Ex-08-Data-Visualization-/assets/118671457/31a8d49f-8c03-4beb-aee3-ee893e994a3d)
![8 9](https://github.com/Kowsalyasathya/Ex-08-Data-Visualization-/assets/118671457/4c6d9960-c21f-4db3-9615-2927131dfd6d)
![8 10](https://github.com/Kowsalyasathya/Ex-08-Data-Visualization-/assets/118671457/642664bf-0677-4269-9bef-3ff2d4c32b2b)
![8 11](https://github.com/Kowsalyasathya/Ex-08-Data-Visualization-/assets/118671457/c671fec4-075f-4502-a9ce-b74511dc565f)

## Result :
Hence the data visualization method for the given dataset applied successfully.
