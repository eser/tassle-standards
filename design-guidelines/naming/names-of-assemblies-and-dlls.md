---
title: "Names of Assemblies and DLLs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: dotnet-standard
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "names [.NET Framework], DLLs"
  - "names [.NET Framework], assemblies"
  - "assemblies [.NET Framework], names"
  - "DLLs, names"
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
ms.workload: 
  - "dotnet"
  - "dotnetcore"
---
# Names of Assemblies and DLLs
An assembly is the unit of deployment and identity for managed code programs. Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL. Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.  
  
 **✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.  
  
 Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies. A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly. For example, an assembly with two namespaces, `Tassle.Helpers.Validation` and `Tassle.Helpers.Reflection`, could be called `Tassle.Helpers.dll`.  
  
 **✓ CONSIDER** naming DLLs according to the following pattern:  
  
 `[<Company>.]<Product>.<Component>.dll`  
  
 where `<Component>` contains one or more dot-separated clauses. For example:  
  
 `Tassle.Caching.dll`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*  
 *Modified by Eser Ozvataf © 2019*
