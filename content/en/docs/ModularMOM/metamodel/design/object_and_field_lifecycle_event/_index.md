---
title: "Object and Field Life-Cycle Events"
weight: 5
---

{{< figure src="/images/object_and_filed_lifecycle_events.png" >}}

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

**AfterExecute:** Triggered as part of Service execution and after 
**BeforeExecute** event is performed and provides additional hooks for custom logic to manipulate the object state as 
required for the service before the object state (transaction) is committed to the storage
**AfterCommit:** Triggered as part of Service execution and after the object state is successfully 
committed to the persistent storage providing hooks for any custom logic to do notifications 
or integration with other systems etc.
**AfterCommitEventFailure:** Triggered as part of Service execution and on failure of the 
**AfterCommit** event providing hooks for custom logic to handle any failures occurring during 
**AfterCommit** event. This event is fired ONLY when ‘AfterCommit’ event fails
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