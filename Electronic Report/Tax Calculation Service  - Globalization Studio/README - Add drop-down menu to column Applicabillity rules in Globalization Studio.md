# Add drop-down menu to column Applicabillity rules in Globalization Studio
If you have created and added a custom column to the Globalization Studio, or for an already existing column, you notice that it is just a text field. It is possible to add a drop-down menu for the column.

## Modify Tax Calculation Data Model
1.	Select custom Tax Calculation Data Model and click on Designer
2.	Select the Taxable document drop down and select Reference model 
3.	Create a new “model root” object 
4.	Select the created root model and create a new node with the Child of an active node, select Record list as item type and preferably end the name with entity 
5.	Add all required fields that you wish to add to the drop-down window.  
6.	On the Action Pane, select Save, and then select Complete.

## Modify FNO Model Mapping
1.	If you haven’t already created a custom Mapping object 
- Click on Create configuration
-	Select option Taxable document model mapping derived from Name: FNO Model Mapping, Microsoft
- In Target model, select the custom Data Model
-	Click “Create configuration”
-	Select Complete to save the initial setup
2.	Select custom FNO Model Mapping and click on Designer
3.	Click on the + Map to reference model button and select the reference model you created in the previous steps 
4.	Select the created model and click on Designer 
5.	Here you will map the datasource to the created fields.
In this example, I have mapped a Table records as datasource, selected the IntrastatTransportMode table and filter on the three fields that I want to bind 
6.	For the Record list, I make sure that it is mapped/bind to the table record list, and the fields are bound to their respective fields 
7.	On the Action Pane, select Save, and then select Complete.
8.	Make sure that the option Default for model mapping is active for the mapping object

## Modify the tax configuration
1.	Select the tax configuration and then, on the Action Pane, select Designer.
2.	In the Data model version field, select the completed version of the tax data model. 
3.	On the Action Pane, select Save, and then select Complete.
4.	Close the page and view the completed version of your tax configuration.

## Verify the custom column and dropdown
1.	Go to workspace Globalization studio
2.	Select Tax calculation
3.	Select the Tax calculation feature and click on Edit
4.	Select the latest configuration version from the drop-down menu 
5.	If you haven’t already added the custom column, or if it is not visible in the grid, follow these steps
-	In the Applicabillity rules tab, select the Manage columns button 
-	Find and select the custom column you created 
-	Select the column and click on the add (->) button and the column will be added 
6.	Make sure that the option Enable lookups in applicability rules option is active and select the Source Legal Entity which you wish to use 
7.	The custom field you created and added should now have the drop-down functionality, and should display row values from the source legal entity
