# MISSION GOAL : ESTABLISH IOT HUB COMMUNICATIONS

We have lost communications with the space station.  However, we have indications that there are still devices running on Mars.  We know that there is a coffee pot on the station that we can communicate with using Azure IoT Hubs, and a command set inspired by the Hypertext Coffee Pot Control Protocol (HTCPCP/v1.0, <a target="_blank" href="https://www.ietf.org/rfc/rfc2324.txt">RFC 2342</a>).  First, we will provide you with some core skill training to help you ramp up an Azure IoT Hubs, then we'll have you to attempt to establish communications with the coffee pot.

____

## CORE SKILL TRAINING

Before you can successfully communicate with the devices, you must first master core Azure IoT Hub skills.  To prepare, first complete the following two exercises:

> **Note**: Even if you are working in teams, it is recommended that each team member complete the core skill training exercises.  This will make sure that the entire team is ready to accomplish the Mission Objectives. 

1. Getting Started with Azure IoT Hubs (pick your preferred langauge):
    - C#: "<a target="_blank" href="https://azure.microsoft.com/en-us/documentation/articles/iot-hub-csharp-csharp-getstarted/">Get started with Azure IoT Hub for .NET</a>"
    - Node.js: "<a target="_blank" href="https://azure.microsoft.com/en-us/documentation/articles/iot-hub-node-node-getstarted/">Get started with Azure IoT Hub for Node.js</a>"
1. Sending Cloud-to-Device (C2D) Messages:
    - C#: "<a target="_blank" href="https://azure.microsoft.com/en-us/documentation/articles/iot-hub-csharp-csharp-c2d/">How to send cloud-to-device messages with IoT Hub and .Net</a>"
    - Node.js: "<a target="_blank" href="https://azure.microsoft.com/en-us/documentation/articles/iot-hub-node-node-c2d/">How to send cloud-to-device messages with IoT Hub and Node.js</a>"

    > **Note**: In the Node.js sample instructions you are told to install the `azure-iothub` npm package.  You must ALSO intsall the `azure-iot-common` npm package:

    ```text
    npm install azure-iothub --save
    npm install azure-iot-common --save
    ```

____

## MISSION OBJECTIVES

The main objective of this mission is to attempt to establish IoT Hub communications with the coffee pot inside the space station.  You will be working as a part of a team on this objective.

Using the skills you mastered in the training, your next task is to accomplish the following objectives:

1. Retrieve your team name from Mission Control
1. Monitor messages from the coffee pot
1. Ping the coffee pot
1. Brew some coffee!

### Retrieve Your Team Name

We need to coordinate the work of multiple teams in this lab.  You will need to contact a representative from Mission Control in the room to retrieve a card with your team name/number.  The card will look something like this:

![Team Card Sample](images/cardsample.png)

The name displayed on your card "teamXX" is your team name.  You must use that name on all communications with the space station to prevent any issues.

## Monitor messages from the coffee pot

Before we send any commands to the coffee pot, we first need to make sure that we are setup to monitor the messages it sends back.  You will need to modify the code you created in the "Get started with Azure IoT Hub..." exercise above to monitor messages on the space station's IoT Hub, and to listen specifically for messages from the coffee pot.  To do that, you will need the following information:

| Item | Value |
| ---- | ----- |
| IoT Hub Host Name | `marsiot.azure-devices.net` |
| Coffee Pot Device ID | `coffeepot` |
| SAS Policy Name | `coffeeclient` |
| SAS Policy Permissions | Service Connect |
| SAS Policy Key | `FkwDl0J3LAI31zo0Q2ThLAXgIUlIhIY3kQUaIUDHgmU=` |
| Complete coffeeclient Connection String | `HostName=marsiot.azure-devices.net;SharedAccessKeyName=coffeeclient;SharedAccessKey=FkwDl0J3LAI31zo0Q2ThLAXgIUlIhIY3kQUaIUDHgmU=` |

Use the information above to modify the code in the "**Receive device-to-cloud messages**" task of core skills exercise as follows:

1. Locate te code:

    1. For .NET it's in the `ReadDeviceToCloudMessages\Program.cs` file, unless you named the project something different.
    1. For Node.js it's in the `readdevicetocloudmessages\ReadDeviceToCloudMessages.js` file unless you named the folder or file something different.

1. Use the "**Complete coffeeclient Connection String**" from above for the value of the `connectionString` variable.  The "**coffeeclient**" SAS Policy on the `marsiot` IoT Hub has "**Service Connect**" permissions. This means that it can connect to the "service" side (not the device side) of the Azure IoT Hub.  It can the listen for "device-to-cloud" messages from the device, or send "cloud-to-device" messages to the device. 

1. Use a specific consumer group for your team.  Your consumer group name is your `teamxx` (all lower case) team name you retrieved previously

    > **Note**: Each "Consumer Group" on an event hub gets its own view of the stream of messages in the event hub.  By using a consumer group that is unique to your team, you ensure that you don't conflict with other teams that may be reading messages at the same time.

    1. For the .NET code, replace:

         `eventHubClient.GetDefaultConsumerGroup()`

         with

         `eventHubClient.GetConsumerGroup("teamxx")`

    1. For Node.js, replace: 

        The `'$Default'` consumer group name

        with

        your `'teamxx'` team name.

1. Once you have completed the modifications, run the "ReadDeviceToCloudMessages" (.NET or Node.js) application to begin listening for messages on the `marsiot` iot hub. If we can get the coffee pot talking, this is where we'll see the messages it sends.  Keep it running to view the responses from the next steps.


## Ping the coffee pot

Now that you are ready to receive messages from the coffee pot, you can attempt to send a message to the coffee pot.

You will use the same connection information provided above.

***Coffee Pot Cloud-to-Device Message Format***

The coffee pot expects messages to be sent to it in a specific format: 

```json
{
  "Command":"",
  "Team":"",
  "Parameters":""
}
```

***Coffee Pot Device-to-Cloud Message Format***

When it receives a message and has completed processing it, it will respond with a message in the following format:

```json
{
  "SentAt": "",
  "Team": "",
  "MessageText":""
}
```

Following are the details for the "**Ping**" command

| Command | Team | Parameters | Response |
| --- | --- | --- | --- |
| **Ping** | Your `teamxx` team name | Any string payload you would like to send | A coffee pot "Device-to-Cloud" message will be sent with the `MessageText` being "Ping Response: ", and your message's `Parameters` value. |

To ping the coffee pot:

1. Locate the code you created in the "Send Cloud-to-Device Message" task of the core skill exercises

    1. For .NET, the code is in the `SendCloudToDevice/program.cs` file unless you named your project something else.

    1. For Node.js, it is in the `SendCloudToDeviceMessage.js` file unless you named the file something else.

1. Use the "**Complete coffeeclient Connection String**" from above for the value of the `connectionString` variable.

1. Use the `coffeepot` device id for the target device instead of the `myFirstDevice` (for .NET) or `myFirstNodeDevice` (for Node.js).

1. Modify the `commandMessage` (For .NET) or the `message` (For Node.js) variable to be a `Message` object with the contents being a string that matches the message "**Coffee Pot Cloud-to-Device Message Format**" described above, and with appropriate values for the "**Ping**" command. 

1. Run the `SendCloudToDevice` (.NET) or `SendCloudToDeviceMessage.js` program to send the ping command to the coffee pot. Repeat the execution to send the command again.

1. Monitor the output of the "ReadDeviceToCloudMessages" from the previous step to see the response.

## Brew some coffee!

Congratulations!  If you have gotten this far, you have successfully established communications with the coffee pot in the space station!  Finally, let's try to get the crew's attention by brewing the coffee.

Here are the details for the "**Brew**" command:

| Command | Team | Parameters | Response |
| --- | --- | --- | --- |
| **Brew** | Your `teamxx` team name | An empty string | A coffee pot "Device-to-Cloud" message will be sent with the `MessageText` of "Brewing Coffee!". |

To brew coffee:

1. Using the same "**Coffee Pot Cloud-to-Device Message Format**" as you did with the "**Ping**" command, modify the code you just used to use the "**Brew**" command instead.
1. Run the `SendCloudToDevice` (.NET) or `SendCloudToDeviceMessage.js` program to send the message to the coffee pot. Repeat the execution to send the command again.
1. Again, monitor the output in the "ReadDeviceToCloudMessages" program.