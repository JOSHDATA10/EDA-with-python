# E-commerce Sales EDA with Python

This repository contains an exploratory data analysis (EDA) project for an e-commerce sales store. The project aims to provide insights into sales, customer behaviors, and profitability trends.

## Dataset
The dataset includes:
- **Customer Information**: Names and purchase categories
- **Sales Metrics**: Sales amount, quantity, discount, and profit
- **Categorical Information**: Category and sub-category of purchased items

The dataset is stored in the `data/` directory.

## Analysis Objectives
- Summarize sales performance by category, sub-category, and customer.
- Identify the top-performing customers based on sales, quantity, and profit.
- Visualize sales distribution across categories and sub-categories.

## Repository Structure
- `data/`: Contains the input dataset.
- `notebooks/`: Includes Jupyter notebooks with Python code for EDA.
- `visuals/`: Stores generated plots and figures.
- `README.md`: Project documentation.
- `requirements.txt`: Python dependencies.

## Visualizations
- Countplot of categories with sub-category distributions.
- Summary tables for top 10 customers by sales, quantity, and profit.

## Prerequisites
- Python 3.8+
- Jupyter Notebook
- Libraries: `pandas`, `numpy`, `seaborn`, `matplotlib`, `openpyxl`

### Python Code
```
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
%matplotlib inline
sales= pd.read_excel(r"C:\Users\USER\Documents\Ecommerce_Sales_Data.xlsx")
sales.head()
cust = sales[['Customer Name','Category','Sub-Category','Sales','Quantity','Discount','Profit']]
Category = cust.groupby('Category').sum('Sales')
plt.style.use('dark_background')
sns.countplot(x='Category',data = cust,hue = 'Sub-Category')
Money = sales[['Customer Name','Category','Sales','Quantity','Discount','Profit']]
Category = cust.groupby('Category')[['Sales', 'Quantity', 'Profit']].sum()
Customer_Name = cust.groupby('Customer Name')[['Sales','Quantity','Profit']].sum()
Customer_Name
# Group by 'Customer Name' and sum 'Sales', 'Quantity', and 'Profit'
Customer_Name = cust.groupby('Customer Name')[['Sales', 'Quantity', 'Profit']].sum()

# Get the top 10 customers by Sales
top_10_sales = Customer_Name.sort_values(by='Sales', ascending=False).head(10)

# Get the top 10 customers by Quantity
top_10_quantity = Customer_Name.sort_values(by='Quantity', ascending=False).head(10)

# Get the top 10 customers by Profit
top_10_profit = Customer_Name.sort_values(by='Profit', ascending=False).head(10)

# Display the top 10 by Sales as an example
print(top_10_sales) ```

