---
title: "Metamodel Usage"
url: /ModularMOM/Metamodel Usage/
description: "This document gives definitions and explains Metamodel Usage"
weight: 30
# no_list: false 
# description_list: true 
# tags: ["Version Control", "Application Lifecycle Management", "Commit", "Collaborate"]
#If moving or renaming this doc file, implement a temporary redirect and let the respective team know they should update the URL in the product. See Mapping to Products for more details.
#This document is mapped to the landing page, update the link there if renaming or moving the doc file.
---

### Configurable Object Definition

#### Object Declaration

As mentioned in the metamodel design, a Configurable Object is represented by declaring a
C# class and building on from the base class types & interfaces provided by the metamodel
framework. Some examples are:

**TO DECLARE AN OBJECT**

_public partial class NamedObject : BaseObject_

_{_

**TO DECLARE A ‘NAMED’ OBJECT**

_public partial class NamedObject : BaseObject, INamed_

_{_

**TO DECLARE A ‘REVISIONED’ OBJECT**

_public abstract class RevisionedObject<TSubClassType> : BaseObject,
IRevisioned<TSubClassType> where TSubClassType : class, IRevisioned<TSubClassType>_

_{_

**TO DECLARE AN ‘SUBENTITY’ OBJECT**

_public abstract class SubentityObjectOf<TParentClassType> : SubentityObject,
ISubentityOf<TParentClassType> where TParentClassType : class, IBaseObject_

_{_

**TO DECLARE A ‘MODELING SERVICE’ OBJECT**

_public partial class NamedDataService<ClassType> : ServiceObject,
INamedModelingService<ClassType> where ClassType : class, INamed_

_{_

**TO DECLARE A ‘REVISIONED MODELING SERVICE’ OBJECT**

_public partial class RevisionedDataService<RevType> : NamedDataService<RevType>,
IRevisionedModelingService<RevType> where RevType : RevisionedObject<RevType>_

_{_

**TO DECLARE A ‘SHOPFLOOR SERVICE’ OBJECT**

_public abstract partial class ShopfloorService : ServiceObject, IShopfloorService_

_{_


#### Field Declaration

As mentioned in the metamodel design, a Configurable Object contains a collection of
‘Fields’ and can be represented in the C# class of the Object leveraging the metamodel
framework built-in types available for the various types of fields. The 3 key steps to define a
field are, Define a backing field, Define an associated property and Register the field by
overriding the ‘ __RegisterFieldTypes()_ ’ method.

**TO DECLARE A ‘STRING’ TYPE FIELD**

_public StringField_ **_EmailField_** _= null;_

_public string_ **_Email_** _{ get { return EmailField.Value; } set { EmailField.Value = value; } }_

_RegisterField(FieldInitializer.StringField<Employee>.Get("Email"));_

**TO DECLARE A ‘DECIMAL’ TYPE FIELD**

_public DecimalField_ **_DefaultStartQtyField_** _= null;_

_public decimal_ **_DefaultStartQty_**

_{ get { return DefaultStartQtyField.Value; } set { DefaultStartQtyField.Value = value; } }_

_RegisterField(FieldInitializer.DecimalField<Product>.Get("DefaultStartQty "));_

**TO DECLARE AN ‘OBJECT’ TYPE FIELD WITH SIMPLE ASSOCIATION RELATIONSHIP**

_public INamedObjectRefField<Factory>_ **_FactoryField_** _= null;_

_public virtual Factory_ **_Factory_**

_{ get { return FactoryField.GetObject(); } set { FactoryField.SetObject(value); } }_

_RegisterField(FieldInitializer.NamedObjectRefField<Employee, Factory>.Get("Factory"));_

**MORE EXAMPLES:**

_// Example of Named Subentity List Field: Ownership = Strong_

_public INamedSubentityListField<Location>_ **_LocationsField_** _= null;_

_public INamedSubentityListField<Location>_ **_Locations_** _=> LocationsField;_

_// Example of Un-Named Subentity Field: Ownership = Strong_

_public ISubentityField<ProductionStatus>_ **_ProductionStatusField_** _= null;_

_public ProductionStatus_ **_ProductionStatus_** _=> ProductionStatusField.GetObject();_

_// Example of Named Subentity Field: Ownership = Strong_

_public INamedSubentityField<Location>_ **_MainLocationField_** _= null;_

_public Location_ **_MainLocation_** _{ get { return MainLocationField.GetObject(); } }_

For some more examples, see the Metadata Sample Model.


#### Object Event Handlers

Each of these configurable objects based on the type of the object, they have a set of built-in
object lifecycle events that get fired. The prescribed way to configure an event handler to
these events to associate some business logic to be executed when they are fired is to
override the _‘_InitializeObjectEvents()’_ method and assign a method to the built-in event,
which is provided by the metamodel framework’s base classes. In the same way, a an event
handler to the Field’s built-in events can be associated using the method
_‘_InitializeFieldEvents()’_. For example:

_// Assign InitializeEvent_

_OnInitialize = Factory_OnInitialize;_

_// Assign Field events_

**_FavoriteEmployeeField_** _.OnSetField += (emp) => { DoSomethingWhenFavEmploeeGetsSet(); };_

**_Employees_** _.OnAddItem += (item) => { Employees_AddItem(item as INamedObjectRef<Employee>); };_

#### Object and Field Attributes

Sample configuration of Object & Field attributes...

{{< figure src="/images/object_and_field_attribute.png" >}}


#### Object & Field Usages

**Object Category** : Object category, such as Named, Revisioned, Service etc., are represented in
the Metamodel as interface types. There are also some abstract base classes defined in the
Metamodel framework to fulfil this requirement. See the section ‘Base Class Library’ for some
additional details.

**Special Fields** : Fields like ‘Name’ property of a Named object or a ‘Revision’ Field of a
Revisioned objects are special fields with certain specific behavior defined as per the
Metamodel design. They are implemented as specific types in the ‘Base Class Library’ that
could be used to represent these Usages on the Field definitions.

#### Workspace Customizations

Aspect details & samples... Work in progress