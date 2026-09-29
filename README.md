# RFM-Customer-Segmentation-and-Insight-Analysis

Overview

Not every customer is worth the same effort. This project scores 946 customers on how recently they bought, how often they buy and how much they spend, groups them into five actionable segments, and then asks the business questions that follow: who drives revenue, who is about to churn, which products each segment prefers, where and when they buy, and what to bundle.

Business Questions Answered

Analysis

How do you clean the data and calculate Recency, Frequency and Monetary values per customer?
How do quantile-based scores turn raw RFM values into segments?
How are customers and revenue distributed across segments?
What do the Recency, Frequency and Monetary distributions look like?
Which granular RFM segments are the largest?

Strategy

Which customers are at risk of churn and how do you win them back?
What marketing approach fits each segment?
Which products should product development prioritise, based on segment preferences?
Where are the high-value and low-engagement regions?
When do segments buy across months and days of the week?
Which product pairs make the best bundles for each segment?
How can repeat purchases and returns refine the segmentation without direct feedback?
Methodology
Clean the data. Load the dataset with Pandas, check for missing values, and fix data types such as converting purchase dates with pd.to_datetime().
Calculate RFM. Group by CustomerID.
Recency is the days between a customer's last purchase and a reference date, the day after the latest transaction in the dataset.
Frequency is the count of unique transactions.
Monetary is the total spend.
Score with quantiles. Apply qcut() to create scores from 1 to 4. Recency is scored in reverse because fewer days is better. Frequency uses rank(method='first') first to handle the many customers with exactly one purchase.
Build segments. Sum the three scores into an RFM score and map it to a named segment.
Analyse and visualise. Use Seaborn and Matplotlib to explore distribution, revenue, product, geography, seasonality and day-of-week patterns.
Segment Definitions
Segment	RFM score	Profile
Champions	10 and above	Recent, frequent, high spenders
Loyal Customers	8 to 9	Good frequency and spend, relatively recent
Potential Loyalists	6 to 7	Recent buyers with average spend and frequency
At Risk	4 to 5	Have not bought recently
Requires Activation	3	Lowest scores across the board
Key Findings
Customer base and revenue

The base is healthy in the middle: Potential Loyalists (334) and Loyal Customers (304) are the two largest groups, followed by Champions (162), At Risk (130) and Requires Activation (16).

Revenue tells a sharper story. Loyal Customers contribute 36.0% and Champions 27.7%, so the top two tiers generate nearly 64% of sales from well under half the customers. At Risk and Requires Activation together add only about 8%.

At the granular level, segment 244 is the largest with 25 customers, a group that historically buys often and spends a lot but has not purchased very recently.

Product preferences by segment
Product C anchors the high-value tiers, with the most purchases from Champions and Loyal Customers.
Product D peaks among Potential Loyalists at 100 purchases, then falls to 49 among Champions, which points to a gateway product that needs an upgrade path.
Product B is strong with Champions and Loyal Customers but almost absent from Requires Activation.
Product A lags among Champions with 43 purchases.
Geography

Tokyo leads on total revenue, followed by New York and London, with Paris lowest. Comparing each city's segment mix separates high-value hotspots from regions with a heavier share of At Risk customers.

Seasonality and day of week

Loyal Customers and Champions both peak in May, while Potential Loyalists are strongest in April and fade by June. Across all customers, Saturday and Wednesday are the highest revenue days.

Recommendations
Segment	Recommended action
Champions	Reward with VIP perks and early access. Avoid over-discounting. Bundle Product B and Product C as a premium kit.
Loyal Customers	Offer a modest discount on a Product A and Product C bundle to lift order value and move them toward Champions.
Potential Loyalists	Focus cross-sell and upsell here for the fastest revenue growth. Create a clear path from Product D to Product C.
At Risk	Trigger automated win-back emails with personalised recommendations. Add a short feedback survey for high-value lapsed buyers.
Requires Activation	Use low-cost, time-limited offers and retargeting. Cap the spend because the return is lowest.

Timing. Launch campaigns two to three weeks before historical peaks, send exclusive drops the day before a segment's peak day, and use quieter months for At Risk clearance offers.

Model improvement. Add a fourth dimension for engagement, measured as one minus return rate, so frequent buyers who return many items are not over-valued.

Tools Used
Python for the full workflow
Pandas and NumPy for cleaning, aggregation and scoring
Seaborn and Matplotlib for visualisation


Author

Urmila Palwal
