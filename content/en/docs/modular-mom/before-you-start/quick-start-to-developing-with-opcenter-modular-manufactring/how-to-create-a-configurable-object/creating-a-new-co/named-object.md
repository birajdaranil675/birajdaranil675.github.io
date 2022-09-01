---
title: "Creating a New Named Object"
weight: 1
---
<!-- 1. [Modular MOM](c:\users\anil.birajdar\desktop\temp\index.html)
1. [Before You Start](c:\users\anil.birajdar\desktop\temp\Before-You-Start_127740192.html)
1. [Quick Start to Developing with Opcenter Modular Manufacturing](c:\users\anil.birajdar\desktop\temp\Quick-Start-to-Developing-with-Opcenter-Modular-Manufacturing_134455239.html)
1. [How to Create a Configurable Object](c:\users\anil.birajdar\desktop\temp\How-to-Create-a-Configurable-Object_125339498.html)
1. [Creating a New CO](c:\users\anil.birajdar\desktop\temp\Creating-a-New-CO_134452147.html)
# **Modular MOM : Creating a New Named Object**  -->
Created by Unknown User (sergey.postoyalko), last modified by Aghazarian, Nick on Apr 07, 2022 

In this page, the model that was set up using **M1\_Template**, will be modified by adding a new named object named **NDO**. Follow this procedure to create a new named object.
## **Procedure**
1. Open Visual Studio.
1. Open **M1\_<***your model name***>.sln** located in <*path of your folder for source code*>\**M1\_**<*your model name*>.
1. Right-click **M1\_<***your model name***>.csproj**.
1. Select **Add** then **New Folder**. (you can rename the new folder as you want.)
1. Right-click the new folder.
1. Select **Add** and then **New Item**.
1. Add a new C# class and name it as you want.
1. Replace all in the new C# class with your code following the code example and its description below.

Click here to see the code example

This code adds a new inherited named object named **NDO** with three fields named **F\_Boolean**, **F\_String**, and **F\_Integer**:

using Siemens.MOM.MetaModel.Framework;

using Siemens.MOM.MetaModel.Framework.AOP\_Aspects;

using Siemens.MOM.Metadata.Common;

using System.Collections.Generic;

namespace M1\_<your model name>.Model

{

`    `[COTypeId("0kTZhcN")]

`    `public partial class NDO : NamedObject

`    `{

`        `protected override void \_RegisterFieldTypes()

`        `{

`            `base.\_RegisterFieldTypes();

`            `RegisterField(FieldInitializer.BooleanField<NDO>.Get("F\_Boolean"));

`            `RegisterField(FieldInitializer.StringField<NDO>.Get("F\_String"));

`            `RegisterField(FieldInitializer.IntegerField<NDO>.Get("F\_Integer"));

`        `}

`        `public BooleanField F\_BooleanField = null;

`        `public bool F\_Boolean

`        `{

`            `get { return F\_BooleanField.Value; }

`            `set { F\_BooleanField.Value = value; }

`        `}

`        `public StringField F\_StringField = null;

`        `public string F\_String

`        `{

`            `get { return F\_StringField.Value; }

`            `set { F\_StringField.Value = value; }

`        `}

`        `public IntegerField F\_IntegerField = null;

`        `public int F\_Integer

`        `{

`            `get { return F\_IntegerField.Value; }

`            `set { F\_IntegerField.Value = value; }

`        `}

`    `}

}

Click here to see description of the code example

|**Code block or code line**|**Description**|
| :- | :- |
|namespace M1\_<your model name>.Model |<p>Specifies the model namespace.</p><p>Replace *<your model name>* with the name of your model.</p>|
|[COTypeId("0kTZhcN")]|<p>**COTypeId** is a unique ID that must be assigned to each object in the model. If the same COTypeId is used in different object, an error is generated while building the model.</p><p>To generate a new COTypeId (assumes the prerequisite of the IdGenerator tool is installed):</p><p>**Create new COTypeId**</p><p>IdGenerator COTypeId</p><p>This will generate and output a unique id which can be copy/pasted into the new class</p><p>![](Creating-a-New-Named-Object\_127733034.002.png)</p>|
|` `public partial class NDO : NamedObject |<p>Defines a new inherited class named **NDO.**  **partial** means that this class can be extended by using different workspaces. If a customer using the Platform wants to extend this class, *partial* will let the customer to create the same class with the same name, make it partial too, and add either necessary fields or functionalities.</p><p>This class is inherited from *NamedObject*. The new named object *NDO* will have all the functionalities from *NamedObject* and its parent *BaseObject*.</p><p>To see the inherited functionalities, you can right-click *NamedObject* and select **Go to Definition**. In the opened **NamedObject.cs**, you can see the functionalities that *NDO* will have. In particular, there are two fields – **Name** and **Description.** Likewise, you can check the functionalities that *NamedObject* inherits from *BaseObject*.</p>|
|protected override void \_RegisterFieldTypes() |<p>**RegisterFieldTypes** is a method that is present in *BasedObject*. This method is used to register all fields.</p><p>To register new fields in *NDO*, **override** is used. It used to override the fields of *NamedObject* and to execute a new function instead of the function in NamedObject.</p>|
|base.\_RegisterFieldTypes();|<p>The base class is not executed if override is used. **base** is used for execution of base class *RegisterFieldTypes* first. It used to register the fields from *NamedObject* – *Name* and *Description*.</p><p></p>|
|<p>RegisterField(FieldInitializer.BooleanField<NDO>.Get("F\_Boolean"));</p><p>RegisterField(FieldInitializer.StringField<NDO>.Get("F\_String"));</p><p>RegisterField(FieldInitializer.IntegerField<NDO>.Get("F\_Integer"));</p>|<p>**RegisterField** is a method of Platform that is used to register a new field. It is required to specify field type and a class the field is registered in, and property name.</p><p>To register a new field, specify field type and class name the field is registered in.</p>|
|<p>public BooleanField F\_BooleanField = null;</p><p>public bool F\_Boolean</p><p>{</p><p>`    `get { return F\_BooleanField.Value; }</p><p>`    `set { F\_BooleanField.Value = value; }</p><p>}</p>|<p></p><p>**public BooleanField F\_BooleanField = null** is a field. Field is something of a container that keeps data. Properties are methods of access to this container.</p><p>The **F\_Boolean** field has two methods :</p><p>- *get* is requested to get data form the container.</p><p>- *set* is requested to load data into the container.</p><p>In this code block, the **Value** field is requested and either a value is loaded into this field or data is loaded from this field and then it is returned.</p>|
1. Save your changes to the C# class file.
1. Right-click the folder you created in step 4.
1. Select **Add** and then **New Item**.
1. Add a new JSON file.

The name of the JSON file must be the same as the C# file name. If your C# class is a generic one, the JSON file should contain the **`1** postfix (for example, NDO`1.json).

1. Replace all in the new JSON file with your code following this code example and its description:

Click to see the code example

For each class, apart from a C# file, there is a JSON file with the same name for specifying additional properties The properties specified in the JSON file will be united with the C# file and a new class will be created (class uniting the properties)

{

`    `"Description": "Named object",

`    `"Label": "NDO\_NamedObject",

`    `"AssociatedServiceName": "Siemens.MOM.Metadata.Common.NamedDataService`1",

`    `"Persistence": {

`        `"TableName": "NDO"

`    `},

`    `"Fields": {

`        `"F\_Boolean": {

`            `"Description": "BooleanField type property",

`            `"Label": "F\_Boolean",

`			`"CreateOnInitialize": true,

`            `"Persistence": {

`                `"ColumnName": "F\_Boolean"

`            `}

`        `},

`        `"F\_String": {

`            `"Description": "StringField type property",

`            `"Label": "F\_String",

`			`"Required": "UserInputRequired",

`            `"Persistence": {

`                `"ColumnName": "F\_String"

`            `}

`        `},

`        `"F\_Integer": {

`            `"Description": "IntegerField type property",

`            `"Label": "F\_Integer",

`            `"Persistence": {

`                `"ColumnName": "F\_Integer"

`            `}

`        `}

`    `}

}

Click here to see description of the code example

|**Code block or code line**|**Description**|
| :- | :- |
|"Description": "Named object",|Each named object has description.|
|"Label": "NDO\_NamedObject", |<p>Each named object has a label. The label is required for future use of a new class. Also, the label is used for internationalization.</p><p></p>|
|"AssociatedServiceName": "Siemens.MOM.Metadata.Common.NamedDataService`1",|<p>Specifies service. If one works with a Modeling object externally, one works with the object by using, for example, an API request or external system but we cannot get data from the object directly.</p><p></p><p></p>|
|<p>"Persistence": {</p><p>`  `"TableName": "NDO"</p>|<p>**Persistence** defines if data of this object will be saved to database. A persistent object is an object that is saved to database. If an object is not saved to database, it is saved in RAM.</p><p>**"TableName": "NDO"** means that for *NDO* there will be a table with the same name in database.</p>|
|"Fields": { |<p>Used to add additional parameters for the fields that were defined in the C# class.</p><p></p>|
|<p>"F\_Boolean": {</p><p>`    `"Description": "BooleanField type property",</p><p>`    `"Label": "F\_Boolean",</p><p>`    `"CreateOnInitialize": true,</p><p>`    `"Persistence": {</p><p>`        `"ColumnName": "F\_Boolean"</p>|<p>- **"F\_Boolean"***:* – field name.</p><p>- **"Description"***:* – each field has description.</p><p>- **"Label"***:* – each field has a label.</p><p>- **"CreateOnInitialize"**: – if there is a request from a user without the *F\_Boolean* field and *CreateOnInitialize* is set to true, the field will be created automatically.</p><p>- **"Persistence"**: – used to define a table column in database.</p><p></p>|
|"Required": "UserInputRequired",|<p>By default, if **Required** is not used, it is set to *Required: None* automatically.</p><p>If **UserInputRequired** is used, a input is required from a user.</p><p>If just **Required** is used, when a user make no input, the system will create it.</p>|
1. Save your changes to the JSON file.
1. Build **M1\_<your model name>.sln**.
## **Next Step**
[Perform Unit Tests on New Model](c:\users\anil.birajdar\desktop\temp\Performing-Unit-Tests-on-New-Model_127733830.html)
## **Attachments:**
![](Creating-a-New-Named-Object\_127733034.003.png) [New C# Class.png](c:\users\anil.birajdar\desktop\temp\attachments\127733034\127733032.png) (image/png) 
![](Creating-a-New-Named-Object\_127733034.003.png) [New JSON File.png](c:\users\anil.birajdar\desktop\temp\attachments\127733034\127733033.png) (image/png) 
![](Creating-a-New-Named-Object\_127733034.003.png) [New Folder.png](c:\users\anil.birajdar\desktop\temp\attachments\127733034\127734036.png) (image/png) 
![](Creating-a-New-Named-Object\_127733034.003.png) [Starting a New Instance of IdGenrator.png](c:\users\anil.birajdar\desktop\temp\attachments\127733034\134447725.png) (image/png) 
![](Creating-a-New-Named-Object\_127733034.003.png) [image2022-4-6_15-36-32.png](c:\users\anil.birajdar\desktop\temp\attachments\127733034\144142055.png) (image/png) 

Document generated by Confluence on Jul 28, 2022 11:21

[Atlassian](https://www.atlassian.com/)
**Created with an evaluation copy of Aspose.Words. To discover the full versions of our APIs please visit: https://products.aspose.com/words/**
