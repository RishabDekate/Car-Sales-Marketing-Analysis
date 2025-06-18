# Car-Sales-Marketing-Analysis
The dataset given to us has data of 2 years wholen 2022 and 2023, consisting of all the sales made in those years by every car company. It also consist of the data of car's type, transmission, mileage, top speed, pricing, customer ratings, etc.

## Project Steps:
1.	Create problem statement.
2.	Data cleaning.
3.	Data processing using SQL.
4.	Visualization of data.
5.	Create a dashboard using Power BI software.
6.	Create the report of all the findings.

## Problem Statement
This project involves a comprehensive analysis of car sales dataset to provide insights into overall sales performance, customer preferences, fuel efficiency impact, price sensitivity, safety features influence, and market trends.
### Key Questions:
- Sales Performance Analysis: Understand the overall sales performance, identifying the best selling models, and explore trends over the year.
- Customer Preference: Analyse customer preferences by examining the populariity of different car makes, models, body type and colors.
- Fuel Efficiency Impact: Investigate the correalation between fuel efficiency (Mileage) and sales figures, identify fuel-efficient models that attract more customers.
- Price sensitivity: Determine the impact of prcing on sales. Analyse the relationship between car prices and customer ratings to understand if higher priced models result's in higher cusotmer satisfaction.
- Safety and Feature Impact: Evaluate the influence of safety features, entertainment features, and overall vehicle feartures on customer rating and sales figures.
- Market Trend Analysis: Identify market trends by analysing the popularity of different car makes and models over the year. Investigate if certain body types or fuel types are gaining tarnscations in the market.
### SQL Analysis:
1) Overview of car sales:
- Top selling car brand by price.
  
      SELECT TOP 1
      Car_Make, SUM(Price) AS total_sales
      FROM dbo.[2023 Car Dataset]
      GROUP BY Car_Make
      ORDER BY total_sales DESC

- Top selling car brand by unit sold.
  
      SELECT TOP 1
      Car_Make, SUM(Sales_Figures_Units_Sold) AS unit_sold
      FROM dbo.[2023 Car Dataset]
      GROUP BY Car_Make
      ORDER BY unit_sold DESC

2) Sales Performance Analysis:

        SELECT TOP 10
        Car_Make, Car_Model, Year, SUM(Sales_Figures_Units_Sold) AS unit_sold
        FROM dbo.[2023 Car Dataset]
        GROUP BY
        Car_Make,
        Car_Model,
        Year
        ORDER BY unit_sold DESC

3) Customer Preferences:

        SELECT TOP 10
        Car_Make, Car_Model, Body_Type, Color_Options,
        SUM(Sales_Figures_Units_Sold) AS unit_sold
        FROM dbo.[2023 Car Dataset]
        GROUP BY 
        Car_Make, Car_Model, Body_Type, Color_Options
        ORDER BY unit_sold DESC

4) Fuel Efficiency Impact:

        SELECT TOP 10
        Car_Make, Car_Model, Mileage_MPG,
        SUM(Sales_Figures_Units_Sold) AS unit_sold
        FROM dbo.[2023 Car Dataset]
        GROUP BY
        Car_Make, Car_Model, Mileage_MPG
        ORDER BY unit_sold DESC

5) Price Sensitivity:

        SELECT TOP 10
        Car_Make, Car_Model,
        SUM(Price) AS total_sales,
        AVG(TRY_CAST(LEFT(Customer_Ratings, 3) AS FLOAT)) AS avg_rating
        FROM dbo.[2023 Car Dataset]
        GROUP BY 
        Car_Make, Car_Model
        ORDER BY 
        total_sales DESC

6) Safety and Features Impact:

        SELECT TOP 10
        Car_Make, Car_Model,
        SUM(Price) AS total_sales,
        AVG(TRY_CAST(LEFT(Customer_Ratings, 3) AS FLOAT)) AS avg_rating,
        Safety_Features, Entertainment_Features
        FROM dbo.[2023 Car Dataset]
        GROUP BY 
        Car_Make, Car_Model, Safety_Features, Entertainment_Features
        ORDER BY 
        total_sales DESC

7) Market Trend Analysis:

        SELECT TOP 10
        Car_Make, Car_Model, Body_Type, Fuel_Type, Year,
        SUM(Sales_Figures_Units_Sold) AS unit_sold
        FROM dbo.[2023 Car Dataset]
        GROUP BY
        Car_Make, Car_Model, Body_Type, Fuel_Type, Year
        ORDER BY
        unit_sold DESC

## Data Visualization
![Dashboard_New](https://github.com/user-attachments/assets/c9cc23b1-97f2-496f-9c54-2b42a4024e3e)

This image is of the dashboard which is been prepared for the client.
### Results / Findings:
- As per sales performance analysis most sold units are 14400 of "Honda" fit car model, with most car sold in 2023. "Black, Grey, and White" are mostly sold with SUV body type.
- Customer preference after getting feedback from customers most of them gave 4.7 rating to 1.8M price for the car model.
- After analysing the correlation between fuel efficiency and sales figures, we can say that as mileage is more the sales figure increases.
-	Most customers gave feedback that cars which has more price to have a rating of 4.7 out of 5.
-	And the analysis for the safety, entertainment features, body type is plotted on the dashboard. 

