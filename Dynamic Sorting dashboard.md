
# Dynamic Dashboard Powerbi 

### Dashboard Link : https://app.powerbi.com/groups/me/reports/986d066b-d13d-4757-bf30-9873769c3bb0/e9e7c78a4640339699ba?experience=power-bi


## Problem Statement

This dashboard presents sales data across different regions, enabling users to analyze quarterly sales and profits dynamically. It provides insights into various regions, categories, and subcategories for the years 2021–2025.
Built using calculated measures and columns, this Power BI dashboard allows users to filter data, track trends, and make real-time business decisions effectively.

### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.

- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.

- Step 3 : It was observed that in none of the columns errors & empty values were present.

- Step 4 : Under Report View , Visualizations add Canvas Background add color.

- step 5: Under report view , drag SLICER and add state/provision column to filed. In visuaization under format slicers settings changes the options style to "TILE" make all format changes to the visual.

    image 1

- step 6: Drag an other SLICER and add Category column to filed. In visuaization under format slicers settings changes the options style to "TILE" make all format changes to the visual.

    image 2

- step 7: Drag an other SLICER and add Segment column to filed. In visuaization under format slicers settings changes the options style to "TILE" make all format changes to the visual.
  
    image 3

- step 8: Add a text box and set a name for the dashboard as "DYNAMIC SORTING" and make all the format required .
  
    image 4

- Step 9 : Now Create a new column and new measures for the following 

      #1. Create new measure for total sales and total profits.

         Total Profits = sum('Sales Data'[Profit])
         Total Sales = sum('Sales Data'[Sales])
  

     #2. Create new column to get QUARTERs for each row based on [Order date]. 

         QTR = "Q" & QUARTER('Sales Data'[Order Date])


      #3. Create new measures to get total profits for each quarter.

         Q1 = CALCULATE([Total Profits],'Sales Data'[QTR]=1)
         Q2 = CALCULATE([Total Profits],'Sales Data'[QTR]=2)
         Q3 = CALCULATE([Total Profits],'Sales Data'[QTR]=3)
         Q4 = CALCULATE([Total Profits],'Sales Data'[QTR]=4)


      #4.Under home tab click center data and add Profit and Sales under column1 and create a table.

    image 5


      #5.Now create a new measure for selected vlaue .To get dynamic results for sales and profits.  

         Selected value = IF(
                             SELECTEDVALUE(
                                           'Table'[Total PS])="Sales",[Total Sales],
                                if(
                                   SELECTEDVALUE('Table'[Total PS])="Profit",[Total Profits],
                                   [Quarter Profit]
                                  )
                             )

      # other measures 
          Quarter Sales = CALCULATE(
                                    SUM('Sales Data'[Sales]),
                                    QUARTER('Sales Data'[Order Date])
                                    )
          Quarter Profit = CALCULATE(
                                    sum('Sales Data'[Profit]),
                                    QUARTER('Sales Data'[Order Date])
                                    )    
          Quarter profit1 = if(SELECTEDVALUE('Sales Data'[Quarters])="Q1",[Q1],
                               if(SELECTEDVALUE('Sales Data'[Quarters])="Q2",[Q2],
                                  IF(SELECTEDVALUE('Sales Data'[Quarters])="Q3",[Q3],
                                    IF(SELECTEDVALUE('Sales Data'[Quarters])="Q4",[Q4]
                                      )
                                    )
                                 )
                               )  

- step 10: Drag Matrix table and add subcategory and product name to rows,
  add table PS  and QRT to columns and selected value measure to values .

    image 6

- step 11: Drag an other SLICER and add QRT column to filed. In visuaization under format slicers settings changes the options style to "TILE" make all format changes to the visual.

    image 7


This dashboard presents sales data across different regions, enabling users to analyze quarterly sales and profits dynamically.Minly focused on creating dynamic charts,measures, columns and tables.






 
