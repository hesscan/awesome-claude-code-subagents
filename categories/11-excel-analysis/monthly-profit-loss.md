**TIER 1: QUICK WINS (5-15 minutes)**

**1. Monthly P&L from Raw Data**

**Context:** You have a CSV export from your accounting system, bank, or expense management tool with transactions that need to be turned into a proper P&L statement.

**Prompt Chain:**

**Step 1 - Data Cleaning:**

"I have raw transaction data with these columns: [list your columns – e.g., Date, Description, Amount, Vendor]. Please:

1.  Create a clean data table starting in cell A1
2.  Ensure dates are formatted as proper dates (MM/DD/YYYY)
3.  Ensure amounts are formatted as currency (no text, properly negative for expenses)
4.  Remove any duplicate transactions
5.  Add a column for "Month" that extracts the month from the date (format as "MMM-yy")
6.  Flag any rows with missing critical data [date, amount, or description] in a "Data Quality" column

Return the cleaned data in a new sheet called "Clean\_Data"."

**Step 2 - Expense Categorization:**

"Using the Clean\_Data sheet, create a new column called "Category" and categorize each transaction into these standard P&L categories:

*   **Revenue categories:** Product Revenue, Service Revenue, Other Revenue
*   **COGS categories:** Cost of Goods Sold, Direct Labor, Fulfillment Costs
*   **Operating Expense categories:** Salaries & Wages, Marketing, Sales, R&D, General & Administrative, Rent, Software & Subscriptions, Professional Services, Travel & Entertainment, Office Expenses, Other Expenses

Use the Description and Vendor fields to intelligently categorize. For example:

*   Payroll processors (Gusto, ADP) -> Salaries & Wages
*   AWS, Google Cloud, hosting -> Software & Subscriptions
*   Landlord payments -> Rent
*   Customer payments -> Product Revenue or Service Revenue

If you're uncertain about a transaction, mark it as "Needs Review" and add a note explaining why it's ambiguous."

**Step 3 - Monthly P&L Structure:**

"Create a new sheet called "P&L" with a proper income statement structure:

**Row structure:**

*   Header row with months across columns (current month and prior 11 months for rolling 12-month view)
*   Revenue section with subtotals
*   Gross Profit Line (Revenue – COGS)
*   Operating Expenses section with subtotals
*   Operating Income Line (Gross Profit – Operating Expenses)
*   Net Income Line

For each category, use SUMIFS to pull amounts from Clean\_Data where:

*   Category matches the row category
*   Month matches the column month

Format with:

*   Bold headers and subtotal rows
*   Currency formatting with $ symbols
*   Indentation for subcategories (using spaces before category names)
*   Border lines above subtotals
*   Different background shading for subtotal rows"

**Step 4 - Add Budget Variance:**

"Add columns next to each actual month for:

1.  Budget (I'll provide budget assumptions separately, or you can create a Budget Assumptions sheet where I can input targets)
2.  Variance ($) – calculated as Actual minus Budget
3.  Variance (%) – calculated as (Actual – Budget) / Budget

Add conditional formatting:

*   Favorable variances in green (revenue higher than budget, expenses lower than budget)
*   Unfavorable variances in red (revenue lower than budget, expenses higher than budget)
*   Apply to both $ and % variance columns

**Important:** Remember that for revenue, Actual > Budget is good (green), but for expenses, Actual < Budget is good (green). Apply the logic correctly."

**Step 5 - Validation:**

"Add a validation section at the bottom of the P&L sheet that checks:

1.  Do revenue totals match the sum of revenue categories in Clean\_Data? (show the difference if any)
2.  Do COGS totals match? (show difference)
3.  Do Operating Expense totals match? (show difference)
4.  Are there any transactions still marked "Needs Review" in Clean\_Data? (show count)
5.  Are all months in the Clean\_Data sheet represented in the P&L? (list any missing)

Display this as a simple checklist with ✓ or ✗ indicators."

**Expected Outcome:** A complete monthly P&L with 12 months of history, budget variance analysis, and built-in validation checks.