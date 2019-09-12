---
title: "Arrays"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: dotnet-standard
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "class library design guidelines [.NET Framework], arrays"
  - "arrays [.NET Framework], usage guidelines"
  - "empty arrays"
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
ms.workload: 
  - "dotnet"
  - "dotnetcore"
---
# Arrays
**✓ DO** prefer using collections over arrays in public APIs. The [Collections](guidelines-for-collections.md) section provides details about how to choose between collections and arrays.  
  
 **X DO NOT** use read-only array fields. The field itself is read-only and can't be changed, but elements in the array can be changed.  
  
 **✓ CONSIDER** using jagged arrays instead of multidimensional arrays.  
  
 A jagged array is an array with elements that are also arrays. The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays. Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.  
  
 *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*  
 *Modified by Eser Ozvataf © 2019*
