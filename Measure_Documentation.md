# Measure Documentation

This document provides detailed explanations for all measures in the Himalaya Financial Dashboard.

## Sales Measures

- **Sales**: Calculates the total sales value from the Sales_Value column in the Fact_Sales table.

- **Margin kr**: Calculates the total margin in Swedish kronor from the Sales_Margin(kr) column.

- **LY Sales 2**: Calculates sales for the same period last year using the SAMEPERIODLASTYEAR function.

- **Product Price**: Calculates the product price by subtracting the margin from sales. The measure shows three alternative calculation methods (only the first one is active).

- **Margin %**: Calculates the margin percentage by dividing the total margin by the total sales value.

- **Ta bort tomma rader för rabatt för månadsnamn (Andreas)**: Utility measure that removes empty rows for discount by month name. Returns the average campaign discount only when a single product is filtered.

- **MTD Sales**: Calculates the month-to-date sales using the TOTALMTD function.

- **QTD Sales**: Calculates the quarter-to-date sales using the TOTALQTD function.

- **WTD Sales**: Calculates the week-to-date sales by determining the current week's start date and summing sales values between that date and the current date.

- **YTD Sales**: Calculates the year-to-date sales using the TOTALYTD function.

## Campaign Measures

- **TB1 (Total Margin After Campaign Weeks)**: Calculates the total margin after campaign discounts. TB1 is a key financial metric representing margin after campaign costs.

- **TG1 (%)**: Calculates TB1 as a percentage of total price including campaign.

- **Total Price incl Campaign**: Calculates the total price including campaign effects by subtracting campaign discounts from sales.

- **Campaign Discount kr**: Calculates the total campaign discount in kronor by multiplying sales value by discount percentage.

- **Result %**: Calculates the result as a percentage of total price including campaign. This shows the profit margin as a percentage.

- **Max TB1 Campaign Week**: Identifies the campaign week with the highest TB1 value. First finds the maximum TB1 value among campaign weeks with discounts, then returns the campaign week number that achieved this maximum value.

## HR Measures

- **Total Working Hours**: Calculates the total working hours by summing hours where the type is "Arbetstid" (Working time).

- **Pension Fee**: Calculates the pension fee based on monthly salary and pension percentage. Multiplied by -1 to show as a cost (negative value).

- **Employer Contribution**: Calculates the employer contribution based on monthly salary and contribution percentage. Multiplied by -1 to show as a cost (negative value).

- **Vacation Pay**: Calculates vacation pay for hourly employees based on monthly salary and vacation pay percentage. Multiplied by -1 to show as a cost (negative value).

- **Total HR Cost**: Calculates the total HR cost by summing all HR-related costs. Includes salary, employer contributions, pension fees, and vacation pay.

- **Total Monthly Salary**: Calculates the total monthly salary cost. Multiplied by -1 to show as a cost (negative value).

- **Average Hours Per Month**: Calculates the average working hours per month. If there are no working hours, returns "Left" (indicating employee has left), otherwise divides total working hours by 12 months.

## Financial Measures

- **TB2**: Calculates TB2 by subtracting other costs from TB1. TB2 is the next level financial metric after accounting for additional costs.

- **Result in kr**: Calculates the final result in kronor by combining TB1, other costs, and HR costs. This represents the bottom line profit/loss after all costs.

- **Other Costs**: Calculates the total of other costs. Multiplied by -1 to show as a cost (negative value).

## Other Cost Breakdown

- **- Rent**: Calculates the rent costs by filtering for "Hyra" cost type. Multiplied by -1 to show as a cost (negative value).

- **- Electricity**: Calculates the electricity costs by filtering for "El" cost type. Multiplied by -1 to show as a cost (negative value).

- **- Waste**: Calculates the waste management costs by filtering for "Sopor" cost type. Multiplied by -1 to show as a cost (negative value).

- **- Water**: Calculates the water costs by filtering for "Vatten" cost type. Multiplied by -1 to show as a cost (negative value).

- **- Other**: Calculates other miscellaneous costs by filtering for "Övrigt" cost type. Multiplied by -1 to show as a cost (negative value).

- **- Telecom**: Calculates the telecommunication costs by filtering for "Tele" cost type. Multiplied by -1 to show as a cost (negative value).

- **- Cleaning**: Calculates the cleaning costs by filtering for "Städning" cost type. Multiplied by -1 to show as a cost (negative value). 