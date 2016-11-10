# MISSION GOAL : Verify Staff Identity with Congnitive Services

We have been able to retrieve a picture from the coffee pot's monitoring camera inside the space station.  We hope that it has captured the crew members.  Your mission is to use Azure Cognitive Services' Face API to detect the faces in the photo, and verify that all crew members are present.  Additionally, we have some telemetry data that indicates additional life forms may be present.  You will use the results returned by Cognitive Services to identify any additional life forms.

____

## CORE SKILL TRAINING

To ensure that you are technically proficient with the Cognitive Services Face API, we ask that you first complete the following core skill's training exercise:

> **Note**: Even if you are working in teams, it is recommended that each team member complete the core skill training exercises.  This will make sure that the entire team is ready to accomplish the Mission Objectives. 

1. [Get Started with Face API in C#](https://www.microsoft.com/cognitive-services/en-us/face-api/documentation/get-started-with-face-api/GettingStartedwithFaceAPIinCSharp)

____

## MISSION OBJECTIVES

Now that you can successfully interact with the Cognitive Services Face API, your mission is to use an image of the crew that was captured via the coffee pot's monitoring camera to detect the faces of the crew.  You need to verify that all six crew members are present and appear healthy.  In addition, our telemetry suggests an additional life form.  There are six crew members posted at the space station:

| Photo | Name | Position | 
| --- | --- | --- |
| ![Anna Malli](images/AnnaMalli.jpg) | Anna Malli | Commander | 
| ![Erika Mustermann](images/ErikaMustermann.jpg) | Erika Mustermann | Mission Specialist |
| ![Ivan Sidorov](images/IvanSidorov.jpg) |Ivan Sidorov | Payload Specialist |
| ![Juan Pérez](images/JuanPerez.jpg) | Juan Pérez | Flight Engineer |
| ![Seán Ó Rudaí](images/SeanORudai.jpg) | Seán Ó Rudaí | Pilot |
| ![Jean Dupont](images/JeanDupont.jpg) | Jean Dupont | Payload Commander |

To verify the crew status:

1. Use a copy of the photo recently retrieved from the coffee pot monitoring camera here: [Crew Photo](images/CrewPhoto.jpg)

1. Upload the photo to congitive services using the application you created in the core skills training exercise above.

    > **Note:** if you had problems creating the app above, or just didn't have time, you can use the sample implementation [here](https://www.microsoft.com/cognitive-services/en-us/face-api)

1. Count the faces, and verify that all six crew members are present. 

1. Look for any additional faces or life forms that may be present.  

