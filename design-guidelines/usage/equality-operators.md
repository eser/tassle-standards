---
title: "Equality Operators"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: dotnet-standard
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "class library design guidelines [.NET Framework], Equals method"
  - "class library design guidelines [.NET Framework], equality operator"
  - "equality operator (==) [.NET Framework]"
  - "Equals method"
  - "== operator (equality) [.NET Framework]"
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
ms.workload: 
  - "dotnet"
  - "dotnetcore"
---
# Equality Operators
This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.  
  
 **X DO NOT** overload one of the equality operators and not the other.  
  
 **✓ DO** ensure that `System.Object.Equals` and the equality operators have exactly the same semantics and similar performance characteristics.  
  
 This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.  
  
 **X AVOID** throwing exceptions from equality operators.  
  
 For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.  
  
## Equality Operators on Value Types  
 **✓ DO** overload the equality operators on value types, if equality is meaningful.  
  
 In most programming languages, there is no default implementation of `operator==` for value types.  
  
## Equality Operators on Reference Types  
 **X AVOID** overloading equality operators on mutable reference types.  
  
 Many languages have built-in equality operators for reference types. The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.  
  
 This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.  
  
 **X AVOID** overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.  
  
 *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*  
 *Modified by Eser Ozvataf © 2019*
