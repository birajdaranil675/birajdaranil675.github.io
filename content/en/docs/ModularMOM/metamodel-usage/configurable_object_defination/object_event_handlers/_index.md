---
title: "Object Event Handlers"
weight: 3
---

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
