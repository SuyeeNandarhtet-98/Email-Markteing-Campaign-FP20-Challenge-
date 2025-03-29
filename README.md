# Email-Markteing-Campaign

### Overview
This analysis examines a dataset of over 90K rows and 15 columns, covering Email Marketing Campaign performance from July 2024 to September 2024. It evaluates key engagement metrics such as open rates, click-through rates, conversions, and audience behavior to identify trends and optimize future campaigns.


### Tool and Technique
- **Power BI** – Designed dynamic dashboards for real-time insights and data exploration.
- **Data Modeling** – Structured efficient data models to enhance performance and usability.
- **DAX Formulas** – Leveraged advanced calculations to generate actionable KPIs.

### Data Modelling
![image](https://github.com/user-attachments/assets/499c8047-1b87-4ed7-b629-ba7784d2fb81)

### Dax Measure
Conversion Rate = 
VAR conversemail = CALCULATE([DelieverEmails],main[Conversion Status] = "Converted")
VAR deliver = [DelieverEmails]
RETURN
DIVIDE(conversemail,deliver,0)

