# Customer-Churn-Analysis-Data-Analytics-
In this project I analyzed the data to create an interactive Dashboard to make Intelligent Business decisions

# Intro
Microsoft PowerApps are great tools to develop applications for wide range of use cases. Power BI is a powerful tool for data analysis and visualization. Customer churn analysis is the process of identifying who are the lost customers, how many are lost, how many are new, and how many are returning. This can help businesses to understand why they are losing customers and how to retain them, as well as to target new and existing customers more effectively.

# About this project
In this project, I used the following steps to create the customer churn analysis:

- I connected to MySQL and Excel data sources and imported the relevant tables into Power BI.
- I created a date table and marked it as a date table in Power BI.
- Created relationships between the tables based on customer ID and date fields.
- Generated measures using DAX functions such as CALCULATE, DISTINCTCOUNT, FILTER, ALLSELECTED, EXCEPT, VALUES, so on. to calculate the count of customers in different categories: lost, new, returning, and existing.
- Prepared reports with slicers for date range and country, and visuals such as cards, gauges, donuts, and tables to show the customer churn metrics and details.
- I created two reports: one for customer churn by month and another for customer churn by different category. I used line charts, bar charts, and matrix tables to show the trends and breakdowns of customer churn.

# ETL
- Most of the tables had null values in their records, The Fact table has interdependent variables hence it was necessary to eleminate these records.
- The date format was UK based hence I used DateMaster table to Extract the dates and Transform them into DD,MMM,YY Format
- To help Business users understand the data easily I have added another column creditCategory which divides the customers in 5 credit categories (from Excellent to Fair)

# Report 1
**This screen below displays the information about the different category of people leaving the bank**

![image](https://user-images.githubusercontent.com/50295990/235179400-b43278df-5c3c-4901-a233-be06130acff3.png)

**The below screen displays the data when you choose the slicer for 2018 and spain**

![image](https://user-images.githubusercontent.com/50295990/235180282-f9a47ef4-2d66-4c3e-9033-8af688efbd0f.png)

To calaulate the credit category using switch statement is necessary which is as follows:-

_credit_score_category = SWITCH(TRUE(),Bank_Churn[CreditScore]>=800 && Bank_Churn[CreditScore]<=850,"Excellent",
Bank_Churn[CreditScore]>=800 && Bank_Churn[CreditScore]<=850,"Excellent", 
Bank_Churn[CreditScore]>=740 && Bank_Churn[CreditScore]<=799,"Very Good", 
Bank_Churn[CreditScore]>=670 && Bank_Churn[CreditScore]<=739,"Good", 
Bank_Churn[CreditScore]>=580 && Bank_Churn[CreditScore]<=669,"Fair", 
Bank_Churn[CreditScore]>=300 && Bank_Churn[CreditScore]<=579,"Poor")_


# Report 2
**This screen below displays the churn percentage on month-month and YoY basis with a small visual hint that reprents if there is a decrease or increase of customers**

![image](https://user-images.githubusercontent.com/50295990/235181031-88fd8457-2a49-4266-a0f7-9ac19ae86bcf.png)

I have added a new measure churn% to calculate the percentage which goes by:-

_churn % = 
var EC= [CustomersExited]
var TC=[Total Customers]
var churnpercent=DIVIDE(EC,TC)
return churnpercent_

# Modeling
For this data I have used star schema as it had one fact table which has all the data needed 
**The below screen snip shows the data model for this project**

![image](https://user-images.githubusercontent.com/50295990/235183384-25bc3bf6-853e-4910-9d4c-02d50840c7b5.png)

# FutureScope
- This project can be extended further to implement ML models to predict the customer churn in coming months
- One can also add more reports by tinkering with more columns and records with this data


_I hope you find this project useful and interesting. Thank you for visiting my GitHub repo!_
