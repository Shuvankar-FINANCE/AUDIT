Excel Financial Audit Tool
Description
The Excel Financial Audit Tool is a Python script designed to audit financial data in .xlsx or .csv files. It verifies compliance with predefined rules for financial reporting (e.g., French GAAP, IFRS, and legal standards). If the data contains errors or discrepancies, the script generates a detailed audit report in Excel format.

Features
Supports .xlsx and .csv Files:
Automatically detects the file format.
Processes single and multi-sheet Excel files.
Compliance Checks:
Total assets must equal liabilities + equity.
Revenue must not be negative.
Depreciation methods must be valid (straight_line or diminishing_balance).
VAT Paid must be greater than or equal to VAT Collected.
Employee expenses must be within legal thresholds.
Detailed Reporting:
Outputs the failed rules and affected rows to an audit results file.
Handles Missing Data:
Logs rows with missing columns or invalid data.
Prerequisites
Python Version:
Python 3.8 or higher is recommended.
Required Libraries:
pandas
openpyxl (for working with .xlsx files)
Install the libraries using:

bash
Copy code
pip install pandas openpyxl
Usage
1. File Preparation
Ensure your financial data is in a properly formatted .xlsx or .csv file.
Verify that column names match the script's expected names:
Total Assets
Total Liabilities
Equity
Revenue
Depreciation Method
VAT Paid
VAT Collected
Employee Expenses
Legal Threshold
2. Run the Script
Place your file (e.g., Q3 2024 Databook KPIs - Excel.xlsx) in the same directory as the script.
Update the input_file_path variable in the script with your file's name:
python
Copy code
input_file_path = "Q3 2024 Databook KPIs - Excel.xlsx"
Run the script:
bash
Copy code
python excel_financial_audit.py
3. Output
The script generates an audit report (audit_results.xlsx) in the same directory.
If no errors are found, the script will notify:
plaintext
Copy code
No flaws found. Audit results are empty.
Sample Input
Input Excel File (financial_data.xlsx):

Total Assets	Total Liabilities	Equity	Revenue	Depreciation Method	VAT Paid	VAT Collected	Employee Expenses	Legal Threshold
100000	60000	40000	120000	straight_line	1200	1000	30000	35000
200000	150000	50000	-500	other	800	900	25000	30000
Sample Output
Audit Results (audit_results.xlsx):

Sheet	Row	Rule	Status
Sheet1	2	Revenue must not be negative	Failed
Sheet1	2	Depreciation method must be valid	Failed
Sheet1	2	VAT Paid must be greater than or equal to VAT Collected	Failed
Customization
Column Names:
If your file uses different column names, update the columns_required values in the run_checks method.
Additional Rules:
Add new rules by appending to the checks list in the script.
Troubleshooting
Issue: "File is not a zip file"
Ensure the file is saved in .xlsx or .csv format.
Open the file in Excel and resave it as .xlsx.
Issue: "Missing Required Columns"
Ensure column names in your file match the expected names.
Update the script to match your file's column names.
Issue: "Empty Audit Results"
If the output file is empty, it means the data complies with all rules. This is a good outcome!
License
This tool is free to use and modify for personal or business purposes.
