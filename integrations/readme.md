[Home](../README.md)
# Integrations with 3rd party system

[Webinar 1](https://www.youtube.com/watch?v=dJET31E0l0E&t=2189s)

[Webinar 2](https://www.youtube.com/watch?v=trD-VEk360Q&t=1678s)

[Doc - Business Central](https://docs.resco.net/wiki/Business_Central)

[Doc - Integrations](https://docs.resco.net/wiki/Integrations)

## Problem
Existing/potential customers would like to connect the Resco Cloud organization to 3rd-party systems without coding custom plugins. The system should be able to provide mapping between local and external schemas.

At the end of this task, the user should be able to integrate Business Central and Dynamics environments with Resco Cloud.


## Solution
Integrations allow you to connect your Resco Cloud organization to various systems using connectors, mapping entities and fields between the two servers for data exchange. Configured connections can be used in Resco Cloud jobs and workflows to automate the synchronization process.

The tool can be described by the image below:

* It provides data exchange between two systems with respect to defined mapping and configuration.

![integrations diagram](integrationsDiagram.png)

* Data is processed by the connector and service.

![odata response to resco](odataResponseToResco.png)

* The connector processes data from the external system and transforms it to the form used by Resco Cloud.

![connector diagram](connectorDiagram.png)

* The service applies defined mapping and stores data in the database. 

![service diagram](serviceDiagram.png)

### Web application
- Editor for managing connections.
- Device code flow was used for authentication, so credentials was securely stored in Resco Cloud.

- Editor for setting up mapping and configuration.
- The user is able to define filters.
- The editor can detect deleted entities or fields.

![editor overview](editorOverview.png)
![lookup mapping](lookupMapping.png)

- The user can preview the export/import.

![import preview](importPreview.png)

### 3rd party system
- A very important part of creating the solution was studying documentation about the external system (Business Central).
- For Business Central, it was necessary to create some extensions that would allow reading the version number of the tables.
- You can see the code for these extensions on the page: [BC Extensions](https://github.com/Resconet/RescoIntegrations)

### Connectors
- The Simple.OData.Client library was used in the OData connector.
- OAuth2.0 device code flow was implemented.

Based on our company strategy, this project was stopped, so other connectors were not implemented. 
From my point of view it was very, very interesting project.

[->Next: Blob storage connectors](../blobStorage/readme.md)