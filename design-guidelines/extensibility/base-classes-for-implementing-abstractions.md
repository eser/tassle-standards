---
title: "Base Classes for Implementing Abstractions"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: dotnet-standard
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "abstractions [.NET Framework]"
  - "base classes, abstractions"
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
ms.workload: 
  - "dotnet"
  - "dotnetcore"
---
# Base Classes for Implementing Abstractions
Strictly speaking, a class becomes a base class when another class is derived from it. For the purpose of this section, however, a base class is a class designed mainly to provide a common abstraction or for other classes to reuse some default implementation though inheritance. Base classes usually sit in the middle of inheritance hierarchies, between an abstraction at the root of a hierarchy and several custom implementations at the bottom.  
  
 They serve as implementation helpers for implementing abstractions. For example, one of the Framework’s abstractions for ordered collections of items is the `System.Collections.Generic.IList` interface. Implementing `System.Collections.Generic.IList` is not trivial, and therefore the Framework provides several base classes, such as `System.Collections.ObjectModel.Collection` and `System.Collections.ObjectModel.KeyedCollection`, which serve as helpers for implementing custom collections.  
  
 Base classes are usually not suited to serve as abstractions by themselves, because they tend to contain too much implementation. For example, the `Collection<T>` base class contains lots of implementation related to the fact that it implements the nongeneric `IList` interface (to integrate better with nongeneric collections) and to the fact that it is a collection of items stored in memory in one of its fields.  
  
 As previously discussed, base classes can provide invaluable help for users who need to implement abstractions, but at the same time they can be a significant liability. They add surface area and increase the depth of inheritance hierarchies and so conceptually complicate the framework. Therefore, base classes should be used only if they provide significant value to the users of the framework. They should be avoided if they provide value only to the implementers of the framework, in which case delegation to an internal implementation instead of inheritance from a base class should be strongly considered.  
  
 **✓ CONSIDER** making base classes abstract even if they don’t contain any abstract members. This clearly communicates to the users that the class is designed solely to be inherited from.  
  
 **✓ CONSIDER** placing base classes in a separate namespace from the mainline scenario types. By definition, base classes are intended for advanced extensibility scenarios and therefore are not interesting to the majority of users.  
  
 **X AVOID** naming base classes with a "Base" suffix if the class is intended for use in public APIs.  
  
 *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*  
 *Modified by Eser Ozvataf © 2019*
