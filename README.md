# Email-Markteing-Campaign

### Overview
This analysis examines a dataset of over 90K rows and 15 columns, covering Email Marketing Campaign performance from July 2024 to September 2024. It evaluates key engagement metrics such as open rates, click-through rates, conversions, and audience behavior to identify trends and optimize future campaigns.


### Tool and Technique
- **Power BI** – Created interactive dashboards for real-time campaign monitoring.
- **Data Modeling** – Established structured relationships to enhance reporting efficiency.
- **DAX Formulas** – Applied advanced calculations to derive key performance indicators (KPIs).
- **Power Query** – Cleaned and transformed data to ensure accuracy and consistency.

### Data Modelling
![image](https://github.com/user-attachments/assets/499c8047-1b87-4ed7-b629-ba7784d2fb81)

### Dax Measure
```DAX
Open Rate = 
VAR openemail = CALCULATE([DelieverEmails],main[Opened Status] = "Opened")
VAR deliver = [DelieverEmails]
RETURN
DIVIDE(openemail,deliver,0)

Conversion Rate = 
VAR conversemail = CALCULATE([DelieverEmails],main[Conversion Status] = "Converted")
VAR deliver = [DelieverEmails]
RETURN
DIVIDE(conversemail,deliver,0)

Subscribed Rate = 
VAR subEmails = CALCULATE([DelieverEmails],main[Unsubscribed Rate]="Subscribed")
VAR delivermail = [DelieverEmails]
RETURN
DIVIDE(subEmails, delivermail, 0)

Click Rate = DIVIDE([Total Click], [Total Email],0)

Bounce Rate = DIVIDE([Total Bounce], [Total Email],0)

Country with Highest Conversion Rate = 
VAR maxconversionrate = 
    CALCULATE(
        MAXX(VALUES(dim_country[country]), [Conversion Rate]), 
        FILTER(ALL(main), MONTH(main[Date]) = 7))
RETURN 
    SELECTCOLUMNS(
        TOPN(
            1, 
            VALUES(dim_country[country]), 
            [Conversion Rate], 
            DESC), 
        "Country", dim_country[country])

Lowest Click Rate Campaign September = 
VAR MinClickRate = CALCULATE(MINX(FILTER(main,MONTH(main[Date]) = 9  ),[Click Rate] ))
RETURN CALCULATE( FIRSTNONBLANK(
            dim_country[country], 1
        ),
    FILTER(
        main,
        MONTH(main[Date]) = 9 && [Click Rate] = MinClickRate
        )
    )
```
### Key Insights and Findings

**Performance by Device & Email Type:**

Mobile (10.90%) had a higher click rate than Desktop (7.05%), suggesting mobile-optimized content is crucial.

Bounce rates varied across email providers, with Gmail and Hotmail showing relatively higher stability.

**Conversion Behavior & Optimization Opportunities:**

Leads had a slightly higher open rate (2.20%) than customers (1.99%), highlighting engagement opportunities at different funnel stages.

Form completions had the highest open rate (49.84%), while sign-ups and web visits had lower engagement, indicating a need for improved CTA strategies.

**Geographic & Provider-Based Trends**

- Highest Conversion Rate: 🇮🇸 Iceland (July)

- Lowest Click Rate: 🇦🇴 Angola (September)

- Email Provider with the Highest Bounce Rate: 📧 AOL

**Time-Based Insights**

Week 27 had the highest unsubscribe rate (0.38%), prompting a review of campaign frequency and messaging strategies.

Engagement trends fluctuate by month, emphasizing the need for seasonal optimization in marketing efforts.

### Dashboard Link ###
[PowerBi Dashboard](https://app.powerbi.com/links/S7xvKqjXC9?ctid=a20d9c8a-2343-47af-9caa-d0d4508edde1&pbi_source=linkShare)





