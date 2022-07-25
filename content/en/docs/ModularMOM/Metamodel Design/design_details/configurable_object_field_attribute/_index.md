---
title: "Configurable Object Field Attributes"
weight: 5
---

Configurable Object Fields also have some attributes that define some aspects of the object
and may influence the behavior of the object.

**Persistence** : Used to configure the ‘Persistence’ options of the field. To make the field
‘persistent’ a value is needed for the ‘ColumnName’. Subclasses can override this
configuration to change the column name or even to switch off persistence. Based on the
type of the field, there could be additional configuration that goes along with this such as
length, scale & precision of the column, or referential information etc.

**Required** : Used to configure the field’s input requirement constraints. Valid options are None,
SystemRequired or UserInputRequired. SystemRequired means that a value is needed for
this field, but it could be assigned through some business logic.


**CreateOnInitialize** : This configuration applies to ‘Subentity’ type of fields only. When set to
true the system creates an instance of this Subentity when the field is initialized, i.e. when
the parent object instance is created.

**DefaultValueExpression** : Used to configure an initial value expression for the field.

**CurrentValueExpression** : Used to configure a current value expression for the field. When a
field’s value is requested, OnGetField event will be fired followed by evaluation of the current
value expression, if configured. This provides for an additional hook to retrieve a value for
the field.

**AllowROR** : This configuration applies to a field of Revisioned object reference type.
Revisioned object can be refernced in one of the following 2 ways – by using a name and
revision or by just using the name only to reference the current revision of record (RoR).
AllowROR is used to configure whether the use of ROR should be allowed on this field.

More attribute...\< Work in progress \>