---
title: "Configuring-the-Development-Environment"
url: /modularmom/before-you-start/quick-start-to-developing-with-opcenter-modular-manufactring/configuring-the-development-environment/
weight: 1
---
<!-- 1. [Modular MOM](c:\users\anil.birajdar\desktop\temp\index.html)
1. [Before You Start](c:\users\anil.birajdar\desktop\temp\Before-You-Start_127740192.html)
1. [Quick Start to Developing with Opcenter Modular Manufacturing](c:\users\anil.birajdar\desktop\temp\Quick-Start-to-Developing-with-Opcenter-Modular-Manufacturing_134455239.html)
# **Modular MOM : Configuring the Development Environment**  -->
Created by Accorsi, Carlo, last modified by Aghazarian, Nick on May 10, 2022 

This document describes how to configure a Visual Studio Environment for Metadata Runtime Solutions and Projects.
## **Prerequisites**
**Required Software**

- Visual Studio 2019 Professional (16.8.3) or newer
- DotNetCore SDKs : 5.0+,  (we should not need 3.1.300+, 2.1.805+)
- Microsoft SQL Server 14.0 Express or greater
- Microsoft SQL Server Management Studio 18.5 or greater

**Required Authentication/Authorization**

- An SWQA domain account to access both this wiki as well as the git repos. So if you're reading this on the wiki, you already have an account.
- Permissions to be configured for both of these systems for appropriate access, e.g. edit for wiki.

[Enable LongPath Support in Windows.](https://momwiki02.industrysoftware.automation.siemens.com/x/MivlBg)
## **Step 1: Install MS SQL database server and SQL Management Studio**
These products are available with MSDN licenses or available for evaluation purposes.  Follow standard procedures to install the **Default** instance, otherwise change the environment configuration in case of an instance-based installation
## **Step 2: Validate the database server is running and you can connect**
**Procedure**

1. Connect to **localhost** server using **Windows Authentication** and SWQA credentials.
1. Verify your login has the sysadmin role.
1. In your Windows system environment variables, define the hostname and then restart Visual Studio to apply environment changes:
   1. Set the variable **MODMOM\_DBHOSTNAME** to the desired name of your database host. Defaults to **localhost**.
   1. Set the variable **MODMOM\_DBNAME** to the desired name of your database. Defaults to **ModMomDb**.
   1. Save and apply variable.
      You can validate the variable is set by starting a new console window.
1. Create an empty database by using the following script :

-- Drop if exists and create database--

-- Note: The database must match your MODMOM\_DBNAME environment variable--

USE master

IF EXISTS(select \* from sys.databases where name='ModMomDb')

BEGIN

ALTER DATABASE ModMomDb SET SINGLE\_USER WITH ROLLBACK IMMEDIATE;

DROP DATABASE ModMomDb

END

CREATE DATABASE ModMomDb

ALTER DATABASE ModMomDb SET ALLOW\_SNAPSHOT\_ISOLATION ON   
## **Step 3: Clone Git Repositories**

For the purposes of this document command line tools are used. Perform equivalent functions from within Visual Studio or any other Git tool.

**Procedure**

1. Prepare an empty directory for source code. Preferably a short path, for example c:\source. You may rename the default directory **MetadataRuntime** if desired.
1. ` `Clone one of the listed repositories into your empty source directory by using either ‘git clone’ or any SCM tool.

|<h5>**Azure Devops Repo Name**</h5>|<h5>**Repo URL**</h5>|
| :- | :- |
|**MetadataRuntime**|<https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/MetadataRuntime>|
1. Change into the git repository and verify master branch.
1. Create a feature branch using **checkout -b** (**git checkout -b** *branch\_name)* and start coding.

Branch names are arbitrary and should convey some meaning as they will proliferate, one simple approach to organizing them is to prefix with *initials/branch\_name* . Creating branches in this form allows UI tools to expand/collapse the list of branches with a tree control.
## **Source Solutions and Projects**
To build MetadataRuntime you can run this PowerShell script:

![](Configuring-the-Development-Environment\_115682527.002.png)

Here below you find a description of each solutions, listed in their build/run order:

1. **Camstar AOP Aspects Solution**
   1. Automation\ILWeavers\Metadata\**Camstar.Metadata.Aspects.sln**
   1. It provides additional tests on metadata weaver to validate the weaver nuget package
      (Optional) If you work on metadata weaver, then build also: Automation\ILWeavers\Metadata\**Camstar.Metadata.Aspects.Tests.sln**

1. **Observability Solution**
   1. Automation\ILWeavers\Observability\**ObservabilityAspects.sln**
   1. It provides additional tests on observability weavers to validate the weavers nuget packages
      (Optional) If you work on observability weavers, then build also: Automation\ILWeavers\Observability\**ObservabilityAspects.Tests.sln**

1. **Main Solution**
   1. Platform\**Platform.sln**
   1. Requires [nuget.org](http://nuget.org)  <http://nuget.org>package source feed until we determine internal server.
1. **Sample Model Solution – Sample Metamodel**
   1. Platform\InputMetadataModel\SampleModel\**Camstar.Core.SampleModel.sln**

1. **DTO Generator Project – Generates Input / Read, Write and Message models from Sample Model**
   1. This is a consolidated generator and covers all code generation of (Sample)
   1. MetaModel.Platform\Siemens.MOM.Model.DtoGenerator\**Siemens.MOM.Model.Generator.csproj**
   1. Run/Debug this project
1. **Generated Models Solution – Where Generators write models, maps and messages are written**
   1. Platform\GeneratedModels\**GeneratedModels.sln**
   1. Ensure Models are generated from the previous step with recent datetimes
1. Build **GeneratedModels.sln**:  3 projects should build successfully
## **Deploy Database Schema**
**2021-04-13 update**: The environment variable **MODMOM\_DBUSERNAME** determines how the governance / database will operate

- When set to **Memory\_Database** the environment will use a SQL in memory only database - No password is needed.
- When set to **Trusted\_Connection** the environment will assume a Windows trusted authentication connection to a MS Sql Server database - Current credentials are used, no password is needed.
- When set to anything else, the password is also expected to be set and these two values form the database credentials. 

**[Matteo: I fear this is not up-to-date[Accorsi, Carlo](https://momwiki02.industrysoftware.automation.siemens.com/display/~carlo.accorsi) [Nagamalli, Ramesh](https://momwiki02.industrysoftware.automation.siemens.com/display/~cs4rjf) could you please verify it?]**

**Database Connection Modes**

- Runtime – Schema is read-only, this is used under normal operation of the system
- Upgrade – Schema is compared with the logical model and differences are deployed to the database.
  - Limits apply, most adds/updates occur without intervention
  - Data is preserved using this method
- Install – Schema is dropped if exists and re-created, all data is lost using this method
- Connection String
  - For development purposes, Windows Authentication is used for connectivity and requires only a hostname and database name.
  - The class Platform\Siemens.MOM.Model.WriteBase\Session\SessionHelper.cs contains the hard-coded hostname and database references.
  - Connectivity will be parameterized / externalized in the future
- From the **Integration Tests Solution**, run the test **WriteModelNhTests.DeployDatabase()**  
  - This connects to the database with the Upgrade Mode
    - Since no tables exist, the result is equivalent to using Install Mode
  - This process deploys tables representing the logical model to the empty database
- Database is ready for use
## **API Configuration**
- The API needs the location and namespaces of the Read/Write assemblies
- These values are defined in the **Manifest.XML** file located in the root of the project **Siemens.MOM.Platform.Api**
- By default, the Sample model values are set. If using another model, make the appropriate updates to paths and namespaces.
## **Launch API**
1. Launch the project **Siemens.MOM.Platform.Api**: The server should start on localhost:5000.
## **Invoke API**
**[Matteo: I fear this is not up-to-date [Nickenig, Gero](https://momwiki02.industrysoftware.automation.siemens.com/display/~gero.nickenig) and [Nagamalli, Ramesh](https://momwiki02.industrysoftware.automation.siemens.com/display/~cs4rjf) could you please verify it?]**

For latest and correct API post, please refer to this repo:

<https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/RestAPISamples>

it contains a set of Postman collections that you can use to check if your local service is running

**Procedure**

1. Do either of the following:
   1. Use <http://localhost:5000> to see the available API endpoints and invoke them here
   1. Use Postman or cURL:

$curl --location --request POST 'http://localhost:5000/api/Factory' \

--header 'Content-Type: application/json' \

--data-raw '{

`  `"tenantId": "string",

`  `"entity": {

`    `"defaultQty": 90,

`    `"description": "string",

`    `"myProp": "prop1",

`    `"name": "f1"

`  `}

}'
## **Sample Inputs**

Due to the frequency of the update in the platform some of this examples may be out of date.
Please refer to this repo for updated collections:

<https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/RestAPISamples>

**Examples of API inputs for various endpoints** 

As of 2021-03-21, the API's are being redone and the input bodies will change. 

- Create Factory & locations added implicitly from the service logic
  **POST /api/Factory**


{

`    `"tenantId": "string",

`    `"entity": {

`        `"defaultQty": 90,

`        `"description": "string",

`        `"myProp": "prop1",

`        `"name": "f1"

`    `}

}

- Create Factory with locations added explicitly & initialize productionstatus
  **POST /api/Factory**


{

`  `"tenantId": "string",

`  `"entity": {

`      `"name": "f2",

`      `"description": "added thru api",

`      `"defaultQty": 900,

`      `"myProp": "f2-prop1",

`      `"locations": [

`          `{

`              `"name": "f2-loc1",

`              `"description": "added thru api",

`              `"status": 1

`          `},

`          `{

`              `"name": "f2-loc2",

`              `"description": "added thru api",

`              `"status": 2

`          `},

`          `{

`              `"name": "f2-loc3",

`              `"description": "added thru api",

`              `"status": 3

`          `}

`      `],

`      `"productionStatus": {

`          `"status": 100

`      `}

`  `}

}

- Create Employee - Set Factory reference by Id
  **POST /api/Employee**


{

"tenantId": "string",

"entity": {

`  `"department": "dept-1",

`  `"description": "blah...",

`  `"email": "no-email",

`  `"factory": {

`    `"guidBasedId": "12EF7ED5-1D68-432D-A515-AC40018140E0"

`  `},

`  `"name": "e0"

}

}

- Create Employee - Set Factory reference by Name
  **POST /api/Employee**


{

`  `"tenantId": "string",

`  `"entity": {

`    `"department": "dept-1",

`    `"description": "blah...",

`    `"email": "no-email",

`    `"factory": {

`      `"refName": "f1"

`    `},

`    `"name": "e1"

`  `}

}

**This document was truncated here because it was created in the Evaluation Mode.**
**Created with an evaluation copy of Aspose.Words. To discover the full versions of our APIs please visit: https://products.aspose.com/words/**
