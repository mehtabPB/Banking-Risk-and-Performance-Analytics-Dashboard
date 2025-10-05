## Banking-Risk-and-Performance-Analytics-Dashboard

This project presents a comprehensive Business Intelligence (BI) solution developed using Power BI and supported by foundational data analysis (EDA) to provide data-driven insights into banking operations, focusing on customer risk and financial performance metrics. The core objective is to apply data analytics to risk management by assessing customer profiles to minimize lending losses.

Project Overview
Problem: To develop an understanding of risk analytics and how data is used to minimize the risk of losing money while lending to customers.
Solution: A Power BI dashboard was created to evaluate applicant profiles to approve loans when the applicant is likely to repay, thus minimizing the risk of loss.
Data Source: The project uses a customer dataset comprising multiple interlinked tables, including Client-Banking, Banking Relationship, Gender, Investment Advisor, and Period.

Data Preparation and Key Measures
To enable deep segmentation and risk analysis, several calculated columns and Key Performance Indicators (KPIs) were defined:

Feature Engineering: New categorical features were created in the source data, including Engagement Timeframe and Income Band (categorizing income into Low, Mid, and High), to segment the customer base. The client's time with the bank was calculated as Engagement Days.

<img width="1270" height="715" alt="BI 1" src="https://github.com/user-attachments/assets/71c721d2-1445-4a1f-beed-90005d9c4a62" />
<img width="1287" height="712" alt="b2" src="https://github.com/user-attachments/assets/8745635d-a0cf-4165-a2d3-162985271aaf" />
<img width="1278" height="718" alt="b3" src="https://github.com/user-attachments/assets/3b1f9722-b98c-4573-a025-b6145779412c" />


Total Loan: Calculated as the sum of Bank Loan, Business Lending, and Credit Cards Balance.
Total Deposit: Calculated as the sum of Bank Deposit, Savings Account, Foreign Currency Account, and Checking Accounts.
Total Fees: Calculated using the SUMX function over the total loan amount multiplied by the calculated Processing Fees.

Key Analytical Findings and Risk Insights
The combined analysis from the EDA and the dashboard visuals reveals critical business and risk intelligence:
Favorable Risk Correlation: The correlation analysis is a key risk finding, showing a negative correlation (≈−0.19) between Estimated Income and Risk Weighting. This indicates that 

higher-income customers are associated with lower credit risk, which is a positive signal for the bank. The majority of clients fall into the lowest risk tiers (Risk Weighting 1 and 2).


Customer Segmentation: The largest segment is European clients and clients within the Mid-Income Band.
Lending Focus: Business Lending is a significant part of the portfolio, with the average Business Lending amount (≈$867K) exceeding the average Bank Loan amount (≈$591K).
Acquisition Signal: The highest volume of loans and deposits is concentrated among clients with less than 1 Year of engagement, which requires monitoring as these are newer relationships.

Strategic Implications
The dashboard provides a foundation for future strategic actions and insights:

Competitive Strategy: The analysis helps identify which type of bank has more clients (e.g., Private Banks), allowing other segments to build strategies to increase their clients.
Lending Prioritization: Managers can easily determine which nationality has the highest bank loans and which income bands contribute most to the portfolio.
Comprehensive Overview: The report gives information about various types of amounts involved in different types of accounts by investors.
Engagement Days: Calculated the difference in days between the Joined Bank date and TODAY().
Engagement Timeframe: Categorized client tenure into bins such as < 1 \text{ Years}, < 5 \text{ Years}, < 10 \text{ Years}, and > 20 \text{ Years}.
Income Band: Categorized Estimated Income into Low (<$100,000), Mid (<$300,000), and High (≥$300,000).
Processing Fees: Assigned a fee percentage based on the Fee Structure (e.g., High = 0.05, Mid = 0.03, Low = 0.01, 0).

 Financial KPIs and Definitions (DAX Measures)
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

4. Key Analytical Insights
The synthesized analysis from the EDA and the dashboard visuals reveals the following:

A. Customer & Segmentation Profile

Customer Base Size: The dataset contains 3,000 unique clients.
Dominant Nationality: The largest customer segment is European (1309 clients), followed by Asian (754).
Income Distribution (Univariate): The majority of the customer base falls in the Mid income band (1517 clients) and Low income band (1027 clients).
Risk Profile: The customer base is heavily skewed towards lower risk (Risk Weighting 1 and 2 account for ≈68.6% of clients), indicating a relatively healthy portfolio.
Relationship Focus: The most common Banking Relationship (BRId 3) accounts for 1352 clients, suggesting a core focus in either the Retail or Private Bank segment.
<img width="1760" height="702" alt="E1" src="https://github.com/user-attachments/assets/52dcdda0-3600-4e5f-abf9-64b64329034c" />
<img width="807" height="817" alt="E3" src="https://github.com/user-attachments/assets/e5af1758-4ccb-4236-9071-d8ed304b4c98" />



B. Financial Health and Risk Metrics

Lending Focus: The average Business Lending (≈$867K) is significantly higher than the average Bank Loan (≈$591K), suggesting a strong emphasis on or success in the business segment.
Wealth & Risk Correlation (Key Risk Finding): A crucial finding from the correlation analysis (heatmap) is the weak negative correlation between Estimated Income and Risk Weighting (≈−0.19). This is a positive indicator for the bank: 
higher-income customers tend to be assigned lower risk weightings.
Product Usage: There is a high correlation (≈0.90) between Bank Deposits and Checking Accounts, indicating intertwined transactional and savings behavior.
<img width="1066" height="523" alt="E2" src="https://github.com/user-attachments/assets/b91133e1-2863-42cc-a7df-c22ed71e2508" />


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
