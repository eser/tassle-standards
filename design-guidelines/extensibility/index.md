---
title: "Designing for Extensibility"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: dotnet-standard
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "extending class libraries"
  - "extensibility with class libraries in .NET Framework"
  - "class library design guidelines [.NET Framework], extensibility"
  - "class library extensibility [.NET Framework]"
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
ms.workload: 
  - "dotnet"
  - "dotnetcore"
---
# Designing for Extensibility
One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered. This requires that you understand the costs and benefits associated with various extensibility mechanisms. This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.  
  
 There are many ways to allow extensibility in frameworks. They range from less powerful but less costly to very powerful but expensive. For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements. Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.  
  
## In This Section  
 [Unsealed Classes](unsealed-classes.md)  
 [Protected Members](protected-members.md)  
 [Events and Callbacks](events-and-callbacks.md)  
 [Virtual Members](virtual-members.md)  
 [Abstractions (Abstract Types and Interfaces)](abstractions-abstract-types-and-interfaces.md)  
 [Base Classes for Implementing Abstractions](base-classes-for-implementing-abstractions.md)  
 [Sealing](sealing.md)  

 *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*  
 *Modified by Eser Ozvataf © 2019*
