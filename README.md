# 1. Vehicle Distribution Analysis


import pandas as pd 
import matplotlib.pyplot as plt
import seaborn as sns


df = pd.read_csv('traffic.csv')


plt.figure(figsize=(12, 6))
sns.boxplot(data=df[['CarCount', 'BikeCount', 'BusCount', 'TruckCount']])
plt.title('Distribution of Vehicle Counts')
plt.show()


df[['CarCount', 'BikeCount', 'BusCount', 'TruckCount']].hist(bins=20, figsize=(12, 8))
plt.suptitle('Histograms of Vehicle Counts')
plt.show()

# 2.Traffic Situation Distribution


plt.figure(figsize=(8, 5))
df['Traffic Situation'].value_counts().plot(kind='bar')
plt.title('Distribution of Traffic Situations')
plt.xlabel('Traffic Situation')
plt.ylabel('Frequency')
plt.show()


plt.figure(figsize=(6, 6))
df['Traffic Situation'].value_counts().plot(kind='pie', autopct='%1.1f%%')
plt.title('Traffic Situation Distribution')
plt.show()

# 3. Variation by Day of the Week

day_counts = df.groupby('Day of the week')[['CarCount', 'BikeCount', 'BusCount', 'TruckCount']].mean()

day_counts.plot(kind='bar', figsize=(12, 6))
plt.title('Vehicle Counts by Day of the Week')
plt.xlabel('Day of the Week')
plt.ylabel('Average Vehicle Count')
plt.show()

# 4.Car Count vs. Traffic Situation 

plt.figure(figsize=(10, 6))
sns.boxplot(x='Traffic Situation', y='CarCount', data=df)
plt.title('Car Count vs Traffic Situation')
plt.show()

# 5.Bike Count vs. Traffic Situation

plt.figure(figsize=(10, 6))
sns.boxplot(x='Traffic Situation', y='BikeCount', data=df)
plt.title('Bike Count vs Traffic Situation')
plt.show()

# 6.Bus Count vs. Traffic Situation

plt.figure(figsize=(10, 6))
sns.boxplot(x='Traffic Situation', y='BusCount', data=df)
plt.title('Bus Count vs Traffic Situation')
plt.show()

# 7.Truck Count vs. Traffic Situation

plt.figure(figsize=(10, 6))
sns.boxplot(x='Traffic Situation', y='TruckCount', data=df)
plt.title('Truck Count vs Traffic Situation')
plt.show()

# 8.Total Vehicle Count and Traffic Situation

total_counts = df.groupby('Traffic Situation')['Total'].sum()

total_counts.plot(kind='bar', figsize=(8, 5))
plt.title('Total Vehicle Count by Traffic Situation')
plt.xlabel('Traffic Situation')
plt.ylabel('Total Vehicle Count')
plt.show()

# 9.Busiest Hours of the Day

df['Hour'] = pd.to_datetime(df['Time']).dt.hour

hourly_counts = df.groupby('Hour')['Total'].sum()

hourly_counts.plot(kind='bar', figsize=(10, 6))
plt.title('Busiest Hours of the Day')
plt.xlabel('Hour of the Day')
plt.ylabel('Total Vehicle Count')
plt.show()
