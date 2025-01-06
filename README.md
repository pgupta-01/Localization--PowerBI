# Localization--PowerBI

Power BI report localization using Translations Builder external Tool.
**Verify Setup for localization before publishing the report on the power BI Service.**
Publish the PBIX to a Premium PBI workspace (not the Power BI Premium sku). Use either method below to verify the localization of your report:
By changing the browser language.
By using the embedded URL, by adding “&language=languageCode&formatlocale= languageCode” at the end. languageCode is the language we want to display, for example en-US, ja-JP, de-DE etc.
**Limitations:**
Page/Report Name cannot be localized.
Use single page/tab in a Report, other page should be hidden.
Do not add too much literal texts in the report i.e., textboxes, shapes, buttons.
Please find below detail feature of external tools:
**Localization Using Translations Builder external tool.**
First we need to installed the Translations Builder .msi file.
TranslationsBuilderSetup.msi version 2.0 support more multiple language.
After installation, open the Power BI Desktop the External Tools menu is shown as below
  
Translations Builder is a tool designed for content creators using Power BI Desktop. Content creators can use this tools to add multi-language support to PBIX project files. The following screenshot shows what Translations Builder looks like when working with a simple PBIX project that supports a small number of secondary languages.
  
Translations Builder provides an Add Language command to add secondary languages to the project’s data model.
  
After adding Language, now challenge is to add the translation. So we can use machine Translations using Azure Translator Service.
To obtain this key and its location by reading Obtaining a Key for the Azure Translator Service.
  
Once a user has configured an Azure Translator Service key, Translations Builder will begin to display additional command buttons which make it possible to generate translations for a single language at a time or for all languages at once. There are also commands to generate machine translations only for the translations that are currently empty.
  
You can create the Localized Labels table to a PBIX project by executing the Create Localized Labels Table command from the Generate Translated Tables menu.
  You can alternatively switch the Add Localized Labels dialog into Advanced Mode which makes it possible to delete all existing report labels at once and to enter a large batch of report labels in a single operation.
  
You can create this table by executing the Generate Translated Localized Labels Table command.
  
The Translated Localized Labels table appears to a report author in the Fields pane when the report is in Report View in Power BI Desktop.
  
Any edits you make will be lost as all the measures in this table are deleted and recreated each time you execute Generate Translated Localized Labels Table.
You can use these labels in the report and save it. After Publishing the report on the Power BI Service, the report will be translated as per user locale.
Browser Locale:
If we updated the edge browser/chrome browser locale language setting For example: Language=”Japanese”, it would automatically fetch the locale and show the translation instead of passing the language parameter in the URL query string.
Document for reference -https://learn.microsoft.com/en-us/power-bi/fundamentals/supported-languages-countries-regions 
Resolution of limitation:
Page Navigation using bookmark
To resolve the limitation of Page/tabs Localization, I created a Page Navigation button feature in the POC report.
Enabling Workflows for Human Translation using Export and Import
The Translations Builder introduces the concept of a translation sheet. A translation sheet is a CSV file that you generate with an export operation to send out to a translator. The human acting as a translator performs the work to update the translation sheet and then returns it back to you. You can then execute an import command to integrate the changes made by a translator back into the current PBIX project’s dataset.
  
Once we received an updated translation sheet back from a translator you can copy it to the Inbox folder. Translations Builder provides an Import Translations command to integrate those updated translations back into the dataset for the current project. Once you’ve received an updated translation sheet back from a translator you can copy it to the Inbox folder. Translations Builder provides an Import Translations command to integrate those updated translations back into the dataset for the current project.
  
**Difference and similarities between below approaches:**
Approach 1 Translation Builder	Approach 2 Tableau Editor V3
We need to publish the .pbix file after any new translation changes.	We need to publish the .pbix file after any new translation changes.
We cannot test localization in Power BI Desktop, only test in Power BI Service in a workspace associated with a Premium capacity.	We cannot test localization in Power BI Desktop, only test in Power BI Service in a workspace associated with a Premium capacity.
We can Export translation sheet for a single language, Export translation sheets for all languages. When we click on Export translation button, Popup will appear with name like PbixProjectName-Translations-Spanish.csv and save in specific folder which we already configure.Once we received an updated translation sheet back from a translator you can copy it to the Inbox folder. Translations Builder provides an Import Translations command to integrate those updated translations back into the dataset for the current project.	We can use the specific folder path for Import/Export the files.
Translation can be done in a single click using Azure translator AI service.	Only Human translator is required to localize the en-US .resx file to multiple languages.Use the seperate tool which is a "HelperTool", to generate multiple language trasnlation.
Support multiple language.	Support multiple language.
Report name/Page tabs in a Power BI report do not support localization Using Translation builder.	Report name/Page tabs in a Power BI report do not support localization using Tableau Editor.
MetaData translation is possible using field parameter.	Through self-created localization resource file. We need to create additional data model to support the localization of content.
Import/ Export translation sheet can be prepare in a single click and share for review.	Export can be done using "GenerateResx.cs" script and share for review.
Easily Import the latest change translation sheet in a single click and update the translation builder translation.	Import the latest change translation .resx file using " importTranslation.cs" script and update the tableau Editor translation.
**End to End flow:**
PBIX File → Go to External Tool → Choose Translation Builder → Export .CSV file (Generate default "en-US" translation) file as like PbixProjectName-Translations-English.csv files → Localization team picks from our repository → Localization files checked into our repository → Dev - Import manually all localization files by single click → Update the translation in the translation Builder Tool → Checked-in the PBI file to the repository → CI-CD team deploys to PBI Service.
Power BI report localization using Translations Builder external Tool.
Verify Setup for localization before publishing the report on the power BI Service.
Publish the PBIX to a Premium PBI workspace (not the Power BI Premium sku). Use either method below to verify the localization of your report:
By changing the browser language.
By using the embedded URL, by adding “&language=languageCode&formatlocale= languageCode” at the end. languageCode is the language we want to display, for example en-US, ja-JP, de-DE etc.
Limitations:
Page/Report Name cannot be localized.
Use single page/tab in a Report, other page should be hidden.
Do not add too much literal texts in the report i.e., textboxes, shapes, buttons.
Please find below detail feature of external tools:
Localization Using Translations Builder external tool.
First we need to installed the Translations Builder .msi file.
TranslationsBuilderSetup.msi version 2.0 support more multiple language.
After installation, open the Power BI Desktop the External Tools menu is shown as below
  
Translations Builder is a tool designed for content creators using Power BI Desktop. Content creators can use this tools to add multi-language support to PBIX project files. The following screenshot shows what Translations Builder looks like when working with a simple PBIX project that supports a small number of secondary languages.
  
Translations Builder provides an Add Language command to add secondary languages to the project’s data model.
  
After adding Language, now challenge is to add the translation. So we can use machine Translations using Azure Translator Service.
To obtain this key and its location by reading Obtaining a Key for the Azure Translator Service.
  
Once a user has configured an Azure Translator Service key, Translations Builder will begin to display additional command buttons which make it possible to generate translations for a single language at a time or for all languages at once. There are also commands to generate machine translations only for the translations that are currently empty.
  
You can create the Localized Labels table to a PBIX project by executing the Create Localized Labels Table command from the Generate Translated Tables menu.
  You can alternatively switch the Add Localized Labels dialog into Advanced Mode which makes it possible to delete all existing report labels at once and to enter a large batch of report labels in a single operation.
  
You can create this table by executing the Generate Translated Localized Labels Table command.
  
The Translated Localized Labels table appears to a report author in the Fields pane when the report is in Report View in Power BI Desktop.
  
Any edits you make will be lost as all the measures in this table are deleted and recreated each time you execute Generate Translated Localized Labels Table.
You can use these labels in the report and save it. After Publishing the report on the Power BI Service, the report will be translated as per user locale.
Browser Locale:
If we updated the edge browser/chrome browser locale language setting For example: Language=”Japanese”, it would automatically fetch the locale and show the translation instead of passing the language parameter in the URL query string.
Document for reference -https://learn.microsoft.com/en-us/power-bi/fundamentals/supported-languages-countries-regions 
Resolution of limitation:
Page Navigation using bookmark
To resolve the limitation of Page/tabs Localization, I created a Page Navigation button feature in the POC report.
Enabling Workflows for Human Translation using Export and Import
The Translations Builder introduces the concept of a translation sheet. A translation sheet is a CSV file that you generate with an export operation to send out to a translator. The human acting as a translator performs the work to update the translation sheet and then returns it back to you. You can then execute an import command to integrate the changes made by a translator back into the current PBIX project’s dataset.
  
Once we received an updated translation sheet back from a translator you can copy it to the Inbox folder. Translations Builder provides an Import Translations command to integrate those updated translations back into the dataset for the current project. Once you’ve received an updated translation sheet back from a translator you can copy it to the Inbox folder. Translations Builder provides an Import Translations command to integrate those updated translations back into the dataset for the current project.
  
Difference and similarities between below approaches:
Approach 1 Translation Builder	Approach 2 Tableau Editor V3
We need to publish the .pbix file after any new translation changes.	We need to publish the .pbix file after any new translation changes.
We cannot test localization in Power BI Desktop, only test in Power BI Service in a workspace associated with a Premium capacity.	We cannot test localization in Power BI Desktop, only test in Power BI Service in a workspace associated with a Premium capacity.
We can Export translation sheet for a single language, Export translation sheets for all languages. When we click on Export translation button, Popup will appear with name like PbixProjectName-Translations-Spanish.csv and save in specific folder which we already configure.Once we received an updated translation sheet back from a translator you can copy it to the Inbox folder. Translations Builder provides an Import Translations command to integrate those updated translations back into the dataset for the current project.	We can use the specific folder path for Import/Export the files.
Translation can be done in a single click using Azure translator AI service.	Only Human translator is required to localize the en-US .resx file to multiple languages.Use the seperate tool which is a "HelperTool", to generate multiple language trasnlation.
Support multiple language.	Support multiple language.
Report name/Page tabs in a Power BI report do not support localization Using Translation builder.	Report name/Page tabs in a Power BI report do not support localization using Tableau Editor.
MetaData translation is possible using field parameter.	Through self-created localization resource file. We need to create additional data model to support the localization of content.
Import/ Export translation sheet can be prepare in a single click and share for review.	Export can be done using "GenerateResx.cs" script and share for review.
Easily Import the latest change translation sheet in a single click and update the translation builder translation.	Import the latest change translation .resx file using " importTranslation.cs" script and update the tableau Editor translation.
End to End flow:
PBIX File → Go to External Tool → Choose Translation Builder → Export .CSV file (Generate default "en-US" translation) file as like PbixProjectName-Translations-English.csv files → Localization team picks from our repository → Localization files checked into our repository → Dev - Import manually all localization files by single click → Update the translation in the translation Builder Tool → Checked-in the PBI file to the repository → CI-CD team deploys to PBI Service.
Power BI report localization using Translations Builder external Tool.
Verify Setup for localization before publishing the report on the power BI Service.
Publish the PBIX to a Premium PBI workspace (not the Power BI Premium sku). Use either method below to verify the localization of your report:
By changing the browser language.
By using the embedded URL, by adding “&language=languageCode&formatlocale= languageCode” at the end. languageCode is the language we want to display, for example en-US, ja-JP, de-DE etc.
Limitations:
Page/Report Name cannot be localized.
Use single page/tab in a Report, other page should be hidden.
Do not add too much literal texts in the report i.e., textboxes, shapes, buttons.
Please find below detail feature of external tools:
Localization Using Translations Builder external tool.
First we need to installed the Translations Builder .msi file.
TranslationsBuilderSetup.msi version 2.0 support more multiple language.
After installation, open the Power BI Desktop the External Tools menu is shown as below
  
Translations Builder is a tool designed for content creators using Power BI Desktop. Content creators can use this tools to add multi-language support to PBIX project files. The following screenshot shows what Translations Builder looks like when working with a simple PBIX project that supports a small number of secondary languages.
  
Translations Builder provides an Add Language command to add secondary languages to the project’s data model.
  
After adding Language, now challenge is to add the translation. So we can use machine Translations using Azure Translator Service.
To obtain this key and its location by reading Obtaining a Key for the Azure Translator Service.
  
Once a user has configured an Azure Translator Service key, Translations Builder will begin to display additional command buttons which make it possible to generate translations for a single language at a time or for all languages at once. There are also commands to generate machine translations only for the translations that are currently empty.
  
You can create the Localized Labels table to a PBIX project by executing the Create Localized Labels Table command from the Generate Translated Tables menu.
  You can alternatively switch the Add Localized Labels dialog into Advanced Mode which makes it possible to delete all existing report labels at once and to enter a large batch of report labels in a single operation.
  
You can create this table by executing the Generate Translated Localized Labels Table command.
  
The Translated Localized Labels table appears to a report author in the Fields pane when the report is in Report View in Power BI Desktop.
  
Any edits you make will be lost as all the measures in this table are deleted and recreated each time you execute Generate Translated Localized Labels Table.
You can use these labels in the report and save it. After Publishing the report on the Power BI Service, the report will be translated as per user locale.
Browser Locale:
If we updated the edge browser/chrome browser locale language setting For example: Language=”Japanese”, it would automatically fetch the locale and show the translation instead of passing the language parameter in the URL query string.
Document for reference -https://learn.microsoft.com/en-us/power-bi/fundamentals/supported-languages-countries-regions 
Resolution of limitation:
Page Navigation using bookmark
To resolve the limitation of Page/tabs Localization, I created a Page Navigation button feature in the POC report.
Enabling Workflows for Human Translation using Export and Import
The Translations Builder introduces the concept of a translation sheet. A translation sheet is a CSV file that you generate with an export operation to send out to a translator. The human acting as a translator performs the work to update the translation sheet and then returns it back to you. You can then execute an import command to integrate the changes made by a translator back into the current PBIX project’s dataset.
  
Once we received an updated translation sheet back from a translator you can copy it to the Inbox folder. Translations Builder provides an Import Translations command to integrate those updated translations back into the dataset for the current project. Once you’ve received an updated translation sheet back from a translator you can copy it to the Inbox folder. Translations Builder provides an Import Translations command to integrate those updated translations back into the dataset for the current project.
  
Difference and similarities between below approaches:
Approach 1 Translation Builder	Approach 2 Tableau Editor V3
We need to publish the .pbix file after any new translation changes.	We need to publish the .pbix file after any new translation changes.
We cannot test localization in Power BI Desktop, only test in Power BI Service in a workspace associated with a Premium capacity.	We cannot test localization in Power BI Desktop, only test in Power BI Service in a workspace associated with a Premium capacity.
We can Export translation sheet for a single language, Export translation sheets for all languages. When we click on Export translation button, Popup will appear with name like PbixProjectName-Translations-Spanish.csv and save in specific folder which we already configure.Once we received an updated translation sheet back from a translator you can copy it to the Inbox folder. Translations Builder provides an Import Translations command to integrate those updated translations back into the dataset for the current project.	We can use the specific folder path for Import/Export the files.
Translation can be done in a single click using Azure translator AI service.	Only Human translator is required to localize the en-US .resx file to multiple languages.Use the seperate tool which is a "HelperTool", to generate multiple language trasnlation.
Support multiple language.	Support multiple language.
Report name/Page tabs in a Power BI report do not support localization Using Translation builder.	Report name/Page tabs in a Power BI report do not support localization using Tableau Editor.
MetaData translation is possible using field parameter.	Through self-created localization resource file. We need to create additional data model to support the localization of content.
Import/ Export translation sheet can be prepare in a single click and share for review.	Export can be done using "GenerateResx.cs" script and share for review.
Easily Import the latest change translation sheet in a single click and update the translation builder translation.	Import the latest change translation .resx file using " importTranslation.cs" script and update the tableau Editor translation.
End to End flow:
PBIX File → Go to External Tool → Choose Translation Builder → Export .CSV file (Generate default "en-US" translation) file as like PbixProjectName-Translations-English.csv files → Localization team picks from our repository → Localization files checked into our repository → Dev - Import manually all localization files by single click → Update the translation in the translation Builder Tool → Checked-in the PBI file to the repository → CI-CD team deploys to PBI Service.
**Flow Diagram - Steps Overview:**
  
End user’s experience:
Customer can access the Power BI Report Template which we share to them. It should be mandatory that they have PBI Premium service workspace.
Translation behavior will work for PBI Embedded Solution as well.
Tips and Tricks:
Below are few design techniques for localization before moving forward with design techniques that do support localization.
1.	In Table, column name should not be use “underscore/_”.
For Example- Database column name is msmix_final_intent , column name should be “Final Intent.”
2.	Column should be similar which we need to display on UI.
For Example- Database column name Value, column name should be “Count.”
•	Don’t use in-built Grand Total option for percent Calculation.
•	For percent calculation, I have created a new measure which will not impact the performance of the report.
•	In Table, column name should be unique. Both in database table and DAX table.
•	Don't format after dropping the property or fields


  
End user’s experience:
Customer can access the Power BI Report Template which we share to them. It should be mandatory that they have PBI Premium service workspace.
Translation behavior will work for PBI Embedded Solution as well.
Tips and Tricks:
Below are few design techniques for localization before moving forward with design techniques that do support localization.
1.	In Table, column name should not be use “underscore/_”.
For Example- Database column name is msmix_final_intent , column name should be “Final Intent.”
2.	Column should be similar which we need to display on UI.
For Example- Database column name Value, column name should be “Count.”
•	Don’t use in-built Grand Total option for percent Calculation.
•	For percent calculation, I have created a new measure which will not impact the performance of the report.
•	In Table, column name should be unique. Both in database table and DAX table.
•	Don't format after dropping the property or fields


  
**End user’s experience:**
Customer can access the Power BI Report Template which we share to them. It should be mandatory that they have PBI Premium service workspace.
Translation behavior will work for PBI Embedded Solution as well.
**Tips and Tricks:**
Below are few design techniques for localization before moving forward with design techniques that do support localization.
1.	In Table, column name should not be use “underscore/_”.
**For Example-** Database column name is msmix_final_intent , column name should be “Final Intent.”
2.	Column should be similar which we need to display on UI.
**For Example**- Database column name Value, column name should be “Count.”
•	Don’t use in-built Grand Total option for percent Calculation.
•	For percent calculation, I have created a new measure which will not impact the performance of the report.
•	In Table, column name should be unique. Both in database table and DAX table.
•	Don't format after dropping the property or fields

