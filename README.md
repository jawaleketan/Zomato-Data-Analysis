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

Step 1: Importing necessary Python libraries

import pandas as pd
import numpy as np
import plotly.express as px
import plotly.graph_objects as go

Step 2: Creating the data frame

df = pd.read_csv('Zomato-data-.csv')

Step 3: Understanding the data

df.info()

df.describe()

