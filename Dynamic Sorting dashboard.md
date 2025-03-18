
# Dynamic Sort Dashboard Powerbi 

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

   ![Image](https://github.com/user-attachments/assets/5c1d2ea9-e9ff-4557-b834-09d13dcb31c7)

- step 6: Drag an other SLICER and add Category column to filed. In visuaization under format slicers settings changes the options style to "TILE" make all format changes to the visual.

    ![Image](https://github.com/user-attachments/assets/901e59ee-1280-445e-a8b5-431a289bcc4c)

- step 7: Drag an other SLICER and add Segment column to filed. In visuaization under format slicers settings changes the options style to "TILE" make all format changes to the visual.
  
    ![Image](https://github.com/user-attachments/assets/190a870f-4601-4e0f-86d8-8de0b2efb2e2)

- step 8: Add a text box and set a name for the dashboard as "DYNAMIC SORTING" and make all the format required .
  
    ![Image](https://github.com/user-attachments/assets/70c6070d-f4d0-40d0-bdda-8ef167f62a42)

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

    ![Image](https://github.com/user-attachments/assets/e04db21a-65b5-4bf0-b9e6-6f15ff7156b4)


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

   ![Image](https://github.com/user-attachments/assets/7151294a-f5fd-45c9-9886-c635985f3552)

   ![Image](https://github.com/user-attachments/assets/483246c9-84e8-4f1f-b7dd-80126dec0ba8)

- step 11: Drag an other SLICER and add QRT column to filed. In visuaization under format slicers settings changes the options style to "TILE" make all format changes to the visual.

    ![Image](https://github.com/user-attachments/assets/9e745447-9fc1-4f2d-bf95-652e798680b8)


This dashboard presents sales data across different regions, enabling users to analyze quarterly sales and profits dynamically.Minly focused on creating dynamic charts,measures, columns and tables.






 
