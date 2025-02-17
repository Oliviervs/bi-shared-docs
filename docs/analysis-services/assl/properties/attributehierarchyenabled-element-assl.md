---
title: "AttributeHierarchyEnabled Element (ASSL) | Microsoft Docs"
description: Learn about the AttributeHierarchyEnabled property element in the Analysis Services Scripting Language (ASSL) schema.
ms.date: 10/31/2023
ms.service: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan

---
# AttributeHierarchyEnabled Element (ASSL)

  Determines whether an attribute hierarchy is enabled for the attribute.  
  
## Syntax  
  
```xml  
  
<DimensionAttribute><!-- or CubeAttribute -->  
   ...  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
   ...  
</DimensionAttribute>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|Data type and length|Boolean|  
|Default value|**True**|  
|Cardinality|0-1: Optional element that can occur once and only once.|  
  
## Element Relationships  
  
|Relationship|Element|  
|------------------|-------------|  
|Parent element|[CubeAttribute](../data-type/cubeattribute-data-type-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Child elements|None|  
  
## Remarks  
 The **AttributeHierarchyEnabled** element determines whether an attribute hierarchy is generated by Analysis Services for the attribute. If the attribute hierarchy is not enabled, then the attribute cannot be used in a user-defined hierarchy, nor can the attribute hierarchy be referenced in Multidimensional Expressions (MDX) statements.  
  
 The elements that correspond to the parents of **AttributeHierarchyEnabled** in the Analysis Management Objects (AMO) object model are <xref:Microsoft.AnalysisServices.CubeAttribute> and <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## See Also  
 [AttributeHierarchyVisible Element &#40;ASSL&#41;](attributehierarchyvisible-element-assl.md)   
 [Properties &#40;ASSL&#41;](properties-assl.md)  
  
  
