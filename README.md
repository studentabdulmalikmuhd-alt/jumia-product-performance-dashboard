**Jumia Product Performance Dashboard**
An interactive Excel dashboard that analyses how pricing, discounts and customer ratings relate to customer engagement (reviews) for Jumia home, kitchen and tools listings.
Project brief: DSEAfrica Data Lab, Excel project (Retail, Beginner). Role: Data Analyst, Jumia marketplace team. Tools: Microsoft Excel (formulas, Tables, PivotTables, PivotCharts, Slicers, Conditional Formatting).
**1. Business problem
Jumia and its sellers set prices and discounts without evidence on whether those choices change customer engagement. Nobody can currently say:
• Do bigger discounts bring more reviews?
• Do well-rated products cost more or less than the rest?
• Which listings are performing well, and which need a different pricing or marketing approach?
Decisions this dashboard supports
Decision
Question the dashboard answers
How deep should a discount be?
Does discount % relate to reviews or ratings?
Where to invest in promotion?
Which products have strong demand, and which have heavy discounts but no engagement?
Which listings need attention?
Which products are low-rated or high-discount with poor feedback?
#2. Dataset
A raw export of 115 Jumia listings with six columns, deliberately messy:
Column
Raw format
Problem
Product
text
Some titles repeat (duplicates)
Current price
text, e.g. KSh 1,525
Currency prefix, thousands separator, and one price range
old price
text
Same as above
Discount
text, e.g. 25%
Stored as text
Review
integer
Stored as negative numbers; 58 blanks
Ratingd
text, e.g. 4.5 out of 5
Misspelt header; text; 58 blanks
#3. Repository contents
• JUMIA_PRODUCT_DASHBOARD.xlsx: raw data, cleaned data, pivot tables, dashboard
• README.md: this document
• images/: screenshots of each stage
Workbook sheets
Sheet
Purpose
Excel_jumia_dataset
Untouched raw export
data_cleared
Cleaned and enriched Excel Table (Table1)
analyzed
PivotTables behind the charts and KPIs
DASHBOARD
Final interactive dashboard with charts and slicers
#4. Data cleaning
The raw sheet was kept untouched; all work was done on a copy.
Step
Issue found
Action
Duplicates
3 exact duplicate rows (identical on all six columns)
Confirmed by matching every column, then removed. 115 to 112 unique listings
Prices
KSh prefix and commas in text
Stripped prefix and separators; converted to numbers
Price range
1 listing (a sofa cover) showed KSh 1,620 - KSh 1,980 / KSh 2,200 - KSh 3,200
Used the upper bound (1,980 / 3,200) so the range is a single comparable value. This slightly overstates that product's price
Discount
Text such as 38%
Converted to a numeric fraction (0.38)
Reviews
Stored negative
Converted to positive whole numbers
Missing reviews
58 blanks (55 after removing duplicates)
Set to 0 reviews: a listing with no reviews has zero reviews
Ratings
4.5 out of 5 text
Extracted the number. Blank ratings are not treated as a score of 0: they mean "no rating yet" and are excluded from rating averages
Header
Ratingd misspelt
Renamed to Rating
Validation
Discount amount vs discount %
Recomputed (old - current) / old; matches the listed discount within 0.5 percentage points (rounding) for every row
5. Data enrichment
New column
Rule
Discount Amount
Old price minus Current price (KSh)
Rating category
Poor: below 3. Average: 3 to 4.5. Excellent: above 4.5. No rating: blank
Discount category
Low: below 20%. Medium: 20% to 40%. High: above 40%
Price category
Budget: under KSh 1,000. Mid-range: KSh 1,000 to 2,000. Premium: over KSh 2,000
Decisions on thresholds
• Gap between 4 and 4.5: the brief leaves it undefined. Everything from 3 up to and including 4.5 is Average, and only ratings above 4.5 are Excellent. This keeps three exhaustive bands with no gaps.
• Price bands: chosen around the data's own spread (median about KSh 990, 75th percentile about KSh 1,660, maximum KSh 3,750). Under 1,000 is the cheaper half of the catalogue, 1,000 to 2,000 is the mid-priced core, and over 2,000 isolates the top tier of 17 listings.
• Products without ratings get their own category rather than being forced into Poor.
6. Descriptive statistics
After cleaning (112 unique listings):
Metric
Value
Total products
112
Total reviews
723
Average reviews per product
6.5 (median 1)
Average current price
KSh 1,189
Average old price
KSh 1,816
Average discount
36.8%
Average discount amount
about KSh 626
Products with at least one rating
57 (55 have none)
Average rating (rated products only)
3.89 / 5
Most expensive
32PCS Portable Cordless Drill Set, KSh 3,750
Least expensive
3PCS Single Head Knitting Crochet Sweater Needle Set, KSh 38
Category counts
Band
Count
Discount: High / Medium / Low
62 / 32 / 18
Price: Budget / Mid-range / Premium
57 / 38 / 17
Rating: Excellent / Average / Poor / No rating
19 / 26 / 12 / 55
7. Analysis and key findings
Do higher discounts lead to more reviews? No.
• Correlation between discount % and reviews is 0.01, which is effectively zero.
• High-discount listings (over 40%) average only 5.4 reviews, versus 11.0 for medium discounts (20% to 40%).
• 32 of the 62 high-discount listings have no reviews at all.
Do highly rated products get more reviews? Only weakly.
• Among rated products, correlation between rating and reviews is 0.06.
• Excellent products average 15.2 reviews, but Poor products average 14.1: popular products collect reviews good or bad.
Are expensive products rated higher? No clear link.
• Correlation between price and rating is 0.11 (very weak).
• Average rating is similar across bands: Budget 3.83, Mid-range 3.99, Premium 3.88.
Do discounts relate to ratings?
• Weak negative correlation of -0.19: deeper discounts do not buy better feedback.
• Deeper discounts sit on cheaper items (price vs discount correlation -0.54).
Top performers
Top by reviews
Product
Reviews
Rating
Discount
120W Cordless Vacuum Cleaners Handheld Electric
69
2.8
49%
137 Pieces Cake Decorating Tool Set
55
4.6
24%
Electronic Digital Display Vernier Caliper
49
4.6
35%
3D Waterproof EVA Plastic Shower Curtain
44
4.6
49%
100 Pcs Crochet Hook Tool Set
39
4.7
34%
The top five listings alone hold 256 of 723 reviews (35%): engagement is highly concentrated.
Top by discount: led by the 6 In 1 Bottle Can Opener (64%), Creative Owl Shape Keychain (61%) and the LASA Folding Table Serving Stand (55%). Both of the top two have zero reviews.
Lowest rated: Wall-mounted Sticker Punch-free Plug Fixer (2.0), 5-PCS Stainless Steel Cooking Pot Set (2.1), Electric LED UV Mosquito Killer Lamp (2.1), Artificial Potted Flowers (2.2), 7-piece Storage Bags Set (2.2).
Several products rated 5.0 have only 1 to 3 reviews, so the top-rated list is not reliable on its own. Rating should be read together with review count.
Flagged outliers
• High discount, low rating: 10 listings discounted over 40% with ratings under 3 (e.g. the Stainless Steel Cooking Pot Set: 55% off, rated 2.1).
• High discount, no engagement: 32 listings discounted over 40% with zero reviews.
• High demand, poor rating: the 120W Cordless Vacuum Cleaner has the most reviews (69) yet a rating of only 2.8.
• Strong demand and strong ratings: Vernier Caliper (49 reviews, 4.6), Shower Curtain (44, 4.6), Cake Decorating Set (55, 4.6).
8. The dashboard
The DASHBOARD sheet is organised in four sections:
1. KPIs: total products, average price, average discount, average rating, total reviews.
2. Product performance: top-10 tables by discount, reviews and rating, plus the 5 lowest rated.
3. Trends: charts for discount vs reviews, rating vs reviews, and price vs rating.
4. Categories: breakdown by rating band and discount band.
Interactivity: slicers for Rating category, Discount category and Price category; conditional formatting highlights extremes.
9. Business insights
1. Discount depth is not driving engagement. Reviews are essentially uncorrelated with discount %, and the deepest discounts often sit on listings nobody has reviewed.
2. Price does not predict quality perception. Ratings are flat across Budget, Mid-range and Premium bands.
3. Engagement is concentrated. A handful of listings (top 5 = 35% of all reviews) carry most of the customer feedback; about half the catalogue has no ratings at all.
4. Demand and satisfaction can diverge. The top listing by reviews, the vacuum cleaner, is rated 2.8: a quality issue hiding behind popularity.
5. Medium discounts perform best. The 20% to 40% band averages the most reviews per listing (11.0) at the highest average rating (4.28).
10. Recommendations
1. Stop using discount depth alone as a growth lever. Discounts over 40% average 5.4 reviews versus 11.0 at 20% to 40%, and 32 of 62 deep-discount listings have no reviews. Sellers should test moderate discounts (20% to 40%) and pair them with visibility tactics.
2. Prioritise getting first reviews on unrated listings. 55 of 112 listings (49%) have no rating. Follow-up review requests and bundling with proven sellers would help more than extra price cuts.
3. Fix or rework high-demand, low-rating and high-discount, low-rating products. The 120W Cordless Vacuum (69 reviews, 2.8) and the 10 listings that are over 40% off but under 3 stars need quality or listing-content fixes before more promotion.
Supporting figures: Sections 6 and 7.
11. Limitations
• Small sample: 112 listings from one category group; results may not generalise to all of Jumia.
• Reviews are a proxy for engagement. Sales volume and views are not in the data.
• Half the products have no rating, so rating-based findings rest on 57 listings.
• Correlation is not causation.
• One price range was reduced to its upper bound.
• Snapshot in time: no dates, so true trends over time are not possible; the trend charts show relationships between variables.
12. How to use the workbook
1. Open JUMIA_PRODUCT_DASHBOARD.xlsx in desktop Excel (slicers need Excel 2013 or later).
2. Go to the DASHBOARD sheet.
3. Click the Rating, Discount or Price slicer buttons to filter. Hold Ctrl to select several; use the funnel-clear icon to reset.
4. To refresh after editing data_cleared, use Data, then Refresh All.
13. Links
• Dev.to article: Building an Interactive Excel Dashboard for E-commerce Product Analysis: A Case Study of Jumia Products (add link)
• GitHub repository: https://github.com/studentabdulmalikmuhd-alt/jumia-product-performance-dashboard
Dataset and brief: DSEAfrica Data Lab. Author: abdulmalik muhammad
