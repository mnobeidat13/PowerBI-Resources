### Tutorial Series: From Excel Workbook to Stunning Report in Power BI Desktop

![image](https://github.com/mnobeidat13/PowerBI-Resources/assets/32016587/980f4490-fc28-41ea-8370-ee2730528380)

#### Objectives

1. **Import Data**
   - Load the Financial sample Excel workbook into Power BI Desktop.

2. **Prepare Data**
   - **Transform Columns**:
     - Change data types for "Date" and "Profit".
     - Format columns for readability.
     - Filter out unnecessary data.

3. **Create Calculations**
   - Write DAX expressions to create measures such as "Total Profit" and "Sales by Product".

4. **Build Visualizations**
   - **Visuals to Create**:
     - Title for the report.
     - Line chart for Profit by Date.
     - Map for Profit by Country.
     - Bar chart for Sales by Product and Segment.
     - Slicer for Year selection.

5. **Format Report**
   - Apply themes and styles for visual clarity and consistency.

6. **Publish Report**
   - Save the report and publish it to the Power BI service for sharing and collaboration.

### Detailed Steps

#### 1. Import Data
- **Load Excel Workbook**:
  1. Open Power BI Desktop.
  2. Click on "Get Data" and select "Excel".
  3. Navigate to the location of the Financial sample Excel workbook and open it.
  4. In the Navigator window, select the relevant sheets and click "Load".

#### 2. Prepare Data
- **Transform Columns**:
  1. Go to the "Home" tab and click on "Transform Data".
  2. In Power Query Editor, select the "Date" column, and change its data type to Date.
  3. Select the "Profit" column and change its data type to Decimal Number.
  4. Format columns as necessary (e.g., currency format for financial data).
  5. Apply any filters needed to remove irrelevant data.
  6. Click "Close & Apply" to save changes.

#### 3. Create Calculations
- **Write DAX Expressions**:
  1. Go to the "Modeling" tab and select "New Measure".
  2. Enter the DAX formula for Total Profit:
     ```DAX
     Total Profit = SUM(Financials[Profit])
     ```
  3. Create other measures as needed, such as "Sales by Product":
     ```DAX
     Sales by Product = SUM(Financials[SalesAmount])
     ```

#### 4. Build Visualizations
- **Add Visuals**:
  1. **Title**:
     - Add a text box from the "Insert" tab and enter the report title.
  2. **Line Chart for Profit by Date**:
     - In the Visualizations pane, select the Line Chart.
     - Drag the "Date" field to the X-axis and the "Total Profit" measure to the Y-axis.
  3. **Map for Profit by Country**:
     - Select the Map visual.
     - Drag the "Country" field to the Location and the "Total Profit" measure to the Size.
  4. **Bar Chart for Sales by Product and Segment**:
     - Select the Clustered Bar Chart.
     - Drag the "Product" field to the Axis, "Segment" field to the Legend, and "Sales by Product" measure to the Values.
  5. **Slicer for Year Selection**:
     - Select the Slicer visual.
     - Drag the "Year" field to the Field box.

#### 5. Format Report
- **Enhance Visual Appeal**:
  1. Apply a theme from the "View" tab by selecting "Themes".
  2. Adjust visual settings, such as colors and fonts, to ensure clarity.
  3. Use alignment tools to organize visuals neatly.

#### 6. Publish Report
- **Save and Publish**:
  1. Save the report by clicking "File" > "Save As".
  2. To publish, click "Home" > "Publish".
  3. Sign in to your Power BI account and select the workspace to publish the report.

For detailed steps, refer to the [tutorial](https://learn.microsoft.com/en-us/power-bi/create-reports/desktop-excel-stunning-report).
