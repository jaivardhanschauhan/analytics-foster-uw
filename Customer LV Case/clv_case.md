## Q1

    df <- data.frame(
      y1_h1 = c(77.99, 22.39, 3.99, 2.995, NA, NA, NA, NA),
      y1_h2 = c(77.99, 22.39, 3.99, 2.995, NA, NA, NA, NA),
      y2_h1 = c(77.99, 22.39, 3.99, 2.995, NA, NA, NA, NA),
      y2_h2 = c(77.99, 22.39, 3.99, 2.995, NA, NA, NA, NA),
      y3_h1 = c(77.99, 22.39, 3.99, 2.995, NA, NA, NA, NA),
      y3_h2 = c(77.99, 22.39, 3.99, 2.995, NA, NA, NA, NA),
      y4_h1 = c(77.99, 22.39, 3.99, 2.995, NA, NA, NA, NA),
      y4_h2 = c(77.99, 22.39, 3.99, 2.995, NA, NA, NA, NA)
    )

    rownames(df) <- c("revenue", "product_cost", "marketing_cost", "delivery_cost",
                      "profit", "customer_staying", "profit_with_attrition", "present_value")

    df["profit", ] <- df["revenue", ] - df["product_cost", ] - df["marketing_cost", ] - df["delivery_cost", ]

    print(df)
    ##                        y1_h1  y1_h2  y2_h1  y2_h2  y3_h1  y3_h2  y4_h1  y4_h2
    ## revenue               77.990 77.990 77.990 77.990 77.990 77.990 77.990 77.990
    ## product_cost          22.390 22.390 22.390 22.390 22.390 22.390 22.390 22.390
    ## marketing_cost         3.990  3.990  3.990  3.990  3.990  3.990  3.990  3.990
    ## delivery_cost          2.995  2.995  2.995  2.995  2.995  2.995  2.995  2.995
    ## profit                48.615 48.615 48.615 48.615 48.615 48.615 48.615 48.615
    ## customer_staying          NA     NA     NA     NA     NA     NA     NA     NA
    ## profit_with_attrition     NA     NA     NA     NA     NA     NA     NA     NA
    ## present_value             NA     NA     NA     NA     NA     NA     NA     NA
    for (t in 1:8) {
      df["customer_staying", t] <- 1 - (0.05 * exp(-0.08 * t))
    }
    df['profit_with_attrition',] <- df['profit',] * df['customer_staying',] 
    for (t in 1:8) {
      df["present_value", t] <- df['profit_with_attrition',t]/((1 + 0.02)^t)
    }
    print(df)
    ##                            y1_h1      y1_h2      y2_h1      y2_h2     y3_h1
    ## revenue               77.9900000 77.9900000 77.9900000 77.9900000 77.990000
    ## product_cost          22.3900000 22.3900000 22.3900000 22.3900000 22.390000
    ## marketing_cost         3.9900000  3.9900000  3.9900000  3.9900000  3.990000
    ## delivery_cost          2.9950000  2.9950000  2.9950000  2.9950000  2.995000
    ## profit                48.6150000 48.6150000 48.6150000 48.6150000 48.615000
    ## customer_staying       0.9538442  0.9573928  0.9606686  0.9636925  0.966484
    ## profit_with_attrition 46.3711349 46.5436515 46.7029043 46.8499132 46.985620
    ## present_value         45.4618970 44.7363048 44.0091898 43.2820780 42.556323
    ##                            y3_h2      y4_h1      y4_h2
    ## revenue               77.9900000 77.9900000 77.9900000
    ## product_cost          22.3900000 22.3900000 22.3900000
    ## marketing_cost         3.9900000  3.9900000  3.9900000
    ## delivery_cost          2.9950000  2.9950000  2.9950000
    ## profit                48.6150000 48.6150000 48.6150000
    ## customer_staying       0.9690608  0.9714395  0.9736354
    ## profit_with_attrition 47.1108923 47.2265336 47.3332839
    ## present_value         41.8331241 41.1135395 40.3985021
    LTV <- sum(df["present_value", ])
    cat("$", format(LTV, nsmall = 2), "\n")                        
    ## $ 343.391

## Q2

    df_case_ii <- data.frame(
      y1_h1 = c(95.99, 22.39, 0, 5.99, NA, NA, NA, NA),
      y1_h2 = c(95.99, 22.39, 0, 5.99, NA, NA, NA, NA),
      y2_h1 = c(95.99, 22.39, 0, 5.99, NA, NA, NA, NA),
      y2_h2 = c(95.99, 22.39, 0, 5.99, NA, NA, NA, NA),
      y3_h1 = c(95.99, 22.39, 0, 5.99, NA, NA, NA, NA),
      y3_h2 = c(95.99, 22.39, 0, 5.99, NA, NA, NA, NA),
      y4_h1 = c(95.99, 22.39, 0, 5.99, NA, NA, NA, NA),
      y4_h2 = c(95.99, 22.39, 0, 5.99, NA, NA, NA, NA)
    )

    rownames(df_case_ii) <- c("revenue", "product_cost", "marketing_cost", "delivery_cost",
                              "profit", "rebuy_probability", "profit_with_rebuy", "present_value")

    df_case_ii["profit", ] <- df_case_ii["revenue", ] - df_case_ii["product_cost", ] - df_case_ii["delivery_cost", ]

    rebuy_probabilities <- seq(0.42, by = -0.03, length.out = 8)
    df_case_ii["rebuy_probability", ] <- rebuy_probabilities

    df_case_ii["profit_with_rebuy", ] <- df_case_ii["profit", ] * df_case_ii["rebuy_probability", ]

    for (t in 1:8) {
      df_case_ii["present_value", t] <- df_case_ii["profit_with_rebuy", t] / (1 + 0.02)^t
    }

    print(df_case_ii)
    ##                      y1_h1   y1_h2    y2_h1    y2_h2    y3_h1    y3_h2    y4_h1
    ## revenue           95.99000 95.9900 95.99000 95.99000 95.99000 95.99000 95.99000
    ## product_cost      22.39000 22.3900 22.39000 22.39000 22.39000 22.39000 22.39000
    ## marketing_cost     0.00000  0.0000  0.00000  0.00000  0.00000  0.00000  0.00000
    ## delivery_cost      5.99000  5.9900  5.99000  5.99000  5.99000  5.99000  5.99000
    ## profit            67.61000 67.6100 67.61000 67.61000 67.61000 67.61000 67.61000
    ## rebuy_probability  0.42000  0.3900  0.36000  0.33000  0.30000  0.27000  0.24000
    ## profit_with_rebuy 28.39620 26.3679 24.33960 22.31130 20.28300 18.25470 16.22640
    ## present_value     27.83941 25.3440 22.93575 20.61219 18.37094 16.20965 14.12606
    ##                      y4_h2
    ## revenue           95.99000
    ## product_cost      22.39000
    ## marketing_cost     0.00000
    ## delivery_cost      5.99000
    ## profit            67.61000
    ## rebuy_probability  0.21000
    ## profit_with_rebuy 14.19810
    ## present_value     12.11794
    total_present_value_case_ii <- sum(df_case_ii["present_value", ])
    cat("Total Present Value (Case II): $", format(total_present_value_case_ii, nsmall = 2), "\n")
    ## Total Present Value (Case II): $ 157.5559

## Q3

    # Function to calculate TPV for subscription case with discount
    # Logic: LTV of subscription case with discount >= LTV of non-subscription case
    # For LTV of subscription case with discount, Adjusted Revenue = Revenue (1 - Discount)

    calculate_tpv_with_discount <- function(discount) {
      # Adjust revenue in the subscription case
      df["revenue", ] <- 77.99 * (1 - discount)
      
      df["profit", ] <- df["revenue", ] - df["product_cost", ] - df["marketing_cost", ] - df["delivery_cost", ]
      
      df["profit_with_attrition", ] <- df["profit", ] * df["customer_staying", ]
      
      for (t in 1:8) {
        df["present_value", t] <- df["profit_with_attrition", t] / (1 + 0.02)^t
      }
      
      return(sum(df["present_value", ], na.rm = TRUE))
    }
    # Binary search to find maximum discount
    # We could also do this with a simple hit and trial and arrive at the discount value 

    lower_bound <- 0
    upper_bound <- 1
    tolerance <- 1e-6

    while ((upper_bound - lower_bound) > tolerance) {
      mid <- (lower_bound + upper_bound) / 2
      tpv_subscription <- calculate_tpv_with_discount(mid)
      
      if (tpv_subscription >= total_present_value_case_ii) {
        lower_bound <- mid # Discount is feasible
      } else {
        upper_bound <- mid # Discount is too high
      }
    }

    # Maximum discount
    max_discount <- lower_bound * 100 # Convert to percentage

    cat("Maximum Discount: ", format(max_discount, nsmall = 2), "%\n")
    ## Maximum Discount:  33.73413 %
    ## Maximum absolute Discount throughout lifetime: 0.33734 * 343.39 = $115.839

## Q4

    avg_ltv <- 0.37 * LTV + 0.63 * total_present_value_case_ii
    print(avg_ltv)
    ## [1] 226.3149

## Q5

The company can attract customers to the subscription service with the
help of:

1.  **Exclusive Benefits**: Offer subscribers perks like early access to
    new products, free delivery, or special add-ons that non-subscribers
    don't get.

2.  **Loyalty Rewards**: Create a points-based system where subscribers
    earn rewards for their purchases, which they can redeem for
    discounts, free items, or premium services.

3.  **Personalized Offers**: Use customer data to send tailored
    recommendations and offers that make subscribers feel valued and
    understood.

4.  **Convenience Features**: Highlight the ease of subscription
    services, such as automatic renewals, hassle-free cancellations, or
    customizable delivery schedules.

5.  **Community Building**: Create a sense of belonging by giving
    subscribers access to an exclusive community, such as discussion
    forums or events related to their interests.

## Q6 

We assumed that revenue, product costs, and delivery costs remain
constant over time for both subscription and non-subscription cases.
However, in reality, these factors are dynamic. Costs may increase due
to inflation, supply chain disruptions, or unexpected inefficiencies,
while revenue might fluctuate based on changes in customer demand,
market trends, or competition. If costs rise faster than revenue or
revenues decline, the subscription model could become significantly less
profitable than anticipated.

Similarly, if churn is higher than expected, the lifetime value of
subscribers will decrease, reducing the profitability of the
subscription model. This could make the non-subscription case more
attractive. Often times, real-world churn rates are influenced by
various factors like customer dissatisfaction, competitors, etc.

Moreover, the rebuy probability in the non-subscription case is modelled
as a linearly decreasing variable over time. This factor is dependent on
promotions, seasonal demand, or personal choices, so this
oversimplification may also result in errors. If the actual rebuy
probability is higher than predicted, the non-subscription model could
outperform the subscription model in terms of total revenue.

Interestingly, we assumed that offering discounts would attract and
retain more customers in the subscription model. However, this may not
hold true if customers are not price-sensitive or if competitors offer
better deals. In such cases, the non-subscription model might become the
more viable option.

Overall, inaccuracies in these assumptions, especially around costs,
customer behavior, and market conditions, could significantly alter the
profitability comparison between the subscription and non-subscription
models.

## Q7

In my opinion, we cannot confidently say that \"offering a subscription
service leads to better profit\". This assignment involved assumptions
and simplified calculations to compare profits from subscription and
non-subscription models. While we analysed the potential outcomes of
these two options, the results are based on theoretical models, not
real-world data. For example, we assumed constant costs, fixed churn
rates, and predictable customer behaviours, but actual customer behavior
can vary significantly.

Causality means we need clear evidence that offering a subscription
service directly causes better profits. Since this assignment doesn't
include real-world testing or controlled experiments, we can only
suggest possibilities, not causality. Offering a subscription might lead
to better profits in some cases, but it depends on how customers respond
and whether the assumptions hold true. Importantly, ensuring external
factors, like market trends or competition, don't skew the results, can
be also quite challenging.
