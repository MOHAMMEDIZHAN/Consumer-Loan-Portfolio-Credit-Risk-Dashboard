# 📊 Consumer Loan Portfolio & Credit Risk Dashboard

![Power BI](https://img.shields.io/badge/Power_BI-2D579B?style=for-the-badge&logo=powerbi&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-FFB900?style=for-the-badge&logo=microsoft&logoColor=black)
![Data Analysis](https://img.shields.io/badge/Data_Analysis-3498DB?style=for-the-badge&logo=googledocs&logoColor=white)

## 📖 Overview
An interactive, end-to-end Power BI dashboard designed to analyze a **$355M consumer loan portfolio** spanning 448 customers. The project focuses on evaluating borrower financial health, segmenting credit risk by profession and demographics, and identifying delinquency patterns to aid in proactive risk mitigation.

## 🎯 Business Objective
Financial institutions must balance portfolio growth with default risk. This dashboard was built to answer critical questions:
* Where is the capital concentrated across different loan categories?
* Which borrower demographics (Age, Occupation, Family Size) exhibit the highest delinquency rates?
* Are customers living beyond their means based on Income vs. Expenditure ratios?
* How can we dynamically flag high-risk profiles based on returned cheques and dishonored bills?

## 🛠️ Data Preparation & Modeling (Power Query)
The raw dataset contained several formatting anomalies typical of real-world financial data, which were resolved in Power Query:
* **Currency Cleaning:** Removed Indian comma formatting (e.g., `10,00,000`) and trailing spaces from the `Loan Amount` column.
* **Data Standardization:** Grouped typos in `Loan Category` (e.g., merging "RESTAURANT" and "RESTAURANTS", fixing "DINNING" to "DINING").
* **Handling Missing Values:** Identified and replaced `BLANK` values in `Income` and `Expenditure` to prevent calculation errors in DAX.
* **Data Validation:** Corrected structural typos in `Customer_ID` (e.g., replacing `1B` with `IB`) and managed duplicate records.

## 🧮 Key DAX Logic
* **Dynamic Risk Categorization:** Created a calculated column using `SWITCH(TRUE())` to automatically classify customers into "High", "Medium", or "Low" risk based on overdue counts, returned cheques, and debt records.
* **Financial Health Metrics:** Calculated `Debt-to-Income Ratio` using `DIVIDE()` to handle edge cases where income was zero.
* **Age Binning:** Dynamically categorized customers into demographic brackets (Young Adult, Adult, Mature Adult, Senior Citizen).

## 📸 Dashboard Features

### Page 1: Portfolio & Risk Segmentation
*(Insert Screenshot 1 Here)*

* **Executive KPIs:** Tracks Total Customers (448), Total Loan Disbursed ($355M), Average Debt-to-Income Ratio (0.58), and Average Overdues (4.93).
* **Portfolio Distribution:** Visualizes the top 10 loan categories, highlighting that **Gold Loans** dominate the portfolio.
* **Demographic Split:** Donut charts breaking down loan distribution by Gender and Marital Status.
* **Risk Matrix:** A dynamic table mapping `Loan Risk` against `Profession`, instantly highlighting which jobs have the most "High Risk" borrowers.

### Page 2: Financial Health & Behavioral Analysis
*(Insert Screenshot 2 Here)*

* **Income vs. Expenditure:** Clustered bar chart comparing average earnings against spending by occupation to identify negative cash flow behaviors.
* **Behavioral Scatter Plot:** Plots `Use Frequency` against `Overdues`, sized by `Debt Record`, to identify toxic borrowing behaviors.
* **Family Size Impact:** Analyzes how the number of dependents correlates with the average loan amount taken.
* **Delinquency Tracking:** Monitors hard metrics like Total Returned Cheques (2K) and Total Dishonoured Bills (2K).

## 💡 Key Insights Uncovered
1. **High-Volume, High-Risk:** While Gold Loans make up the largest chunk of the portfolio, they also exhibit highly clustered delinquency rates compared to Housing or Educational loans.
2. **Cash Flow Discrepancies:** Specific white-collar professions show average expenditures dangerously close to, or exceeding, their average income, correlating with higher returned cheque frequencies.
3. **Family Size Factor:** Borrowers with a family size of 6 or more show a disproportionate spike in both loan amounts and overdue frequencies, indicating financial strain.

## 🚀 How to View
1. Download the `Consumer_Loan_Dashboard.pbix` file from the repository.
2. Ensure you have [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/) installed on your machine.
3. Double-click the `.pbix` file to open and interact with the dashboard.

## 📌 Future Enhancements
* [ ] Integrate predictive machine learning models (e.g., logistic regression) to predict probability of default.
* [ ] Add a date table to track portfolio performance over time (currently a static snapshot).
* [ ] Implement Row-Level Security (RLS) to restrict data views by branch or region.
