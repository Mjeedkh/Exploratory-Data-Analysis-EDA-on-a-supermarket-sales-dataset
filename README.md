import pandas as pd 
import numpy as np
import matplotlib.pyplot as plt 
import seaborn as sns 
import calmap
# Initial data exploration
from pandas_profiling import ProfileReport
df = pd.read_csv('supermarket_sales - Sheet1.csv')
df.head(10)
# univarite analysis 
# Replace infinite values with NaN for the entire DataFrame
df.replace([float('inf'), -float('inf')], pd.NA, inplace=True)

# Alternatively, specifically for the 'Rating' column
df['Rating'] = df['Rating'].replace([float('inf'), -float('inf')], pd.NA)

# Plot the data
sns.displot(df['Rating'])
#use the Seaborn library to plot out that distribution
# It looks like a uniform distribution, which means none off the rating numbers particularly spikes out. It looks like there's an equal chance someone rated 4 or 10 or 6 or any number in between

sns.displot(df['Rating'])
plt.axvline(x= np.mean(df['Rating']),c='red')
plt.axvline(x= np.percentile(df['Rating'],25),c='red')
plt.axvline(x= np.percentile(df['Rating'],75),c='red')
# plot the lines for the 25th and 75th percentile

df.hist(figsize=(10,10)

sns.countplot(data=df, x='Branch')
sns.countplot(data=df, x='Payment')
sns.scatterplot(x=df['Rating'],y=df['gross income'])
sns.regplot(x=df['Rating'],y=df['gross income'])
sns.boxplot(x=df['Rating'],y=df['gross income'])

# Sample DataFrame
df = pd.read_csv('supermarket_sales - Sheet1.csv') 

# Ensure 'Date' is in datetime format
df['Date'] = pd.to_datetime(df['Date'], errors='coerce')

# Convert 'gross income' to numeric, coercing errors to NaN
df['gross income'] = pd.to_numeric(df['gross income'], errors='coerce')

# Drop rows with NaN values in 'Date' or 'gross income' if they exist
df.dropna(subset=['Date', 'gross income'], inplace=True)

# Now plot the data
sns.lineplot(data=df, x='Date', y='gross income')
