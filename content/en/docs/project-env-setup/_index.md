---
title: "Project Environment Setup"
url: /project_env_setup/
---

### 1. Mod MOM Project Env 

#### Installation 

1. Visual Studio 2022[\[LINK\]](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&channel=Release&version=VS2022&source=VSLandingPage&cid=2030&passive=false)

2. GIT[\[LINK\]](https://download.tortoisegit.org/tgit/2.13.0.0/TortoiseGit-2.13.0.1-64bit.msi)

3. MS SQL Server[\[LINK\]](https://go.microsoft.com/fwlink/?linkid=866658)

4. MS SQL Server Studio[\[LINK\]](https://aka.ms/ssmsfullsetup)

5. Visual Studio Code[\[LINK\]](https://code.visualstudio.com/download)

6. Node js[\[LINK\]](https://nodejs.org/en/download/)

1.2.  Server Setup[\[LINK\]](https://momwiki02.industrysoftware.automation.siemens.com/display/RevMOM/How+to+setup+the+SQL+Server+sa+user+on+Opcenter+X+VDI)

1.2.1. Reset sa account password [\[LINK\]](https://momwiki02.industrysoftware.automation.siemens.com/display/RevMOM/How+to+setup+the+SQL+Server+sa+user+on+Opcenter+X+VDI)

1.3. ![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.002.png) Sample Model

1.3.1. 1

1.3.1.1. Create DataBase 

1.3.1.1.1. Script

1.3.1.1.1.1. USE master
IF EXISTS(select \* from sys.databases where name='test1')
BEGIN
ALTER DATABASE test1 SET SINGLE\_USER WITH ROLLBACK IMMEDIATE
DROP DATABASE test1
END

CREATE DATABASE test1
ALTER DATABASE test1 SET ALLOW\_SNAPSHOT\_ISOLATION ON

1.3.2. 2

1.3.2.1. Create Project Directory 

1.3.2.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.003.png)

1.3.3. 3

1.3.3.1. Clone MetadataRuntime Repo[\[LINK\]](https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/MetadataRuntime)

1.3.3.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.004.png)

1.3.3.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.005.png)

1.3.3.1.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.006.png)

1.3.3.1.1.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.007.png)

1.3.4. 4

1.3.4.1. Launch Platform Solution

1.3.4.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.008.png)

1.3.5. 5

1.3.5.1. Set Startup Project

1.3.5.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.009.png)

1.3.6. 6

1.3.6.1. Update the DataBase name

1.3.6.1.1. With system configuration

1.3.6.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.010.png)

1.3.6.1.2. With json changes

1.3.6.1.2.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.011.png)

1.3.6.1.2.1.1. Before

1.3.6.1.2.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.012.png)

1.3.6.1.2.1.2. After

1.3.6.1.2.1.2.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.013.png)

1.3.7. 7

1.3.7.1. Generate DTO - Build Entire Solution

1.3.7.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.014.png)

1.3.8. 8

1.3.8.1. Observe the output

1.3.8.1.1. built output

1.3.8.1.1.1. Before

1.3.8.1.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.015.png)

1.3.8.1.1.2. After

1.3.8.1.1.2.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.016.png)

1.3.8.1.1.3. Final

1.3.8.1.1.3.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.017.png)

1.3.8.1.1.3.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.018.png)

1.3.9. 9

1.3.9.1. Test the Model

1.3.9.1.1. http://localhost:5000/index.html

1.4. ![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.002.png) Sample Model - Quick Launch

1.4.1. 1

1.4.1.1. Create DataBase 

1.4.1.1.1. Script

1.4.1.1.1.1. USE master
IF EXISTS(select \* from sys.databases where name='test1')
BEGIN
ALTER DATABASE test1 SET SINGLE\_USER WITH ROLLBACK IMMEDIATE
DROP DATABASE test1
END

CREATE DATABASE test1
ALTER DATABASE test1 SET ALLOW\_SNAPSHOT\_ISOLATION ON

1.4.2. 2

1.4.2.1. Update the DataBase name

1.4.2.1.1. With system configuration

1.4.2.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.010.png)

1.4.3. 3

1.4.3.1. Create Project Directory 

1.4.3.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.003.png)

1.4.4. 4

1.4.4.1. Clone MetadataRuntime Repo[\[LINK\]](https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/MetadataRuntime)

1.4.4.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.004.png)

1.4.4.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.005.png)

1.4.4.1.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.006.png)

1.4.4.1.1.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.007.png)

1.4.5. 5

1.4.5.1. Generate DTO - Build Entire Solution

1.4.5.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.014.png)

1.4.6. 6

1.4.6.1. Observe the output

1.4.6.1.1. built output

1.4.6.1.1.1. Before

1.4.6.1.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.015.png)

1.4.6.1.1.2. After

1.4.6.1.1.2.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.016.png)

1.4.6.1.1.3. Final

1.4.6.1.1.3.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.017.png)

1.4.6.1.1.3.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.018.png)

1.5. ![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.002.png) Order Management Model

1.5.1. 1

1.5.1.1. Create DataBase 

1.5.1.1.1. Script

1.5.1.1.1.1. USE master
IF EXISTS(select \* from sys.databases where name='test1')
BEGIN
ALTER DATABASE test1 SET SINGLE\_USER WITH ROLLBACK IMMEDIATE
DROP DATABASE test1
END

CREATE DATABASE test1
ALTER DATABASE test1 SET ALLOW\_SNAPSHOT\_ISOLATION ON

1.5.2. 2

1.5.2.1. Create Project Directory 

1.5.2.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.003.png)

1.5.3. 3

1.5.3.1. Clone Repo

1.5.3.1.1. Clone MetadataRuntime Repo[\[LINK\]](https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/MetadataRuntime)

1.5.3.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.004.png)

1.5.3.1.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.005.png)

1.5.3.1.1.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.006.png)

1.5.3.1.1.1.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.007.png)

1.5.3.1.2. Clone OrderManagement Repo[\[LINK\]](https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/M1_OrderManagement)

1.5.3.1.2.1. Main Module

1.5.3.1.2.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.004.png)

1.5.3.1.2.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.019.png)

1.5.3.1.2.1.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.006.png)

1.5.3.1.2.2. Sub Module

1.5.3.1.2.2.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.020.png)

1.5.3.1.2.2.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.021.png)

1.5.3.1.2.2.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.022.png)

1.5.4. 4

1.5.4.1. Cleanup

1.5.4.1.1. Metadata Runtime Folder

1.5.4.1.1.1. Before

1.5.4.1.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.023.png)

1.5.4.1.1.2. After

1.5.4.1.1.2.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.024.png)

1.5.4.1.2. Database

1.5.4.1.2.1. Before

1.5.4.1.2.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.025.png)

1.5.4.1.2.2. Script

1.5.4.1.2.2.1. USE master
IF EXISTS(select \* from sys.databases where name='test1')
BEGIN
ALTER DATABASE test1 SET SINGLE\_USER WITH ROLLBACK IMMEDIATE
DROP DATABASE test1
END

CREATE DATABASE test1
ALTER DATABASE test1 SET ALLOW\_SNAPSHOT\_ISOLATION ON

1.5.4.1.2.3. After

1.5.4.1.2.3.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.026.png)

1.5.5. 5

1.5.5.1. Update the DataBase name

1.5.5.1.1. With system configuration

1.5.5.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.010.png)

1.5.5.1.2. With json changes

1.5.5.1.2.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.011.png)

1.5.5.1.2.1.1. Before

1.5.5.1.2.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.012.png)

1.5.5.1.2.1.2. After

1.5.5.1.2.1.2.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.013.png)

1.5.6. 6

1.5.6.1. Generate OrderManagement dlls

1.5.6.1.1. 

1.5.6.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.027.png)

1.5.6.1.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.028.png)

1.5.6.1.1.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.029.png)

1.5.7. 7

1.5.7.1. Consume Order Management dll's 

1.5.7.1.1. Make Model Generator Settings

1.5.7.1.1.1. 

1.5.7.1.1.1.1. Launch Platform Solution (36 projects)

1.5.7.1.1.1.1.1. 

![](Mod%20Mom%20Project%20Env\_setupMod%20MOM%20Project%20En.008.png)

1.5.7.1.1.1.2. Go To Model Generator Project

**This document was truncated here because it was created in the Evaluation Mode.**
**Created with an evaluation copy of Aspose.Words. To discover the full versions of our APIs please visit: https://products.aspose.com/words/**
