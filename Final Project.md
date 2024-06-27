# Final Project: Healtcare Data Analysis

Download the data:
[Healthcare_Data.xlsx](https://github.com/user-attachments/files/16009835/Healthcare_Data.xlsx)

### Detailed Steps for Power BI Training Project (Healthcare Sector)

### 1. Data Loading and Transformation

#### Steps:

1. **Load Data:**
   - Load the provided CSV files for Patients, Treatments, Medications, Doctors, Hospitals, and Dates into Power BI.
   - Use the `Get Data` feature and select the CSV files.

2. **Transform Data:**
   - Open Power Query Editor.
   - **Patients Table:**
     - Remove any rows with null values in `PatientID`, `FirstName`, `LastName`, `Gender`, and `DateOfBirth`.
     - Ensure `PatientID` is a whole number, `DateOfBirth` is a date, and `Email` is text.
   - **Treatments Table:**
     - Remove any rows with null values in `TreatmentID`, `PatientID`, `DoctorID`, `TreatmentDate`, and `Cost`.
     - Ensure `TreatmentID` is a whole number, `TreatmentDate` is a date, and `Cost` is a decimal number.
   - **Medications Table:**
     - Remove any rows with null values in `MedicationID`, `PatientID`, `MedicationName`, `Dosage`, `StartDate`, and `EndDate`.
     - Ensure `MedicationID` is a whole number, `StartDate` and `EndDate` are dates.
   - **Doctors Table:**
     - Remove any rows with null values in `DoctorID`, `FirstName`, `LastName`, `Specialty`, and `HospitalID`.
     - Ensure `DoctorID` is a whole number and `HospitalID` is a whole number.
   - **Hospitals Table:**
     - Remove any rows with null values in `HospitalID`, `HospitalName`, `City`, `State`, and `Region`.
     - Ensure `HospitalID` is a whole number.
   - **Dates Table:**
     - Ensure `Date` is a date and other columns are of appropriate data types (whole number for day, month, year, quarter; text for weekday).

### 2. Merging Data

#### Steps:

1. **Merge Queries:**
   - **Treatments and Patients:**
     - Merge Treatments with Patients on `PatientID`.
     - Keep columns from Treatments: `TreatmentID`, `PatientID`, `DoctorID`, `TreatmentDate`, `TreatmentType`, `Cost`.
     - Keep columns from Patients: `FirstName`, `LastName`, `Gender`, `DateOfBirth`.
   - **Treatments and Doctors:**
     - Merge the resulting table with Doctors on `DoctorID`.
     - Keep columns from Doctors: `FirstName` (rename to `DoctorFirstName`), `LastName` (rename to `DoctorLastName`), `Specialty`, `HospitalID`.
   - **Doctors and Hospitals:**
     - Merge Doctors with Hospitals on `HospitalID`.
     - Keep columns from Hospitals: `HospitalName`, `City`, `State`, `Region`.

### 3. Creating Columns and Tables

#### Steps:

1. **Create Calculated Columns:**
   - **AgeAtTreatment:**
     - In the Treatments table, create a calculated column `AgeAtTreatment` using the formula:
       ```DAX
       AgeAtTreatment = YEAR(Treatments[TreatmentDate]) - YEAR(Patients[DateOfBirth])
       ```
   - **FullName:**
     - In the Patients table, create a calculated column `FullName` using the formula:
       ```DAX
       FullName = Patients[FirstName] & " " & Patients[LastName]
       ```

2. **Create Calculated Tables:**
   - **Summary Table:**
     - Create a summary table for Treatments by Region using DAX:
       ```DAX
       SummaryByRegion = SUMMARIZE(
         Treatments,
         Hospitals[Region],
         "TotalCost", SUM(Treatments[Cost]),
         "TotalTreatments", COUNT(Treatments[TreatmentID])
       )
       ```

### 4. Creating Relationships

#### Steps:

1. **Define Relationships:**
   - Create relationships between the tables:
     - **Treatments to Patients:** `PatientID` to `PatientID`.
     - **Treatments to Doctors:** `DoctorID` to `DoctorID`.
     - **Doctors to Hospitals:** `HospitalID` to `HospitalID`.
     - **Treatments to Dates:** `TreatmentDate` to `Date`.

### 5. Creating Measures and Quick Measures

#### Steps:

1. **Create Measures:**
   - **Total Treatment Cost:**
     - Create a measure `TotalTreatmentCost` using the formula:
       ```DAX
       TotalTreatmentCost = SUM(Treatments[Cost])
       ```
   - **Average Treatment Cost per Patient:**
     - Create a measure `AverageTreatmentCostPerPatient` using the formula:
       ```DAX
       AverageTreatmentCostPerPatient = AVERAGEX(SUMMARIZE(Treatments, Treatments[PatientID], "Cost", SUM(Treatments[Cost])), [Cost])
       ```

2. **Create Quick Measures:**
   - **YTD Treatment Cost:**
     - Use the Quick Measures feature to create a Year-to-Date (YTD) Treatment Cost measure.

### 6. Creating and Managing Roles

#### Steps:

1. **Define Roles:**
   - **Doctors Role:**
     - Create a role named `Doctors` and restrict data to only show treatments performed by the logged-in doctor.
   - **Hospital Administrators Role:**
     - Create a role named `HospitalAdministrators` to restrict data to show only the hospitals they manage.

### 7. Creating Multipage Reports

#### Steps:

1. **Create Pages:**

   - **Page 1: Patient Overview:**
     - **Visuals:**
       - **Table of Patients:**
         - Add a table visual.
         - Fields: `FullName`, `Gender`, `DateOfBirth`, `Email`.
       - **Pie Chart for Gender Distribution:**
         - Add a pie chart visual.
         - Fields: `Gender` to Legend and `PatientID` to Values (Count).
       - **Age Distribution Histogram:**
         - Add a histogram visual.
         - Fields: `AgeAtTreatment` to Axis and `PatientID` to Values (Count).

   - **Page 2: Treatment Analysis:**
     - **Visuals:**
       - **Line Chart for Treatment Cost Over Time:**
         - Add a line chart visual.
         - Fields: `TreatmentDate` to Axis and `Cost` to Values (Sum).
       - **Bar Chart for Treatment Types:**
         - Add a bar chart visual.
         - Fields: `TreatmentType` to Axis and `Cost` to Values (Sum).
       - **Treemap for Treatment Costs by Region:**
         - Add a treemap visual.
         - Fields: `Region` to Group and `Cost` to Values (Sum).

   - **Page 3: Doctor Performance:**
     - **Visuals:**
       - **Table of Doctors with Treatment Counts:**
         - Add a table visual.
         - Fields: `DoctorFirstName`, `DoctorLastName`, `Specialty`, `TreatmentID` (Count).
       - **Bar Chart for Treatment Costs by Doctor:**
         - Add a bar chart visual.
         - Fields: `DoctorFirstName` & `DoctorLastName` (concatenated) to Axis and `Cost` to Values (Sum).
       - **Scatter Plot for Doctor Performance:**
         - Add a scatter plot visual.
         - Fields: `DoctorFirstName` & `DoctorLastName` (concatenated) to Details, `TreatmentID` (Count) to X-Axis, `Cost` (Sum) to Y-Axis.

2. **Add Slicers and Filters:**
   - **Date Slicer:**
     - Add a slicer for `TreatmentDate`.
   - **Region Slicer:**
     - Add a slicer for `Region`.
   - **Treatment Type Filter:**
     - Add a filter for `TreatmentType`.

3. **Drill Through:**
   - Set up drill-through from the summary page to a detailed treatment page by right-clicking on visuals and enabling drill-through.

4. **Grouping and Pinning:**
   - Group related visuals and pin them to a dashboard for quick access.

### 8. Final Report and Dashboard

#### Steps:

1. **Create a Final Report:**
   - Combine all the pages into a comprehensive report.
   - Ensure the report is well-organized and visually appealing.

2. **Publish to Power BI Service:**
   - Publish the report to the Power BI service.
   - Create dashboards and share them with the relevant stakeholders.
