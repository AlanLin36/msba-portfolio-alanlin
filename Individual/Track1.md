\# Track 1 – Where the Data Comes From



In a real company, churn modeling would typically combine multiple source systems rather than a single flat dataset. Based on the variables available in this dataset, I would expect the following source tables.



---



\## 1. Customer Profile Table



\- One row represents: one customer

\- Key fields:

&nbsp; - cust\_ref (unique customer identifier)

&nbsp; - acct\_ref (account reference)

&nbsp; - gender

&nbsp; - age\_years

&nbsp; - is\_married

&nbsp; - has\_dependents

&nbsp; - dependents\_count



\## 2. Subscription \& Contract Table



\- One row represents: one customer subscription record

\- Key fields:

&nbsp; - cust\_ref

&nbsp; - contract\_term

&nbsp; - internet\_plan

&nbsp; - internet\_tech

&nbsp; - home\_phone

&nbsp; - multi\_line

&nbsp; - tech\_support\_std

&nbsp; - premium\_support

&nbsp; - unlimited\_data\_opt

&nbsp; - add\_on\_security

&nbsp; - add\_on\_backup

&nbsp; - add\_on\_protection

&nbsp; - stream\_tv

&nbsp; - stream\_movies

&nbsp; - stream\_music



\## 3. Billing \& Financial Table



\- One row represents: one customer per billing period (e.g., monthly)

\- Key fields:

&nbsp; - cust\_ref

&nbsp; - monthly\_fee

&nbsp; - total\_billed

&nbsp; - avg\_long\_dist\_fee

&nbsp; - long\_dist\_fees\_total

&nbsp; - extra\_data\_fees\_total

&nbsp; - refunds\_total

&nbsp; - pay\_method

&nbsp; - e\_bill\_opt\_in

&nbsp; - fiscal\_qtr



---



\## Keys to Connect the Data



The primary key used to connect these tables would be:



\- \*\*cust\_ref\*\* — this is the unique customer identifier and should serve as the main joining key across all source systems.



A secondary key would be:



\- \*\*acct\_ref\*\* — this may represent account-level relationships if a customer has multiple services or billing structures.

\- \*\*fiscal\_qtr\*\* — this would be important for aligning time-based billing records and ensuring proper sequencing of customer behavior over time.



When building a churn model, it is critical to align all financial and subscription data to a specific time window. Only data available before a churn event (left\_flag = 1) should be included as predictors.



---



\## Risks and Mitigation Strategies



\### Risk 1: Data Leakage



Some financial variables, such as refunds\_total or extra\_data\_fees\_total, may include information that reflects activity occurring after a customer has already decided to churn. If these values are not properly time-aligned, the model could learn from future information, artificially inflating performance.



\*\*Mitigation:\*\*

\- Define a strict modeling cutoff date for each customer.

\- Use only billing and subscription data that occurred prior to the churn event.

\- Validate timestamps during feature construction to prevent leakage.



---



\### Risk 2: Duplicate or Inconsistent Records



Because acct\_ref is not necessarily unique, improper joins between tables could duplicate customer records, leading to inflated row counts and biased model training. Additionally, inconsistent customer information across systems may introduce noise.



\*\*Mitigation:\*\*

\- Use cust\_ref as the primary join key.

\- Perform uniqueness checks before and after joins.

\- Validate row counts after merging tables to ensure no unintended duplication.

\- Flag and investigate conflicting customer records prior to modeling.



