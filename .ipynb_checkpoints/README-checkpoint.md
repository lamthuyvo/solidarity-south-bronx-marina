# Analysis of Contributions to South Bronx City Council Candidates from Solidarity PAC Donors # 

This repository contains data and code analyzing Board of Elections Solidarity PAC Contributions data and New York City Campaign Finance Data for candidates Clarisa Alayeto and Raymond Santana

## Data ##

This analysis uses three public datasets containing campaign finance data from the [NYS Board of Elections](https://elections.ny.gov/) and [NYC Campaign Finance Board](https://www.nyccfb.info/). The spreadsheet comes from two sources:

- NYS Board of Elections Contributions by Recipient (Solidarity PAC Inc.):
    -  `BOE_SolidarityPAC.csv`: Raw Data of contributions filed between March 11, 2024 and December 30, 2024
    -  Updated according to NYS Campaign Finance Filing Calendar
- NYC Campaign Finance Board Candidate Contributions for Clarisa Alayeto and Raymond Santana:
    -  `Santana_20250417171857281.csv`: Raw data of Santana's contributions filed between February 24, 2025 and March 13, 2025
    -  `Alayeto_20250417171817101.csv`: Raw data of Alayeto's contributions filed between December 3, 2024 and March 13, 2025

The `BOE_SolidarityPAC.csv` spreadsheet contains the following columns relevant to the analysis:
-  `Contributor Name`— Name of contributor.
-  `Amount`— Contribution amount.
-  `Contribution Type`— Category of the donations made to candidate, committee, or political organization.

The `Santana_20250417171857281.csv` and `Alayeto_20250417171817101.csv` spreadsheets contain, among others, the following columns releavant to the analysis: 
-  `NAME`– Name of Contributor.
-  `AMNT`– Contribution amount.
-  `MATCHAMNT`– Public matching funds received in relation to Contributor `AMNT`
-  `CITY`— City of contributor's residence

For a full list of definitions, please refer to the NYC Campaign Finance Board's help file, `CY2013_CONTRIBUTION_KEY.xls`

## Methodology ##

The notebook `southbronx-solidaritypac-analysis.ipynb` cleans the spreadsheets `Santana_20250417171857281.csv`, `Alayeto_20250417171817101.csv`, and `BOE_SolidarityPAC.csv` and formats them for analysis.

**Part 1: Clean Board of Elections Data**

- Format the the `Amount` column as floats. 
- Remove special characters that prevent formatting the column as a float.
- Reduce the columns to only include relevant information.

**Part 2: Clean Candidate Data (Applied to both `Santana_20250417171857281.csv`, `Alayeto_20250417171817101.csv`)
- Remove any null values from the `NAME` column.
- Reduce the columns to only include relevant information.
- Sort by `AMNT` to see the highest donors.

**Part 3: Find Solidarity PAC Donors Who Contributed to South Bronx Candidates**
- Remove any extraneous spaces from the `NAME` column to ensure standarization when matching values across datasets.
- Create a new column called `Solidarity Donor` in the candidates' datasets which will be filled whether a value is found in both the `Contributor Name` column of Board of Elections Solidarity PAC Contributions data and the `NAME `column of the candidate data
- Filter the data to find the Solidarity PAC contributors who also donated to South Bronx candidates
- Group the Solidarity PAC contributors by their donation amount
- Find the sum of donations for each candidates
- Group the Solidarity PAC donors by city of residence


## Outputs ##

**Part 1** is saved as `output/boe_solidarity_donors_only.csv`

**Part 3** is saved in two files. The final output for Clarisa Alayeto is `clarisa_solidarity.csv` and Raymond Santana'a is saved as `santana_solidarity.csv`

## Running the analysis yourself ##

You can run the analysis youtself. To do so you'll need the following installed on your computer:
- Python 3
- The Python libraries specified in `requirements.txt`

## Licensing ##

All code in this repository is available under the MIT License. The data file in the output/ directory is available under the Creative Commons Attribution 4.0 International (CC BY 4.0) license. All files in the data/ directory are released into the public domain.

## Feedback / Questions? ##


Contact Marina Samuel at marinasamuel114@gmail.com
