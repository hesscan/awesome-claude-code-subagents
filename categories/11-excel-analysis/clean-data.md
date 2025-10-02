**"Clean up this Export" - Complete Prompt**

**textCONTEXT:** I have a messy data **export** from [specify: bank/Salesforce/Quickbooks/etc.] that needs to be cleaned and organized for business analysis.

**CURRENT STATE:** The data has issues like: inconsistent formatting, duplicate entries, missing categories, mixed date formats, text in number fields, and unclear column headers.

**EDITING TASK:** Transform this into a clean, analysis-ready dataset by:

**1. DATA CLEANING:**
*   Standardize all date formats to MM/DD/YYYY
*   Remove duplicate entries (flag count of duplicates removed)
*   Clean up text fields (proper case, remove extra spaces)
*   Convert text numbers to actual numbers
*   Fill in obvious missing data where possible

**2. CATEGORIZATION:**
*   Create standard business expense categories: Office Supplies, Travel, Software, Marketing, Professional Services, Rent/Utilities, Meals & Entertainment, Other
*   Categorize each expense automatically where clear, flag ambiguous ones for manual review
*   Add a "Review Needed" column for items requiring human judgment

**3. ANALYSIS PREPARATION:**
*   Create monthly summary totals by category
*   Add variance to budget column (if budget data provided)
*   Calculate running totals and averages
*   Flag any entries over $[specify threshold] as "Large Expense"

**4. QUALITY CHECKS:**
*   Verify total of cleaned data matches original
*   List all assumptions made during cleaning
*   Highlight any data that couldn't be automatically categorized
*   Create a summary of changes made

**OUTPUT FORMAT:** Clean dataset with summary dashboard showing total by category, monthly trends, and items requiring review.

**VALIDATION:** Ensure all formulas are error-free and totals reconcile to source data.