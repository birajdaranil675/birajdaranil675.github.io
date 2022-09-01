---
title: "Base Class Library"
weight: 2
---

The **Base Class Library** , as the name indicates, is a library of basic and fundamental
components of the Metamodel such as the built-in types, etc. which are used in defining the
metadata. The main components of the Metamodel BCL are the Interfaces and the Abstract
Base Classes.

**INTERFACES**

**Object Type Interfaces:** Interfaces are used to markup the configurable objects with certain
types traits, such as:

_IBaseObject_ – markup an object as Configurable Object

_INamed_ – to markup an object as a ‘Named’ object

_IRevisioned_ – to markup an object as a ‘Revisioned’ object

_ISubentity_ – to markup an object as a composable object, also called as a ‘Subentity’ object

_IService_ – to markup an object as a ‘Service’ type of object

_Etc._ – and more

{{< figure src="/images/design_details.png" >}}

**Field Type Interfaces:** These interfaces indicate the intended behaviors of the various types of
‘Fields’ supported by this Metamodel, such as:

_ISingleValueField_ – indicates that the field holds a scalar value, single value

_IMultiValueField_ – indicates that the field holds multiple values, i.e. a list type of field

_IObjectRefField_ – indicates that the field represents an ‘Association’ type object relationship


_ISubentityField_ – indicates that the field represents an ‘Composition’ type object relationship

_Aspect Types_ – AOP style aspects to toggle cross-cutting features of the system

{{< figure src="/images/abstaract_base_class.png" >}}

**ABSTRACT BASE CLASSES**

The **Abstract Base Classes** are the basic implementation of the concepts of the Metamodel
such as the Configurable Object and are intended to be used as base classes for the actual
concreate classes that are to be defined in the metadata. The following are some abstract
base classes defined in this BCL.

**BaseObject:** The absolute root or the base class for all the Configurable objects

**RevisionBase<>:** Generic base class to represent the holder ( _IRevisionBase_ ) for the Configurable
objects that implement the _IRevisioned_

**SubentityObject:** Base class for the Configurable objects that implement the _ISubentity_

**ServiceObject:** Base class for all the Configurable objects that implement the _IService_

**Any Aspect Classes:** Support and framework for the AOP style Aspect based feature toggling

**FIELD TYPE CLASSES**

The **Field Type Classes** are the specific types defined in this framework to define the different
type of Fields possible in this Metamodel. Classes to represent native type fields such as
String, Integer etc., along with types to represent various types of Object type of fields
include reference types. There are also specific types defined for defining the multi-valued
list type of fields as well. See sections ‘Field Types’ and ‘Field Declaration’ for more details and
examples.