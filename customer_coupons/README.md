# Will a customer accept the coupon?

### Data Cleaning and Preparation

To ensure the dataset was ready for analysis, the following steps were taken:

1. **Dropped Columns with Excessive Missing Values**:
    - The `car` column was dropped because it contained over 12,000 missing values, making it unsuitable for analysis.

2. **Renamed Columns for Clarity**:
    - The column `passanger` was renamed to `passenger` to correct a spelling mistake.

3. **Filled Missing Values**:
    - The columns `CoffeeHouse`, `CarryAway`, `RestaurantLessThan20`, and `Restaurant20To50` had missing values filled with the mode (`'never'`) to ensure consistency and avoid data loss.

   ```python
   # Fill missing values
   columns_to_fill = ['CoffeeHouse', 'CarryAway', 'RestaurantLessThan20', 'Restaurant20To50']
   for col in columns_to_fill:
       data[col] = data[col].fillna('never')
   ```

These steps helped standardize the dataset and improve its suitability for deriving meaningful insights.

### Proportion of Coupons Accepted

To determine how many observations chose to accept the coupon, we calculated the total number of coupons and the proportion of accepted coupons:

- **Total Coupons**: 12684
- **Proportion of Accepted Coupons**: **56.84%**

This shows that over half of the observations chose to accept the coupon, indicating a strong overall interest in the coupon offers.

---

### Coupon Categories and Acceptance Rates

To understand how different categories of coupons were accepted, the following breakdown was observed:

| Coupon Category            | Accepted Count |
|----------------------------|----------------|
| Coffee House               | 1995           |
| Restaurant (<20)           | 1970           |
| Carry out & Take away      | 1760           |
| Bar                        | 827            |
| Restaurant (20-50)         | 658            |

The data indicates that Coffee House and Restaurant (<20) coupons were the most accepted categories, while Bar and Restaurant (20-50) had comparatively lower acceptance counts.


### Bar Key Observations Recap

1. **Proportion of Bar Coupons Accepted**:
    - **Total Bar Coupons**: 2017
    - **Accepted Coupons**: 827
    - **Proportion Accepted**: **41.00%**

2. **Acceptance by Frequency of Visits**:
    - Drivers who visited a bar 3 or fewer times a month had an acceptance rate of **25.29%** (510 accepted).
    - Drivers who visited more than 3 times a month had a significantly lower acceptance rate of **7.59%** (153 accepted).

3. **Acceptance by Frequency and Age**:
    - **Frequent bar-goers over 25** had an acceptance rate of **14.48%** (292 accepted).
    - **Frequent bar-goers under 25** had a lower acceptance rate of **5.85%** (118 accepted).
    - **Infrequent bar-goers over 25** had a rate of **13.88%** (280 accepted).
    - **Infrequent bar-goers under 25** had the lowest rate at **6.40%** (129 accepted).

4. **Specific Scenarios**:
    - Drivers who went to bars more than once a month, traveled with non-kid passengers, and had occupations other than farming, fishing, or forestry had an acceptance rate of **6.94%** (140 accepted).

    - Drivers who went to bars more than once a month, traveled with non-kid passengers, and were not widowed had an acceptance rate of **6.94%**.
    - Drivers under 30 had a higher acceptance rate at **12.35%**.
    - Drivers who went to cheap restaurants more than 4 times a month and had an income less than $50K had an acceptance rate of **7.73%**.

---

### Hypotheses About Drivers Who Accepted Bar Coupons

1. **Infrequent Visitors Are More Likely to Accept**:
    - Drivers who visit bars less frequently (3 or fewer times a month) are more receptive to coupons. This could be because infrequent visitors view coupons as an incentive to go out more often or reduce the cost of their outings.

2. **Age Influences Acceptance Rates**:
    - Older drivers (over 25) are more likely to accept bar coupons than younger drivers (under 25), regardless of frequency. This suggests that older drivers might prioritize cost savings or are more willing to explore promotional opportunities.

3. **Passenger Type and Social Influence**:
    - Drivers traveling with non-kid passengers (e.g., friends or partners) are more likely to accept bar coupons. This highlights the influence of social settings and peer encouragement on decision-making.

4. **Economic Sensitivity Matters**:
    - Drivers with lower incomes and those who frequent inexpensive restaurants are more likely to accept bar coupons. This indicates that financial considerations and cost-saving behaviors play a role in their decisions.

5. **Lifestyle and Demographics**:
    - Drivers who are not widowed or have occupations outside of farming, fishing, or forestry tend to accept bar coupons more. This suggests that lifestyle and personal circumstances impact coupon usage.


### Coffee House Key Observations Recap

1. **Acceptance by Frequency of Visits**:
    - Drivers who visited a Coffee House 3 or fewer times a month had a higher acceptance rate (**29.85%**) compared to those who visited more than 3 times a month (**14.86%**).

2. **Acceptance by Frequency and Age**:
    - **Frequent coffee-goers over 25** had an acceptance rate of **21.70%**.
    - **Frequent coffee-goers under 25** had a lower acceptance rate of **10.06%**.
    - **Infrequent coffee-goers over 25** had a rate of **13.94%**.
    - **Infrequent coffee-goers under 25** had the lowest rate at **4.23%**.

3. **Specific Scenarios**:
    - Drivers who went to Coffee Houses more than once a month, traveled with non-kid passengers, and were not widowed had an acceptance rate of **13.89%**.
    - Drivers under 30 had a higher acceptance rate (**16.99%**).
    - Drivers with lower incomes and who frequently visited inexpensive restaurants had a lower acceptance rate (**9.96%**).

4. **Overall Coffee House Coupon Acceptance**:
    - Across all drivers, the overall acceptance rate for Coffee House coupons was **13.89%**.

---

### Hypotheses About Drivers Who Accepted Coffee House Coupons

1. **Infrequent Visitors Are More Likely to Accept**:
    - Drivers who visit Coffee Houses less frequently (3 or fewer times a month) are more receptive to coupons. This could be because infrequent visitors view coupons as an incentive to go more often or reduce the cost of a rare outing.

2. **Age Influences Acceptance Rates**:
    - Older drivers (over 25) are more likely to accept Coffee House coupons than younger drivers (under 25), regardless of frequency. This suggests that older drivers might prioritize cost savings or are more willing to explore promotional opportunities.

3. **Economic Sensitivity Matters**:
    - Drivers with lower incomes and those who frequent inexpensive restaurants are more likely to accept Coffee House coupons. This indicates that financial considerations and cost-saving behaviors play a role in their decisions.

4. **Passenger Type and Social Influence**:
    - Drivers traveling with non-kid passengers (e.g., friends or partners) are more likely to accept Coffee House coupons. This highlights the influence of social settings and peer encouragement on decision-making.

5. **Marital Status and Lifestyle**:
    - Drivers who are not widowed tend to have higher acceptance rates, suggesting that lifestyle and personal circumstances impact coupon usage.

---

### General Hypothesis

Drivers who accept Coffee House coupons are likely to be cost-conscious individuals, particularly infrequent visitors, older drivers (over 25), and those influenced by social factors like traveling with friends or partners. Financial considerations and lifestyle characteristics (e.g., income, passenger type, marital status) significantly influence acceptance rates.

---

### Recommendations and Next Steps

1. **Target Specific Demographics**:
    - Focus marketing efforts on infrequent visitors and older drivers (over 25), as they show higher acceptance rates.
    - Tailor messaging to younger drivers under 30, emphasizing the value or unique experience provided by the coupon.

2. **Leverage Social Influence**:
    - Highlight offers that encourage group outings, particularly with friends or partners.
    - Include referral-based incentives to capitalize on social settings.

3. **Income-Based Targeting**:
    - Promote coupons that appeal to cost-sensitive individuals by partnering with inexpensive venues or offering exclusive discounts for low-income customers.

4. **Refine Messaging for Frequent Visitors**:
    - Understand why frequent visitors have lower acceptance rates and adjust coupon offers to appeal to them (e.g., loyalty rewards or premium experiences).

5. **Experiment with Personalized Offers**:
    - Use data-driven insights to craft personalized coupon recommendations based on user behavior, demographics, and preferences.

6. **Test and Iterate**:
    - Run A/B testing on various coupon types and formats to identify what resonates most with different target groups.
    - Monitor changes in acceptance rates and refine strategies accordingly.

