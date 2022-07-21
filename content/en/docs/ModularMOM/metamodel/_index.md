---
title: "MetaModel Concept"
url: /metamodel-concept/quickstart-guide/
weight: 1
description: "Learn what is MOD MOM Platform."
tags: ["microflows", "widgets", "app", "nanoflow", "app development"]
---
<!-- 
## 1 Introduction 

Welcome to the MOD MOM quickstart guide for building an app. 

* Part 1: [Build a Responsive Web App](/refguide/quickstart-part1/) (estimated time to complete: 25 minutes)
* Part 2: [Add a Native Mobile App](/refguide/quickstart-part2/) (estimated time to complete: 25 minutes)

{{% alert type="info" %}}
Put some alert msg here.....
{{% /alert %}} -->

## Introduction
In Metadata-driven systems/architectures, the Metadataforms the crux of the business solution the system provides. The structure and the form of the metadata is governed by the MetadataDSLor the Metamodel. As Modular MOM is built using the Metadata-driven architecture, there is a specific Metamodel that is used to define the Metadata for Modular MOM.


## The Basics

Modular MOM Metamodel is inspired from the architecture & Metamodel of Opcenter Ex Core. 
The salient features of the Modular MOM Metamodel are:
- Object-Oriented: Enables the definition of metadata thatadheres to the OO principles, such as Abstraction, Encapsulation, Inheritance & Polymorphism
- Imperative: The logic definition adheres to the imperative programming paradigm
- StronglyTyped: Provides a Strong Type System for the primary components of the Metadata, but it also allows for some dynamictypes to be used in the logic definitions
- Relational: Enables the definition of an Object Model which is based on Relational Model and supports relationships like Association, Composition & Aggregation
- Aspect-Oriented: Enables adding of cross-cutting functionality based on annotations like in an aspect-oriented programming paradigm
- Persistence: Enables configurable Object-Relational Mapping based persistence mechanism for the user data



## The DesignThe 

‘Configurable Object’ forms the core of the Metamodel design. Since the Metadata adheres to the OO principles, a ‘Class or Object Type’ that describes an ‘object instance’ becomes the central idea of the Metadata, and, the ‘Configurable Object’ enables the creation of these ‘Classes’ or ‘Object Types’. Applying the Metadata Abstraction level concepts from the ‘The OMG Group’, the ‘Configurable Object’ represents an instance at M2 level, that means thatthe instances of the ‘Configurable Objects’ represent the instance at M1 level, which, form the ‘type’ definitions for the object instances at M0 level -the actual instance data.
Nagamalli, Ramesh (DI SW MOM R&D AI RI)5Modular MOM MetamodelThe 

## ‘Configurable Object’

{{< figure src="/images/configobject.png" >}}

The ‘Configurable Object’ is composed of:
- Fields: These define the ‘properties’ of the object. There are several predefined types 
of ‘Field’ definitions that can be used to define the properties on an object. 
- Methods: The logic associated with the objects are defined as methods like in any 
Object-Oriented programming language
- Event Handlers: Every ‘Configurable Object’ has a set of pre-defined object life-cycle 
related events that are automatically fired by the system during the life of an object 
based on some external or internal triggers. Event-Handlers are the logic blocks that 
could be associated to these built-in event types. These event handlers get executed 
when these ‘events’ are fired during the life of an object instance.
- Field Event-Handlers: The ‘Fields’ also have some pre-defined life-cycle events 
that are fired by the system on external of internal triggers like in the case of 
an object. Event handlers, logic block, can be associated to these events to 
configure any logic to be executed when these events are fired.
- Attributes: These define additional characteristics that could be related to the aspects 
that are either used at the ‘design’ time by the configuration tools or behavioral 
aspects that could take effect at the system runtime. These ‘Attributes’ can be 
defined both at the ‘Configurable Object’ level and at the ‘Field’ level as well. 
Examples include: ‘Description’ – which describes the item, ‘Category’ – which puts 
the object into a particular group which could be used by the configuration tools, 
‘Cache-able’ – which defines if this the instances of this object could be cached by 
the system at runtime, etc. ‘Attributes’ are further classified into 2 categories:
Nagamalli, Ramesh (DI SW MOM R&D AI RI) 6 Modular MOM Metamodel
    - Overridable – these attributes can be overridden by the sub-classes or by 
                    customizations
    - Non-Overridable – these attributes are NOT allowed to be overridden by the 
                        sub-classes or by customizations.
- Persistence Options: These provide the ORM mapping to facilitate the object instance 
to be persisted into a database storage (more details in separate section…)

## Object Categories

Configurable Objects are classified into the following high-level types based on the intended 
purpose of the objects.
Business Objects: Objects in this category are intended to represent the concepts from the 
Business domain model.

- Service Objects: Business operations are modelled using the Service type of objects and these 
objects become the interface between the external world and this metadata-based system. 
Service definitions serve the purpose of an API to the business services provided by this 
metadata. Every interaction with the external world other than just querying the model is 
always through the execution of a ‘Service’ type of object.

- Persistent Objects: The state of the Business Objects which represent the concepts from the 
Business domain model are typically persisted in some form of storage. This Metamodel 
provides a framework through ORM to facilitate the persistence of these objects. The 
Business Objects that are configured to be persistent are called or classified as ‘Persistent 
Objects’

- Transient Objects: Objects such as Service objects and some Business Objects that do not 
require the state to be persisted are called as Transient Objects. The main purpose of these 
transient objects is to aid during the execution of business functionality to keep and track 
some internal state but are not required to be persisted.
Named Objects: All objects have a unique identifier assigned automatically by the system to 
identify and reference these objects. Some Business Objects within the business domain 
model that can be identified by a unique name are called ‘Named’ objects. The name serves 
the purpose of an alternate logical key for the object.

- Revisioned Objects: Object Revision Control is the ability of an object to have multiple 
revisions and still be able to be managed as one object. Objects that support revision control 
are generally referred to as ‘Revisioned Objects’. Within this Metamodel, Revisioned Objects 
implement the following pattern for revision control mechanism.
      - Revisioned Objects are standard objects like any other Business object
      - Revisioned Objects can have one or more ‘Revisions’
      - Revisioned Objects will have ONE revision marked as 'Revision of Record', aka ‘RoR’
      - Revisioned Objects have the following 2 alternate logical keys of identification:

1. Name only, which always refers to the current ‘RoR’ object
2. Name and Revision, which uniquely identifies a specific single revision

- Subentity Objects: Composable objects and are also called as Subentity objects. 

- Named Subentity Objects: Subentity objects can, optionally, be ‘Named’ objects such as that 
they can be uniquely identified by a name within the context of it composing object.


## Field Types

{{< figure src="/images/field_object.png" >}}


At the highest level, the fields fall into the 2 broad categories – Scalar (Single-valued) or List 
(Multi-valued) types. Within each of these categories these are the several ‘data’ types that 
are supported by the Metamodel type system:

**Primitive Types:** Basic data types like ‘String’, Boolean’ ‘Datetime’ and numeric types like 
Integer & Decimal are supported.

**Complex Types:** Complex Types are used to represent Object relationships. The following 
types of relationships are supported: Association, Composition, Aggregation

## Object Relationships


Relationship between Objects are explicitly expressed through ‘Object’ Type Fields like any 
other Field.

{{< figure src="/images/object_relationship.png" >}}
**Inheritance:** This Metamodel implements Single Inheritance Model only with full support for 
polymorphism.

- Navigation between the object and its super classes is through the ‘this’ or ‘base’ like 
keywords as defined by the underlying language

**Association:** An association is a “using” relationship between two or more objects in which 
the objects have their own lifetime and there is no owner. Association can also be defined as 
a semantically weak relationship between otherwise unrelated objects. Associated objects 
can be referenced by Id or any of the alternate logical keys to uniquely identify the object. A 
few aspects of the ‘Association’ relationship within this Metamodel are:
- Navigation between related objects are implicitly expressed by the Fields defined
- One-way navigation is implied in the direction defined by the user in the form of a 
  Field
- Back-navigation needs to be explicitly expressed by the user
    - Back-navigation could automatically be configured through the tool 
           automations, if needed
**Composition:** Composition is a strong type of relationship like in whole/part or parent/child 
relationship. Composition defines ‘ownership’ between the composing & composed objects,
such that, if the lifecycle of the composed objects is linked to the composing object. For 
example, when the composing object is destroyed, then the composed objects also cease to 
exist. Within this Metamodel, a composed object is called as ‘Subentity’ and the creation of 
these Subentity objects are always within the context of the parent/owner/composing 
object. Navigation aspects of this relationship are: 
- Forward navigation expressed explicitly by the user when defining composition
- Back-navigation is provided automatically through ‘Parent’ field
**Aggregation:** It is a specialized form of relationship to represent a collection - One-to-Many 
multiplicity dimension. Aggregation supports both ‘Association’ & ‘Composition’ types with 
navigation aspects being same as the underlying relationship type.

## Object and Field Life-Cycle Events
{{< figure src="/images/Object_and_field_life-cycle_events.png" >}}

### OBJECT EVENTS
**OnInitialize:** Triggered when the object is created. Provides hooks to initialize the object with 
custom logic
PERSISTENT OBJECT EVENTS
**AfterOpen:** Triggered when an object is retrieved from the storage and after the internal 
initialization is complete. Provides hooks for custom logic to initialize/update the state 
and/or initialize the non-persistent state of the object
**BeforeSave:** Triggered when an object is ready to be persisted to the storage to provide hooks 
for any custom logic to adjust the state of the object before it gets persisted
SERVICE OBJECT EVENTS
**BeforeValidate:** Triggered as part of Service execution but before the system validation is 
performed to provide hooks for custom logic to manipulate the object state before the 
system validation
**Internal System Validate:** Validate the input requirements of all the fields from the service & its 
details. It is NOT a hook for customization.
**AfterValidate:** Triggered as part of Service execution but after the system validation is 
performed to provide hooks for custom logic to manipulate the object state for the actual 
service execution
**BeforeExecute:** Triggered as part of Service execution but after all the validations are 
performed and provides hooks for custom logic to manipulate the object state as required 
for the service
Internal System Execute: Internal system logic and it is NOT a hook for customization

**AfterExecute:** Triggered as part of Service execution and after ‘BeforeExecute’ event is 
performed and provides additional hooks for custom logic to manipulate the object state as 
required for the service before the object state (transaction) is committed to the storage
**AfterCommit:** Triggered as part of Service execution and after the object state is successfully 
committed to the persistent storage providing hooks for any custom logic to do notifications 
or integration with other systems etc.
AfterCommitEventFailure: Triggered as part of Service execution and on failure of the 
‘AfterCommit’ event providing hooks for custom logic to handle any failures occurring during 
the ‘AfterCommit’ event. This event is fired ONLY when ‘AfterCommit’ event fails
FIELD EVENTS
**OnInitialize:** Triggered when the object is created to provide hooks into initializing field with 
custom logic
**OnGetField:** Triggered when the value of a field is requested by the consumer of the object to 
provide hooks into executing custom logic to return the value of the field
**OnSetField:** Triggered when the value is assigned to a field by the consumer of the object to 
provide hooks into executing custom logic to assign the value for the field or to manipulate 
any other state
**OnSelectValues:** Triggered when there is an explicit request to retrieve ‘List of Values’ or 
‘Selection Values’ for a specific field. This is mostly used to populate the ‘List of Values’ on a 
UI component. It could also be used to perform any custom logic validations of the field to 
restrict the values to the pre-configured set only checking the field value against the 
selection values
LIST FIELD EVENTS
**GetItem:** Triggered when a single item is requested from a list field to provide hooks for any 
custom logic to be executed
**AddItem:** Triggered when an item is added to a list field to provide hooks for any custom logic 
to be executed
**UpdateItem:** Triggered when a single item is updated on a list field to provide hooks for any 
custom logic to be executed
**DeleteItem:** Triggered when an item is removed from a list field to provide hooks for any 
custom logic to be executed. When the list field represents a ‘Composition’ type of object 
relationship then the item being removed from the list is also explicitly deleted.

## Configurable Object Maps
Configurable Object Map, also known as a CDO Map, is a feature that provides a 
configurable way of mapping information between any two Configurable Objects. A CDO Map 
has a source object and a target object. It contains a collection of Field Mappings, which are 
an evaluable expression bound to the source object and mapped to a specific field on the 
target object. When a CDO Map is applied/executed at runtime, the source field expression 
is evaluated, and the corresponding result value is copied to the target field on the target 
object. 
CDO Maps support object-oriented features such as Inheritance and Polymorphism. With 
these features, the concept of CDO Maps would be a very powerful feature that can simplify 
a lot of simple assignment statements in the business logic definition.
Triple Dispatch: Multiple dispatch is a feature of some programming languages in which a function can 
be dynamically dispatched based on the run time (dynamic) type or, in the more general case, some 
other attribute of more than one of its arguments [WIKI].
With CDO Maps, the dynamic dispatching is based on the three factors that are in play – the 
source object, the target object & the map. Since both the Configurable Object & the CDO 
Map support inheritance and polymorphism, the actual runtime type information of these 
instances will determine which map is executed at runtime.
Business Logic Templates
Business Logic Templates are a feature of the Metadata built into the M1 abstraction space 
leveraging the concepts and features provided by the Metamodel, M2 level. These 
templates provide a structure to the design of logic flow to configure the business specific 
functionalities. As such, these templates add another abstraction layer on top of the 
Metamodel features to provide a way for simpler configuration experience for the end users. 
There are a couple of basic Business Logic Templates, out-of-the-box. Since the templates 
themselves are bootstrapped into the configurable Metadata, the M1 space, users could 
define their own templates or customize existing templates, as needed. Out-of-the-box 
templates include:
- Service Templates, such as, Modelling, Shopfloor, Inquiry, Compound, etc.
- Feature Templates, such as Where Used, Electronic Signatures, etc.
- et al.
Workspaces
Workspaces are a concept in the Modular MOM Metamodel that allows for:
- Ability to customize out-of-the-box solutions as per customer’s needs
- Ability to easily upgrade customized solutions automatically on new release
- Ability to build Industry specific solutions on top of the out-of-the-box
- Ability for Partners to build solutions on top of the out-of-the-box 
Nagamalli, Ramesh (DI SW MOM R&D AI RI) 12 Modular MOM Metamodel
Object & Field Usages
‘Usages’, as exist in Opcenter Ex Core, are a concept that allows for configuring some crosscutting feature functionality on Configurable Objects & Fields. Examples of such features 
include: 
- Specify Object Category
- Represent Special Fields
- Toggle Caching
- Enable WIP Messages
- Toggle Reversibility
- Etc.
Object Category: Object category, such as Named, Revisioned, Service etc., is a type of Usage 
that defines certain aspects of the Configurable Objects.
Special Fields: Fields like ‘Name’ property of a Named object or a ‘Revision’ Field of a 
Revisioned objects fall under this category of special fields since they have certain specific 
functionality defined for them. 
Caching: This toggle determines whether an object can be cached at runtime. It provides for a 
mechanism to toggle this feature per Object definition for fine grained control of caching.
WIP Messages: Work in progress (WIP) messages can be defined for specific modeling objects 
so that the message appears to a user when a traceable material with specific attributes 
reaches a certain processing point.
Reversibility: Toggle for Transaction reversibility <To PrM: do we need this?>
Doc Attachments: <Define>
<More>
