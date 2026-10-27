Dog Adoption Analysis — Power BI & Tableau
A data analytics and visualization project exploring dog adoption patterns using a dog-adoption dataset obtained from Kaggle. The project focuses on understanding the dogs represented in the dataset, examining adoption status, and comparing adoption patterns across attributes such as age, breed, gender, size, and location where those fields are available.

The analysis is designed to be explored in Power BI and Tableau, with Python used for exploratory data analysis (EDA) and initial data checks.
Note: This README documents the project workflow and planned analyses based on the project details available. The exact Kaggle dataset title, column names, final dashboard screenshots, and numerical findings were not available when this file was prepared. Replace the placeholders below with the exact details from your dataset and finished dashboards. Do not report figures that have not been calculated from the data.

Table of contents
- Project overview
- Objectives
- Tools and technologies
- Dataset
- Questions explored
- Data preparation
- Exploratory data analysis
- Power BI dashboard
- Tableau dashboard
- Suggested measures
- How to reproduce the project
- Key findings
- Limitations
- Future improvements
- Project structure
- Author
Project overview
Dog shelters and adoption platforms manage information about animals that need homes. Looking at this information through charts can help people understand the types of dogs listed and how adoption status varies across different groups.

This project turns a dog-adoption CSV dataset into an interactive analytics experience. It uses exploratory analysis and dashboards to examine:
- The number of dogs included in the dataset.
- The distribution of adoption statuses.
- Dog age, breed, gender, and size patterns.
- Differences in adoption status across dog attributes.
- Location-based patterns, if the dataset includes location fields.
- Relationships between available numerical and categorical variables.
The goal is to make the dataset easier to understand through clear visuals and interactive filters—not to claim that a particular attribute causes a dog to be adopted.
Objectives
1. Load and inspect a dog-adoption dataset sourced from Kaggle.
2. Check data quality, including missing values, duplicate records, and inconsistent categories.
3. Explore the dataset using Python and visualizations.
4. Build an interactive dashboard in Power BI.
5. Build a comparable interactive dashboard in Tableau.
6. Compare adoption status across available attributes such as age, breed, gender, and size.
7. Present useful observations in a form that is easy to understand.
Tools and technologies
Tool	Purpose
Python	Initial data inspection and exploratory analysis
pandas	Loading, checking, and preparing tabular data
Matplotlib / Seaborn	EDA charts, if used in the notebook
Power BI Desktop	Data transformation, measures, and interactive dashboard
Power Query	Cleaning and transforming data in Power BI
DAX	Creating calculated measures in Power BI
Tableau Desktop / Tableau Public	Building worksheets, dashboards, and filters
CSV	Dataset file format


Only list a library or tool here if it was actually used in your final project.
Dataset
- Source: Kaggle
- Dataset name: [Add the exact Kaggle dataset title]
- Dataset URL: [Paste the Kaggle dataset URL]
- File: [Add the CSV filename]
- Rows: [Add row count after loading]
- Columns: [Add column count after loading]
The dataset contains records about dogs and their adoption-related details. The exact fields depend on the selected Kaggle dataset. Possible fields to look for include:
Data category	Example fields (confirm against your CSV)	What it can help examine
Adoption	Adoption status, adopted flag, adoption date	Adoption outcomes
Dog details	Age, breed, gender, size, color	Characteristics of listed dogs
Location	City, state, shelter, or region	Geographic patterns
Listing details	Listing date, shelter ID, record ID	Listing activity and record tracking


Important: The examples above are not a claim that every field exists in the selected dataset. Use the actual column names from the CSV, and document any renamed or derived fields.
Questions explored
The project is intended to answer questions such as:
1. How many dog records are present in the dataset?
2. What proportion of records fall into each adoption-status category?
3. Which age groups appear most often?
4. Which breeds occur most frequently?
5. How is the dataset divided by gender?
6. Does adoption status vary across age groups?
7. Do some breeds show different adoption-status distributions?
8. Does adoption status vary by gender or size?
9. Are there visible differences across locations, if location data is available?
10. Which relationships between numerical variables are worth investigating?
The answers should be based on the actual charts and calculations, not assumptions.
Data preparation
The CSV should be checked before creating dashboard visuals. The cleaning process may include the following steps, depending on what the data requires:
1. Load the file: Import the CSV into Python, Power Query, and Tableau.
2. Inspect the schema: Review column names, data types, row count, and sample records.
3. Check missing values: Identify which columns have missing data and decide whether to retain, replace, or exclude affected records.
4. Check duplicates: Look for duplicate rows and, if available, repeated record IDs. Remove records only when they are genuinely duplicated.
5. Standardize categories: Make inconsistent labels consistent, such as capitalization or extra spaces in breed, gender, or status values.
6. Correct data types: Convert numeric fields to numbers, dates to date types, and categories to appropriate text or categorical types.
7. Validate age values: Check for impossible, negative, or clearly incorrect ages before grouping them.
8. Review adoption status: Confirm what each status means and avoid treating unknown or pending statuses as adopted or not adopted without a documented rule.
9. Create derived fields if useful: For example, age groups or a numeric adopted flag, provided the original fields support the calculation.
10. Validate totals: Compare record counts and category totals before and after cleaning.
Document the final cleaning decisions so the analysis can be reproduced.
Exploratory data analysis
Python EDA can be used to understand the dataset before designing the dashboards. The planned checks include:
- Dataset shape and data types.
- Missing-value counts.
- Duplicate-row counts.
- Summary statistics for numerical columns.
- Frequency counts for categorical columns.
- Age distribution.
- Most common breeds.
- Gender distribution.
- Adoption-status distribution and adoption rate, if status is defined clearly.
- Adoption status compared with age, breed, gender, and size.
- Correlations between suitable numerical variables.
For categorical variables, compare counts or percentages across groups. For numerical variables, inspect distributions and outliers before drawing conclusions. Correlation does not prove causation.
Power BI dashboard
The Power BI workflow uses Power BI Desktop to import the CSV, clean it with Power Query, create measures with DAX, and arrange visuals on an interactive report page.
Recommended visuals
Visual	Purpose
Total Dogs card	Shows the number of dog records represented
Adoption Rate card	Shows the adoption rate when the dataset supports a valid definition
Adoption Status chart	Compares the number of records in each status
Age Distribution chart	Shows how dogs are distributed by age or age group
Top Breeds chart	Highlights the most frequent breeds
Gender chart	Shows the distribution by gender
Age vs Adoption chart	Compares adoption outcomes across age groups
Breed vs Adoption chart	Compares adoption outcomes for selected breeds
Gender vs Adoption chart	Compares adoption outcomes by gender
Size chart	Shows size distribution or adoption status by size, if available
Location map/chart	Shows geographic distribution when reliable location data exists
Slicers	Let users filter by available fields such as status, breed, gender, age group, size, or location


These are recommended visual types based on the project plan. Keep only the visuals that appear in the actual report.
Example DAX measures
The measure definitions must match the actual table and column names. The following examples assume a table named Dogs and a status column named AdoptionStatus. Replace these names and status labels to match the CSV.
Total Dogs =
COUNTROWS(Dogs)
If each row represents one unique dog, the measure above counts records. If a reliable unique dog ID exists, a distinct count may be more appropriate.
Adopted Dogs =
CALCULATE(
    COUNTROWS(Dogs),
    Dogs[AdoptionStatus] = "Adopted"
)
Adoption Rate =
DIVIDE(
    [Adopted Dogs],
    CALCULATE(
        COUNTROWS(Dogs),
        NOT ISBLANK(Dogs[AdoptionStatus])
    ),
    0
)
Format Adoption Rate as a percentage. This example excludes blank statuses from the denominator but may need adjustment if the dataset has categories such as Pending, Unknown, or Returned. Confirm the meaning of each category before finalizing the measure.
Power BI workflow
1. Open Power BI Desktop.
2. Import the CSV using Get Data → Text/CSV.
3. Select Transform Data to open Power Query.
4. Check column names, data types, missing values, duplicates, and category consistency.
5. Apply the transformations and load the cleaned data.
6. Create the measures needed for totals and adoption analysis.
7. Add charts, KPI cards, and slicers.
8. Configure interactions so filters affect the intended visuals.
9. Check titles, labels, tooltips, number formats, and accessibility.
10. Validate displayed totals against the source data and save the .pbix file.
Tableau dashboard
The Tableau workflow connects to the same cleaned CSV, creates worksheets for individual analyses, and combines them into a dashboard.
Recommended worksheets
- Total Dogs KPI
- Adoption Rate KPI
- Adoption Status
- Age Distribution
- Top 10 Breeds
- Gender Distribution
- Age vs Adoption
- Breed vs Adoption
- Gender vs Adoption
- Location view, if the data supports geographic mapping
Tableau workflow
1. Open Tableau Desktop or Tableau Public.
2. Connect to the CSV file.
3. Review field names and assign suitable data types.
4. Clean or standardize fields where needed.
5. Create calculated fields for adoption rate, age groups, or other derived values only when supported by the data.
6. Build separate worksheets for the required KPIs and analyses.
7. Combine the worksheets into a dashboard.
8. Add filters for available attributes such as adoption status, breed, gender, age group, size, and location.
9. Configure filter actions and tooltips.
10. Check that totals and percentages agree with the source data and Power BI report.
11. Save the workbook and publish it only if the project requires an online version.
Example Tableau calculations
These examples assume [Adoption Status] is the actual field and "Adopted" is the exact status label in the data. Adjust the names and labels as necessary.

Adopted flag
IF [Adoption Status] = "Adopted" THEN 1
ELSE 0
END
Adoption rate
SUM([Adopted Flag]) / COUNT([Adoption Status])
Format the result as a percentage. This calculation assumes each non-null status represents one dog record and that the status categories have been checked. If the dataset has other statuses that should not be included in the denominator, define the denominator explicitly.
Suggested measures
Use definitions that match the data and clearly state the denominator.
Measure	Definition
Total dog records	Number of records after documented cleaning
Adopted records	Number of records whose status meets the dataset's adopted definition
Adoption rate	Adopted records divided by eligible records with a known status
Dogs by age group	Number of records in each defined age group
Dogs by breed	Number of records in each breed category
Adoption rate by group	Adopted records in a group divided by eligible records in that group
Unknown-status records	Number of records with a missing or unknown adoption status


If the dataset contains repeated listings, multiple records per dog, or a time period with incomplete outcomes, record counts and rates may not represent unique dogs or final adoption outcomes. Explain those limitations.
How to reproduce the project
1. Download the dataset from the Kaggle link recorded above.
2. Place the CSV in the project data folder.
3. Run the EDA notebook or Python script, if one is included.
4. Apply the documented cleaning steps.
5. Open the cleaned CSV in Power BI and follow the Power BI workflow.
6. Open the same cleaned CSV in Tableau and follow the Tableau workflow.
7. Compare totals and adoption-rate definitions across both tools.
8. Save the dashboard files and add screenshots to the repository.
9. Update the findings section with observations supported by the finished dashboards.
No Python package installation commands are included here because the exact notebook and dependency list have not been confirmed. Add a requirements.txt if the project includes a Python environment.
Key findings
Add the actual results from your analysis here. For each finding, include the relevant number or percentage and the visual that supports it.
- Dataset summary: [Number of records, columns, and date range if available]
- Adoption status: [Counts and percentages for each status]
- Age pattern: [Observed age-group pattern]
- Breed pattern: [Observed breed pattern]
- Gender pattern: [Observed gender pattern]
- Other observation: [A supported result involving size, location, or another available field]
Do not leave these placeholders in a final portfolio version. Avoid statements such as “younger dogs are adopted more often” unless the calculated rates in the dataset actually support that conclusion.
Limitations
- The analysis reflects only the records and time period included in the selected dataset.
- Missing or inconsistent values can affect comparisons.
- Adoption-status labels may not describe the same stage of the adoption process.
- A high number of records for a breed does not necessarily mean that breed has a high adoption rate.
- Observed associations do not establish cause and effect.
- Geographic analysis depends on the completeness and quality of location fields.
- If the data contains listings rather than unique dogs, duplicate or repeated listings may affect counts.
Future improvements
- Add a documented data dictionary for every column.
- Create consistent age groups and status definitions.
- Add time-based analysis if listing or adoption dates are available.
- Compare Power BI and Tableau results using the same measures and filters.
- Add dashboard screenshots and a short explanation of each major insight.
- Publish an interactive version, if permitted by the dataset licence and project requirements.
- Automate data-quality checks for missing values, duplicate IDs, and invalid categories.
Project structure
A suggested repository structure is:
dog-adoption-analysis/
├── data/
│   └── dog_adoption.csv
├── notebooks/
│   └── dog_adoption_eda.ipynb
├── power-bi/
│   └── dog_adoption_dashboard.pbix
├── tableau/
│   └── dog_adoption_dashboard.twbx
├── screenshots/
│   ├── power-bi-dashboard.png
│   └── tableau-dashboard.png
├── README.md
└── requirements.txt
This is a suggested structure, not a claim about the files currently present in your repository. Rename the example files to match your actual project. Do not commit a large raw dataset unless its licence and repository requirements allow it.
Author
Sajin Reyans J
- GitHub: SajinReyans
Built as a data analytics project to explore dog adoption data and present the results through interactive dashboards in Power BI and Tableau.
