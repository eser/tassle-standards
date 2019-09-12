---
title: "System.Xml Usage"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: dotnet-standard
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
ms.workload: 
  - "dotnet"
  - "dotnetcore"
---
# System.Xml Usage
This section talks about usage of several types residing in `System.Xml` namespaces that can be used to represent XML data.  
  
 **X DO NOT** use `System.Xml.XmlNode` or `System.Xml.XmlDocument` to represent XML data. Favor using instances of `System.Xml.XPath.IXPathNavigable`, `System.Xml.XmlReader`, `System.Xml.XmlWriter`, or subtypes of `System.Xml.Linq.XNode` instead. `XmlNode` and `XmlDocument` are not designed for exposing in public APIs.  
  
 **✓ DO** use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.  
  
 Use these abstractions instead of `XmlDocument`, `XmlNode`, or `System.Xml.XPath.XPathDocument`, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or `System.Xml.XPath.XPathNavigator`.  
  
 **X DO NOT** subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.  
  
 *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*  
 *Modified by Eser Ozvataf © 2019*
