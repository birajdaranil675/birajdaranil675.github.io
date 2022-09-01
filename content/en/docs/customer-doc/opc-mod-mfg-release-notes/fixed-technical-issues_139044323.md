---
title: "Fixed Technical Issues"
url: 
weight: 7
---

**Created by Alvarez Villanueva, Beatriz, last modified on Apr 26, 2022**  


The following technical issues have now been solved in version 2207 of  Opcenter Modular Manufacturing:

|**Internal ID**|**Description**|
| :-: | :-: |
|**23671**|<p>Could not use SortingFields from revisionedBase obj.</p><p>In the **Material Definitions** page, you can sort also by the columns **Material** and **Active.**</p>|
|**23952**|<p>SQ Code smell: Provide an 'AssemblyVersion' attribute for assembly 'M1\_OrderManagement'.</p><p>Product libraries display the Attribute assembly version in the details.</p>|
|**26006**|Advanced Query configuration for Enum must respect PersistAs Attribute value<br>Inner platform functionality can now correctly handle enumeration fields.|
|**26874**|Save button works even if it is disabled<br>In all Opcenter Modular Manufacturing pages, all disabled buttons in the command bar on the right cannot be clicked.|
|**26963**|Back navigation functionality on OM UI<br>In all Opcenter Modular Manufacturing pages, the **Back** button works properly.|
|**27556**|Messages appear on Login screen at wrong location and in wrong style.<br>If you are already logged in the system,  you can now  login again with no error messages.|
|**27832**|Race Condition in Data Load In PO View<br>In the **Production Orders** page, all commands are executed separately.|
|**27834**|PO and WO View - Fields coming from ChangeDetails cannot be sorted<br>In the **Production Orders** and the **Work Orders** pages, you can sort by the following columns: **Created On**, **Created By**, **Last changed on**, **Last changed by**.|
|**27919**|Retry and Recovery Management does not work correctly on OS with OrderManagement- >MaterialManagement (missing deadline in communication channel).<br>In case of inner message propagation failure, the Retry mechanism works correctly.|
|**27934**|InstanceId when used in query returns Field is not persistent:query:<br>Inner platform functionality can now correctly handle CO instance Id fields.|
|**27971**|PO Details : URL with POName is not getting displayed.<br>If you select a production order and click **Open**, the **Production Orders**  page displays the URL of the selected production order name.|
|**28012**|OM: Import production order (B2MML\CSV) - the reference to the operation definition is missing when the operation definition revision is not provided<br>When you launch a production order imported successfully, the **LaunchProductionOrder** succeeds, the work order is created and the state of the production order is .|
|**28057**|Remove group command button from "Import PO" on Vertical Command Bar<br>The **Import** button of the **Production Orders** page works properly.|
|**28058**|<p>Race Condition - PO View Details if data are not properly loaded, changing tab generate issue</p><p>In the **Production Orders** page, you can select a production order and click **Operations** or **Materials** tab.</p>|
|**28062**|<p>Operator Terminal - Context area data cannot be read</p><p>In the **Operator Terminal** page, the context area data can now be read.</p>|
|**28070**|UI TNT - refresh on details page issue<br>In the **Operations** page of the Track and Trace app, when you click **Refresh** all buttons located in the command bar on the right are now shown.|
|**28098**|Import CSV - field OperationLocation is not needed<br>The field **OperationLocation** in the schema has been removed.|
|**28138**|Operations are not shown at all once clicking another operation, if history is open for other<br>In the **Operations** page, when you select an operation, select the **History** tab and then select another operation, all buttons are displayed after refreshing.|
|**28184**|TNT GetAll: Status field contains only value and not display name<br>In the Track and Trace app, the **Status** field contains translated value.|
|**28185**|TNT WorkOrderOperationInquiryService: Status field contains only display name and not value<br>In the Track and Trace app, the **Status** field contains all translated values.|
|**28186**|NT UI: WorkOrder and Operations status multi language not supported<br>The status of work orders and operations are displayed with an icon and a string in multi language.|
|**28187**|OM UI: PO statuses Pending and Launching have unknown icon<br>In the **Production Orders** page of the Order Management app, the production orders in state **Pending** or **Launching** display known icons.|
|**28221**|<p>Sharp cannot be used in all CO Names (PO, PO Op, PO Po Material) - Input validation should be performed during Import:</p><p>The '#' character can now be used in Configurable Object names.</p>|
|**41921**|<p>Sort functionality is not working for Material Definitions</p><p>In the **Material Definitions** page, if you select the column header, the commands **Sort Ascending** and **Sort Descending** work properly.</p>|



