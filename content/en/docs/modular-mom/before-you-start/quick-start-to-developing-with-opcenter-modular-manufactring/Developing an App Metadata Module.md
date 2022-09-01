---
title: "Developing an App / Metadata Module"
url: /modularmom/before-you-start/quick-start-to-developing-with-opcenter-modular-manufactring/developing-an-app-metadata-module/
weight: 5
---

<!-- 1. [Modular MOM](c:\users\anil.birajdar\desktop\temp\index.html)
1. [Before You Start](c:\users\anil.birajdar\desktop\temp\Before-You-Start_127740192.html)
1. [Quick Start to Developing with Opcenter Modular Manufacturing](c:\users\anil.birajdar\desktop\temp\Quick-Start-to-Developing-with-Opcenter-Modular-Manufacturing_134455239.html)
# **Modular MOM : Developing an App / Metadata Module**  -->
Created by Alvarez Villanueva, Beatriz, last modified by Nagamalli, Ramesh on Feb 09, 2022 

A Metadata Module is an isolated and independently deployable unit that can be composed with other loosely couple modules in order to create a customized Product. A metadata model is used to configure the business objects and processes used by a Modular MOM application. A metadata model will have dependencies on many other models that are maintained separately and stored in their own git repos.
## **Directory Structure**
Because the metadata is persisted as C# files and must be compiled into a single binary, a module and all of its dependencies must all be accessible to the project, both during development (for intelligence to work properly) and during the build. However, nested dependencies will cause compilation issues if they are all included. To address this, each module will specify a flat list of all of the dependencies required as you can see in the examples below. 

**Example of nested dependencies and the obvious duplicates**

- MESApp
  - **Common**
  - Dispatch
    - **Common**
    - ESigs
      - Common
  - TrackAndTrace
    - **Common**
    - DataCollection
      - **Common**
    - ESigs
      - **Common**
  - ESigs
    - **Common**
  - DataCollection
    - **Common**

**Example of the module dependencies without the duplication**

- MESApp
  - Common
  - Dispatch
  - TrackAndTrace
  - ESigs
  - DataCollection

In order to create a consistent Module directory structure, Modular MOM uses the submodules feature of git, so each model must observe a consistent directory structure.

The complete repos for each dependency will be cloned into a directory under the **Code** folder, excluding any deeper dependencies.

Each module will have an associated **.Tests** repo managed as a dependency to the module.
## **Module Directory Layout**
To fulfill this requirement, Modular MOM is utilizing the submodules feature of git. To more easily manage these dependency submodules, each model will conform to a consistent directory structure. The structure *without any dependencies added* will have the following structure:

MESApp
`    `\Code
`        `\Model
`        `\Services
`        `\Tracking
`        `dependencies.props
`        `nuget.config
`        `.csproj
`    `\Tests
`    `MESApp.sln
`    `[README.md](http://README.md)
`    `.gitmodules
`    `Copy-From-MESApp.ps1

The complete repos for each dependency will be cloned into a directory under the **Code** folder:

MESApp
`    `\Code
`        `\M1\_Common
`        `\M1\_DataCollection
`        `\M1\_Dispatch
`        `\M1\_ESigs
`        `\M1\_TrackAndTrace

One effect of this change is that each module will have an associated .Tests repo, and this repo is treated as a dependency to the module.

MESApp.Tests
`    `\IntegrationTests\MyApp.IntegrationTests
`    `\Unit.Tests

MESApp
`    `\Tests
`        `\MyApp.Tests
## **Creating a New Module**
To create a new module you have to modify a copy of the module **M1\_Template**. 

DO NOT clone the new git repo to your local machine. The  */***Copy-From-Template.ps1 MESApp*** will create the repo and push it to the remote repo.

**Prerequisites**

Git version 2.3 or higher to run the script **Copy-From-Template.ps1**. It is highly recommended to install the latest version.

**Procedure**

The procedure below explains how to create the **MeSApp** module. module. Follow the steps below to create the **MESApp** module:

1. Create the "remote" repos. This requires the assistance of someone who has the permission to add repos. These repos should be empty (i.e. without history).
   1. Module: **M1\_MESApp**
   1. Module tests: **M1\_MESApp.Tests**
1. Open a Powershell command prompt window
1. Navigate to the directory containing the repos **CD \Repos**
1. If you have not yet, get or update the Template repos
   1. git clone [https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/M1_Template](https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/WS_M1_Template) M1\_Template
   1. git clone [https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/M1_Template.Tests](https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/WS_M1_Template.Tests) M1\_Template.Tests
1. Copy the template as a starting point for the new model:
   1. CD M1\_Template
   1. Execute the script **./Copy-From-Template.ps1** with the following parameters:

|**Parameter**|**Description**|
| :- | :- |
|**newName**|The name of the repo to create. In this example: **MESApp**|
|**newURL**|The URL of the remote git server where the model will be created. It defaults to the same repo as the M1\_Template. If you're using a separate git server, e.g. <https://gitlab.com/username/><br> |
|**-replaceRepo**|This switch will replace any data in the remote repo.|

Example: **./Copy-From-Template.ps1 MESApp -replaceRepo**

1. Using your IDE, search for **TODO**  and manually make the changes described such as the module description.
## **Modifying a Module Open a Powershell command prompt window**
1. Go to the directory that contains the repos: **CD \Repos**
1. Get the module code: git clone [https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/M1_MESApp](https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/WS_M1_MESApp) M1\_MESApp
1. Enter the module directory:  **CD M1\_MESApp**
1. Pull the code for existing dependencies: git submodule update --init --depth=1
1. Put the Tests submodule onto the main branch:
   1. cd Tests/M1\_MESApp.Tests
   1. git checkout main
## **Adding a  Submodule to an existing module**
1. Add the new module e.g. ESigs:  git submodule add [https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/M1_ESigs](https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/WS_M1_ESigs) Code/M1\_ESigs
## **Building the Module**
1. Open the module solution.
1. Build the module project. 

Notes for Troubleshooting

- Building submodules is not needed and will cause problems in compiling the containing module.
- In case of an error indicating that something cannot be found in Comon.Tests, check if the "--depth=1" was missing from the **git submodule update** command
## **Updating Test Code**
1. Open the module solution.
1. Make the changes to the test project.
1. Commit and push the changes from the test submodule and then:
   1. From the **Tests/MESApp.Tests** directory, this will update the reference in the module to the new commit point.
   1. From the **M1\_MESApp** directory, this will save the updated commit point for the next time it's cloned
## **Updating a Submodule to a new Commit Point**
Once changes have been made to a submodule repo, the other repos that depend on the submodule must be updated to reference the new commit point.

1. Navigate to the submodule directory : cd /repos/M1\_MESApp/Code/ESigs
1. Get potential commit points: git fetch
1. Update the commit point: git checkout \[main | branchName]
1. cd ../..
1. Commit and push the changes to the **M1\_MESApp** module
## **Removing a Submodule from an Existing Module**
1. Remove the code: git submodule deinit  Code/M1\_ESigs
1. Remove the reference: git rm Code/M1\_ESigs
1. Cleanup git: Remove-Item -LiteralPath ".git/modules/M1\_ESigs" -Force -Recurse
## **Troubleshooting**
**Symptom**:

remote: TF401035: The object '0bfc9ad18ee19be277937ff25a8f70ea0acab2d2' does not exist.
fatal: protocol error: bad pack header

**Cause:**

A submodule was updated in place (e.g. changes made to M1\_POC\Code\M1\_Common instead of \M1\_Common) and committed but not pushed. and the submodule reference in the parent module was committed and pushed. This causes the remote repo to reference a commit identifier from the local repo that hasn't been pushed to the remote repo.

**Fix:**

Go to the submodule and checkout main.

## **Comments:**

|<p>[De Pascale, Mauro](https://momwiki02.industrysoftware.automation.siemens.com/display/~mauro.de_pascale) [Alvarez Villanueva, Beatriz](https://momwiki02.industrysoftware.automation.siemens.com/display/~ITR00446): If the module developer must be aware about which platform version he has to reference, a note about it would be useful. See also discussion in teams development channel:</p><p>[Simone, Maurizio (DI SW MOM R&D CL MOC): Build error creating new metadata module ](https://teams.microsoft.com/l/message/19:51e32cfa324c4a5ea5850dfb1633234c@thread.tacv2/1635532763872?tenantId=6b5bd02b-92d2-40b2-9ffd-c9c94280c757&groupId=0c5fcaad-b1cb-4b6a-9a4c-5a2d7ecc14dd&parentMessageId=1635532763872&teamName=Modular%20MOM%202.x&channelName=Development&createdTime=1635532763872)<br>posted in Modular MOM 2.x / Development at venerdì 29 ottobre 2021 20:39:23</p><p>[De Pascale, Mauro (DI SW MOM R&D CL EMI): Hi Modular MOM 2.x, I just built a new STAB… ](https://teams.microsoft.com/l/message/19:51e32cfa324c4a5ea5850dfb1633234c@thread.tacv2/1635854757551?tenantId=6b5bd02b-92d2-40b2-9ffd-c9c94280c757&groupId=0c5fcaad-b1cb-4b6a-9a4c-5a2d7ecc14dd&parentMessageId=1635854757551&teamName=Modular%20MOM%202.x&channelName=Development&createdTime=1635854757551)<br>posted in Modular MOM 2.x / Development at martedì 2 novembre 2021 13:05:57</p><p>and this bug: [Bug 25616](https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_workitems/edit/25616): "ModMoM Module template is out of date (repos: M1\_Template\.Tests)"<br><br>There's a new page with the description of the platform\model versioning: [Platform & Model Versioning](https://momwiki02.industrysoftware.automation.siemens.com/pages/viewpage.action?pageId=134457576)<br> </p><p><br> </p><p>![](134455247.002.png) Posted by ITR00527 at Nov 02, 2021 16:18 </p>|
| :- |
Document generated by Confluence on Jul 28, 2022 11:21

[Atlassian](https://www.atlassian.com/)
**Created with an evaluation copy of Aspose.Words. To discover the full versions of our APIs please visit: https://products.aspose.com/words/**
