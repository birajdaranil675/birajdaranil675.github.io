---
title: "Field Decleartion"
weight: 2
---

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




