[Home](../README.md)
# Migration Tool For UAT Environments
## Problem
![actual situation](actualSituationDiagram.png)
Resco Server offers the possibility to migrate data and schema between UAT environments. However, it would be beneficial to add the ability for users to migrate only smaller components and to create a clone of the organization with just a few clicks.
In addition, the migration/cloning process should be implemented as a long-running job, allowing users to continue working without waiting on the page.


## Solution
![solution diagram](solutionDiagram.png)
* Data is divided into smaller selectable components.
* The user is able to select which components should be migrated.
* The user is able to clone the whole organization with just a few clicks.
* Last, but not least, the migration process is implemented as a long-running job, which is executed every 5 minutes, and data is migrated in smaller batches.

<!-- UI-Component selection:
![export selection](exportSelection.png)
UI-Metadata comparison-Import preview
![schema comparison](metadataComparison.png) -->

[->Next: Integrations with a third-party system.](../integrations/readme.md)