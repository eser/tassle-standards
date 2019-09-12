---
title: "Capitalization Conventions"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: dotnet-standard
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "camel-case names [.NET Framework]"
  - "class library design guidelines [.NET Framework], capitalization"
  - "Pascal-case names [.NET Framework]"
  - "case sensitivity, capitalization conventions"
  - "names [.NET Framework], capitalization"
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
ms.workload: 
  - "dotnet"
  - "dotnetcore"
---
# Capitalization Conventions
The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.  
  
## Capitalization Rules for Identifiers  
 To differentiate words in an identifier, capitalize the first letter of each word in the identifier. Do not use underscores to differentiate words, or for that matter, anywhere in identifiers. There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:  
  
-   PascalCasing  
  
-   camelCasing  
  
 The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:  
  
 `IOStream`  
  
 The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples. As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ DO** use PascalCasing for all public and internal member, type, and namespace names consisting of multiple words.  
  
 **✓ DO** use camelCasing for all private, protected, internal protected members and also parameter names.  
  
 The following table describes the capitalization rules for different types of identifiers.  
  
|Identifier|Casing|Example|  
|----------------|------------|-------------|  
|Namespace|Pascal|`namespace System.Security { ... }`|  
|Type|Pascal|`public class StreamReader { ... }`|  
|Interface|Pascal|`public interface IEnumerable { ... }`|  
|Method|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|Property|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|Event|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|Constant|Pascal|`public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|Public/Internal Field|Pascal|`public class MessageQueue {` <br />  `public static TimeSpan` <br /> `InfiniteTimeout;` <br /> `}`|  
|Other Fields|Camel|`public class MessageQueue {` <br />  `protected readonly DateTime` <br /> `minDateTimeValue;` <br /> `}`|  
|Enum value|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|Parameter|Camel|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## Capitalizing Compound Words and Common Terms  
 Most compound terms are treated as single words for purposes of capitalization.  
  
 **X DO NOT** capitalize each word in so-called closed-form compound words.  
  
 These are compound words written as a single word, such as endpoint. For the purpose of casing guidelines, treat a closed-form compound word as a single word. Use a current dictionary to determine if a compound word is written in closed form.  
  
|Pascal|Camel|Not|  
|------------|-----------|---------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## Case Sensitivity  
 Languages that can run on the CLR are not required to support case-sensitivity, although some do. Even if your language supports it, other languages that might access your framework do not. Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.  
  
 **X DO NOT** assume that all programming languages are case sensitive. They are not. Names cannot differ by case alone.  
  
 *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*  
 *Modified by Eser Ozvataf © 2019*
