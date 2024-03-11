[Home](../README.md)
# IoT - Smart Lighting System (Likavka)

[Video](https://www.youtube.com/watch?v=a-1eh9SjFxM)

[Article](https://www.lepsiaobec.sk/viete-kto-je-vitazom-madhack-iot-pre-lepsiu-obec/
)

## Problem
The mayor of the village Likavka faces the challenge of lacking a monitoring and management system for both existing old lamps and potential new installations. Limited financial resources prevent the acquisition of modern lamps with integrated systems available in the market. The goal is to develop a cost-effective IoT-based solution that can monitor and manage both old and new lamps, providing notifications to field technicians in case of any issues or damages.

## Solution
![solution diagram](solutionDiagram.png)
* Current sensors, in combination with IoT devices, were installed on city lamps.
* IoT devices read values every hour from the sensor and send data to the gateway (The Things Network).
* A plugin on the Resco server is executed every 30 minutes, reading new data from The Things Network Hub.
* The data is processed and saved to the database.
* Field Technicians are able to sync the app with the server and view the state of the lamps. Additionally, if the plugin on the Resco Server detects an incorrect value for the lamp, it sends a notification to the Field Technician.

![app for field teschnician](tabletApp.png)

![app for field teschnician](madhackWinners.jpg)

[->Next: Biomedical Engineering](../biomedicalEngineering/readme.md)
