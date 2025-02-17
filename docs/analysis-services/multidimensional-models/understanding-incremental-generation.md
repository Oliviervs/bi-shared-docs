---
title: "Understanding Incremental Generation | Microsoft Docs"
description: Use incremental translation to change cube and dimension definitions by using SQL Server Data Tools, and then rerun the Schema Generation Wizard.
ms.date: 05/02/2018
ms.service: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan

---
# Understanding Incremental Generation
[!INCLUDE[appliesto-sqlas](../includes/appliesto-sqlas.md)]
  Following the initial schema generation, you can change cube and dimension definitions by using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], and then rerun the Schema Generation Wizard. The wizard updates the schema in the subject area database and in the associated data source view to reflect the changes, and retaining the data that currently exists in the tables to be regenerated, to the extent possible. If you changed the tables after the initial generation, the Schema Generation Wizard preserves those changes when possible by using the following rules:  
  
-   If a table was previously generated by the wizard, the table is overwritten. You can prevent a table that was generated by the wizard from being overwritten by changing the **AllowChangesDuringGeneration** property for the table in the data source view to **false**. When you take control of a table, the table is treated like any other user-defined table and is not affected during regeneration. After you remove a table from generation, you can later change the **AllowChangesDuringGeneration** property for the table in the data source view to **true** and reopen the table for changes by the wizard. For more information, see [Change Properties in a Data Source View &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md).  
  
-   If a table was added to the data source view or to the underlying database by something other than the wizard, the table is not overwritten.  
  
 When the Schema Generation Wizard regenerates tables that were previously generated in the subject area database, you can choose to have the wizard preserve existing data in those tables.  
  
## Supporting Data Preservation  
 As a general rule, the Schema Generation Wizard preserves data that is stored in the tables that it generated. In addition, if you add columns to tables that the wizard generated, the wizard preserves that data as well. You can use this capability to add or modify your dimensions and cubes and then regenerate the underlying objects without having to reload the data stored in the underlying tables.  
  
> [!NOTE]  
>  If you are loading data from delimited text files, you can also choose whether the Schema Generation Wizard overwrites these files and the data contained in them during regeneration. Text files are either overwritten completely or not at all. The Schema Generation Wizard does not partially overwrite these files. By default, these files are not overwritten.  
  
### Partial Preservation  
 The Schema Generation Wizard cannot preserve existing data under some circumstances. The following table provides examples of situations in which the wizard cannot preserve all the existing data in the underlying tables during regeneration.  
  
|Type of data change|Treatment|  
|-------------------------|---------------|  
|Incompatible data type change|The Schema Generation Wizard uses standard [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data type conversions, whenever possible, to convert existing data from one data type to another. However, when you change an attribute's data type to a type that is incompatible with the existing data, the wizard drops the data for the affected column.|  
|Referential integrity errors|If you change a dimension or cube that contains data and the change causes a referential integrity error during regeneration, the Schema Generation Wizard drops all data in the foreign key table. The data that is dropped is not limited to the column that caused the foreign key constraint violation or to the rows that contain the referential integrity errors. For example, if you change the dimension key to an attribute that has non-unique or null data, all existing data in the foreign key table is dropped. Furthermore, dropping all the data in one table can have a cascading effect and can cause other referential integrity violations.|  
|Deleted attribute or dimension|If you delete an attribute from a dimension, the Schema Generation Wizard deletes the column that is mapped to the deleted attribute. If you delete a dimension, the wizard deletes the table that is mapped to the deleted dimension. In these cases, the wizard drops the data that is contained in the deleted column or table.|  
  
 The Schema Generation Wizard issues a warning before it drops any data so that you can cancel the wizard without losing any data. However, the Schema Generation Wizard is not able to differentiate between anticipated data loss and unanticipated data loss. When you run the wizard, a dialog box lists the tables and columns that contain data that will be dropped. You can either have the wizard continue and drop the data, or you can cancel the wizard and revise the changes you made to the tables and columns.  
  
## Supporting Cube and Dimension Changes  
 When you change the properties of dimensions and cubes, the Schema Generation Wizard regenerates the appropriate objects in the underlying subject area database, as well as in the related data source view, as described in the following table.  
  
 Deleting an object, such as a dimension, cube, or attribute.  
 The Schema Generation Wizard deletes the underlying objects to which the deleted object is mapped. If you add columns to a table that the wizard generated, the new columns do not prevent that table from being deleted. Deleting an object causes the data stored in the underlying objects to be dropped, and may also cause other data to be dropped if referential integrity errors occur.  
  
 Renaming an object, such as a dimension, cube, or attribute.  
 The Schema Generation Wizard renames the underlying objects to which the renamed object is mapped. The wizard also renames all affected objects, such as primary keys. Existing data stored in the underlying objects is preserved.  
  
 Modifying an object, such as changing its data type.  
 The Schema Generation Wizard modifies the underlying objects to which the changed object is mapped. Existing data stored in the underlying objects in the databases is preserved, unless the new data type is incompatible with the existing data.  
  
 Adding a new object, such as a dimension, cube, or attribute.  
 The Schema Generation Wizard adds underlying objects to which the new object is mapped.  
  
 If the Schema Generation Wizard cannot make the required change because of the presence of a user object in the subject area database (because the Database Engine returns an error), the Schema Generation Wizard fails and displays the error returned by the Database Engine. For example, if you create a primary key constraint or a non-clustered index on a table after the wizard generated the table, the Schema Generation Wizard does not drop that table because it did not create the constraint or the index.  
  
## Supporting Schema Changes  
 When you change the properties of the tables or columns in the subject area database or in the associated data source view, the Schema Generation Wizard treats the changes as described in the following table.  
  
 Deleting a table or a column generated by the Schema Generation Wizard.  
 If you delete a table or a column generated by the Schema Generation Wizard, the wizard regenerates the deleted table. The wizard provides no warning that the deleted table or column will be regenerated.  
  
 Changing the properties of a table or column generated by the Schema Generation Wizard.  
 If you modify the properties of a table or a column generated by the Schema Generation Wizard, the wizard regenerates the changed table without the change. For example, if you change the data type or nullability of a column, or the filegroup of a table generated by the Schema Generation Wizard, the change does not survive the regeneration. The wizard provides no warning that the changed object will be regenerated without the change.  
  
 Adding a column to a table generated by the Schema Generation Wizard or adding a table to the subject area database or staging area database.  
 If you add a column to a table generated by the Schema Generation Wizard, the wizard preserves the additional column, along with any data stored in it, during regeneration. However, if you add a table to the subject area database or the staging area database, the Schema Generation Wizard does not incorporate the new table. The added column, or the added table, is not reflected in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the DTS packages, the data source view, or any other place in the schema that is generated.  
  
## Supporting Data Source and Data Source View Changes  
 When the Schema Generation Wizard is rerun, it reuses the same data source and data source view that it used for the original generation. If you add a data source or a data source view, the wizard does not use it. If you delete the original data source or data source view after the initial generation, you must run the wizard from the beginning. All previous settings in the wizard are also deleted. Any existing objects in an underlying database that were bound to a deleted data source or data source view are treated as user-created objects the next time you run the Schema Generation Wizard.  
  
 If the data source view does not reflect the actual state of the underlying database at the time of generation, the Schema Generation Wizard may encounter errors when it generates the schemas for the subject area database and the staging area database. For example, if the data source view specifies that the data type for a column is set to **int**, but the data type for the column is actually set to **string**, the Schema Generation Wizard sets the data type for the foreign key to **int** to match the data source view and then fails when it creates the relationship because the actual data type is **string**.  
  
 On the other hand, if you change the data source connection string to a different database from the previous generation, no error is generated. The new database is used, and no change is made to the previous database.  
  
## See Also  
 [Manage Changes to Data Source Views and Data Sources](../../analysis-services/multidimensional-models/manage-changes-to-data-source-views-and-data-sources.md)   
 [Schema Generation Wizard &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/schema-generation-wizard-analysis-services.md)  
  
  
