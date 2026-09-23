# HR-Analytics-Capstone-Python
My project on Analytics using Python in Jupyter Notebook

# HR Analytics & Employee Performance
> A Python ETL pipeline that ingests, cleans, and merges multi-source HR datasets into a single master analytics dataframe — engineering performance metrics that power HR leadership reporting and decision-making.

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat-square&logo=python) ![Pandas](https://img.shields.io/badge/Library-Pandas%20%7C%20NumPy-green?style=flat-square) ![Jupyter](https://img.shields.io/badge/Notebook-Jupyter-orange?style=flat-square&logo=jupyter)
## Business Questions Answered

1. **Project Outcomes & Financial Impact** – Which employees are linked to completed vs. failed projects, and what is the resulting financial impact?
2. **Cost Attribution** – How does total project cost break down by manager?
3. **Promotion Eligibility** – Which employees qualify for a designation promotion based on age and performance criteria?
4. **Bonus Distribution** – How are bonus payouts distributed across completed projects?
5. **Geographic Concentration** – Which city clusters have the highest concentration of project-active employees?

## 💡 Key Outputs Delivered

| Output | Detail |
|---|---|
| **Master analytics dataframe** | Single merged table across employees, projects, and seniority — ready for reporting |
| **Bonus column engineered** | 5% of project cost applied automatically to all "Finished" status projects |
| **Designation adjustments applied** | Employees on failed projects demoted; employees aged 29+ promoted — rule-based logic |
| **Per-manager cost totals** | Grouped aggregation of total project spend per reporting manager |
| **City-based employee filter** | Segment of employees by geographic cluster for regional HR planning |

## 🔧 ETL Pipeline — Step by Step
Raw Data (3 .xls files)

        │
        ▼
[1] Load & Inspect
    • Read employee.xls, project.xls, seniority.xls into DataFrames
    • Check dtypes, null counts, shape

        │
        ▼
[2] Clean & Transform
    • Fill missing Cost values using running average (for-loop logic)
    • Split full Name into First_Name and Last_Name columns
    • Add title prefix (Mr./Mrs.) based on Gender → drop Gender column
    • Cast data types for consistency

        │
        ▼
[3] Merge
    • LEFT JOIN: employees + projects on employee ID
    • LEFT JOIN: merged df + seniority on employee ID
    • Result: single master dataframe

        │
        ▼
[4] Feature Engineering
    • Bonus = 5% of Cost WHERE Status = 'Finished'
    • Designation -= 1 WHERE Status = 'Failed' (demotion)
    • Designation += 1 WHERE Age > 29 (promotion)
    • Total_Project_Cost = SUM(Cost) GROUP BY Manager

        │
        ▼
[5] Output
    • Final master dataframe exported to CSV
    • Jupyter Notebook with inline commentary for stakeholder review
    
## Tasks Completed

| # | Task | Technique |
|---|---|---|
| 1 | Created 3 DataFrames from raw XLS files | `pd.read_excel()` |
| 2 | Filled missing cost values | Running average loop |
| 3 | Split full name into First/Last | `str.split()`, column assignment |
| 4 | Merged all 3 DataFrames into master | `pd.merge()` (LEFT JOIN) |
| 5 | Added bonus column (5% for finished projects) | `np.where()`, conditional assignment |
| 6 | Demoted designation for failed project employees | Boolean mask + in-place update |
| 7 | Added Mr./Mrs. prefix, dropped Gender column | `np.where()`, `df.drop()` |
| 8 | Promoted designation for employees aged 29+ | Conditional logic |
| 9 | Computed total project cost per employee | `groupby().sum()` |
| 10 | Filtered employees by city name containing 'o' | `str.contains()` |
    
