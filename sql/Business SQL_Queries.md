

# CUSTOMER ANALYTICS BUSINESS QUERIES (MYSQL Workbench)



Dataset Size : 5,000 Customers

Objective:
Solve business-oriented SQL problems to analyze customer
behavior, revenue contribution, customer segmentation,
retention, and loyalty using MySQL.

### Skills Demonstrated:

- Joins \& Aggregations

- Subqueries

- Window Functions

- CASE Statements

- CTEs

- Customer Segmentation

- CLV Analysis

- Churn Analysis

- Revenue Analysis

- Business KPI Reporting


#### Objective:

SQL Concept:
Aggregate Function (AVG), Subquery


---

### SQL-Queries

## Q1

**Identify customers spending above the overall average to recognize high-value customers for retention initiatives.**

Find all customers whose total spending is above the average spending.

Ans.

&#x20;   select customer\_id,total\_spend from customer\_data

where total\_spend>(select avg(total\_spend) from customer\_data);





## Q2

**Identify the top spending customers for VIP campaigns, loyalty programs, and personalized marketing.**



Display the Top 20 customers based on Total Spend.

Ans.

&#x20;   select customer\_id,total\_spend from cleaned\_data

order by total\_spend desc

limit 20;



## Q3

**Analyze customer distribution across membership tiers to understand customer segmentation.**

Count customers in each Membership Type.

Ans.

&#x20;   select membership\_type,count(customer\_id) as customer\_count,membership\_type from cleaned\_data

group by membership\_type;



## Q4

**Compare average customer age across genders to understand demographic characteristics.**

Find average age of customers by Gender.

Ans.

&#x20;    select gender,avg(age) as customer\_average\_age from cleaned\_data

group by gender;

## Q5

**Evaluate which membership type contributes the highest revenue to the business.**

Calculate total revenue generated from each Membership Type.

Ans.

&#x20;   select membership\_type,sum(total\_spend) as total\_revenue from cleaned\_data

group by membership\_type;

## Q6

**Identify inactive customers for customer retention and re-engagement campaigns.**

Find customers who have not purchased in the last 60 days.

Ans.

&#x20;  select  customer\_id,days\_since\_last\_purchase from cleaned\_data

where days\_since\_last\_purchase>60;



## Q7

**Identify highly engaged customers based on transaction frequency.**

Display customers who made more than 25 transactions.

Ans.

&#x20;   select customer\_id,num\_transactions from cleaned\_data

where num\_transactions>25;

## Q8

**Compare average transaction values across city tiers to understand regional purchasing behaviour.**


Find the average transaction value by City Tier.

Ans.

&#x20;  select city\_tier,sum(avg\_transaction\_value) as average\_transaction from cleaned\_data

group by city\_tier;



## Q9

**Measure discount utilization across membership types to evaluate promotional effectiveness.**

Find the total discount given for each membership type.

Ans.

&#x20;   select membership\_type,sum(discount\_used) as discount\_membership from cleaned\_data

group by membership\_type;


## Q10

**Comparing the number of high-value and regular customers within the customer base.**


Count High Value vs Normal Customers.

Ans.

&#x20;   select high\_value\_customer,count(customer\_id) as customer\_count from cleaned\_data

group by high\_value\_customer;



## Q11

**Ranking customers according to spending to identify the highest-value customers.**

Rank customers by Total Spend using Window Functions.

Ans.

&#x20;   select customer\_id,total\_spend,

rank() over(order by total\_spend desc) as customer\_rank from cleaned\_data;

## Q12

**Identify the top-performing customers within each membership category.**


Find Top 5 customers in each Membership Type.

Ans.

&#x20;   select \* from(select customer\_id,membership\_type,total\_spend,rank() over (partition by membership\_type order by total\_spend desc) as customer\_rank

from cleaned\_data) as customer\_data

where customer\_rank<=5;



## Q13

**Developing a Customer Engagement Score by combining customer visits, purchase frequency, and product diversity to identify the most engaged customers.**

Create a Customer Engagement Score by combining customer visits, purchase frequency, and product category diversity. Rank customers based on their engagement score.

Ans.

&#x20;  select customer\_id,

(

num\_transactions+

num\_visits+

product\_categories\_purchased

) as customer\_engagement\_score,row\_number () over (order by num\_transactions+num\_visits+product\_categories\_purchased) as engagement\_rank

from cleaned\_data;



## Q14.

**Segment customers into spending quartiles for targeted marketing and customer prioritization.**

Assign customers into spending quartiles using NTILE().

Ans.

&#x20;   select customer\_id, total\_spend,

ntile(4) over (order by total\_spend ) as spending\_quantile,



case ntile(4) over (order by total\_spend)



when 1 then 'Low Spenders'

when 2 then 'Medium Spending'

when 3 then 'High Spending'

when 4 then 'Premijum spending'

&#x20;                               End as spending\_segment



&#x20;from cleaned\_data;

## Q15

**Measuring each membership type's contribution to total business revenue.**


Find percentage contribution of every membership type towards total revenue.

Ans.

&#x20;   select membership\_type,sum(total\_spend) as membership\_revenue,

ROUND(

&#x20;sum(total\_spend)  \* 100 /

&#x20;(Select sum(total\_spend) from cleaned\_data),2

&#x20;)

&#x20;as revenue\_percentage

&#x20;

&#x20;from cleaned\_data

group by membership\_type

order by membership\_revenue desc;


## Q16

**Compare purchasing behaviour between high-value and regular customers.**

Find average number of transactions for High Value Customers vs Normal Customers.

Ans.

&#x20;   select high\_value\_customer,avg(num\_transactions) as average\_number\_transacs from cleaned\_data

group by high\_value\_customer;



## Q17
**Customers spending above their membership group's average represent exceptional performers within their segment and provide valuable insights into purchasing behavior and upselling opportunities.**

Find customers whose spending is greater than their membership average.

Ans.

&#x20;   select \* from (

select customer\_id,total\_spend,avg(total\_spend) over (partition by membership\_type)

&#x20;as membership\_average from cleaned\_data) as membership\_table

where total\_spend>membership\_average;



## Q18

**Evaluating the average revenue generated per customer visit across different membership types to measure customer engagement efficiency and identify the most profitable  membership segment.**

Find average spend per visit by membership type

Ans.

&#x20;   select membership\_type, 

round(

SUM(total\_spend)/sum(num\_visits),2) as revenue\_visits

from cleaned\_data

group by membership\_type

order by revenue\_visits desc;



## Q19

**Identify the highest-performing city tiers based on average customer spending.**

Find Top 3 City Tiers having highest average spending.

Ans.

&#x20;   select city\_tier,avg(total\_spend) as average\_spending from cleaned\_data

group by city\_tier

order by average\_spending desc

limit 3;

## Q20

**Identify customers receiving above-average discounts for promotional effectiveness analysis.**\*

Find customers who receive higher-than-average discounts.

Ans.

&#x20;   select customer\_id,discount\_used from cleaned\_data

where discount\_used> (select avg(discount\_used) from cleaned\_data);



## Q21

**Estimation of long-term customer value.**

Create a Customer Lifetime Value (CLV) metric

Ans.

Example



CLV = Avg Transaction × Number of Transactions



Rank customers.

&#x20;Ans.

&#x20;

select customer\_id,(num\_transactions\*avg\_transaction\_value) as clv,

rank() over (order by (num\_transactions\*avg\_transaction\_value)) as customer\_rank from cleaned\_data;



**INSIGHT:Customers with lowest estimation clv exhibits infrequent purchases and low spending ,making them suitable targets for promotional campaigns aimed at increasing frequency purchase.**




## Q22

Calculate Revenue Share by Gender.

Ans.

&#x20;  select gender,sum(total\_spend) as revenue\_share

from cleaned\_data

group by gender;



## Q23
**Comparing revenue across membership types helps identify the most profitable membership programs and supports decisions on pricing, loyalty benefits, and membership upgrades.**
Calculate Revenue Share by Membership.

Ans.

&#x20;  select membership\_type,sum(total\_spend) as revenue\_share

from cleaned\_data

group by membership\_type;



## Q24

Find correlation-like insight


Which membership has


a)highest spend

b)lowest visits

c)highest transactions

Ans.

&#x20;   select membership\_type,max(total\_spend) as highest\_spending,

min(num\_visits) as lowest\_visits,max(num\_transactions)as highest\_transactions from cleaned\_data

group by membership\_type

order by

&#x20;

;

## Q25

Create Customer Risk Flag

(

If

Days Since Last Purchase > 60

AND

Transactions < 10

Flag as "Likely Churn"

)

Ans.

&#x20;   select customer\_id,case

when days\_since\_last\_purchase>60 and num\_transactions<10 then '1' else '0'

end as churn\_risk\_flag

&#x20;from cleaned\_data;


## Q26  
**Customer segmentation highlights distinct purchasing behaviours, enabling targeted marketing strategies such as loyalty rewards for premium customers, promotional offers for discount-sensitive customers, and re-engagement campaigns for inactive customers.**

Create Customer Personas
(

Like

Premium Loyal

Discount Hunter

Frequent Shopper

Inactive Customer


using CASE.

)

Ans.

&#x20;   select customer\_id, case

when

&#x20;    total\_spend>=20000

&#x20;    and

&#x20;    num\_transactions>=36

&#x20;    then 'Premium Loyal'

&#x20;

when

&#x20;   discount\_used>=800

&#x20;   and

&#x20;   total\_spend<=9000

&#x20;   then 'Discount Hunter'

when

&#x20;    num\_transactions>=30

&#x20;    then 'Frequent Shopper'

&#x20;when

&#x20;    days\_since\_last\_purchase>50

&#x20;    then 'Inactive Customer'

&#x20;end as customer\_personas

&#x20;from cleaned\_data;





## Business Logic

|*Persona*|*Business Meaning*|
|-|-|
|Premium Loyal|VIP Customer(High Spender + Frequent orders)|
|Discount Hunter|Sensitive to promotions|
|Frequent Shopper|Good retention rate|
|Inactive Customer|Needs re-engagement(No purchase for 50+ days)|



## Q27

**High-value customer identification using percentile analysis to get top 10% customers to target them with loyalty rewards ,personalized offers , premium services.**

Find customers spending above 90th percentile.

Ans.

&#x20;   select \* from (

select customer\_id, rank() over (order by total\_spend) as percentile\_rank from cleaned\_data) as customer\_table

where percentile\_rank>=4500.0;



## Q28



**Analyzing spending across age groups helps identify the most valuable customer demographics, enabling age-specific marketing campaigns and product recommendations.**

Find average spending after grouping Age into bins.
{
18-25

26-35

36-45

46-60

60+
}
Ans.

&#x20;   select case

&#x20;

when age between 18 and 25 then '18-25'

when age between 26 and 35 then '26-35'

when age between 36 and 45 then '36-45'

when age between 46 and 60 then '46-60'

when age between 60 and 75 then '60-75'

end as age\_bins,avg(total\_spend) as average\_spend



from cleaned\_data



group by age\_bins



&#x20;   order by

&#x20;     average\_spend desc;



## Q29

Find membership having maximum revenue per visit.

Ans.)

&#x20;    select membership\_type,(count(num\_visits))  as visits ,sum(total\_spend) as revenue from cleaned\_data

group by membership\_type

order by revenue  desc

limit 1;

## Q30

**Identify highly engaged visitors who are purchasing from only a limited range of products, representing cross-selling opportunities**

Find customers who visit frequently but spend little.

Ans.

&#x20;

&#x20;  select customer\_id,max(num\_visits) as freq\_visits,sum(total\_spend) as spending from cleaned\_data

group by customer\_id

having

&#x20;    freq\_visits>50 and spending<3000

order by

freq\_visits desc,

spending asc;

---