---
title: "Metadata Components Overview - General"
url: /ModularMOM/Metadata-design/Metadata-Components-Overview-General/
weight: 40
no_list: false 
description_list: true 
tags: ["runtime", "runtime server", "mendix client", "cluster leader"]
---

{{< figure src="/images/metadata_overview_general.png" >}}

### Metadata Layers – Modular

{{< figure src="/images/metadata_layer_modular.png" >}}

### Common Metadata Components

#### Object Model

##### DOMAIN MODEL

**Modelling Objects:** Objects that define the business domain model. This model can be defined
using the following object categories provided by the system: like **Named** Objects, **Revisioned**
Objects, **Subentity** Objects. Examples of domain model objects include: **Product** , **Work Order** ,
**Operation** , etc. The business model would be based on what actual business functionality will
be implemented in Modular MOM.

**WORKFLOW MODEL**

In Opcenter Execution Core, the unit of work is controlled and configured through a concept
called **Workflow** model. A workflow is a series of sequential tasks that are carried out based
on user-defined rules or conditions, to execute a business or a manufacturing process. It is a
collection of data, rules, and tasks that need to be completed to achieve a certain business
outcome. A Workflow visually depicts a detailed sequence of business activities and
information flows needed to complete a process. Actual flow of the unit of work through this
workflow is controlled by various design time and runtime parameters such as the Product
being produced or the corresponding Manufacturing Order, or what equipment is being used
and even such parameters as process control measurements or any other information
associated with the current unit of work.

**OPERATIONAL MODEL**

**Traceable Object:** Manufacturing operations revolves around tracking the manufacturing
processes and the units of work flowing through these processes. A **Traceable** Object
category represents a unit of work that is intended to be tracked through the various
manufacturing processes. In Opcenter Execution Core, this concept is represented by an
object type called ‘ **Container** ’. Most of the Manufacturing Business operations are modelled
around this Traceable object. To help simply the definition of the actual business
functionality and the configurability of the system, various business logic templates are
created that are centered around the Traceable object.

**AUDIT TRAIL MODEL**

An audit trail is simply a log of the path that a unit of work has taken and all the collected
information during such flow of work. Audit trail captures key details such as: date and time
the unit of work was started, name of user who started, operations performed, additional
parameters collected etc.

Modular MOM Metadata provides a structured and configurable way to track and collect the
necessary information towards the audit trail during the manufacturing operations. This


configuration is implemented as part of Business Logic templates of the system that tie in
various such key functional features together and provide a unified mechanism for
configurability and customizability.

More Details about the actual model...

#### Service Model

As mentioned in the Metamodel concepts chapter, ‘ _Business operations are modelled using the
Service type of objects and these objects become the interface between the external world and this
metadata-based system_ ’. And, as mentioned in the preceding sections, the Business Logic
Templates provide a framework for easier, simpler & a configurable way to define business
operations.

At the Metamodel level, the following are the basic types of service models, and, a specific
Business Logic Template is defined for these service types in the Metadata layer:

- **Update** – services that create or manipulate the state of the persisted data
    o **Modeling** services provide a template for the creation and manipulation of the
       Engineering model, aka, Factory model instances. They provide the basic
       CRUD (Create, Read, Update, Delete) operations on the corresponding objects
    o **Shopfloor** details
- **Inquiry** – services that do not have any effects on the persisted data and they provide
    capabilities for reporting like functionality
- **Compound** – services that are composed of more than one service and they provide a
    mechanism to choregraph the execution of these composed services

#### Business Logic Templates

**MODELING SERVICES**

Details to be developed...

**SHOPFLOOR SERVICES**

Details to be developed...

**INQUIRY SERVICES**

Details to be developed...

**COMPOUND SERVICES**

Details to be developed...


#### Feature Templates

##### ELECTRONIC SIGNATURES

Details to be developed...

**INTEROPERABILITY (MESSAGING...)**

Details to be developed...

**MORE FEATURE TEMPLATES**

Data Collection, WIP Messages, Document Attachments, Where Used, etc.

**FUNCTIONAL FEATURE – ELECTRONIC PROCEDURES**

Details to be developed...

**MORE FUNCTIONAL FEATURES**

More examples...
