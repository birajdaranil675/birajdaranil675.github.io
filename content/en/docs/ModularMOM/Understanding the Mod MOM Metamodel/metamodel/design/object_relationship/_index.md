---
title: "Object Relationship"
weight: 4
---

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