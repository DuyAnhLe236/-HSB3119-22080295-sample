#Tile
Welcome to Duy Anh's website

##Heading 1
Python

###Heading 2
My picture 

![](images/2191845e-9fbb-4c3e-83d6-b887bd9e7689 (1).jpg)

# A first-level heading
a
## A second-level heading
b
c
### A third-level heading
d

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
df = pd.read_csv('/content/Details.csv')

# Display the first few rows of the dataset
print("Initial Dataset:")
print(df.head())



# 2. Visualization and Discussion

# Chart 1: Sales by Category
sales_by_category = df.groupby('Category')['Amount'].sum().reset_index()

plt.figure(figsize=(10, 6))
plt.bar(sales_by_category['Category'], sales_by_category['Amount'], color='skyblue')
plt.title('Total Sales by Product Category')
plt.xlabel('Product Category')
plt.ylabel('Total Sales Amount')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# Discussion for Chart 1
highest_sales_category = sales_by_category.loc[sales_by_category['Amount'].idxmax()]
print(f"Category with highest sales: {highest_sales_category['Category']} - ${highest_sales_category['Amount']}")

# Chart 2: Sales by Payment Method
sales_by_payment = df.groupby('PaymentMode')['Amount'].sum().reset_index()

plt.figure(figsize=(10, 6))
plt.bar(sales_by_payment['PaymentMode'], sales_by_payment['Amount'], color='lightgreen')
plt.title('Total Sales by Payment Method')
plt.xlabel('Payment Method')
plt.ylabel('Total Sales Amount')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# Discussion for Chart 2
most_popular_payment = sales_by_payment.loc[sales_by_payment['Amount'].idxmax()]
print(f"Most popular payment method: {most_popular_payment['PaymentMode']} - ${most_popular_payment['Amount']}")

# Chart 3: Quantity Sold by Sub-Category
subcategory_quantity = df.groupby('Sub-Category')['Quantity'].sum().reset_index()
plt.figure(figsize=(12, 6))
sns.barplot(x='Sub-Category', y='Quantity', data=subcategory_quantity)
plt.title('Quantity Sold by Sub-Category')
plt.xlabel('Sub-Category')
plt.ylabel('Total Quantity Sold')
plt.xticks(rotation=45)
plt.show()

# Chart 4: Average Profit by Category
category_profit = df.groupby('Category')['Profit'].mean().reset_index()
plt.figure(figsize=(10, 6))
sns.barplot(x='Category', y='Profit', data=category_profit)
plt.title('Average Profit by Category')
plt.xlabel('Category')
plt.ylabel('Average Profit')
plt.xticks(rotation=45)
plt.show()

# Chart 5: Profit Margin by Sub-Category
df['Profit Margin'] = df['Profit'] / df['Amount']
subcategory_profit_margin = df.groupby('Sub-Category')['Profit Margin'].mean().reset_index()
plt.figure(figsize=(12, 6))
sns.barplot(x='Sub-Category', y='Profit Margin', data=subcategory_profit_margin)
plt.title('Average Profit Margin by Sub-Category')
plt.xlabel('Sub-Category')
plt.ylabel('Average Profit Margin')
plt.xticks(rotation=45)
plt.show()

# Discussion:
# - Identify sub-categories with the highest profit margins.
# - Focus on high-margin sub-categories for profitability.
# Discussion:
# - Determine which sub-categories are the most popular.
# - Helps in inventory management and deciding which products to stock more.


# Optional: Save the cleaned DataFrame to a new CSV
df.to_csv('cleaned_online_sales_data.csv', index=False)

# Note: Ensure to install required packages if you haven't done so:
# pip install pandas matplotlib
## Online Sales Data Analysis Report


