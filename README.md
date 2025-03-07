# Himalaya Financial Dashboard

A Power BI project that integrates sales, financial, HR, and campaign data to provide comprehensive business analytics. The model connects dimension tables (Date, Product, Department, Personnel, Campaign) with fact tables (Sales, Time reports, Financial data) to enable multi-dimensional analysis of business performance across different time periods, departments, and products.

<img width="1439" alt="Image" src="https://github.com/user-attachments/assets/c978aed1-1cc5-4e9d-9f71-7b1b8d477517" />
<img width="1440" alt="Image" src="https://github.com/user-attachments/assets/76797a33-e8c5-462c-9a7d-522ea98ccf12" />
<img width="1453" alt="Image" src="https://github.com/user-attachments/assets/f00573fb-f70c-4dfc-b230-eccac5fbe018" />

## Data Model

The project uses a star schema model with the following main components:

### Dimension Tables

1. **Dim_Date**: Time dimension containing date, year, month, week, and other time-related attributes.
   - Used for time-based analysis and filtering

2. **Dim_Product**: Product dimension containing product information.
   - Key fields: Product ID, Product EAN/PLU, Product Name, Product VGR (grouping)

3. **Dim_Department**: Department dimension containing information about company departments.
   - Connected to products via the Product VGR field

4. **Dim_Personnel**: Personnel dimension containing information about employees.
   - Contains data such as employee ID, birth date, start date, end date

5. **Dim_Campaign**: Campaign dimension containing information about marketing campaigns.
   - Contains campaign week, start and end dates, discount levels
   - Connected to products via EAN/PLU number

### Fact Tables

1. **Fact_Sales**: Contains sales data.
   - Key measures: Sales_Quantity, Sales_Weight, Sales_Value, Sales_Margin(kr)
   - Connected to Dim_Date via Sales Date
   - Connected to Dim_Product via Product ID
   - Also contains campaign information such as Campaign Week and Campaign Discount %

2. **Fact_TimeReports**: Contains data about personnel time reports.
   - Connected to Dim_Personnel via EmployeeID
   - Connected to Dim_Date via Date

3. **Fact_Finance**: Contains financial data.
   - Contains Cost Type and Other Costs
   - Connected to Dim_Date via Date

### Relationships

The data model has the following main relationships:
- Fact_Sales is connected to Dim_Date via Sales Date
- Fact_Sales is connected to Dim_Product via Product ID
- Dim_Product is connected to Dim_Department via Product VGR
- Fact_TimeReports is connected to Dim_Personnel via EmployeeID
- Fact_TimeReports is connected to Dim_Date via Date
- Dim_Campaign is connected to Dim_Product via Product EAN/PLU
- Fact_Finance is connected to Dim_Date via Date

### Measures

For detailed documentation of all measures used in this project, please refer to the [Measure Documentation](./Measure_Documentation.md) file. This documentation provides comprehensive explanations of all measures organized by category:

- Sales Measures
- Campaign Measures
- HR Measures
- Financial Measures
- Other Cost Breakdown

## Reports and Visualizations

The dashboard contains several report pages focusing on different aspects of the business:

1. **Financial Overview**: Shows financial key metrics, cost analysis, and trends over time.
2. **HR Analysis**: Shows personnel efficiency, resource utilization, and personnel-related metrics.
3. **Campaign Analysis**: Analyzes the effectiveness of marketing campaigns and their impact on sales.
4. **Sales Analysis**: Shows sales trends, product performance, and margins.

## Data Sources

The project retrieves data from the following sources:
- SQL database (Xlent_Himalaya_DW) on the server utbildning.database.windows.net for sales, product, department, and personnel data
- Excel files for campaign and financial data (Campaign.xlsx, Finance.xlsx) stored both locally and on SharePoint
- Some data sources are configured to be retrieved from local files for development and testing
- SharePoint files are used to enable collaboration and central data storage

The data sources are configured with parameters to easily switch between different environments (local, SharePoint, production server).

### Parameter Configuration

To ensure correct data loading, you need to update the following parameters in Himalaya Financial Dashboard.SemanticModel/definition/expressions.tmdl:

Update the following parameter values:
- **server**: Set to your SQL Server address (default: utbildning.database.windows.net)
- **financeUrl**: Set to the path of your Finance.xlsx file
- **campaignUrl**: Set to the path of your Campaign.xlsx file
- **urlSharepoint**: Set to your SharePoint URL if using SharePoint for data storage

These parameters are used throughout the data model to connect to the correct data sources.