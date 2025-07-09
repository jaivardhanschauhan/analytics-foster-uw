Q1

![A screenshot of a computer program Description automatically
generated](media/image1.png){width="6.268055555555556in"
height="2.1486111111111112in"}

Q2

![A screenshot of a computer program Description automatically
generated](media/image2.png){width="6.268055555555556in"
height="3.0805555555555557in"}

![A screenshot of a computer Description automatically
generated](media/image3.png){width="6.268055555555556in"
height="2.842361111111111in"}

![A graph of a graph Description automatically
generated](media/image4.jpeg){width="6.147540463692039in"
height="3.7936843832020997in"}

Customers are assigned RFM scores using a 5-quantile method. A score of
1 in R, F, or M indicates the best case (e.g., recent purchase, highest
frequency, or highest monetary value), while 5 indicates the worst case.
This creates 125 unique combinations.

Customers with a R score of 1 have the highest offer used rate, which is
expected as these customers have purchased more recently. We observe a
general incremental trend in the likelihood of the offer acceptance as R
score goes from 5 to 1. The rise is rather steady and we don't see any
unexpected or surprising findings.

![A graph with a bar graph Description automatically
generated](media/image5.jpeg){width="6.268055555555556in"
height="3.8680555555555554in"}

Customers with the best-case frequency, which is 1, have the highest
chances of redeeming the offer. These are the most engaged customers,
and the graph shows that it could be very profitable if these users are
targeted. Moreover, we notice a steep decline in the probability of
offer acceptance as F goes from 1 to 5.

![A graph with a bar graph Description automatically
generated](media/image6.jpeg){width="6.268055555555556in"
height="3.8680555555555554in"}

Likewise, we notice a similar trend in the monetary graph with the best
performing segment as M = 1. It means that customers who have spent the
highest amount are most likely to use the offer.

Q3

![A screenshot of a computer program Description automatically
generated](media/image7.png){width="6.268055555555556in"
height="2.488888888888889in"}

![A graph of a number of rectangular objects Description automatically
generated with medium
confidence](media/image8.jpeg){width="6.196527777777778in"
height="3.823915135608049in"}![A graph of a number of rectangular
objects Description automatically generated with medium
confidence](media/image9.jpeg){width="6.268055555555556in"
height="3.8680555555555554in"}![A graph of a number of rectangular
objects Description automatically
generated](media/image10.jpeg){width="6.268055555555556in"
height="3.8680555555555554in"}

Interestingly, we could say from the above graphs that the normal price
paid is more or less very similar across customer of varying RFM
indices. It means that the customers are likely purchasing items with
similar prices as they use the offer. We also see an exception wherein M
= 5 customers are on and average purchase less costly items with the
offer coupon. The exception is understandable as this segment has the
least purchasing power, historically, in terms of monetary amount.

Q4

![A screenshot of a computer code Description automatically
generated](media/image11.png){width="6.268055555555556in"
height="2.5631944444444446in"}

Q5

![A screenshot of a computer code Description automatically
generated](media/image12.png){width="6.268055555555556in"
height="1.648611111111111in"}

Q6

![A screenshot of a computer code Description automatically
generated](media/image13.png){width="6.268055555555556in"
height="2.2777777777777777in"}

Q7

![A screenshot of a computer program Description automatically
generated](media/image14.png){width="6.268055555555556in"
height="3.2631944444444443in"}

![A screenshot of a computer code Description automatically
generated](media/image15.png){width="6.268055555555556in"
height="1.5756944444444445in"}

![A screenshot of a computer Description automatically
generated](media/image16.png){width="4.175666010498688in"
height="3.6856124234470693in"}

In the previous case, we were sending offer coupons to Sephora's entire
customer base and wasting a lot of money on people who were not likely
to respond to the offer. RFM analysis is based on the principle of
reducing these costs and increasing the overall profitability of the
marketing campaign. After RFM, we only target customers who are above
the breakeven rate, and hence significantly decrease campaign costs. The
target_customer_share is the corresponding share of customers we want to
target. We can see the Return on Marketing cost has significantly jumped
from 27.83% to 396.28% while the profits have increased to \$39861567.

Q8

![A screenshot of a computer Description automatically
generated](media/image17.png){width="6.268055555555556in"
height="3.463888888888889in"}

![](media/image18.png){width="6.268055555555556in"
height="0.6034722222222222in"}

![A screenshot of a spreadsheet Description automatically
generated](media/image19.png){width="6.268055555555556in"
height="1.2958333333333334in"}

Lift is based on comparing the response rate within each quantile to the
overall average response rate. Higher lift values are observed in top
quantiles. Whereas, gain measures the cumulative percentage of total
responses captured as more quantiles are included.

Life curve steeply declines after the top quantile, showing that the
highest-probability segments drive most of the response. Gain curve
demonstrates that a small portion of high-value customers account for
the majority of responses.

Both Lift and gain analyses confirm that targeting lower performing
quantiles adds minimal value while incurring higher costs.

Q9

**Shortcomings**:

- Equal RFM Weighting: We have treated R, F, and M as equally important.
  Now this is oversimplifying customer behavior. Some metrics might hold
  greater predictive power.

- Static Customer Behavior: Assumes that RFM scores and response
  probabilities remain constant, ignoring seasonal changes.

- Fixed Marginal Costs: Also assumed a static cost of annoyance, which
  may vary based on email content or campaign frequency.

**Assumptions**:

- Uniform Revenue Margins: Assuming the same profit margin (24%) across
  all purchases may not account for product-specific variability.

- Predictive Accuracy: Relies on historical behavior as a perfect
  predictor of future actions, which may not account for evolving
  preferences.

- Exclusion Effects: Ignores potential alienation of lower RFM segments
  who might still respond positively under certain conditions.

**Conclusion:** While the analysis provides actionable insights, adding
dynamic RFM weighting, temporal behavior changes, or campaign-specific
variations would improve accuracy in real-world scenarios.
