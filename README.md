# Zomato-Data-Analysis
Zomato Data Analysis with Python

# Problem Statement

We have to answer following inquiries :

1. Distribution of Ratings
2. Distribution of Approximate Cost
3. Ratings vs. Approximate Cost
4. Online Order vs. Ratings
5. Book Table vs. Ratings
6. Restaurant Type Analysis
7. Average Rating by Restaurant Type
8. Average Cost by Restaurant Type
9. Do a greater number of restaurants provide online delivery as opposed to offline services?

#### `Step 1:` Importing necessary Python libraries
```
import pandas as pd
import numpy as np
import plotly.express as px
import plotly.graph_objects as go
```

#### `Step 2:` Creating the data frame
```
df = pd.read_csv('Zomato-data-.csv')
```

#### `Step 3:` Understanding the data
```
df.info()
df.describe()
```
##### Data Understanding:
```
DataFrame shape - 148 rows × 7 columns
There is no NULL value
In rate column we have to remove "/5" denominator
Change column names:
"name" to "restaurant_name",
"approx_cost(for two people)" to "approx_cost",
"listed_in(type)" to "restaurant_type"
```

#### `Step 4:` Data cleaning and processing
```
Changing column names
df = df.rename(columns={'name': 'Restaurant Name'})
df = df.rename(columns={'approx_cost(for two people)': 'approx_cost'})
df = df.rename(columns={'listed_in(type)': 'restaurant_type'})
```
```
Clean rate column
df['rate'] = df['rate'].str.replace('/5', '')
df['rate'] = pd.to_numeric(df['rate'], errors='coerce')
```

### Exploratory Data Analysis (EDA)

Let's explore the data to answer interesting questions.
```
1. Distribution of Ratings:

fig_rate = px.histogram(df, x = 'rate', nbins = 20, title = 'Distribution of Ratings')
fig_rate.show()

Insights:
Max ratings (30) are received in between 3.8 and 3.9
```

