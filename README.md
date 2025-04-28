# Project Title: Corporate Credit Rating Model

## Overview:
### 0) Project Objective:
The primary goal of this project is to automate the process of assessing corporate credit ratings by utilizing artificial intelligence to learn existing credit evaluation methodologies, while simultaneously scraping corporate financial statements from online sources. The aim is to streamline and automate the traditional corporate credit rating services.

### 1) What is a Corporate Credit Evaluation Service?
A corporate credit evaluation service involves the assessment of a company’s overall ability to meet its financial obligations in a timely manner, specifically evaluating the likelihood of defaulting on debt.

### 2) Types of Corporate Credit Evaluations:
Credit evaluations can be classified into three categories: main evaluation, periodic evaluation, and ad-hoc evaluation. The main evaluation is based on a company’s most recent financial statements, providing an overall assessment of its debt repayment capabilities and determining the credit rating. The periodic evaluation occurs annually during the validity period of the main evaluation, based on the company's semi-annual or annual financial performance, to determine if the rating needs adjustment. The ad-hoc evaluation, meanwhile, takes place in the event of significant environmental changes that may impact the company’s credit standing. For this project, a classification model will be developed that predicts credit ratings based on the main evaluation criteria.

### 3) Evaluation Methodology:
The evaluation is divided into financial and non-financial elements. Financial factors, which account for 70% of the credit rating, include assessments of stability, profitability, efficiency, growth potential, and cash flow based on quantitative financial data. Specific financial metrics include the debt ratio, return on equity (ROE), operating profit margin, net profit margin, interest coverage ratio, financial cost burden, revenue growth rate, total asset growth rate, operating profit growth rate, and accounts receivable turnover days. Non-financial factors, which contribute 30% to the rating, consist of both quantitative and qualitative elements such as company size, the reliability of financial statements, and management risks.

### 4) Types of Ratings:
Credit ratings range from AAA (prime credit) to D (default). The 10 levels are AAA, AA, A, BBB, BB, B, CCC, CC, C, and D, with the creditworthiness decreasing as the ratings descend. For intermediate grades from AA to CCC, a “+” or “-” may be appended to indicate relative standing within the grade.

### 5) Types of Companies:
Corporations are classified into financial and non-financial entities, with differences in financial statement components based on this classification. For this project, we focus on non-financial companies, using evaluation criteria such as stability, growth potential, and cash flow.

## Non-Financial/Financial Credit Rating Model

### 1) Non-Financial Credit Rating Model:
The non-financial model involves crawling data to generate a credit rating model based on non-financial factors. Using Naver news articles related to the companies being rated, the headlines are scraped and analyzed to predict credit ratings. Non-financial factors primarily involve internal company information, which is not available through crawling, so we opted to use news headlines as the non-financial dataset. Headlines, often crafted to capture attention and filter out unnecessary details, are more appropriate for this model than the full articles. The scraped headlines are tokenized using the 'kb-albert' model.

### 2) Financial Credit Rating Model:
The financial model involves scraping financial data from the NICE Credit Rating website, collecting metrics such as stability, profitability, efficiency, growth potential, and cash flow. Using tools like `bs4` and `selenium.webdriver`, we built an automated scraping system that downloads the financial statements of non-financial companies. After scraping, we preprocess the data and engineer features to extract numerical values for financial assessment.

#### Financial Metric Calculation Methods (Source: NICE):
All ratios are multiplied by 100.
- Debt Ratio = Total Liabilities / Total Equity
- Borrowing Dependency = Total Liabilities / Total Assets
- Fixed Asset to Long-Term Liability Ratio = Tangible Assets + Intangible Assets / Tangible Assets + Intangible Assets + Long-Term Investments
- Return on Equity (ROE) = Net Income / Total Equity
- Operating Profit Margin = Operating Income / Total Sales
- Net Profit Margin = Net Income / Total Sales
- Interest Coverage Ratio = EBIT / Interest Payment
- Financial Cost Burden = Total Financial Costs / Total Sales
- Net Financial Cost Burden = (Total Financial Costs - Total Interest Income) / Total Sales
- Revenue Growth Rate = (This Year’s Revenue / Last Year’s Revenue) - 1
- Total Asset Growth Rate = (This Year’s Assets / Last Year’s Assets) - 1
- Equity Growth Rate = (This Year’s Equity / Last Year’s Equity) - 1
- Days Sales Outstanding (DSO) = Receivables / Sales * 365
- Days Inventory Outstanding (DIO) = Inventory / Cost of Goods Sold * 365
- Days Payable Outstanding (DPO) = Payables / Cost of Goods Sold * 365
- Debt Service Coverage Ratio (DSCR) = Net Income + Depreciation + Other Amortization + Financial Costs / Short-Term Borrowings + Long-Term Borrowings + Bonds + Financial Costs
- Total Borrowing Repayment Capacity = Cash Flow / Total Borrowings
- Free Cash Flow / Total Borrowings (%) = Free Cash Flow / Total Borrowings * 100
- Operating Cash Flow / Total Liabilities (%) = Operating Cash Flow / Total Liabilities * 100

![image](https://github.com/user-attachments/assets/3215c677-df52-4916-b203-a659107309cd)

### 3) Integration of Non-Financial/Financial Credit Rating Models:
The rating process reflects the real-world balance of financial and non-financial elements, where financial factors contribute 70% and non-financial factors 30% to the final rating. For this project, financial factors (calculated from the financial data) will comprise 70% of the score, and non-financial factors (quantified news headline data) will make up the remaining 30%. The final rating will be assigned as follows: a score of 70 or higher corresponds to an AAA rating, 67–69 to AA+, 64–66 to AA, and so on, with scores below 10 assigned to a D rating.



