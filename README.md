# Jumia Product Performance Dashboard

## 1. Project Overview

The **Jumia Product Performance Dashboard** is an interactive Microsoft Excel project developed as part of the DSEAfrica Data Lab project series.

The project analyzes Jumia home, kitchen, and tools product listings to explore how product prices, discounts, customer ratings, and review counts relate to product performance and customer engagement.

The goal is to transform raw e-commerce data into a clean, structured, and interactive dashboard that helps Jumia sellers explore product performance and make more informed pricing and promotional decisions.

## 2. Business Problem

Jumia sellers need to understand whether their pricing and discount strategies are associated with customer engagement and product ratings.

This project explores questions such as:

- Do products with higher discounts receive more customer reviews?
- Do highly rated products receive more reviews?
- Are more expensive products rated higher than less expensive products?
- Which products have the highest ratings, review counts, and discounts?
- Which products may require further pricing or marketing attention?

## 3. Project Objectives

- Clean and standardize the raw product dataset.
- Identify and handle duplicate records and missing values.
- Convert price, discount, review, and rating fields into usable numeric values.
- Create calculated columns for discount amounts and product categories.
- Calculate descriptive statistics and compare product performance.
- Analyze relationships between discounts, ratings, prices, and reviews.
- Build an interactive Excel dashboard with KPIs, charts, tables, and slicers.
- Develop actionable recommendations supported by the analysis.

## 4. Tools and Technologies

- Microsoft Excel
- Excel formulas and calculated columns
- PivotTables and PivotCharts
- Excel charts and slicers
- Conditional formatting
- Data cleaning and exploratory data analysis
- GitHub for project documentation and version control

## 5. Dataset Description

The original dataset contains 115 Jumia product listings across home, kitchen, and tools categories.

The dataset includes six main fields:

- Product name
- Current price
- Old price
- Discount percentage
- Number of reviews
- Product rating

The raw export contains data-quality issues, including currency-formatted prices, some price ranges, negative review counts, text-formatted ratings, missing values, and duplicate records.

## 6. Data Cleaning and Preparation

The raw dataset was preserved, and a separate cleaned dataset was prepared for analysis.

The cleaning workflow included:

- Checking for missing values and duplicate records.
- Reviewing duplicate rows before removing confirmed duplicates.
- Standardizing currency prefixes and thousands separators in price fields.
- Reviewing price ranges and documenting the approach used to convert them into numeric values.
- Converting discount percentages into numeric values.
- Converting negative review counts into positive whole numbers where appropriate.
- Extracting numeric ratings from text such as "4.5 out of 5".
- Recording cleaning decisions and retaining the original raw data for reference.

**Data integrity note:** Price ranges, missing values, and records without ratings should be handled consistently and documented rather than silently removed or replaced.

## 7. Data Enrichment

The analysis includes calculated fields designed to make product comparisons easier.

- **Discount Amount:** Old Price minus Current Price.
- **Rating Category:** Groups products according to their rating.
- **Discount Category:** Groups discounts into Low, Medium, and High bands.
- **Price Category:** Groups products into price bands using documented thresholds.

The rating and discount category boundaries should be applied consistently. Any rating values that fall between the categories defined in the project brief should be handled explicitly.

## 8. Descriptive and Comparative Analysis

The project examines the following measures:

- Total number of products.
- Average current price.
- Average old price.
- Average discount percentage.
- Average product rating.
- Total customer reviews.
- Most and least expensive products.

Product comparisons also include:

- Top 10 products by discount percentage.
- Top 10 products by review count.
- Top 10 products by rating.
- Five lowest-rated products.
- Products with high discounts and relatively low ratings or engagement.

## 9. Interactive Dashboard Features

The Excel dashboard is designed to help users explore product performance through:

- KPI cards summarizing key metrics.
- Product performance tables.
- Charts comparing discounts, ratings, reviews, and prices.
- Rating and discount category breakdowns.
- Interactive slicers for rating category, discount category, and price category.
- Conditional formatting to highlight important values and potential outliers.

The dashboard supports exploratory analysis and helps users compare products across different segments.

## 10. Business Insights and Recommendations

The analysis is intended to help answer the following business questions:

- How are discount percentages associated with customer review counts?
- How do ratings compare across different price levels?
- Which products combine strong ratings with high review activity?
- Which heavily discounted products may require further investigation?
- Which products might benefit from a closer review of their pricing or promotional strategy?

Recommendations should be based on the actual results, charts, and calculated metrics from the workbook.

A discount or review-count relationship should not automatically be interpreted as proof of causation. Review counts can also be influenced by product age, visibility, popularity, and other factors not included in the dataset.

## 11. Repository Contents

- `JUMIA_PRODUCT_DASHBOARD.xlsx` — Excel workbook containing the raw data, cleaned data, analysis, and dashboard.
- `README.md` — Project documentation.
- `clearing_data.png` — Data-cleaning screenshot.
- `dashboard.png` — Final dashboard screenshot.

## 12. How to Explore the Project

1. Download the Excel workbook from this repository.
2. Open it using Microsoft Excel.
3. Review the raw and cleaned data sheets.
4. Explore the analysis tables, PivotTables, and charts.
5. Open the dashboard sheet and use the available slicers to filter the results.

## 13. Learning Outcomes

This project provided practical experience in data cleaning, numeric data transformation, calculated columns, PivotTables, PivotCharts, interactive dashboard design, and communicating business questions through data visualization.

It also reinforced the importance of documenting data-quality decisions and supporting recommendations with evidence.

## 14. Project Information

**Project:** Jumia Product Performance Dashboard  
**Role:** Data Analyst — simulated Jumia marketplace team  
**Level:** Beginner  
**Industry:** E-commerce and Retail Analytics  
**Tools:** Microsoft Excel  
**Project Platform:** DSEAfrica Data Lab

## Conclusion

The Jumia Product Performance Dashboard demonstrates how spreadsheet-based analysis and visualization can help transform raw e-commerce listings into a more structured view of product performance.

By exploring pricing, discounts, ratings, and customer reviews together, the project provides a foundation for evidence-based product comparisons and further investigation of seller pricing strategies.
