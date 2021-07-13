# Udacity Provided Project

## Project Summary
We are given the task to study tourism behaviours and are called to clean up, process and develop a data model to catalyze the start of a project which will hopefully lead to a better interface for more efficient data collection and experimentation.
From the data collection, the hopes is that data analysts will be able to form relationships and patterns between cities where non-immigrants visit and the demographics of these cities.


# Step 1: Scoping the project and gathering data

## Datasets
- I94 Immigration Data:
This data comes from the US National Tourism and Trade Office.
This is where the data source is from: https://travel.trade.gov/research/reports/i94/historical/2016.html
This data was already provided inside sas_data folder in parquet file type.
We will use the following records:
1. i94Bir - Age of non-immigrant in years
2. admnum - Admission Number
3. i94res - 3 digit code of nationality
4. i94port - 3 character code of destination USA city
5. arrdate - arrival date in the USA (SAS date numeric field)
6. i94mode - 1 digit mode (plane, boat, etc) of travel code
7. i94visa - reason for immigration
8. gender - Non-immigrant sex
9. depdate - departure date in the USA (SAS date numeric field)
10. count - Used for summary statistics

- U.S. City Demographic Data comes from OpenSoft in csv file. We will use the following records:
1. City
2. Male Population
3. Female Population
4. Median Age (overall median age within the city population)
5. Total Population
6. Foreign-Born (number of foreign born residences)
7. State Code (USA state abbreviation of the City column)
8. Race (specifies race category suchas Asian, Alaskan Indian, Black, Hispanic, etc)
9. Count (number of people under specific race category anotated by Race column)



# Step 2: Explore and assess the data
Cleaning and Transforming the US Cities Demographics Dataset
- We can start by creating 2 separate datasets, 1) US and 2) US Race Count, by separating both race and count columns from the US demo dataset.
- US Race Count dataset includes 'City' and 'State Code' columns, as the interface to link them to the US dataset.
- If we were to join the two datasets, we will remove duplicate rows from the US dataset and pivot the US Race Count dataset, such that (theoretically), both datasets will have same number of rows for joining back into a single transformed table. (capstoneproject.ipynb)

capstoneproject.ipynb contains information on cleaning all data sets needed for this capstone project.



# Step 3: Define the Data Model
Dimensional tables will be saved as parquet files, and we can implement them on columnar databases -- Star schema model.
Star Schema makes it easier for Data Analysts / Data Scientists to apply queries with better flexibility.



# Step 4: Running the ETL to model the data
This project's data pipeline is built inside etl.py


# Step 5: Complete the project write-up
The project write-up can be found in `5_project_writeup.txt`


Reference:
https://github.com/paul-data-science/Udacity_Data_Engineering_Capstone





# Addressing Feedback:
To pass this specification, please also justify the choice of the data model. Why do you use star schema? Does it have any advantage compared to other schemas?
- Star schema is simpler than JOIN logic required to retrieve data from a normalized transactional schema
- When compared to highly normalized schemas, star schema simplifies common business reporting logic
- Star schemas provide better query performance for read-only reporting applications, compared to highly normalized schemas
- Simpler queries from star schemas provide improved performance for aggregation operations

Running etl.py:
- Run was executed with this log: etl-run-log.txt
- Parquet files were generated within /data
- Grouped code into functions

Data quality checks in capstoneproject.ipynb:
- Refactored code, grouping quality checks into functions.

Sample query if found in `capstoneproject.ipynb`
- Database Diagram found in `databasediagram1.PNG`