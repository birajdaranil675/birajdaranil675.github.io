---
title: "Configurable object Maps"
weight: 6
---

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