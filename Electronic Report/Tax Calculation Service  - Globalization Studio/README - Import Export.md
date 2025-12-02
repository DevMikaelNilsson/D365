## Export configuration from environment
Access the Tax configuration from the **Electronic Reporting** workspace by making sure that the correct repository is selected, and click on **Tax configurations**.

### Export Tax Data Model
1. To export the Tax Data Model, select the model that you want to export.
2. Make sure that the latest record with the status “Completed” is selected.
3. Click on the Exchange and then the Export as XML file button.
4. The system will now download the Data Model as a XML file.

### Export FNO Model Mapping
1. To export the FNO Model Mapping, select the mapping object that you want to export.
2. Make sure that the latest record with the status “Completed” is selected.
3. Click on the Exchange and then the Export as XML file button.
4. The system will now download the FNO Model Mapping as a XML file.

### Export Tax Calculation Configuration
1. To export the Tax Calculation Configuration, select the mapping object that you want to export.
2. Make sure that the latest record with the status “Completed” is selected.
3. Click on the Exchange and then the Export as XML file button.
4. The system will now download the Tax Calculation Configuration as a XML file.

## Import configuration to new environment

### Validate that the versions are equal between the environments
Before you start with importing, make sue that the environments have the same version on the **standard** base model, 
Data Model, Model Mapping and Calculation Configuration.

If the versions are not equal, update the base objects on the environment before you start to import your own files. 
When you are updating the files to the right version, make sure that you follow the import sequence!

### Important Import sequence
When importing your objects, it is important to follow the right import sequence.
The import sequence is as follows:
1.	Tax Calculation Data Model
2.	FNO Model Mapping
3.	Tax Calculation Configuration

If you don’t follow this sequence, the import process might fail.

### Import Tax Data Model
1. Highlight the Tax Data Model in the tree hierarchy, and select Exchange and then Load from XML file
2. Select the exported Tax Calculation Data Model xml file you previously exported and click on OK.
3. The imported Tax Calculation Data Model should now appear in the tree hierarchy as its own record.

### Import FNO Model Mapping
1. Highlight the FNO Model Mapping in the tree hierarchy, and select Exchange and then Load from XML file
2. Select the exported FNO Model Mapping xml file you previously exported and click on OK.
3. The imported FNO Model Mapping should now appear in the tree hierarchy as its own record.

### Import Tax Calculation Configuration
1. Highlight the Tax Calculation Configuration in the tree hierarchy, and select Exchange and then Load from XML file
2. Select the exported Tax Calculation Configuration xml file you previously exported and click on OK.
3. The imported Tax Calculation Configuration should now appear in the tree hierarchy as its own record.

