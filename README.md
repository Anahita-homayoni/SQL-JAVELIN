# SQL-JAVELIN
JAVELIN CODE


SELECT "Stock_Trans_Log"."Trans_Date", 

"Part"."Part_No", 

"Stock_Trans_Log"."Qty_Change", 

"Part"."Part_Prim_Desc", 

"Stock_Trans_Log"."Supplier_Customer", 

"Stock_Trans_Log"."From_ROO", 

"SO_Items"."SO_Line_Value", 

"Customer"."Customer_Name", 

"Stock_Trans_Log"."SO_No", 

"Stock_Trans_Log"."SO_Line_No", 

"SO_Items"."Selling_Price"

FROM   ((("Manu211_Live"."stock"."Stock_Trans_Log" "Stock_Trans_Log" 

INNER JOIN "Manu211_Live"."production"."Part" "Part" ON "Stock_Trans_Log"."Part_No"="Part"."Part_No") 

INNER JOIN "Manu211_Live"."stock"."Stock_Trans_Types" "Stock_Trans_Types" ON "Stock_Trans_Log"."Tran_Type"="Stock_Trans_Types"."Type") 

LEFT OUTER JOIN "Manu211_Live"."sales"."Customer" "Customer" ON "Stock_Trans_Log"."Supplier_Customer"="Customer"."Customer_No") 

LEFT OUTER JOIN "Manu211_Live"."sales"."SO_Items" "SO_Items" ON ("Stock_Trans_Log"."SO_No"="SO_Items"."SO_No") AND ("Stock_Trans_Log"."SO_Line_No"="SO_Items"."SO_Line_No")

WHERE  ("Stock_Trans_Types"."Description"=N'Return of sales issue' OR "Stock_Trans_Types"."Description"=N'Sales issue')

ORDER BY "Stock_Trans_Log"."Trans_Date" DESC
 
