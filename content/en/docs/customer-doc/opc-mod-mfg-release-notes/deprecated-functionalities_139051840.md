---
title: "Deprecated Functionalities"
url: 
weight: 4
---

**Created by Alvarez Villanueva, Beatriz, last modified on Apr 26, 2022**   

The following functionalities have been deprecated and  will no longer be supported in the upcoming versions.

Configure Metadata model query statements in momsql.json files

In order to configure Metadata model query statements, the usage of the  **SqlTexts** section within **momsql.json** file is replaced by separate **momsql.sql** files, one file for each database type.

The example below reflects the new configuration files:

- queryName.**momsql**.json
- queryName.**Standard**.momsql.**sql**
- queryName.**PostgreSQL**.momsql.**sql**

