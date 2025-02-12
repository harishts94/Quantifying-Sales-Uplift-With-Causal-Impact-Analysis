# Quantifying-Sales-Uplift-With-Causal-Impact-Analysis

## Project Overview
### Context
Earlier in the year, our client, a grocery retailer, ran a campaign to promote their new “Delivery Club” - an initiative that costs a customer $100 per year for membership, but offers free grocery deliveries rather than the normal cost of $10 per delivery.

They want to understand if customers who did join the club have increased their spend in the three months following. The hypothesis is that, if customers are not paying for deliveries, they will be tempted to shop more frequently, and hopefully purchase more each time.

The aim of this work is to understand and quantify the uplift in sales for customers that joined the club, over and above what they would have spent had the club not come into existence!

### Actions
We applied Causal Impact Analysis (see full details below) using the pycausalimpact library.

In the client database, we have a campaign_data table which shows us which customers received each type of “Delivery Club” mailer, which customers were in the control group, and which customers joined the club as a result.

Since Delivery Club membership was open to all customers - the control group we have in the campaign_data table would help us measure the impact of contacting customers but here, we are actually look to measure the overall impact on sales from the Delivery Club itself. Because of this, we instead used customers who did not sign up as the control. The hypothesis was that customers who did not sign up should continue their normal shopping habits after the club went live, and this will help us create the counter-factual for the customers that did sign-up.

Sales data was from the transactions table and was aggregated from a customer/transaction/product area level to customer/date level as per the requirements of the algorithm.

We used a 3 months pre-period for the algorithm to model, 3 months post-period for the counterfactual.

### Results
We saw a 41.1% uplift in sales for those customers that joined the Delivery Club, over and above what we believe they would have spent, had the club not been in existence. This was across the three month post-period, and the uplift was deemed to be significantly significant (@ 95%).
