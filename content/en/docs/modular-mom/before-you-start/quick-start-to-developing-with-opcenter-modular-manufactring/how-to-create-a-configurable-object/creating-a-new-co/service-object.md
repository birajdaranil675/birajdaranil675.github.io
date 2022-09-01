---
title: "Creating a New Service Object"
weight: 2
---
<!-- 1. [Modular MOM](c:\users\anil.birajdar\desktop\temp\index.html)
1. [Before You Start](c:\users\anil.birajdar\desktop\temp\Before-You-Start_127740192.html)
1. [Quick Start to Developing with Opcenter Modular Manufacturing](c:\users\anil.birajdar\desktop\temp\Quick-Start-to-Developing-with-Opcenter-Modular-Manufacturing_134455239.html)
1. [How to Create a Configurable Object](c:\users\anil.birajdar\desktop\temp\How-to-Create-a-Configurable-Object_125339498.html)
1. [Creating a New CO](c:\users\anil.birajdar\desktop\temp\Creating-a-New-CO_134452147.html)
# **Modular MOM : Creating a New Service Object**  -->
Created by Unknown User (sergey.postoyalko), last modified by Aghazarian, Nick on Apr 07, 2022 

In this page, a new service object named **NamedService** will be created for *NDO* that was created in [How to Create a Configurable Object](c:\users\anil.birajdar\desktop\temp\How-to-Create-a-Configurable-Object_125339498.html). Follow this procedure to create a new service object
## **Procedure**
1. Open Visual Studio.
1. Open **M1\_<***your model name***>.sln** located in <*path of your folder for source code*>\**M1\_**<*your model name*>.
1. Right-click **M1\_<***your model name***>.csproj**.
1. Select **Add** then **New Folder** (you can rename the new folder as you want.)
1. Right-click the new folder.
1. Select **Add ,** then **New Item**.
1. Add a new C# class and name it as you want.
1. Replace all in the new C# class with your code following the code example and its description below.

Click here to see the code example

This code adds a new inherited service object named **NamedService** that will allow you to add, update, and delete *NDO*:

using System.Collections.Generic;

using Siemens.MOM.MetaModel.Framework;

using Siemens.MOM.MetaModel.Framework.AOP\_Aspects;

using Siemens.MOM.MetaModel.Interfaces;

using Siemens.MOM.Platform;

namespace M1\_<your model name>.Services

{

`    `[COTypeId("0x2rLbn")]

`    `public partial class NamedService<ClassType> : ServiceObject, INamedModelingService<ClassType> where ClassType : class, INamed

`    `{

`        `public ClassType MyData { get; protected set; }

`        `IBaseObject IModelingService.GetModelingObject() => MyData;

`        `IBaseObject IModelingService.Create() => Add() as IBaseObject;

`        `bool IModelingService.Update(IBaseObject obj) => Update(obj as ClassType);

`        `bool IModelingService.Delete(IBaseObject obj) => Delete(obj as ClassType);

`        `public ClassType Add()

`        `{

`            `MyData = Create<ClassType>();

`            `return MyData;

`        `}

`        `public virtual ClassType Add(string name)

`        `{

`            `MyData = Create<ClassType>();

`            `MyData.ObjectName = name;

`            `return MyData;

`        `}

`        `public virtual bool Update(ClassType newData)

`        `{

`            `MyData = newData;

`            `return Update\_User();

`        `}

`        `public virtual bool Update\_User()

`        `{ return true; }

`        `public virtual bool Delete(ClassType data)

`        `{

`            `MyData = null;

`            `return (data as BaseObject).Delete();

`        `}

`        `public virtual bool Delete(string name)

`        `{

`            `return (Get(name) as BaseObject).Delete();

`        `}


`        `public IBaseObject Get(InstanceId id)

`        `{

`            `MyData = \_ExecutionContext.GetById<ClassType>(id);

`            `return MyData;

`        `}

`        `public virtual ClassType Get(string name)

`        `{

`            `MyData = \_ExecutionContext.GetByName<ClassType>(name);

`            `return MyData;

`        `}

`        `public IEnumerable<IBaseObject> GetAll(QueryOption queryOption)

`        `{

`            `return \_ExecutionContext.GetAll<ClassType>(queryOption);

`        `}

`        `INamed INamedModelingService.Get(string name) => Get(name);

`    `}

}

Click here to see description of the code example

|**Code block or code line**|**Description**|
| :- | :- |
|namespace M1\_<your model name>.Services|<p>Specifies the model namespace.</p><p>Replace *<your model name>* with the name of your model.</p>|
|[COTypeId("0kTZhcN")]|<p>**COTypeId** is a unique ID that must be assigned to each object in the model. If the same COTypeId is used in different object, an error is generated while building the model.</p><p>To generate a new COTypeId (assumes the prerequisite of the IdGenerator tool is installed):</p><p>**Create new COTypeId**</p><p>IdGenerator COTypeId</p><p>This will generate and output a unique id which can be copy/pasted into the new class</p><p>![](Creating-a-New-Service-Object\_134453962.002.png)</p>|
|public partial class NamedService<ClassType> : ServiceObject, INamedModelingService<ClassType> where ClassType : class, INamed |<p>Defines a new inherited class named **NamedService.** **partial** means that this class can be extended by using different workspaces. If a customer using the Platform wants to extend this class, *partial* will let the customer to create the same class with the same name, make it partial too, and add either necessary fields or functionalities.</p><p>**NamedService** is inherited from *ServiceObject*. Base functionalities of *NamedService* are realized in *ServiceObject*. So, all services that we want to implement must be inherited either from *ServiceObject* or its successors.</p><p>**INamedModelingService** is an extended version of the IModeling interface. This interface is designed to interact with the Modeling objects.</p><p>You can right-click **INamedModelingService** and select **Go to Definition**. You will see what interfaces must be realized. The following methods must be created: Add, Delete, and Update and the CRUD operations. They are basic operations that allow you to create, remove, and update objects.</p><p>where* **ClassType : class, INamed** – specifies that ClassType must realize the methods from the INamed interface.</p>|
|<p>public ClassType MyData { get; protected set; }</p><p>IBaseObject IModelingService.GetModelingObject() => MyData;</p><p>IBaseObject IModelingService.Create() => Add() as IBaseObject;</p><p>bool IModelingService.Update(IBaseObject obj) => Update(obj as ClassType);</p><p>bool IModelingService.Delete(IBaseObject obj) => Delete(obj as ClassType);</p>|The type is specified by using **ClassType** as this a generic class. Apart from the class,  ClassType is also submitted. In this case, **ClassType** is NDO that is created in [Creating a New Named Object](c:\users\anil.birajdar\desktop\temp\Creating-a-New-Named-Object_127733034.html).|
|<p>public ClassType Add()</p><p>{</p><p>`    `MyData = Create<ClassType>();</p><p>`    `return MyData;</p><p>}</p><p></p><p>public virtual ClassType Add(string name)</p><p>{</p><p>`    `MyData = Create<ClassType>();</p><p>`    `MyData.ObjectName = name;</p><p>`    `return MyData;</p><p>}</p>|An object of the ClassType type is created and added to MyData.|
|<p>public virtual bool Update(ClassType newData)</p><p>{</p><p>`    `MyData = newData;</p><p>`    `return Update\_User();</p><p>}</p><p>public virtual bool Update\_User()</p><p>{ return true; }</p>||
|<p>public virtual bool Delete(ClassType data)</p><p>{</p><p>`    `MyData = null;</p><p>`    `return (data as BaseObject).Delete();</p><p>}</p><p></p><p>public virtual bool Delete(string name)</p><p>{</p><p>return (Get(name) as BaseObject).Delete();</p><p>} </p>|This is the Delete method. **MyData** is set to null. Whatever the information, MyData is set to null and the base Delete method of BaseObject is requested.|
|<p>public IBaseObject Get(InstanceId id)</p><p>{</p><p>`    `MyData = \_ExecutionContext.GetById<ClassType>(id);</p><p>`    `return MyData;</p><p>}</p><p>public virtual ClassType Get(string name)</p><p>{</p><p>`    `MyData = \_ExecutionContext.GetByName<ClassType>(name);</p><p>`    `return MyData;</p><p>} </p>|**Get** is an additional method. It returns a specific object after receiving ID. If we need to receive NDO and we know the ID, we can use the Get method. |
|<p>public IEnumerable<IBaseObject> GetAll(QueryOption queryOption)</p><p>{</p><p>`    `return \_ExecutionContext.GetAll<ClassType>(queryOption);</p><p>}</p><p></p><p>INamed INamedModelingService.Get(string name) => Get(name);</p>|**GetAll** is an additional method. It returns all objects of the type that satisfies parameters of QueryOption. If the parameters are not defined, all the objects of NDO are returned.|
1. Save your changes to the C# class file.
1. Build **M1\_<***your model name***>.sln**.
## **Next Step**
[Perform Unit Tests on New Model](c:\users\anil.birajdar\desktop\temp\Performing-Unit-Tests-on-New-Model_127733830.html)
## **Attachments:**
![](Creating-a-New-Service-Object\_134453962.003.png) [New Folder.png](c:\users\anil.birajdar\desktop\temp\attachments\134453962\134452153.png) (image/png) 
![](Creating-a-New-Service-Object\_134453962.003.png) [New C# Class.png](c:\users\anil.birajdar\desktop\temp\attachments\134453962\134452157.png) (image/png) 
![](Creating-a-New-Service-Object\_134453962.003.png) [Starting a New Instance of IdGenrator.png](c:\users\anil.birajdar\desktop\temp\attachments\134453962\134452155.png) (image/png) 
![](Creating-a-New-Service-Object\_134453962.003.png) [New JSON File.png](c:\users\anil.birajdar\desktop\temp\attachments\134453962\134452156.png) (image/png) 
![](Creating-a-New-Service-Object\_134453962.003.png) [New C# Class.png](c:\users\anil.birajdar\desktop\temp\attachments\134453962\134452160.png) (image/png) 
![](Creating-a-New-Service-Object\_134453962.003.png) [New C# Class.png](c:\users\anil.birajdar\desktop\temp\attachments\134453962\134452154.png) (image/png) 
![](Creating-a-New-Service-Object\_134453962.003.png) [image2022-4-6_15-36-32.png](c:\users\anil.birajdar\desktop\temp\attachments\134453962\144142057.png) (image/png) 

Document generated by Confluence on Jul 28, 2022 11:21

[Atlassian](https://www.atlassian.com/)
**Created with an evaluation copy of Aspose.Words. To discover the full versions of our APIs please visit: https://products.aspose.com/words/**
