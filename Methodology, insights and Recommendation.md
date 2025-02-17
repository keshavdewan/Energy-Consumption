# Methodology
This dashboard was developed using Power BI to provide a clear and actionable view of energy consumption data. The process involved several key steps:

1. Data Review and Familiarization:  The provided dataset consisted of three tables: Building Master (listing 11 buildings), Energy Consumptions (units consumed by building and year), and Rates (per unit cost by energy type and year).
An initial review confirmed data consistency across all tables.  This step aligns with my research background, where understanding the data's context is crucial.

2. Data Transformation (Power Query): To enable effective data modeling, a unique "ID" column was created in both the Rates and Energy Consumptions tables by combining the Year and Energy Type.
This allowed for a robust relationship to be established

![image](https://github.com/user-attachments/assets/d25c2049-f23f-418f-85aa-0d89257d7b1c)


4. Data Modeling (Power BI): Relationships were established between the Energy Consumption table and the Building Master table (using the "Building" column)
and between the Energy Consumption table and the Rates table (using the newly created "ID" column).

![image](https://github.com/user-attachments/assets/f8a8f893-9d3e-4fcf-ba70-8991da052c68)


6. DAX Measures for Analysis: Several DAX measures were created to derive key metrics:

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

5. Data Visualization and Dashboard Development: The dashboard is structured into four sections:
-  Overview
![image](https://github.com/user-attachments/assets/b19d7950-f363-4eae-9c20-92db7da11036)

-  Water
![image](https://github.com/user-attachments/assets/82bf234a-011a-4b08-a0b1-f3614c47dcb6)

-  Electricity
![image](https://github.com/user-attachments/assets/61ef45ef-10cd-4722-9888-61a8491719a7)

-  Gas
![image](https://github.com/user-attachments/assets/59e99ae0-b1b1-47d3-bf25-68305a86c329)


This structure allows for both a high-level view and granular exploration. Different visualizations were employed to best represent the data and facilitate understanding

## Insights
The analysis revealed several key findings:

-  Water Dominance and Cost Stability: Water consumption represents the largest portion (88.49%) of total energy usage. Despite yearly fluctuations in consumption (peaking in 2017),
the overall cost has remained relatively stable. This suggests potential opportunities for targeted water conservation initiatives, aligning with my interest in data-driven solutions.

-  Downward Trend in Gas Consumption and Costs: Gas consumption, while the lowest overall, has shown a significant decrease from 2016 to 2019.
  This positive trend is also reflected in the decreasing gas costs.  Further investigation is needed to understand the drivers behind this reduction, a typical next step in any consulting engagement.

-  Need for Deeper Analysis: While the current data provides a good starting point, additional context (e.g., building type, usage patterns) is needed to fully understand consumption behaviors.
  This is a common challenge in data analysis, and I'm familiar with the process of iteratively refining the analysis as more data becomes available.

-  Potential for Further Insights:  Analyzing data by location or time of day could reveal further opportunities for optimization.
  This aligns with my focus on providing actionable insights that can drive real change.

## Recommendations
Based on these insights, I recommend the following:
-  Targeted Conservation: Implement water conservation strategies based on the dashboard insights.
-  Efficiency Exploration: Investigate the reasons for reduced gas consumption and explore further efficiency gains.
-  Expanded Analysis: Incorporate additional data (building type, location, time of day) for a more comprehensive understanding.
-  Continuous Monitoring: Utilize the dashboard for ongoing monitoring to track trends and identify areas for improvement.
