---
title: "Metadata Customization"
weight: 6
---

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