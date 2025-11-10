# Customer-CHURN-Analysis
Customer churn analysis focuses on identifying why customers discontinue a product or service and predicting which customers are most likely to leave. In this project, historical customer data is analyzed to detect behavioral patterns, key churn indicators, and actionable business insights.

# objective
The main goals of this Customer Churn Analysis:           
1. Measure total customers, active vs inactive members             
2. Track number of exiting customers month-wise           
3. Compare current month exit vs previous month exit            
4. Analyze churn by gender, credit card ownership, and location                
5. Provide actionable insights to reduce churn and improve retention

# Steps Followed

1️⃣ Data Loading:                  
        Imported customer dataset into Power BI                 

2️⃣ Data Cleaning (Power Query):                   
        Enabled Data Profiling (Column Quality, Distribution, Profile), Checked for nulls, duplicates, incorrect data types. Ensured clean fields for Age, Gender, Active Status, Credit Card, Month Name

3️⃣ Data Modeling:                       
        Created calculated columns for Month Sorting                
        Built DAX measures for KPIs:                         
        1. Total Customers                 
        2. Active Members               
        3. Inactive Members              
        4. Exit Customers                
        5. Retained Customers                      

4️⃣ Visualization:                         
       Added slicers for Year, Month, Geography, Active Category, Gender. Built KPI cards and comparison charts. Formatting & color theme

5️⃣ Insights & Interpretation:                    
       Identified which segment has highest churn and when churn spikes

 # DAX Measures Used

1. Total Customers =                                  
                    COUNTROWS(Customer)

2. Active Members =                            
                   CALCULATE(
                            COUNTROWS(Customer),
                             Customer[ActiveCategory] = "Active"
                              )

3. Inactive Members =                      
                     CALCULATE(
                              COUNTROWS(Customer),
                               Customer[ActiveCategory] = "Inactive"
                                )

4. Credit Card Holders =                  
                        CALCULATE(
                                 COUNTROWS(Customer),
                                 Customer[CreditCard] = "Yes"
                                 )

5. Non Credit Card Holders =                        
                            CALCULATE(
                                      COUNTROWS(Customer),
                                      Customer[CreditCard] = "No"
                                       )

6. Exit Customers =                     
                  CALCULATE(
                          COUNTROWS(Customer),
                           Customer[Exit] = "Yes"
                            )

7. Retain Customers =                                   
                      [Total Customers] - [Exit Customers]
                 
8. Previous Month Exit =                             
                        CALCULATE(
                               [Exit Customers],
                                DATEADD(Customer[Date], -1, MONTH)
                                   )
 
9. Exit % =                                      
            DIVIDE([Exit Customers], [Total Customers], 0)

 # visuals

 **KPI Cards:**        Total customers, active vs inactive, credit card holders, churn           
 **Column Chart:**     Total customers month-wise with active vs inactive comparison                    
 **Line Chart:**       Month-wise churn vs previous month churn                                     
 **Donut Chart:**      Exit customers by gender                                                     
 **Bar Chart:**        Exit customers by credit type                                                               
 **Slicers:**          Year, Month, Geography, Active Category, Gender         

 # Key Insights from Dashboard

✔ Total Customers: 10,000
✔ Active Members: 5,151
✔ Inactive Members: 4,849
✔ Exit Customers: 2,037
✔ Retained Customers: 7,963

# Major Findings

1. Highest churn months: November, December, September                
2. Most churned customers are Male (≈ 56%)                  
3. Credit score "Good" category has highest exits (753 customers)                 
4. Exit rate decreases steadily after March (seasonal effect visible)                  
5. Churn is higher among inactive members and non-credit card holders                      
