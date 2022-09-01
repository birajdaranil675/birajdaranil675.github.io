---
title: "Object Declearation"
weight: 1
---

As mentioned in the metamodel design, a Configurable Object is represented by declaring a
C# class and building on from the base class types & interfaces provided by the metamodel
framework. Some examples are:

**TO DECLARE AN OBJECT**

_public partial class NamedObject : BaseObject_

_{_

**TO DECLARE A ‘NAMED’ OBJECT**

_public partial class NamedObject : BaseObject, INamed_

_{_

**TO DECLARE A ‘REVISIONED’ OBJECT**

_public abstract class RevisionedObject<TSubClassType> : BaseObject,
IRevisioned<TSubClassType> where TSubClassType : class, IRevisioned<TSubClassType>_

_{_

**TO DECLARE AN ‘SUBENTITY’ OBJECT**

_public abstract class SubentityObjectOf<TParentClassType> : SubentityObject,
ISubentityOf<TParentClassType> where TParentClassType : class, IBaseObject_

_{_

**TO DECLARE A ‘MODELING SERVICE’ OBJECT**

_public partial class NamedDataService<ClassType> : ServiceObject,
INamedModelingService<ClassType> where ClassType : class, INamed_

_{_

**TO DECLARE A ‘REVISIONED MODELING SERVICE’ OBJECT**

_public partial class RevisionedDataService<RevType> : NamedDataService<RevType>,
IRevisionedModelingService<RevType> where RevType : RevisionedObject<RevType>_

_{_

**TO DECLARE A ‘SHOPFLOOR SERVICE’ OBJECT**

_public abstract partial class ShopfloorService : ServiceObject, IShopfloorService_

_{_