---
title: "METADATA – MODEL EXECUTION"
url: /ModularMOM/Metadata-design/METADATA – MODEL EXECUTION/
weight: 5
description: "Learn what is MOD MOM Platform."
tags: ["microflows", "widgets", "app", "nanoflow", "app development"]
---

### Metadata Engine

Metadata Engine is an embeddable engine that understands and processes the Metadata. It
is an engine that is also responsible for taking the user’s input and executing the business
transaction as defined in the Metadata.

#### Interfaces

{{< figure src = "/images/metadata_model_execution.png" >}}


##### INTERFACES EXPOSED

**Invocation API:** Contains Interfaces and Classes to support the creation of the Metadata
Engine and as well as create ‘Service’ type objects and execute them.

**Introspection API:** Provides API for the discovery of the metadata model at the runtime.

**INTERFACES CONSUMED**

**Persistence API:** This platform API is provided by the embedding layer (Execution Engine) and
is consumed by the embedded Metadata Engine to handle object persistence.

**Integrations/Communications API:** This platform API is provided by the embedding layer
(Execution Engine) and is consumed by the embedded Metadata Engine to handle any
interactions/communication with external components such as for pub/sub of messages or
any other supported communication patterns.

**Governance/Observability API:** This platform API is provided by the embedding layer (Execution
Engine) and is consumed by the embedded Metadata Engine to provide an ability to govern
and monitor the metadata engine by the outer execution engine.


#### Engine Factory

Metadata Engine provides ‘Factory’ style API for the creation of the Metadata Engine
instances. Classes and interfaces provide runtime context for the model execution (business
logic).

**BizLogicEngineFactory:** This class implements the ‘Factory’ pattern and provides the API to
create instance of the Metadata Engine

**IMetadataEngine:** This interface defines the contract exposed by the Metadata Engine

{{< figure src = "/images/IMetadataEngine.png" >}}

#### Runtime Context

##### OBJECT RUNTIME EXECUTION CONTEXT

Base classes and interfaces to provides runtime context for the business logic execution.

**ServiceExecutionContext:** This class provides the runtime context to the invocation of a
‘Service’. Every instance of a service gets a new instance of the context that provides local
caching lookup of objects being instantiated during the context of this service invocation.

An instance of this type is available through a property ‘_ **_ExecutionContext’_** that is available
on every Configurable Object.

Sample usage of this property:

```
_ ExecutionContext. GetByName <ClassType>(name);
_ ExecutionContext. GetById <ClassType>(id.AsObjectId());
_ ExecutionContext. GetAll <ClassType>();
```