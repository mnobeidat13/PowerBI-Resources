### Power BI Tutorial: Building a Report Using IBM HR Analytics Employee Attrition & Performance Dataset

![image](https://github.com/mnobeidat13/PowerBI-Resources/assets/32016587/d400769e-a7b2-4629-813f-8eebee100d1d)

#### Objectives

1. **Import Data**
   - Load the IBM HR Analytics Employee Attrition & Performance dataset into Power BI Desktop.

2. **Prepare Data**
   - **Transform Columns**:
     - Change data types as needed (e.g., Date columns).
     - Filter and clean the data.

3. **Create Calculations**
   - Write DAX expressions to create measures like "Total Attrition Rate", "Average Age", and "Average Monthly Income".

4. **Build Visualizations**
   - **Visuals to Create**:
     - **Pie Chart**: Overall Attrition Rate.
     - **Bar Chart**: Attrition by Department and Job Role.
     - **Line Chart**: Attrition over Time.
     - **Table**: Employee Demographics (Age, Gender, Education).
     - **Slicer**: Filter by Department, Job Role, Gender, etc.

5. **Format Report**
   - Apply themes and styles for visual clarity.
   - Add titles, labels, and tooltips.

6. **Publish Report**
   - Save the report and publish it to the Power BI service for sharing and collaboration.

---

### Detailed Steps

#### 1. Import Data
   - Download the dataset from [Kaggle](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset).
   - Open Power BI Desktop.
   - Go to `Home` > `Get Data` > `Text/CSV`.
   - Select the IBM HR Analytics Employee Attrition & Performance dataset file and load it.

#### 2. Prepare Data
   - Go to `Transform Data`.
   - **Change Data Types**:
     - Select the `Age` column and change its data type to `Whole Number`.
     - Select the `MonthlyIncome` column and change its data type to `Currency`.
   - **Filter and Clean Data**:
     - Remove any rows with missing values by using the `Remove Rows` function.
     - Filter out any irrelevant columns that are not needed for the analysis.

#### 3. Create Calculations
   - Go to `Modeling` > `New Measure`.
   - Create measures such as:
     ```DAX
     Total Attrition Rate = CALCULATE(COUNT(EmployeeID), Attrition = "Yes") / COUNT(EmployeeID)
     Average Age = AVERAGE(Age)
     Average Monthly Income = AVERAGE(MonthlyIncome)
     ```

#### 4. Build Visualizations
   - **Pie Chart**:
     - Go to `Visualizations` > `Pie Chart`.
     - Add the `Total Attrition Rate` measure.
   - **Bar Chart**:
     - Go to `Visualizations` > `Clustered Bar Chart`.
     - Add `Department` to Axis and `Attrition` to Values.
   - **Line Chart**:
     - Go to `Visualizations` > `Line Chart`.
     - Add `YearsAtCompany` to Axis and `Attrition` to Values.
   - **Table**:
     - Go to `Visualizations` > `Table`.
     - Add columns like `Age`, `Gender`, `Education`, and `Department`.
   - **Slicer**:
     - Go to `Visualizations` > `Slicer`.
     - Add fields like `Department`, `Job Role`, and `Gender`.

#### 5. Format Report
   - Customize visuals by applying themes from `View` > `Themes`.
   - Add titles, labels, and tooltips to enhance clarity.
   - Adjust the size and position of each visual for better layout and readability.

#### 6. Publish Report
   - Go to `File` > `Save As` and save your report.
   - Go to `Home` > `Publish` to upload your report to the Power BI service for sharing and collaboration.

By following these detailed steps, you can create a comprehensive HR analytics report in Power BI using the IBM HR Analytics Employee Attrition & Performance dataset.
