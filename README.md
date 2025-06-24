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

1. DataFrame shape - 148 rows × 7 columns
2. There is no NULL value
3. In rate column we have to remove "/5" denominator
4. Change column names:
5. "name" to "restaurant_name",
6. "approx_cost(for two people)" to "approx_cost",
7. "listed_in(type)" to "restaurant_type"

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
```
2. Distribution of Approximate Cost

fig_cost = px.histogram(df, x = 'approx_cost', nbins = 20, title = 'Distribution of Approximate Cost')
fig_cost.show()

Insights:
Price 300 paid by most of the people (23).
```
```
3. Ratings vs. Approximate Cost

fig_scatter = px.scatter(df, x = 'approx_cost', y = 'rate', title = 'Ratings vs. Approximate Cost')
fig_scatter.show()

Insights :
Good ratings (4 to 5) is given by people who paid price between 300 to 850.
```
```
4. Online Order vs. Ratings

fig_online_order = px.box(df, x = 'online_order', y = 'rate',  title = 'Online Order vs. Ratings')
fig_online_order.show()

Insights:
Customers who order online are more likely to provide good ratings.
```
```
5. Book Table vs. Ratings

fig_book_table = px.box(df, x = 'book_table', y = 'rate', title = 'Book Table vs Ratings')
fig_book_table.show()

Insights:
Customers who book table are more likely to provide good ratings.
```
```
6. Restaurant Type Analysis

fig_type_count = px.bar(df['restaurant_type'].value_counts().reset_index(), x='restaurant_type', y='count', title='Count of Restaurants by Type', labels={'restaurant_type': 'Restaurant Type', 'count': 'Count'})
fig_type_count.show()

Insights:
Most prefered restaurant type is Dining Restaurants.
```
```
7. Average Rating by Restaurant Type

avg_rating_by_type = df.groupby('restaurant_type')['rate'].mean().reset_index()
fig_avg_rating = px.bar(avg_rating_by_type, x='restaurant_type', y='rate', title='Average Rating by Restaurant Type', labels={'restaurant_type': 'Restaurant Type', 'rate': 'Average Rating'})
fig_avg_rating.show()

Insights:
There is not much difference in rating by restaurant type. Ratings are in between 3.5 and 3.9.
```
```
8. Average Cost by Restaurant Type

avg_cost_by_type = df.groupby('restaurant_type')['approx_cost'].mean().reset_index()
fig_avg_cost = px.bar(avg_cost_by_type, x='restaurant_type', y='approx_cost', title='Average Cost by Restaurant Type', labels={'restaurant_type': 'Restaurant Type', 'approx_cost': 'Average Cost'})
fig_avg_cost.show()

Insights:
High avg cost is paid by customers who chose restaurant type "Buffet" and "Other".
```
```
9. Do a greater number of restaurants provide online delivery as opposed to offline services?

online_counts = df['online_order'].value_counts().reset_index()
fig_online_delivery = px.pie(online_counts, names='online_order', values='count', title='Online Delivery vs. Offline')
fig_online_delivery.show()

Insights:
Most of the restaurants like to provide "Offline Services".
```
#### Conclusions:

1. Max ratings (30) are received in between 3.8 and 3.9
2. Price 300 paid by most of the people (23)
3. Good ratings (4 to 5) is given by people who paid price between 300 to 850
4. Customers who order online are more likely to provide good ratings
5. Customers who book table are more likely to provide good ratings
6. Most prefered restaurant type is Dining Restaurants
7. There is not much difference in rating by restaurant type. Ratings are in between 3.5 and 3.9
8. High avg cost is paid by customers who chose restaurant type "Dinner" and "Other"
9. Most of the restaurants like to provide "Offline Services"
