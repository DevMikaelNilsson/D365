# Add custom column to Applicabillity rules in Globalization Studio
It is possible to add custom columns to the Globalization studio directly in F&O without any code implementation.
However, to make use of the custom column with the tax calculation service, you will need to extend a couple of classes.

## Create Tax Calculation Data Model
1.	In Microsoft Dynamics 365 Finance, go to Electronic Reporting > Tax configurations.
2.	In the configuration tree, select Tax Calculation Data Model. Then, on the Action Pane, select Create configuration.
3.	In the drop-down dialog box, select Taxable document model derived from Name: Tax Calculation Data Model, Microsoft, enter a name for the new tax data model, and then select Create configuration. 
4.	Select the tax data model that you just created, and then, on the Action Pane, select Designer.
5.	Expand the data model tree, select Lines, and then select New 
6.	In the Create node dialog box, enter a name, specify the item type, and then select Add. 
7.	Add any required columns. 
8.	On the Action Pane, select Save, and then select Complete.
9.	Close the page and view the completed version of your tax data model.

## Customize the tax configuration
1.	In Finance, go to Electronic reporting > Tax configurations.
2.	In the configuration tree, select Tax Calculation Configuration. Then, on the Action Pane, select Create configuration.
3.	In the drop-down dialog box, select Tax service configuration derived from Name: Tax Calculation Configuration, Microsoft, enter a name for the new tax configuration, and then select Create configuration.
4.	Select the tax configuration that you just created, and then, on the Action Pane, select Designer.
5.	In the Properties section, in the Data model field, select the customized tax data model that you created earlier. 
6.	In the Data model version field, select the completed version of the tax data model. 
7.	On the Action Pane, select Save, and then select Complete.
8.	Close the page and view the completed version of your tax configuration.

## Verify the custom column
1.	Go to workspace Globalization studio
2.	Select Tax calculation
3.	Select the Tax calculation feature and click on Edit. 
_(When there is no available draft, click on new and create a new draft, and then click on edit.)_

4.	Select the latest configuration version from the drop-down menu
5.	In the Applicabillity rules tab, select the Manage columns button
6.	Find and select the custom column you created
7.	Select the column and click on the add (->) button and the column will be added
8.	The column is automatically added to the grid
