---
title: "How to Create a Configurable Object"
url: /modularmom/before-you-start/quick-start-to-developing-with-opcenter-modular-manufactring/how-to-create-a-configurable-object/
weight: 3
---

<!-- 1. [Modular MOM](c:\users\anil.birajdar\desktop\temp\index.html)
1. [Before You Start](c:\users\anil.birajdar\desktop\temp\Before-You-Start_127740192.html)
1. [Quick Start to Developing with Opcenter Modular Manufacturing](c:\users\anil.birajdar\desktop\temp\Quick-Start-to-Developing-with-Opcenter-Modular-Manufacturing_134455239.html)
# **Modular MOM : How to Create a Configurable Object**  -->
Created by Unknown User (sergey.postoyalko), last modified by Aghazarian, Nick on Apr 07, 2022 

A Configurable Object contains a collection of Fields and can be represented in the C# class of the Object. It is the core of the Metamodel design because it enables the creation of classes or object types to describe an object instance, the central idea of the Metadata. 
## **Prerequisites**
The following software is required to create a new CO for Opcenter Modular Manufacturing:

- Visual Studio version 16.8.3 or newer as well as the following Visual Studio workloads :
  - ASP.NET and web development
  - .NET desktop development
- Latest version of .NET 5.0 SDK
- SQL Server Management Studio version 14.0 Express or newer.
- SQL Server version 14.0 Express or newer. Follow standard procedures to install the **Default** instance, otherwise change the environment configuration in case of an instance-based installation. Then open SQL Server Management Studio and verify that you can connect to the server by using the Windows authentication.
- A  tool to clone Git repositories. It is recommended to use either Sourcetree or Git Bash.
## **Workflow**
1. [Prepare a database](/modularmom/before-you-start/quick-start-to-developing-with-opcenter-modular-manufactring/how-to-create-a-configurable-object/preparing-a-database/).
1. Create an empty folder for source code with a short name. For convenience the path to the created folder should contain no spaces.
1. Clone the following Git repositories into your folder for source code:

|**Git repository name**|**Git repository URL**|
| :- | :- |
|**MetadataRuntime**|<https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/MetadataRuntime>|
|**M1\_Template**|<https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/M1_Template>|
|**M1\_Template.Tests**|<https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/M1_Template.Tests>|
1. [Update NuGet.Config](/modularmom/before-you-start/quick-start-to-developing-with-opcenter-modular-manufactring/how-to-create-a-configurable-object/updating-nuget.config/).
1. Empty the folder C:\Users\<*your user folder*>\.nuget\**packages**.
1. [Install System supplied tools and scripts](/modularmom/before-you-start/quick-start-to-developing-with-opcenter-modular-manufactring/how-to-create-a-configurable-object/install-system-supplied-tools-and-scripts/)
1. [Prepare the MetadataRuntime Platform.](/modularmom/before-you-start/quick-start-to-developing-with-opcenter-modular-manufactring/how-to-create-a-configurable-object/preparing-metadataruntime-platform/)
1. [Set up a new model from the template](/modularmom/before-you-start/quick-start-to-developing-with-opcenter-modular-manufactring/how-to-create-a-configurable-object/preparing-metadataruntime-platform/).
1. [Create a new CO](/modularmom/before-you-start/quick-start-to-developing-with-opcenter-modular-manufactring/how-to-create-a-configurable-object/creating-a-new-co/).
1. Optionally, [perform unit test on the new model](c:\users\anil.birajdar\desktop\temp\Performing-Unit-Tests-on-New-Model_127733830.html).
1. [Publish, deploy, and test End-to-End](c:\users\anil.birajdar\desktop\temp\127733170.html)
1. [Set the system variables](c:\users\anil.birajdar\desktop\temp\Setting-System-Variables_127739693.html).
1. [Generate the new model](c:\users\anil.birajdar\desktop\temp\Generating-New-Models_127739806.html).
1. [Build the solutions](c:\users\anil.birajdar\desktop\temp\Building-Solutions_127739810.html).
1. [Publish the Platform API](c:\users\anil.birajdar\desktop\temp\Publishing-Platform-API_127739830.html).
1. [Publish the data model](c:\users\anil.birajdar\desktop\temp\Publishing-Data-Model_127739832.html).
1. [Configure the Platform API](c:\users\anil.birajdar\desktop\temp\Configuring-Platform-API_127739834.html).
1. [Launch the generated API](c:\users\anil.birajdar\desktop\temp\Launching-Generated-API_127739837.html).
1. [Cleaning MetadataRuntime Platform](c:\users\anil.birajdar\desktop\temp\Cleaning-MetadataRuntime-Platform_134454467.html)
1. Enter *http://localhost:5000* in the address bar of your browser.
## **Result**
The new Configurable Object is created in a new module and works correctly.
## **Attachments:**
![](How-to-Create-a-Configurable-Object\_125339498.002.png) [SQL Server Instance Configuration.png](c:\users\anil.birajdar\desktop\temp\attachments\125339498\125340228.png) (image/png) 
![](How-to-Create-a-Configurable-Object\_125339498.002.png) [Connecting to SQL Server.png](c:\users\anil.birajdar\desktop\temp\attachments\125339498\125340240.png) (image/png) 
![](How-to-Create-a-Configurable-Object\_125339498.002.png) [SQL Login Properties.png](c:\users\anil.birajdar\desktop\temp\attachments\125339498\125340246.png) (image/png) 
![](How-to-Create-a-Configurable-Object\_125339498.002.png) [Checking Login Properties.png](c:\users\anil.birajdar\desktop\temp\attachments\125339498\125340249.png) (image/png) 
![](How-to-Create-a-Configurable-Object\_125339498.002.png) [New C# Class.png](c:\users\anil.birajdar\desktop\temp\attachments\125339498\125340799.png) (image/png) 
![](How-to-Create-a-Configurable-Object\_125339498.002.png) [New JSON File.png](c:\users\anil.birajdar\desktop\temp\attachments\125339498\125340822.png) (image/png) 
![](How-to-Create-a-Configurable-Object\_125339498.002.png) [Starting New Instance in VS.png](c:\users\anil.birajdar\desktop\temp\attachments\125339498\125341391.png) (image/png) 
## **Comments:**

|<p>Create a new CO.</p><p>After creating a CO, add some steps on how to define unit tests and run the tests</p><p>![](How-to-Create-a-Configurable-Object\_125339498.003.png) Posted by cs4rjf at Jul 22, 2021 23:46 </p>|
| :- |
Document generated by Confluence on Jul 28, 2022 11:21

[Atlassian](https://www.atlassian.com/)
**Created with an evaluation copy of Aspose.Words. To discover the full versions of our APIs please visit: https://products.aspose.com/words/**
