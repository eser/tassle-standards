---
title: "Static Class Design"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: dotnet-standard
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "type design guidelines, static classes"
  - "class library design guidelines [.NET Framework], classes"
  - "classes [.NET Framework], static"
  - "static classes [.NET Framework]"
  - "classes [.NET Framework], design guidelines"
  - "type design guidelines, classes"
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
ms.workload: 
  - "dotnet"
  - "dotnetcore"
---
# Static Class Design
A static class is defined as a class that contains only static members (of course besides the instance members inherited from `System.Object` and possibly a private constructor). Some languages provide built-in support for static classes. In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.  
  
 Static classes are a compromise between pure object-oriented design and simplicity. They are commonly used to provide shortcuts to other operations (such as `System.IO.File`), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as `System.Environment`).  
  
 **✓ DO** use static classes sparingly.  
  
 Static classes should be used only as supporting classes for the object-oriented core of the framework.  
  
 **X DO NOT** treat static classes as a miscellaneous bucket.  
  
 **X DO NOT** declare or override instance members in static classes.  
  
 **✓ DO** declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.  
  
 *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*  
 *Modified by Eser Ozvataf © 2019*
