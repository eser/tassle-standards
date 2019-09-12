---
title: "Dependency Properties"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: dotnet-standard
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
ms.workload: 
  - "dotnet"
  - "dotnetcore"
---
# Dependency Properties
A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.  
  
 An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).  
  
 **✓ DO** provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.  
  
## Dependency Property Design  
 **✓ DO** inherit from `System.Windows.DependencyObject`, or one of its subtypes, when implementing dependency properties. The type provides a very efficient implementation of a property store and automatically supports WPF data binding.  
  
 **✓ DO** provide a regular CLR property and public static read-only field storing an instance of `System.Windows.DependencyProperty` for each dependency property.  
  
 **✓ DO** implement dependency properties by calling instance methods `System.Windows.DependencyObject.GetValue` and `System.Windows.DependencyObject.SetValue`.  
  
 **✓ DO** name the dependency property static field by suffixing the name of the property with "Property."  
  
 **X DO NOT** set default values of dependency properties explicitly in code; set them in metadata instead.  
  
 If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.  
  
 **X DO NOT** put code in the property accessors other than the standard code to access the static field.  
  
 That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.  
  
 **X DO NOT** use dependency properties to store secure data. Even private dependency properties can be accessed publicly.  
  
## Attached Dependency Property Design  
 Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it. A special kind of dependency property is the attached dependency property.  
  
 A classic example of an attached property is the `System.Windows.Controls.Grid.Column` property. The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.  
  
```  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:  
  
```  
public class Grid {  
    public static readonly DependencyProperty ColumnProperty =  
        DependencyProperty.RegisterAttached(  
            "Column",  
            typeof(int),  
            typeof(Grid)  
    );  
  
    public static int GetColumn(DependencyObject obj) {  
        return (int)obj.GetValue(Grid.ColumnProperty);  
    }  
  
    public static void SetColumn(DependencyObject obj, int value) {  
        obj.SetValue(Grid.ColumnProperty, value);  
    }  
}  
```  
  
## Dependency Property Validation  
 Properties often implement what is called validation. Validation logic executes when an attempt is made to change the value of a property.  
  
 Unfortunately dependency property accessors cannot contain arbitrary validation code. Instead, dependency property validation logic needs to be specified during property registration.  
  
 **X DO NOT** put dependency property validation logic in the property’s accessors. Instead, pass a validation callback to `DependencyProperty.Register` method.  
  
## Dependency Property Change Notifications  
 **X DO NOT** implement change notification logic in dependency property accessors. Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the `System.Windows.PropertyMetadata`.  
  
## Dependency Property Value Coercion  
 Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.  
  
 **X DO NOT** implement coercion logic in dependency property accessors.  
  
 Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*  
 *Modified by Eser Ozvataf © 2019*
