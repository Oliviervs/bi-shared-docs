---
title: "Analysis Services Internet Sales tutorial (1200 compatibility level) | Microsoft Docs"
description: An overview of lessons on how to create an Analysis Services tabular model at the 1200 compatibility level.
ms.date: 01/28/2020
ms.service: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan

---
# Adventure Works Internet Sales tutorial (1200)
[!INCLUDE[appliesto-sql2016-later-aas](../includes/appliesto-sql2016-later-aas.md)]

This tutorial provides lessons on how to create an Analysis Services tabular model at the [1200 compatibility level](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md) by using Visual Studio, and deploy your model to an Analysis Services server on-premises or in Azure.  

> [!IMPORTANT]
> This tutorial is no longer being updated. It's recommended you create tabular models at the latest compatibility level supported by your server. Later compatibility level models provide improved performance, additional features, and will upgrade to future compatibility levels more seamlessly. If you're using Azure Analysis Services or SQL Server 2017 or later Analysis Services, and you want to create your model at the 1400 or higher compatibility level, use the [Tabular modeling (1500 compatibility level)](../tutorial-tabular-1400/as-adventure-works-tutorial.md). This updated version of the tutorial uses the modern Get Data feature to connect and import source data, uses the M language to configure partitions, and includes additional supplemental lessons.
  
## What you learn   
  
-   How to create a new tabular model project in Visual Studio.
  
-   How to import data from a SQL Server relational database into a tabular model project.  
  
-   How to create and manage relationships between tables in the model.  
  
-   How to create and manage calculations, measures, and Key Performance Indicators that help users analyze model data.  
  
-   How to create and manage perspectives and hierarchies that help users more easily browse model data by providing business and application-specific viewpoints.  
  
-   How to create partitions dividing table data into smaller logical parts, that can be processed independent from other partitions.  
  
-   How to secure model objects and data by creating roles with user members.  
  
-   How to deploy a tabular model to an Analysis Services server on-premises or in Azure.  
  
## Scenario

This tutorial is based on Adventure Works Cycles, a fictitious company. Adventure Works is a large, multinational manufacturing company that produces  bicycles, parts, and accessories for commercial markets in North America, Europe, and Asia. With headquarters in Bothell, Washington, the company employs 500 workers. Additionally, Adventure Works employs several regional sales teams throughout its market base.  
  
To better support the data analysis needs of sales and marketing teams and of senior management, you are tasked with creating a tabular model for users to analyze Internet sales data in the AdventureWorksDW sample database.  
  
In order to complete the tutorial, and the Adventure Works Internet Sales tabular model, you must complete a number of lessons. In each lesson is a number of tasks; completing each task in order is necessary for completing the lesson. While in a particular lesson there may be several tasks that accomplish a similar outcome, but how you complete each task is slightly different. This is to show that there is often more than one way to complete a particular task, and to challenge you by using skills you've learned in previous tasks.  
  
The purpose of the lessons is to guide you through authoring a basic tabular model running in In-Memory mode by using many of the features included in Visual Studio. Because each lesson builds upon the previous lesson, you should complete the lessons in order. Once you've completed all of the lessons, you have authored and deployed the Adventure Works Internet Sales sample tabular model on an Analysis Services server.  
  
This tutorial does not provide lessons or information about managing a deployed tabular model database by using SQL Server Management Studio, or using a reporting client application to connect to a deployed model to browse model data.  
  
## Prerequisites

In order to complete this tutorial, you need the following prerequisites:  
  
-   The latest version of [Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt) with Analysis Services projects extension.

-   The latest version of [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms). 
  
-   A client application such as [Power BI Desktop](https://powerbi.microsoft.com/desktop/) or Excel.    
  
-   A SQL Server instance with the Adventure Works DW sample database. This sample database includes the data necessary to complete this tutorial. [Get the latest version](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).  
  
-   An Azure Analysis Services or SQL Server 2016 or later Analysis Services instance to deploy your model to. [Sign up for a free Azure Analysis Services trial](https://azure.microsoft.com/services/analysis-services/).
  
## Lessons  
This tutorial includes the following lessons:  
  
|Lesson|Estimated time to complete|  
|----------|------------------------------|  
|[Lesson 1: Create a New Tabular Model Project](lesson-1-create-a-new-tabular-model-project.md)|10 minutes|  
|[Lesson 2: Add Data](lesson-2-add-data.md)|20 minutes|  
|[Lesson 3: Mark as Date Table](lesson-3-mark-as-date-table.md)|3 minutes|  
|[Lesson 4: Create Relationships](lesson-4-create-relationships.md)|10 minutes|  
|[Lesson 5: Create Calculated Columns](lesson-5-create-calculated-columns.md)|15 minutes|
|[Lesson 6: Create Measures](lesson-6-create-measures.md)|30 minutes|  
|[Lesson 7: Create Key Performance Indicators](lesson-7-create-key-performance-indicators.md)|15 minutes|  
|[Lesson 8: Create Perspectives](lesson-8-create-perspectives.md)|5 minutes|  
|[Lesson 9: Create Hierarchies](lesson-9-create-hierarchies.md)|20 minutes|  
|[Lesson 10: Create Partitions](lesson-10-create-partitions.md)|15 minutes|  
|[Lesson 11: Create Roles](lesson-11-create-roles.md)|15 minutes|  
|[Lesson 12: Analyze in Excel](lesson-12-analyze-in-excel.md)|20 minutes| 
|[Lesson 13: Deploy](lesson-13-deploy.md)|5 minutes|  
  
## Supplemental lessons  
This tutorial also includes Supplemental Lessons. Topics in this section are not required to complete the tutorial, but can be helpful in better understanding advanced tabular model authoring features.  
  
|Lesson|Estimated time to complete|  
|----------|------------------------------|  
|[Implement Dynamic Security by Using Row Filters](supplemental-lesson-implement-dynamic-security-by-using-row-filters.md)|30 minutes|  

## Next steps  
To begin the tutorial, continue to the first lesson: [Lesson 1: Create a New Tabular Model Project](lesson-1-create-a-new-tabular-model-project.md).  
  
  
  

