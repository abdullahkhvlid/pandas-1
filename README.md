📊 Superstore Data Analysis with Pandas & NumPy
This project dives into structured analytics on the Superstore dataset, showcasing practical data wrangling and exploratory operations using Pandas and NumPy.

We cover grouped aggregations, column transformations, conditional logic, and business-specific metrics like CV (coefficient of variation) and discount analysis — all using clean, efficient Python code.

🔍 Problem Statements Solved
1️⃣ Total Sales and Average Quantity per Region
How much is each region contributing in sales and what’s their average order quantity?

python
Copy
Edit
df.groupby("region").agg(
    total_sales=("sales", "sum"),
    avg_quantity=("quantity", "mean")
)
2️⃣ Standard Deviation & CV of Sales by Category
Which categories are more volatile in terms of sales?

python
Copy
Edit
df.groupby("category").agg(
    std=("sales", "std"),
    cv=("sales", lambda x: (x.std() / x.mean()) * 100)
)
3️⃣ High Discount Flag Based on Segment-Wise Average
For each segment, mark rows where the discount offered is higher than the average discount in that segment.

python
Copy
Edit
df["high_discount"] = df["discount"] > df.groupby("segment")["discount"].transform("mean")
4️⃣ Filter Sub-Categories with Sales > 1000
Only keep rows where sub-category total sales are greater than 1000.

python
Copy
Edit
df[df.groupby("sub-category")["sales"].transform("sum") > 1000]
🧠 Key Concepts Used
groupby() with named aggregations

transform() for row-wise group logic

Lambda functions in aggregations

Conditional column creation

Row-level filtering using group-wise calculations

Coefficient of Variation (CV) as a normalized volatility metric

📁 Dataset
Source: Superstore Dataset CSV

Cleaned by replacing spaces in column names with underscores and converting to lowercase.

🛠️ Technologies
Python 3.8+

Pandas

NumPy

🚀 How to Run
bash
Copy
Edit
pip install pandas numpy
python your_script_name.py
📈 Output Samples
Table of region-wise sales

CV heatmap of categories (optional)

Boolean column for high_discount

Filtered sub-categories with strong revenue

💡 Extensions You Can Build
Visualizations with Matplotlib or Seaborn

Export filtered DataFrames to CSV

Build a Streamlit dashboard

Add price elasticity or margin analysis
