---
title: "Configurable Object Attribute"
weight: 4
---

Configurable Objects have some attributes that also define some aspects of the object and
may influence the behavior of the object.

**Persistence** : Used to configure the ‘Persistence’ options of the object. To make an object
‘persistent’ a value is needed for the ‘TableName’. Subclasses can override this
configuration to change the table name or even to switch off persistence.

**AssociatedServiceName** : This configuration applies to modeling type of objects which
represent the engineering model. These objects need CRUD operations and this attribute
defines which service can be used to perform CRUD operations on this object.

More attributes...\< Work in progress \>