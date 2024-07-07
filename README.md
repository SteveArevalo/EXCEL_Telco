# EXCEL_Telco

## Introduction:

I used Excel to clean and analyze data to find the top 10 internet types for the top 10 cities, the top 10 revenue cities, and reasons for customer churn. Here's how I utilized Excel's powerful functions—XLOOKUP, INDEX, MATCH, SUM, and IF—to accomplish this task.

XLOOKUP:

We use an XLOOKUP function to populate the "City," "Internet Service," and "Internet Type" columns from the telco dataset. The lookup value is the cell A2, which was selected from the InternetService sheet. The lookup array in the XLOOKUP function is the customerID column from the telco sheet, matching the lookup value. This acts as the primary key, ensuring we populate the correct information for each customer ID.

The return array is the "City" column from the telco sheet. The final XLOOKUP function is:

=XLOOKUP(A2, telco!$A$2:$A$7044, telco!$Y$2:$Y$7044, "", 0)

The "" at the end is the "if not found" portion, indicating that the function should return nothing if the lookup value is not found. The 0 specifies that we want an exact match.

I also used this function with the appropriate lookup arrays and return values to retrieve the "Internet Service" and "Internet Type" columns.

INDEX/MATCH:

For the "Streaming Service Use" and "Unlimited Data" columns, I chose to use an INDEX function. To start, we select our array from the "Streaming TV," "Streaming Movies," "Streaming Music," and "Unlimited Data" columns from the telco dataset.

For the row number portion of the INDEX function, we use the MATCH function, which requires a lookup value and a lookup array. The lookup value is the CustomerID from the InternetService dataset, and the lookup array is the CustomerID column from the telco dataset.

Next, for the column number, we use another MATCH function. The lookup value for this MATCH function is E1, which represents the "Streaming TV" column. The lookup array includes the "Streaming TV," "Streaming Movies," "Streaming Music," and "Unlimited Data" columns from the telco dataset. We specify an exact match by entering 0 for the match type.The final INDEX function is:

=INDEX(telco!$AE$2:$AH$7044, MATCH(InternetService!$A2, telco!$A$2:$A$7044, 0), MATCH(E$1, telco!$AE$1:$AH$1, 0))

This function ensures that the correct data for each customer is retrieved from the telco dataset based on their CustomerID and the specified columns.

IF:

For the "Internet Type" column, some cells display "None." Stakeholders prefer these cells to be empty instead. To address this, I created a new column called "Internet Type." In the first cell of this column, I used the IF function to handle different internet types.

The function checks for "DSL," "Fiber Optic," "Cable," and "None." If the cell contains "None," it will be replaced with an empty space. The final IF function is:

SUM:

To find the total revenue from all accounts I used the SUM function. I chose a cell next to the the TotalRevenue The final total SUM function is:

=SUM(H:H)

This signifies that I have chosen the entire Total Revenue Column

Pivot Table:

To create a pivot table from your total revenue table in Excel, select your data range, go to the "Insert" tab, and choose "PivotTable." Specify where you want the pivot table to be placed and drag fields like "City," "Total Revenue" and "Total Refunds" into the appropriate areas (rows, columns, and values). Once the pivot table is created, I select it, go to the "Home" tab, click on "Conditional Formatting," and apply rules based on revenue values to visually enhance the table's insights, such as highlighting top 10 revenue values.
