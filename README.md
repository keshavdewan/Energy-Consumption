# Energy Consumption Dashboard🔌💧🔥
![Energy](https://github.com/user-attachments/assets/1fa61617-7b12-46db-b7dc-ea7346ebb734)

## Introduction
This dashboard uses Power BI to create an energy consumption dashboard. It addresses a company's challenge of monitoring energy consumption across buildings in various US cities from the year 2016 to 2019. Our approach involves utilizing Power BI to create dedicated pages for each energy type. Each page provides detailed insights into consumption patterns, anomalies, and cost-effectiveness metrics. The dashboard is divided into four sections: overview, water, electricity, and gas consumption insights.

## Challenge 💪
The company faced the challenge of monitoring energy consumption across buildings in different countries. They needed a centralized platform to consolidate data from various sources and present it in a visually appealing and informative manner.

## Solution
Use Power BI to create a comprehensive energy consumption dashboard. This dashboard provides an overview of the company's energy consumption across all buildings, as well as detailed insights into each energy type.


***

## Methodology 🧰

This dashboard was developed using Power BI to provide a clear and actionable view of energy consumption data. The process involved several key steps:

1. Data Review and Familiarization:  The provided dataset consisted of three tables: Building Master (listing 11 buildings), Energy Consumptions (units consumed by building and year), and Rates (per unit cost by energy type and year).
An initial review confirmed data consistency across all tables.  This step aligns with my research background, where understanding the data's context is crucial.

2. Data Transformation (Power Query): To enable effective data modeling, a unique "ID" column was created in both the Rates and Energy Consumptions tables by combining the Year and Energy Type.
This allowed for a robust relationship to be established

![image](https://github.com/user-attachments/assets/d25c2049-f23f-418f-85aa-0d89257d7b1c)


3. Data Modeling (Power BI): Relationships were established between the Energy Consumption table and the Building Master table (using the "Building" column)
and between the Energy Consumption table and the Rates table (using the newly created "ID" column).

![image](https://github.com/user-attachments/assets/f8a8f893-9d3e-4fcf-ba70-8991da052c68)


4. DAX Measures for Analysis: Several DAX measures were created to derive key metrics:

```` sql 
-  Cities Presence = DISTINCTCOUNT('Building Master'[City])
-  No. of buildings = DISTINCTCOUNT('Building Master'[Building])
-  Total cost = SUMX('Energy Consumptions','Energy Consumptions'[Unit]*RELATED(Rates[Price Per Unit]))
-  Water Cost = CALCULATE([Total Cost], 'Energy Consumptions'[Energy Type] = "Water")
-  Electricity Cost = CALCULATE([Total Cost], 'Energy Consumptions'[Energy Type] = "Electricity")
-  Gas Cost = CALCULATE([Total Cost], 'Energy Consumptions'[Energy Type] = "Gas")
-  Total Units Consumed = SUM('Energy Consumptions'[Unit])
-  Water Unit consumed = CALCULATE([Total Units Consumed], 'Energy Consumptions'[Energy Type] = "Water")
-  Electicity unit consumed = CALCULATE([Total Units Consumed], 'Energy Consumptions'[Energy Type] = "Electricity")
-  Gas units consumed = CALCULATE([Total Units Consumed],'Energy Consumptions'[Energy Type] = "Gas")
-  % Water consumption = DIVIDE([Water Unit consumed],[Total Units Consumed],0)
-  % Electricity consumed = DIVIDE([Electicity unit consumed],[Total Units Consumed],0)
-  % Gas consumption = DIVIDE([Gas units consumed],[Total Units Consumed],0)
-  Remaining Water unit consumed = [Total Units Consumed] - [Water Unit consumed]
-  Remaining Electricity unit consumed = [Total Units Consumed] - [Electicity unit consumed]
-  Remaining Gas unit consumed = [Total Units Consumed] - [Gas units consumed]
 ````

## Dashboard Overview 👀
The dashboard is divided into four sections:

-  Overview: This section provides a high-level overview of the company's energy consumption, including total consumption, consumption by cities, and consumption by energy type.
  ![image](https://github.com/user-attachments/assets/b19d7950-f363-4eae-9c20-92db7da11036)

-  Water: This section provides detailed insights into water cost and consumption, including total cost and consumption by building and by month.
  ![image](https://github.com/user-attachments/assets/82bf234a-011a-4b08-a0b1-f3614c47dcb6)

-  Electricity: This section provides detailed insights into electricity cost and consumption, including total cost and consumption by building and by month.
  ![image](https://github.com/user-attachments/assets/61ef45ef-10cd-4722-9888-61a8491719a7)
-  Gas: This section provides detailed insights into gas cost and consumption, including total cost and consumption by building and by month.
  ![image](https://github.com/user-attachments/assets/59e99ae0-b1b1-47d3-bf25-68305a86c329)
  

## Insights 📚
The analysis revealed several key findings:

-  Water Dominance and Cost Stability: Water consumption represents the largest portion (88.49%) of total energy usage. Despite yearly fluctuations in consumption (peaking in 2017),
the overall cost has remained relatively stable. This suggests potential opportunities for targeted water conservation initiatives, aligning with my interest in data-driven solutions.

-  Downward Trend in Gas Consumption and Costs: Gas consumption, while the lowest overall, has shown a significant decrease from 2016 to 2019.
  This positive trend is also reflected in the decreasing gas costs.  Further investigation is needed to understand the drivers behind this reduction, a typical next step in any consulting engagement.

-  Need for Deeper Analysis: While the current data provides a good starting point, additional context (e.g., building type, usage patterns) is needed to fully understand consumption behaviors.
  This is a common challenge in data analysis, and I'm familiar with the process of iteratively refining the analysis as more data becomes available.

-  Potential for Further Insights:  Analyzing data by location or time of day could reveal further opportunities for optimization.
  This aligns with my focus on providing actionable insights that can drive real change.

## Recommendations ✔️
Based on these insights, I recommend the following:
-  Targeted Conservation: Implement water conservation strategies based on the dashboard insights.
-  Efficiency Exploration: Investigate the reasons for reduced gas consumption and explore further efficiency gains.
-  Expanded Analysis: Incorporate additional data (building type, location, time of day) for a more comprehensive understanding.
-  Continuous Monitoring: Utilize the dashboard for ongoing monitoring to track trends and identify areas for improvement.

***

## Key Features 🏁
The dashboard includes a number of key features, including:

-  Interactive visualizations: The dashboard includes a variety of interactive visualizations, such as charts, graphs, and tables. This allows to explore the data in different ways and to drill down to see more detailed information.
-  Filters: The dashboard includes a number of filters to filter the data by building, energy type, month, or other criteria.
-  Drill-down functionality: The dashboard includes drill-down functionality, which allows to drill down into the data to see more detailed information.
-  Customizable dashboards: The dashboard is customizable, so we can add or remove features to meet our specific needs.


## Benefits 🙏
The dashboard provides a number of benefits to the company, including:

-  Improved visibility: The dashboard provides a centralized platform for monitoring energy consumption, which improves visibility and transparency.
-  Increased efficiency: The dashboard can be used to identify areas where energy consumption can be reduced, which can help to increase efficiency and save money.
-  Better decision-making: The dashboard provides data-driven insights that can be used to make better decisions about energy management.

## Conclusion 👍
The dashboard monitors energy consumption and improve energy efficiency. It is a valuable asset for any company that is looking to reduce its energy costs and improve its sustainability.

***

#### Project inspiration -  [Medium](https://nks96.medium.com/energy-consumption-dashboard-using-power-bi-8d62b2c018e1)
#### Dashboard link - [Power BI](https://app.powerbi.com/view?r=eyJrIjoiZWJjZWYzZmMtNzk0Zi00MGJmLWFlNWItMDI1MmUxZGYxOTdjIiwidCI6ImQ1YjdmMzZhLTAyNTktNDMzZS1iYTNkLTZmM2Y3MTFkMDNiYyIsImMiOjh9)
