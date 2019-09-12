---
title: "Protected Members"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: dotnet-standard
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "members [.NET Framework], protected"
  - "protected members"
  - "classes [.NET Framework], unsealed"
  - "classes [.NET Framework], protected members"
  - "unsealed classes"
  - "customizing class behavior"
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
ms.workload: 
  - "dotnet"
  - "dotnetcore"
---
# Protected Members
Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful. They can be used to expose advanced customization options without unnecessarily complicating the main public interface.  
  
 Framework designers need to be careful with protected members because the name "protected" can give a false sense of security. Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.  
  
 **✓ CONSIDER** using protected members for advanced customization.  
  
 **✓ DO** treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.  
  
 Anyone can inherit from a class and access the protected members.  
  
 *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*  
 *Modified by Eser Ozvataf © 2019*
