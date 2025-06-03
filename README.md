📘 README: Netflix Data Cleaning, Analysis and Visualization
📌 Project Overview
This project focuses on cleaning, analyzing, and visualizing a Netflix dataset to extract meaningful insights. It involves handling missing data, exploring trends, and creating engaging visualizations using Python libraries like pandas, seaborn, and matplotlib.

📂 Dataset
File Name: netflix1.csv

Contains:

Titles of Netflix content

Type (Movie or TV Show)

Cast, Director, Country

Date added to Netflix

Release year

Duration

Genre (Category/Listed_in)

Description

🛠️ Technologies & Libraries Used
Python

pandas

numpy

matplotlib

seaborn

WordCloud

📊 Key Steps & Code Explanation
✅ 1. Import Libraries
python
Copy
Edit
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from wordcloud import WordCloud
Used for data manipulation, visualization, and word cloud generation.

📥 2. Load the Dataset
python
Copy
Edit
data = pd.read_csv('netflix1.csv')
print(data.head())
Loads the Netflix dataset using pandas.read_csv.

🧹 3. Data Cleaning
Check for missing values:

python
Copy
Edit
print(data.isnull().sum())
View data types and memory info:

python
Copy
Edit
data.info()
Drop duplicates:

python
Copy
Edit
data.drop_duplicates(inplace=True)
🧼 4. Handling Null Values
Fill or drop based on context:

python
Copy
Edit
data['Country'].fillna(data['Country'].mode()[0], inplace=True)
data.dropna(subset=['Director'], inplace=True)
🧮 5. Date Conversion
Convert 'date_added' to datetime:

python
Copy
Edit
data['date_added'] = pd.to_datetime(data['date_added'])
🔎 6. Exploratory Data Analysis (EDA)
🟢 Type Distribution
python
Copy
Edit
sns.countplot(data=data, x='type')
Shows count of Movies vs TV Shows.

🌍 Content by Country
python
Copy
Edit
top_countries = data['Country'].value_counts().head(10)
sns.barplot(x=top_countries.values, y=top_countries.index)
📆 Content Added per Year
python
Copy
Edit
data['year_added'] = data['date_added'].dt.year
sns.countplot(data=data, x='year_added')
⌛ Duration Distribution
Separate 'duration' values for Movies and TV Shows:

python
Copy
Edit
data['duration'].value_counts()
☁️ Word Cloud of Descriptions
python
Copy
Edit
wordcloud = WordCloud(background_color='black').generate(' '.join(data['description'].dropna()))
plt.imshow(wordcloud, interpolation='bilinear')
📌 Insights Derived
Netflix has more Movies than TV Shows.

Majority of content originates from the United States and India.

A major influx of content happened around 2019–2020.

Most movies have a duration of 90 minutes, while TV shows are commonly 1 season.

▶️ How to Run This Project
Install Required Libraries

bash
Copy
Edit
pip install pandas numpy matplotlib seaborn wordcloud
Download the Dataset
Make sure netflix1.csv is in the same directory as the notebook.

Run the Notebook
Open in Jupyter Notebook or VS Code and run each cell sequentially.

📁 File Structure
nginx
Copy
Edit
Netflix Data Cleaning, Analysis and Visualization.ipynb
netflix1.csv
README.md
🧠 Author Notes
This project is ideal for those learning EDA, data cleaning, and basic visualization in Python.

It can be extended to include genre-based trends, rating analysis, or even recommendation systems