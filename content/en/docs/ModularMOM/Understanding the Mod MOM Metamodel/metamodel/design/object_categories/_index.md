---
title: "Object categories"
weight: 2
---

Configurable Objects are classified into the following high-level types based on the intended 
purpose of the objects.

**Business Objects:** Objects in this category are intended to represent the concepts from the 
Business domain model.

**Service Objects:** Business operations are modelled using the Service type of objects and these 
objects become the interface between the external world and this metadata-based system. 
Service definitions serve the purpose of an API to the business services provided by this 
metadata. Every interaction with the external world other than just querying the model is 
always through the execution of a ‘Service’ type of object.

**Persistent Objects:** The state of the Business Objects which represent the concepts from the 
Business domain model are typically persisted in some form of storage. This Metamodel 
provides a framework through ORM to facilitate the persistence of these objects. The 
Business Objects that are configured to be persistent are called or classified as ‘Persistent 
Objects’

**Transient Objects:** Objects such as Service objects and some Business Objects that do not 
require the state to be persisted are called as Transient Objects. The main purpose of these 
transient objects is to aid during the execution of business functionality to keep and track 
some internal state but are not required to be persisted.

**Named Objects:** All objects have a unique identifier assigned automatically by the system to 
identify and reference these objects. Some Business Objects within the business domain 
model that can be identified by a unique name are called ‘Named’ objects. The name serves 
the purpose of an alternate logical key for the object.

**Revisioned Objects:** Object Revision Control is the ability of an object to have multiple 
revisions and still be able to be managed as one object. Objects that support revision control 
are generally referred to as ‘Revisioned Objects’. Within this Metamodel, Revisioned Objects 
implement the following pattern for revision control mechanism.
      - Revisioned Objects are standard objects like any other Business object
      - Revisioned Objects can have one or more ‘Revisions’
      - Revisioned Objects will have ONE revision marked as 'Revision of Record', aka ‘RoR’
      - Revisioned Objects have the following 2 alternate logical keys of identification:

1. Name only, which always refers to the current ‘RoR’ object
2. Name and Revision, which uniquely identifies a specific single revision

**Subentity Objects:** Composable objects and are also called as Subentity objects. 

**Named Subentity Objects:** Subentity objects can, optionally, be ‘Named’ objects such as that 
they can be uniquely identified by a name within the context of it composing object.