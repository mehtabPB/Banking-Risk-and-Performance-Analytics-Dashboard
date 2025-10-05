# Banking-Risk-and-Performance-Analytics-Dashboard

Banking Risk and Performance Analytics Dashboard
This project presents a comprehensive business intelligence solution developed using Power BI, supported by foundational data analysis (EDA) using Python/Jupyter, to provide insights into banking operations, focusing primarily on customer risk and financial performance metrics.


1. Project Goal & Solution
Component	Detail
Problem	
To develop a basic understanding of risk analytics in banking and financial services and understand how data is used to minimize the risk of losing money while lending to customers.

Solution	
A Power BI dashboard was created to facilitate data-driven lending decisions. The dashboard assesses an applicant's profile to determine the likelihood of loan repayment, thus helping to minimize risk.


Export to Sheets
2. Data Structure and Preparation
The analysis is built upon a database containing information about bank details and various client details, linked across multiple tables.


Data Tables 

Banking Relationship

Client-Banking

Gender

Investment Advisor

Period

Key Calculated Features (DAX/M-Language)
To enable deep segmentation and risk analysis, several calculated columns were added to the dataset:


Engagement Days: Calculated the difference in days between the Joined Bank date and TODAY().



Engagement Timeframe: Categorized client tenure into bins such as < 1 \text{ Years}, < 5 \text{ Years}, < 10 \text{ Years}, and > 20 \text{ Years}.


Income Band: Categorized Estimated Income into Low (<$100,000), Mid (<$300,000), and High (≥$300,000).


Processing Fees: Assigned a fee percentage based on the Fee Structure (e.g., High = 0.05, Mid = 0.03, Low = 0.01, 0).

3. Financial KPIs and Definitions (DAX Measures)
The dashboard utilizes the following defined measures to present the bank's operational health:

KPI	Description	DAX Formula (Core Logic)
Total Clients	
Total number of clients in banking.

DISTINCTCOUNT(’Clients - Banking’[Client ID]) 


Total Loan	
Sum of all loan-related balances.

[Bank Loan]+[Business Lending]+[Credit Cards Balance] 

Total Deposit	
Sum of all deposit-related balances.

[Bank Deposit]+[Savings Account]+[Foreign Currency Account]+[Checking Accounts] 

Total Fees	
Amount charged for account setup/maintenance.

SUMX(’Clients - Banking’,[Total Loan]×’Clients - Banking’[Processing Fees]) 

Bank Loan	
The amount of loan to be repaid by the client to the bank.

SUM(’Clients - Banking’[Bank Loans]) 

Business Lending	
The loan amount given to small businesses.

SUM(’Clients - Banking’[Business Lending]) 


Export to Sheets
4. Key Analytical Insights
The synthesized analysis from the EDA and the dashboard visuals reveals the following:

A. Customer & Segmentation Profile

Customer Base Size: The dataset contains 3,000 unique clients.



Dominant Nationality: The largest customer segment is European (1309 clients), followed by Asian (754).


Income Distribution (Univariate): The majority of the customer base falls in the Mid income band (1517 clients) and Low income band (1027 clients).


Risk Profile: The customer base is heavily skewed towards lower risk (Risk Weighting 1 and 2 account for ≈68.6% of clients), indicating a relatively healthy portfolio.


Relationship Focus: The most common Banking Relationship (BRId 3) accounts for 1352 clients, suggesting a core focus in either the Retail or Private Bank segment.

B. Financial Health and Risk Metrics

Lending Focus: The average Business Lending (≈$867K) is significantly higher than the average Bank Loan (≈$591K), suggesting a strong emphasis on or success in the business segment.

Wealth & Risk Correlation (Key Risk Finding): A crucial finding from the correlation analysis (heatmap) is the weak negative correlation between Estimated Income and Risk Weighting (≈−0.19). This is a positive indicator for the bank: 

higher-income customers tend to be assigned lower risk weightings.


Product Usage: There is a high correlation (≈0.90) between Bank Deposits and Checking Accounts, indicating intertwined transactional and savings behavior.

C. Segmented Performance Example (Private Bank - Female)
The dashboard breakdown for the "Private Bank - Female" segment shows:


Total Loan: $30.34M.

Lending Priority: Business Lending ($17.47M) exceeds Bank Loans ($12.83M).


Client Tenure: The highest loan volume across all categories is attributed to clients with <1 Years of engagement, which could signal a recent successful acquisition strategy or an area for closer risk monitoring.


Top Contributors: European clients provide the largest share of both loans ($4.91M) and deposits ($20M) in this segment.

5. Strategic Implications and Future Work
The dashboard empowers managers to make informed decisions and strategize by:


Risk Mitigation: Assessing an applicant's profile to minimize the risk of financial loss before approving a loan.


Market Strategy: Identifying successful business models (e.g., Private Banks having more clients) to help other segments build strategies.


Performance Tracking: Providing detailed insights on loan distribution, fee calculation, and deposit composition across investor types and nationalities.
