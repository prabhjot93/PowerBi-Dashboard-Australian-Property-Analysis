# PowerBi-Dashboard-Australian-Property-Analysis

[Live Dashboard Link](https://www.novypro.com/project/industry-connectmvp-studio-australian-property-analysis-report)

Australia_Property_Analysis_Report

Completed ‘Property Analysis’ project by extracting raw data from multiple Australian property datasets. Standardised data by creating snowflake schema model and automated ETL pipeline. Leveraged Visual Studio for SSRS paginated report.Compiled data from different datasets such as ‘Local Schools’, ‘Local Crime records’, ‘Local Transport data’, ‘Median House value’, and ‘Median Rental value’ to deliver professional PowerBI dashboard.Shared expertise and perspective with stakeholders to make decisions about buying, selling and investing in potential areas across Australia.

Please find key learnings, detailed description and key DAX measures used below:

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

Key core DAX Measures used:

1.  % of total housevalue = 
var _TotalValueBySuburbs =
    CALCULATE([TotalHouseValue],
    ALL())
return 
DIVIDE([TotalHouseValue],
    _TotalValueBySuburbs)

2.  %of RentalRangeInSuburb = var _RangesInSub= CALCULATE([TotalCountRange],ALL()) return
    DIVIDE([TotalCountRange],_RangesInSub)

3.  Avg Rent = AVERAGEX(FactRentalValue,FactRentalValue[RentalAmount])

4. Crime_DYNAMIC_LINK_SSRS = "http://my/ReportServer/Pages/ReportViewer.aspx?%2fAdvanceTaskSSRS%2fReportCrime&rs:Command=Render&state=" & SELECTEDVALUE('DimSuburb'[state])& "&city=" & SELECTEDVALUE('DimSuburb'[city]) & "&suburb=" & SELECTEDVALUE('DimSuburb'[suburb])

5.   GrandTotalHouseValue = var _TotalValueBySuburbs =
    CALCULATE([TotalHouseValue],
    ALL())
return 
    _TotalValueBySuburbs

6.   HouseValue_DYNAMIC_LINK_SSRS = "http://my/ReportServer/Pages/ReportViewer.aspx?%2fAdvanceTaskSSRS%2fReportHouse&rs:Command=Render&state=" & SELECTEDVALUE('DimSuburb'[state])& "&city=" & SELECTEDVALUE('DimSuburb'[city]) & "&suburb=" & SELECTEDVALUE('DimSuburb'[suburb])

7.   
MaxRentalValue = MAX(FactRentalValue[RentalAmount])

8. NSWAvgRentalValue = CALCULATE([Avg Rent],FILTER(FactRentalValue,FactRentalValue[state_code]="NSW") )

9. 
SelectedValue = SELECTEDVALUE(DimSuburb[state]) &"-"& SELECTEDVALUE(DimSuburb[city]) & "-"& SELECTEDVALUE(DimSuburb[suburb])

10. Top5CitiesByRent = TOPN(5,SUMMARIZE(DimSuburb,"g",KeyCoreMeasures[MaxRentalValue]))

11. TotalCountRange = COUNTAX(FactRentalValue,FactRentalValue[RentalRange $])

12. UserTopNValuesOffenceCategory = if([Rank category by recordedIncidenta]<='Top Values '[Top Values  Value], [Total Incidents  sub,city,state])









 
