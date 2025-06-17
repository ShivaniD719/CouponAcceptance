# Will the customer accept the coupon?
## Problem Statement:
Analyze the survey data and predict what scenarios have higher possibility of accepting a specific type of coupon.
### Analysis
#### Data Cleaning
Car column doesn’t have any values for 12576 rows out of 12684 rows. Having data only for 108 rows, 0.85% of total dataset, would not be useful to predict anything about the data so dropped the column.

Column 'Bar, CoffeeHouse, CarryAway, RestaurantLessThan20, Restaurant20to50' have some null values but it seems those values cannot be derived from other columns so filling them out with value ‘NA’. Using dropna for all these columns removes 12684-12079 = 605 rows, 4.77% of total data so dropping rows where any of these values are null seems to be a good approach. These columns are used to determine the possibility of customer accepting coupon or not so it would be good to have not null data in these columns. The data is now saved under ‘data2’ dataframe.
### EDA
6877 out of 12079 drivers accepted the coupon so total 56.93% accepted the coupon.
There are total of 5 categories of coupons: Bar, Carry out & Take away, Coffee House, Restaurant(20-50), Restaurant(<20). The following chart shows total coupons per category along with the acceptance rate for each one.
![image](https://github.com/user-attachments/assets/b081b396-5072-4bb9-9cdc-b31d8e8442da)

 

I have analyzed 2 categories in detail below: ‘Bar’ and ‘Coffee House’ to understand what parameters impacted acceptance of the coupon vs rejection of the coupon.
### Results
Bar coupons:
Based on the guided analysis in the attached prompt.ipynb file, the acceptance rate for bar coupons highly depends on these factors: 
 1. Driver's frequency of going to bar: more times a person has been going to bar per month have higher possibility of accepting a Bar coupon. 
 2. Age: People with age between 25 and 30 have more possibility of accepting a Bar coupon.
 3. Passengers: who don't have kid as a passenger have more possibility of accepting a Bar coupon. 
 4. Occupation other than 'farming, fishing, or forestry', Driver's history of 'not' going to cheap restaurants 4 times a month and income more than 50k: these factors seem to make higher possibility of accepting a Bar coupon as well when considered with above listed conditions.

Coffee House Coupons:
I analyzed some columns one by one and the acceptance rate for Coffee House coupons depends on these factors: 
1. Driver's frequency of going to bar: more times a person has been going to Coffee House per month have higher possibility of accepting a Bar coupon. 
 2. Age: People with age between 21 to 25 have more possibility of accepting a Bar coupon.
 3. Passengers: who have ‘Friend(s)’ as a passenger have more possibility of accepting a Coffee House coupon. 
 4. destination = 'No Urgent Place' have higher acceptance rate than other destinations.


#### findings
Recommendations:
•	Direction_same and direction_opp are mutually exclusive so one of the columns can be dropped.
•	Adding another column for ‘Total extra miles added to destination’ or ‘Total extra time added to destination’ would be helpful to analyze coupon acceptance.
o	There are 3 separate columns for ‘toCoupon_GEQ<x>min’ with binary value (1/0): they can be combined into 1 column and can indicate min rather than binary value.
