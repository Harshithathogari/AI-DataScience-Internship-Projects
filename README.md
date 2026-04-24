# 📌 Import Libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# 📂 Load Dataset
df = pd.read_csv("zomato.csv")

# 👀 View Data
print(df.head())
print(df.info())

# 🧹 Data Cleaning
# Drop duplicates
df.drop_duplicates(inplace=True)

# Handle missing values
df.dropna(inplace=True)

# Convert ratings to numeric (if needed)
df['rating'] = pd.to_numeric(df['rating'], errors='coerce')

# 📊 Basic Analysis
print("Average Rating:", df['rating'].mean())
print("Top Locations:\n", df['location'].value_counts().head())

# 📈 Visualization 1: Rating Distribution
plt.figure()
sns.histplot(df['rating'], bins=10)
plt.title("Rating Distribution")
plt.xlabel("Rating")
plt.ylabel("Count")
plt.show()

# 📈 Visualization 2: Cost vs Rating
plt.figure()
sns.scatterplot(x='approx_cost(for two people)', y='rating', data=df)
plt.title("Cost vs Rating")
plt.xlabel("Cost for Two")
plt.ylabel("Rating")
plt.show()

# 📈 Visualization 3: Top Locations
plt.figure()
df['location'].value_counts().head(10).plot(kind='bar')
plt.title("Top Locations")
plt.xlabel("Location")
plt.ylabel("Number of Restaurants")
plt.show()

# 📈 Visualization 4: Popular Cuisines
plt.figure()
df['cuisines'].value_counts().head(10).plot(kind='bar')
plt.title("Top Cuisines")
plt.xlabel("Cuisine")
plt.ylabel("Count")
plt.show()
