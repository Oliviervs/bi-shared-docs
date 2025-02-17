---
title: "MeasureGroupID Element (XMLA) | Microsoft Docs"
description: Learn how the MeasureGroupID element identifies a measure group within a parent element that contains an object reference.
ms.date: 01/05/2020
ms.service: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan

---
# MeasureGroupID Element (XMLA)

  Identifies a measure group within a parent element that contains an object reference.  
  
## Syntax  
  
```xml  
  
<Object> <!-- or one of the elements listed below in the Element relationships table -->  
   ...  
   <MeasureGroupID>...</MeasureGroupID>  
   ...  
</Object>  
```  
  
## Element characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|Data type and length|String|  
|Default value|None|  
|Cardinality|See the table below.|  
  
|Ancestor or Parent|Cardinality|  
|------------------------|-----------------|  
|[Source](../xml-elements-properties/source-element-xmla.md), [Target](../xml-elements-properties/target-element-xmla.md)|1-1: Required element that occurs once and only once.|  
|All others|0-1: Optional element that can occur once and only once.|  
  
## Element relationships  
  
|Relationship|Element|  
|------------------|-------------|  
|Parent elements|[Object](../xml-elements-properties/object-element-xmla.md), [ParentObject](../xml-elements-properties/parentobject-element-xmla.md), [Source](../xml-elements-properties/source-element-xmla.md), [Target](../xml-elements-properties/target-element-xmla.md)|  
|Child elements|None|  
  
## Remarks  
