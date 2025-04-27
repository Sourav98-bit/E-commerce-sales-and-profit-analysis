# E-commerce-sales-and-profit-analysis
## Project Overview
This project analyzes sales and profit data from a sample superstore to uncover trends, patterns, and business insights. The analysis covers multiple dimensions including time-based trends, product categories, customer segments, and profitability metrics.

## Data Description
The dataset contains 4,578 records with 21 columns including:
- Order details (ID, date, ship mode)
- Customer information (ID, name, segment)
- Geographic data (country, city, postal code, region)
- Product information (category, sub-category, product name)
- Financial metrics (sales, quantity, discount, profit)

## Analysis and Visualizations

### 1. Yearly Sales Analysis
*Key Findings:*
- Sales increased from $266,166 in 2014 to $340,403 in 2017
- Significant growth in 2017 compared to previous years

*Visualization:* Bar chart showing total sales by year

### 2. Monthly Sales Trends
*Key Findings:*
- Highest sales months: November ($164,482) and September ($149,513)
- Lowest sales month: February ($19,465)

*Visualization:* Interactive line chart showing monthly sales patterns

### 3. Sales by Product Category
*Key Findings:*
- Technology products generated highest sales ($406,939)
- Furniture and Office Supplies had similar sales (~$330,000 each)
- Technology accounted for 38% of total sales

*Visualization:* Pie chart showing sales distribution by category

### 4. Sales by Sub-Category
*Key Findings:*
- Top performing sub-categories: Phones ($158,592), Chairs ($149,947), Storage ($105,661)
- Lowest performing: Fasteners ($1,563), Labels ($5,806), Envelopes ($8,129)

*Visualization:* Interactive pie chart with all sub-categories

### 5. Profitability Analysis
#### By Month:
*Key Findings:*
- Most profitable months: March ($12,930), May ($11,651)
- Least profitable months: February ($2,841), April ($3,097)

*Visualization:* Bar chart showing monthly profits

#### By Category:
*Key Findings:*
- Technology most profitable ($58,012)
- Office Supplies ($54,078) significantly more profitable than Furniture ($7,910)
- Furniture has much lower profit margins despite similar sales to Office Supplies

*Visualization:* Bar chart comparing category profits

### 6. Segment Performance
*Key Findings:*
- Consumer segment generates highest sales ($539,090) and profits ($64,942)
- Home Office has smallest sales volume but decent profitability
- Corporate segment shows lowest sales-to-profit ratio (9.69 vs 8.42 for Consumers)

*Visualization:* Grouped bar chart showing sales and profit by segment

## Key Insights and Recommendations

1. *Seasonal Trends:*
   - Capitalize on strong November/December performance with targeted promotions
   - Investigate reasons for February slump and develop strategies to boost sales

2. *Product Performance:*
   - Focus on high-profit Technology products, especially Phones
   - Review Furniture category profitability - potential pricing or cost issues
   - Consider reducing inventory of low-performing sub-categories (Fasteners, Labels)

3. *Customer Segments:*
   - Consumer segment is most valuable - enhance loyalty programs
   - Corporate segment shows room for profit improvement
   - Home Office segment has good potential for growth

4. *Operational Improvements:*
   - Analyze why March and May are most profitable months to replicate success
   - Investigate Furniture category's poor profit performance
   - Optimize inventory based on seasonal and category trends

## Technical Implementation

python
# Key code snippets from analysis:

# Data Preparation
data['Order Date'] = pd.to_datetime(data['Order Date'])
data['Order Month'] = data['Order Date'].dt.month
data['Order Year'] = data['Order Date'].dt.year

# Yearly Sales Analysis
yearly_sales = data.groupby('Order Year')['Sales'].sum().reset_index()
px.bar(yearly_sales, x='Order Year', y='Sales', title='Yearly Sales Analysis')

# Category Analysis
sales_by_category = data.groupby('Category')['Sales'].sum().reset_index()
px.pie(sales_by_category, values='Sales', names='Category', 
       title='Sales Distribution by Category')

# Profit Analysis
profit_by_category = data.groupby('Category')['Profit'].sum().reset_index()
px.bar(profit_by_category, x='Category', y='Profit', 
       title='Category-wise Profit Analysis')

# Segment Analysis
sales_profit_by_segment = data.groupby('Segment').agg({'Profit':'sum', 'Sales':'sum'}).reset_index()
px.bar(sales_profit_by_segment, x='Segment', y=['Profit', 'Sales'],
       title='Sales and Profit by Segment', barmode='group')


## Conclusion
This comprehensive analysis reveals significant opportunities to optimize product mix, pricing strategies, and marketing efforts. The visualizations clearly highlight seasonal patterns, profitable product categories, and customer segment performance that can inform data-driven business decisions.
