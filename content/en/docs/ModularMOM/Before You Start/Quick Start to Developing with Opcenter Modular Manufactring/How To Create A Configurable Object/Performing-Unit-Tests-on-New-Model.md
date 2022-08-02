---
title: "Performing Unit Tests on New Model"
weight: 7
---
<!-- 1. [Modular MOM](c:\users\anil.birajdar\desktop\temp\index.html)
1. [Before You Start](c:\users\anil.birajdar\desktop\temp\Before-You-Start_127740192.html)
1. [Quick Start to Developing with Opcenter Modular Manufacturing](c:\users\anil.birajdar\desktop\temp\Quick-Start-to-Developing-with-Opcenter-Modular-Manufacturing_134455239.html)
1. [How to Create a Configurable Object](c:\users\anil.birajdar\desktop\temp\How-to-Create-a-Configurable-Object_125339498.html)
# **Modular MOM : Performing Unit Tests on New Model**  -->
Created by Unknown User (sergey.postoyalko), last modified by Alvarez Villanueva, Beatriz on Nov 04, 2021 

The model that was set up following the steps in [Setting Up a New Model from Template](c:\users\anil.birajdar\desktop\temp\Setting-Up-a-New-Model-from-Template_127733030.html) with the named object and service object created following the steps in [Creating a New Named Object](c:\users\anil.birajdar\desktop\temp\Creating-a-New-Named-Object_127733034.html) and [Creating a New Service Object](c:\users\anil.birajdar\desktop\temp\Creating-a-New-Service-Object_134453962.html) respectively is used here as the example of how to unit test a new model. Follow these steps to unit test your new model.
## **Procedure**
1. Open Visual Studio.
1. Open **M1\_<***your model name***>.sln** located in <path of your folder for source code>\**M1\_**<*your model name*>.
1. In Solution Explorer, expand **M1\_<***your model name***>.Tests**.
1. Select **M1\_<***your model name***>\_UnitTests.cs**.
   The selected C# file contains the test class that was generated to perform tests. By default, the test class name is *<your model* *name*>**\_UnitTest**. The test class contains predefined fields that are designed to help with testing. Follow description of the test class below.

Click here to see description of the genrated test class

|**Code line**|**Description**|
| :- | :- |
|readonly BLEngineConfig blConfig = new BLEngineConfig("TestModel", System.IO.Path.GetFullPath(@".\M1\_MyModel.dll"));|blConfig is a configuration file that contains the name of your model and the path to the .dll file that was generated while setting up the new model. The path is relative.|
|readonly BizLogicEngineFactory blEngineFactory = new BizLogicEngineFactory();|<p>Contains Factory. Factory is the factory for creation of Engine. Engine is a basic object providing the capability to perform tests. Engine creates Meta-Metamodel.</p><p>The new Metamodel named <**M1\_**<*your model name*> was created following the steps in [Setting Up a New Model From Template](https://momwiki02.industrysoftware.automation.siemens.com/display/RevMOM/Setting+Up+a+New+Model+From+Template?src=contextnavpagetreemode) and [Creating a New CO.](https://momwiki02.industrysoftware.automation.siemens.com/display/RevMOM/Creating+a+New+CO?src=contextnavpagetreemode) The new Metamodel contains the NDO object (the NDO objects contain the model). The Meta-Metamodel contains a class that describes your model. Your model has different attributes that will be used for testing.</p>|
|Mock<ILogger> mockLogger;|Logger is used for logging. It will not be used in this topic.|
|Assert.IsNotNull(blEngine, "blEngine is null");|Checks blEngine to be created and not to be null.|
1. Add your test method following the code example and its description below:

Click here to expand...

This test method is designed to test *NDO* that was created in [Creating a New Named Object](c:\users\anil.birajdar\desktop\temp\Creating-a-New-Named-Object_127733034.html).

`        `[TestMethod]

`        `public void TestMetaMetadata()

`        `{

`            `// Make sure Configurable 'Types' are initialized

`            `var configTypes = blEngine.ConfigurableTypes;

`            `Assert.IsTrue(configTypes.Any()); 



`            `System.Type type = blEngine.GetType("M1\_<your model name>.Model.NDO");

`            `Assert.IsNotNull(type); 



`            `var metaType = blEngine.GetMetaType(type);

`            `Assert.IsNotNull(metaType); 

`            `Assert.IsFalse(metaType.IsService());

`            `Assert.IsTrue(metaType.IsPersistent());

`            `Assert.IsTrue(metaType.IsNamed()); 

`            `Assert.IsFalse(metaType.IsFrameworkDefinedType());

`            `Assert.IsFalse(metaType.IsSystemObject()); 



`            `foreach (var fmKVP in metaType.Fields)

`            `{

`                `var fm = fmKVP.Value;

`                `\_ = fm.FieldType;

`                `\_ = fm.DataType;

`                `\_ = fm.IsList();

`                `\_ = fm.IsPersistent();

`                `\_ = fm.TypeCategory;

`                `bool val;

`                `// scalar types

`                `val = fm.IsNamedRef();

`                `val = fm.IsRevisionedRef();

`                `val = fm.IsSubentityRef();

`                `val = fm.IsNamedSubentityRef();

`                `val = fm.IsSubentity();

`                `val = fm.IsNamedSubentity(); 

`                `// list types

`                `val = fm.IsNamedRefList();

`                `val = fm.IsRevisionedRefList();

`                `val = fm.IsSubentityRefList();

`                `val = fm.IsNamedSubentityRefList();

`                `val = fm.IsSubentityList();

`                `val = fm.IsNamedSubentityList();

`            `}

`            `var fields = metaType.Fields;

`            `var fld = fields["F\_Boolean"];

`            `Assert.IsNotNull(fld);

`            `Assert.IsTrue(fld.CreateOnInitialize);

`            `Assert.AreEqual(fld.Required, RequiredFieldFlag.None);

`            `fld = fields["F\_String"];

`            `Assert.IsNotNull(fld);

`            `Assert.IsFalse(fld.CreateOnInitialize);

`            `Assert.AreEqual(fld.Required, RequiredFieldFlag.UserInputRequired);

`            `Assert.AreEqual(fld.TypeCategory, FieldTypeCategory.Native);

`        `}


`    `}

}

Click here to expand...

|**Code block/Code line**|**Description**|
| :- | :- |
|var configTypes = blEngine.ConfigurableTypes;|Checks blEngine to initialize Configurable Types.|
|Assert.IsTrue(configTypes.Any());|configTypes.Any lets to make sure the Configurable Types are not empty.|
|System.Type type = blEngine.GetType("M1\_<your model name>.Model.NDO"); |<p>Gets the type by the type name. The type variable gets the NDO class.</p><p>This line finds the NDO class with the three fields that was defined while following the steps in Creating a New CO.</p>|
|Assert.IsNotNull(type);|Checks the type to be found and not to be null.|
|var metaType = blEngine.GetMetaType(type);|<p>Gets the meta-metamodel of the NDO. GetMetaType gets description of the NDO. metaType lets to check properties of the NDO class.</p><p>The type contains different properties. In particular, these three fields were defined while following the steps in [Creating a New Named Object](c:\users\anil.birajdar\desktop\temp\Creating-a-New-Named-Object_127733034.html):</p><p>- F\_Boolean</p><p>- F\_Integer</p><p>- F\_String</p><p>In the test method, after getting the type, the NDO class is inserted in the variable. Then, we get metaType of this type.</p>|
|Assert.IsNotNull(metaType); |Checks the NDO to be got and its name has no mistypes.|
|Assert.IsFalse(metaType.IsService()); |Checks the NDO class not be a service.|
|Assert.IsTrue(metaType.IsPersistent()); |<p>Checks the NDO class to be persistent.</p><p>While following the steps in [Creating a New Named Object](c:\users\anil.birajdar\desktop\temp\Creating-a-New-Named-Object_127733034.html), persistence was defined in the .json file.</p>|
|Assert.IsTrue(metaType.IsNamed());|Checks the class to realize the INamed interface.|
|Assert.IsFalse(metaType.IsFrameworkDefinedType()); |<p>Checks the metaType not be a framework type.</p><p>This line checks that the NDO class we get is a custom class, not a class in the framework.</p>|
|Assert.IsFalse(metaType.IsFrameworkDefinedType()); |<p>Checks the metaType not be a system object.</p><p>This line checks that the NDO class we get is not a system object.</p>|
|||
|foreach (var fmKVP in metaType.Fields)|metaTypeFields contains a collection of all fields including fields in the parent NDO.|
|<p>var fm = fmKVP.Value;</p><p>\_ = fm.FieldType;</p><p>\_ = fm.DataType;</p><p>\_ = fm.IsList();</p><p>\_ = fm.IsPersistent();</p><p>\_ = fm.TypeCategory;</p>|<p>Fields for each field that can be useful. For example, to check that it is a list, field a is persistent one.</p><p></p>|
|<p>// scalar types</p><p>val = fm.IsNamedRef();</p><p>val = fm.IsRevisionedRef();</p><p>val = fm.IsSubentityRef();</p><p>val = fm.IsNamedSubentityRef();</p><p>val = fm.IsSubentity();</p><p>val = fm.IsNamedSubentity();</p>|Checks that each field realizes a particular interface.|
|<p>// list types</p><p>val = fm.IsNamedRefList();</p><p>val = fm.IsRevisionedRefList();</p><p>val = fm.IsSubentityRefList();</p><p>val = fm.IsNamedSubentityRefList();</p><p>val = fm.IsSubentityList();</p><p>val = fm.IsNamedSubentityList();</p>|<p>Checks that fields are lists of different types. We check nothing here, but provide a list of useful methods for metType that can be needed for the user in the future.</p><p></p>|
|var fields = metaType.Fields;|Records all the fields of our metaType in the Fields variable.|
|var fld = fields["F\_Boolean"];|Gets access to a specific field and starts working with it. In this line, get access to the F\_Boolean field.|
|Assert.IsNotNull(fld);|Checks the field to be found, that it exists, and there is no mistype.|
|Assert.IsTrue(fld.CreateOnInitialize);|Checks that CreateOnInitialize is set to true.|
|Assert.AreEqual(fld.Required, RequiredFieldFlag.None);|<p>Checks that the Required value of our field is set to none.</p><p>In the JSON, we don't have it. By default, if we did not define it, it is set to none.</p>|
|fld = fields["F\_String"];|Gets access to a specific field and starts working with it. In this line, get access to the F\_String field.|
|Assert.IsNotNull(fld);|Checks the field to be found, that it exists, and there is no mistype.|
|Assert.IsFalse(fld.CreateOnInitialize);|Checks that CreateOnInitialize is set to false.|
|Assert.AreEqual(fld.Required, RequiredFieldFlag.UserInputRequired);|<p>Checks that the Required value of our field is set to UserInputRequired.</p><p>This was defined in the .js. Tihis field was defined there clearly, if it was not, it would be none.</p>|
|Assert.AreEqual(fld.TypeCategory, FieldTypeCategory.Native);|<p>Checks TypeCategory of native and that the field is of prime and scalar value.</p><p>Scalar are all prime values like Boolean String Decimal DataTime and so on.</p>|



1. Depending on your model, add another test methods following the code example and its description below:

Click here to expand...

This test method is designed to test **NamedService*** that was created in [Creating a New Service Object](c:\users\anil.birajdar\desktop\temp\Creating-a-New-Service-Object_134453962.html).

`        `[TestMethod]

`        `public void TestNamedService()

`        `{

`            `var svcType = blEngine.GetActualTypeFromGeneric("M1\_<your model name>.Services.NamedService`1", "M1\_<your model name>.Model.NDO");

`            `Assert.IsNotNull(svcType);

`            `var metaType = blEngine.GetMetaType(svcType);

`            `Assert.IsNotNull(metaType);

`            `Assert.IsTrue(metaType.IsService());

`            `Assert.IsFalse(metaType.IsPersistent());

`            `Assert.IsFalse(metaType.IsFrameworkDefinedType());

`            `Assert.IsFalse(metaType.IsSystemObject());

`            `IService service = blEngine.CreateService(svcType);

`            `string entityName = service + "\_NdoTestEntity";

`            `// Test Add(name)

`            `dynamic instance = (service as dynamic).Add(entityName);

`            `Assert.IsNotNull(instance);

**This document was truncated here because it was created in the Evaluation Mode.**
**Created with an evaluation copy of Aspose.Words. To discover the full versions of our APIs please visit: https://products.aspose.com/words/**
