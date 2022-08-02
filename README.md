# General_Practice_Performance_Analysis

This project focuses on deploying an interactive visualization dashboard that provides useful insights into the cost of drugs prescribed by general practitioners from various perspectives for budget planning and drug-approval decision making. Given that NHS is a non-profit organization that seeks to provide free healthcare for everyone, NHS obtains its funds for covering the cost of prescribed drugs by general practitioners from general taxation. 

In recent years, the spending cost of drugs prescribed by GP practices rises every year, and this figure certainly increased exponentially with the rapid production of immunological products and vaccines. By designing an interactive dashboard for cost analysis, NHS would be able to obtain hidden insights related to the cost of drugs prescribed by GP practices from different levels of detail and the government would also be able to use this dashboard for allocating their annual budget, especially for NHS to cover the cost of drugs prescribed.

---

## Project Goals & Objectives
### Goals
- Conduct a cost analysis of drugs prescribed by General Practitioners on different hierarchy levels (i.e. General Practitioners, Locality, and Health boards) for various counties and BNF chapters.

### Objectives
- Build an interactive dashboard for analyzing the cost of drugs prescribed from various perspectives
- Provide useful insights into data provided by NHS for budget planning and drug approval decision-making

---

## Data Dictionary
For designing a cost analysis dashboard, these following relevant features are selected:

Table Name | Field Names | Description
--- | --- | --- 
GPData<Period> | PracticeID | Unique practice identifier starting with W. And this is code for the practice. It can potentially be used to linked to other data that uses the practice code as is defined by the NHS Digital Organisation Data Service (ODS). The format is Wxxxxx where "W" is a letter and "xxxxx" is a 5 digit number.
GPData<Period> | BNFCode | British National Formulary code which identifies the drug prescribed
GPData<Period> | Items | This gives the number of items for this presentation that were dispensed in the specified month.
GPData<Period> | NIC | This is the basic cost of a drug as used in primary care. This is the cost at list price excluding VAT, i.e. the price listed in the national Drug Tariff or in standard price lists and is not necessarily the price the NHS paid.
GPData<Period> | ActCost | From July 2012 onwards, the formula used to calculate 'Actual Cost' has been changed to include the new reimbursement payments which will be charged back to practices from dispensed prescriptions.
GPData<Period> | HB | Responsible Health Board for Practice
GPData<Period> | Locality | Responsible Locality within Health Board
GPData<Period> | Period | The year and month to which the data relates e.g. December 2012 would be 201212.
BNF | BNFChapter | Index of BNF Chapters
BNF | ChapterDesc | Name of BNF Chapters
BNF | BNFChemical | The first 9 characters of the BNF code.
Address | Period | The year and month to which the data relates e.g. December 2012 would be 201212.
Address | PracticeID | For a GP practice - Wxxxxx where x is a 5 digit number. For localities and Health Boards this is a 3 character code.
Address | Street | Often this is the name of the practice, when this is not available then the first line of the address will be shown.
Address | Area | 2nd line of the address
Address | Posttown | 3rd line of the address
Address | County | 4th line of the address
Address | Postcode | Postal code
(External Source) | NADP | National Average Discount Percentage is used to calculate actual cost shown in NHS Prescription Services prescribing and financial reports.

---

## Data Preprocessing
Using Python programming in Jupyter Notebook, the process of data cleaning to extract relevant features from various available table sources are as follows:
1. Combining dataset from every month into individual tables
- Monthly datasets for address, BNF and GP data are combined into 3 different tables, comprising of data for all relevant months
2. Data cleaning on features identified to have anomalies
- Any duplicated rows identified from the dataset is removed and anomalies related to incorrect names of BNF Chapters are addressed. Miscellaneous data transformations are also done on this stage.
3. Merging multiple tables into single table
- Address, BNF and GP tables are combined into a single table after some initial data cleaning.
4. Adding additional data relevant for analysis
- Information related to NADP (National Average Discount Percentage) and Counties based on postcode information are added accordingly from external sources, before merging with previously combined dataset.

---

## Dashboard Insights
The following screenshots below represents the initial view of the Tableau dashboard:

![image](https://user-images.githubusercontent.com/34255556/182285344-441ad78a-dc15-47c5-808d-fe17ad74685a.png)

![image](https://user-images.githubusercontent.com/34255556/182285382-7a976c41-b1f1-4869-b8aa-c8f626204639.png)

Here are some of the main insights that can be derived from the given dataset:

<b>1. Total actual cost by Top 5 counties</b>

<img src="https://user-images.githubusercontent.com/34255556/182286261-2b8a5163-3b25-4c1e-9d7d-a63f8f994095.png" height="500" width="700">

<b>2. Average reimbursement expense by Bottom 3 counties</b>

<img src="https://user-images.githubusercontent.com/34255556/182286331-4ead7b6e-ee40-46ab-be1d-df91724f8cb6.png" height="500" width="700">

<b>3. Trend analysis of total actual cost from All counties</b>

![image](https://user-images.githubusercontent.com/34255556/182286370-0e59a2fc-0f7a-4806-8512-abf24b1b54c5.png)

<b>4. Trend analysis of total reimbursement expense from All counties</b>

![image](https://user-images.githubusercontent.com/34255556/182286414-51c65742-b581-4a11-b14d-222d7bcccbd7.png)

<b>5. Median actual cost from All counties by BNF chapters</b>

![image](https://user-images.githubusercontent.com/34255556/182286470-bd4fa34b-63cc-4c6f-b87b-25691cd5d4ed.png)

<b>6. Outlier analysis of Average actual cost for Immunological Products and Vaccines Chapter in Swansea</b>

![image](https://user-images.githubusercontent.com/34255556/182286545-f74b6a7d-e537-4829-a718-ff4770c3f76e.png)

For more details about the insights derived, refer to the following website for access to the interactive Tableau dashboard: https://public.tableau.com/app/profile/yi.xian.liaw/viz/NHSCostAnalysisDashboard/CostAnalysisbyCountyPracticeID

---

## Legality
This is an internship project made with 360DIGITMG for non-commercial uses ONLY. This project will not be used to generate any promotional or monetary value for me, the creator, or the user.
