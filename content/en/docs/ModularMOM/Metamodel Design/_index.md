---
title: "Metamodel Design"
url: /refguide/metamodel-design/
weight: 2
no_list: false 
description_list: true 
tags: ["studio pro"]
#If moving or renaming this doc file, implement a temporary redirect and let the respective team know they should update the URL in the product. See Mapping to Products for more details.
aliases:
    - /howto/mobile/
---

### Premise

A business analyst is one who is more business focused and less involved with technology,
whereas, a technologist, like a solutions architect or a software developer, is more
technology focused. The primary intention for this Metamodel design is to be able to cater to
a business analyst needs, in much the same was as catering to a more technology-oriented
persona.

{{< figure src="/images/premise.png" >}}

### Design Approach

Metamodel is a like programming language that allows to configure the business model, the
domain model, the business logic and other aspects of the business model. Modular MOM
Metamodel leverages a ubiquitous programming language and transforms it into a language
capable of configuring all aspects of a business model.

The widely popular, open-source, dotnet core-based platform agnostic, object-oriented,
aspect-oriented, multi-paradigm programming language ‘ **C#’** is used as the base. An
abstraction layer is built on top to define the conceptual DSL for the Modular MOM
Metamodel.

{{< figure src="/images/design_approach.png" >}}


### Design Details

#### Metadata Model Framework

Metadata Model Framework provides the basis for the definition of Metadata. This
framework implements the Configurable Object and all the plumbing needed to support this
Metamodel. The primary pillars of this framework are the **Base Class Library** and the **Runtime
Class Library** which define the framework for the Configurable Object and, also provide the
runtime execution support.

#### Base Class Library

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


#### Runtime Class Library

The **Runtime Class Library** , as the name indicates, is a library that contains the implementation
to support the runtime aspects of the Configurable Objects. The primary components of this
library are:

**OBJECT LIFE CYCLE MANAGEMENT**

Provides API for creating the instances of the Configurable Objects, manages the object
state and, also the execution of the system built-in life-cycle events of the objects and its
fields.

**OBJECT METADATA SERVICES**

Provides API for the discovery of the metadata model at the runtime.

**OBJECT RUNTIME EXECUTION CONTEXT**

Provides runtime context for the business logic execution.

#### Configurable Object Attributes

Configurable Objects have some attributes that also define some aspects of the object and
may influence the behavior of the object.

**Persistence** : Used to configure the ‘Persistence’ options of the object. To make an object
‘persistent’ a value is needed for the ‘TableName’. Subclasses can override this
configuration to change the table name or even to switch off persistence.

**AssociatedServiceName** : This configuration applies to modeling type of objects which
represent the engineering model. These objects need CRUD operations and this attribute
defines which service can be used to perform CRUD operations on this object.

More attributes...<Work in progress>

#### Configurable Object Field Attributes

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

More attribute...<Work in progress>

#### Metadata Customizations

The primary agenda for customization techniques of the metadata is to ensure clean and
easy upgrades of the customized metadata to the newer versions of the out-of-the-box
metadata. The key factor for this technique is to keep all the out-of-the-box artifacts
untouched and have all the customizations & extensions written out to new artifacts. To
support for such customizations & extensions of the metadata the following methods can be
employed:

**Ability to override or extend logic by sub-classing**

C# is an object-oriented programming language this functionality falls in place, naturally.
Object Model Classes could be sub-classed or inherited from, to extend the Object Model,
and base class implementation could be overridden to customize & extend Business Logic
by using C#’s natural ways. These techniques include:

- Overrides to virtual functions
- Overloaded function definitions
- New function definitions
- New Properties

**Ability to override or customize logic without having to sub-class**

In an object hierarchy, when logic is needed to be customized or extended at a base class
level then having to sub-class for that purpose would not be conducive since that would
require re-implementing the entire hierarchy by sub-classing from the new extended base
class. This approach is not practical hence a technique for override or customization that
does not require sub-classing an object is needed.


IL Weaving approach is chosen to facilitate such customization techniques where the
original source artifacts are not required to be touched to apply the customizations or
extensions. Aspect oriented techniques, such as, Method Interception, Dynamic Code
Injection could be employed to weave in the customized logic into place. The Metamodel
framework provides the implementation of custom aspects that could be employed to
metadata customizations.

#### Metadata Artifacts

##### MODEL ARTIFACTS

**Model:** Model definition artifacts are stored as C# code files. The object model definition and
the business logic could be separated out into different code files for convenience and
naming convention like ‘object_name’ and ‘object_name_logic’ could be employed.

**Configuration:** Model configuration is stored as json based side-car files along with the model
definition artifacts.

**WORKSPACE OVERRIDES**

The concept of Workspace provides an isolation context for the metadata definition. When a
model definition is overridden in the context of a workspace, new artifacts are created with
the overrides and are placed alongside the original artifacts of the model being overridden.
This technique protects the original artifacts from being modified by other workspaces and
avoids conflicting changes.

#### Metadata Packaging

The packaging or prepping up of the metadata for runtime consumption is a simple &
straightforward build of the underlying code files. The build process results in the generation
of a dotnet core assembly for each Metadata model. This metadata assembly is now ready
to be consumed by the Metadata Engine Runtime. <Work in progress>


