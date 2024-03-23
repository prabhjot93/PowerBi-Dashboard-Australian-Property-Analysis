# PowerBi-Dashboard-Australian-Property-Analysis

[Live Dashboard Link](https://www.novypro.com/project/industry-connectmvp-studio-australian-property-analysis-report)

Australia_Property_Analysis_2017_Dataset
The Australian Property Analysis powerBI dashboard report includes exploring weekly rental values, house values, type of schools, 
crime rates and transport availability across distinct suburbs(postcodes), cities and states. It compiles analyzed data and delivers easily consumable and actionable insights for users.

Key Learnings:
Load Data, ETL, SSIS, Handling data cleaning, missing information, and duplicates, appending queries, merging tables. Used Power query for data transformations and to have conditional coiumns, custom columns to enter own M language formulas.
Created snowflake schema with facts and dimension tables to load clean and useful data to data model. Established relationships in schema diagram.
Developed DAX measures to analyse KPIs for comparing median house values, rental prices in order to suggest affordable locations.

TransportReport
This report visualises existence of different modes of transport and their locations across suburb/states.

HouseValueReport
It compares property prices by states/metropolitan cities/regional cities and demonstrates average price values in different categories/groups, which in turns provides insights for most expensive vs affordable areas to invest and reside.

SchoolReport
 Schools report covers important details of school location, type of institution(
primary schools/high schools/central community schools/daycare centres), nearby transport availability, cost of living in terms of median house value/rental prices and recorded crimes in particular suburb.

CrimeIncidentsReport
The crime report contains analysis of different top crime categories and their respective subcategories. It also demonstrates house value and rental amount with respect to crime rate in particular location.

RentalValueReport
Rental Value Report compares average rental values, highest rental amount by house type among different locations. Amount has been divided into various groups to show maximum and minimum rental cost ranges within a selected city/state.
