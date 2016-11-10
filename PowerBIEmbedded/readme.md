# MISSION GOAL : Validate Data with Power BI Embedded

We've just discovered that work you did previously somehow caused crew health statistics to start being published to the Azure SQL Database. We have an existing report that shows each crew member along with their current health statistics. Your mission is to use Power BI Embedded to view the report.
To ensure that you know how to use Power BI Desktop and Power BI Embedded, we'll first help you come up to speed with some core skill training.  Then, once you have mastered the technologies, we'll ask you to review the crew health report. 
____

## CORE SKILL TRAINING

To help you come up to speed quickly with Power BI Desktop and Power BI Embedded, we ask that you first complete the following walkthrough:

> **Note**: Even if you are working in teams, it is recommended that each team member complete the core skill training exercises.  This will make sure that the entire team is ready to accomplish the Mission Objectives. 


1. <a target="_blank" href="https://vlabs.holsystems.com/vlabs/technet?eng=VLabs&auth=none&src=vlabs&altadd=true&labid=25796&lod=true">Developing a Web App with Azure Power BI Embedded</a>

    > **Note**: When you launch the lab, a SQ00125.PDF file should be automatically downloaded.  Open that PDF file to get the step-by-step instructions for the lab.  If you can't find the file, you can [download a copy from here](DevelopingAWebAppWithAzurePowerBIEmbedded.pdf) 

____

## MISSION OBJECTIVES

Now that you have successfully used Power BI Desktop and Power BI Embedded to work with a report, you can view the crew health report to verify that all the crew is present, and healthy. 

There are six crew members posted at the space station on mars:

| Photo | Name | Position | 
| --- | --- | --- |
| ![Anna Malli](images/AnnaMalli.jpg) | Anna Malli | Commander | 
| ![Erika Mustermann](images/ErikaMustermann.jpg) | Erika Mustermann | Mission Specialist |
| ![Ivan Sidorov](images/IvanSidorov.jpg) |Ivan Sidorov | Payload Specialist |
| ![Juan Pérez](images/JuanPerez.jpg) | Juan Pérez | Flight Engineer |
| ![Seán Ó Rudaí](images/SeanORudai.jpg) | Seán Ó Rudaí | Pilot |
| ![Jean Dupont](images/JeanDupont.jpg) | Jean Dupont | Payload Commander |

The report you need to verify already exists, and points at an Azure SQL Database where the health telemtry systems publish there data to.  Here are the details you need to view the report:

| Item | Value |
| --- | --- |
| Report File URL | <a target="_blank" href="http://aka.ms/crewhealthpbix">http://aka.ms/crewhealthpbix</a> |
| Azure SQL Server | marsql.database.windows.net |
| Azure SQL Database | marsdb |
| SQL Login | reportuser |
| SQL Password | P@ssw0rd |

To view the report:

1. Ensure that you have the latest version of Power BI Desktop installed.  You can download the latest version from the <a target="_blank" href="https://powerbi.microsoft.com/en-us/desktop/">Power BI Desktop Downloads</a>.

    > **Note**: If you prefer, you can continue to work inside the Lab VM created for you during the core skill training exercise above.  Just beware that the lab environment times out after a while, and you will still need to update to the latest version of Power BI Desktop.

1. Download the <a target="_blank" href="http://aka.ms/crewhealthpbix">CrewHealth.pbix</a> file.

1. Open the downloaded `CrewHealth.pbix` file in Power BI Desktop.

1. If prompted, update the database connection using the details provided above.

1. Review the data in the report to ensure:

    1. All six crew members have data present

    1. All the health data (Body Temperature and Heart Rate) values appear to be in safe ranges.
