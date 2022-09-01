---
title: "Known Technical Issues"
url: 
weight: 6
---

**Created by Alvarez Villanueva, Beatriz, last modified on Apr 26, 2022**  

Technical Limitation

System has been tested with import of 40 Production Orders, each of them with 10 operation and 4 material each.

Known Issues

|**Internal ID**|**Description**|
| :-: | :-: |
|**29950**|<p>Panel and Panel Content Styles + restricted interaction in PO, User groups, Roles</p><p>The following panels shall be modal so that users can only interact with the panel. Everything on the background, included vertical command bar, shall be hidden by a transparent lightbox to forbid interaction:</p><p>**Add Role** panel of the **Roles** page<br>**Add User Group** panel of the **User Groups** page<br>**Assign User Groups** panel of the **Roles** page<br>**Change Priority** panel of the **Production Orders** page</p>|
|**37888** |<p>User is not informed about unique name condition on creation of factory node</p><p>When you add a new factory unit with the same name as one of the parent node child, the message that appears is misleading.</p>|
|**43657**|<p>unwanted Session & state Token information in URL</p><p>The URL of the Operator Terminal displays unwanted information.</p>|
|**47927**|<p>MetadataRuntime: Capability to set values into the custom RevisionBase type through the API is not working.</p><p>When you create a custom RevisionBase type for a revisioned object type and add a new persistent field, the Create Object API is not working when in the input you set the value of such new field by extending from 'Base' (example: "base": { "newField": "someValue" } )</p>|
|**48034**|<p>Style of the About dialog is different in Access Management</p><p>In the Access Management app, the style of the **About** dialog box is different.</p>|
|**48742**|<p>If I select a filter, then I delete the text and I select either revision or location an error occur</p><p>In the **Production Orders** page, if you select a filter, remove the text to filter and then select either revision or location, an error message appears.</p>|
|**49331**|<p>Status management of the informational operation (via StartOperation and UpdateTask)</p><p>When you start a manual operation linked to one or more informational operation, the status of the manual operation is In Process but the informational operations remain in status Pending and also should become In Process.</p><p>When all tasks are completed, all operations are in status Completed.</p>|
|**49488**|<p>Metadata runtime: unique key violation error, trying to delete an create items in a INamedSubentityListField field when executed in the same service execution context</p><p>If you try to delete and create items from a INamedSubentityListField field in the same service execution context, an error appears in the ServiceObject Commit phase.</p>|
|**51419**|<p>MetadataRuntime 2.2.0: malformed rest api response body when the SystemFiledValidation error is raised</p><p>When you call a Rest API, the error **SysFieldValidationFailed ( 0011605)** appears.</p>|
|**52469**|<p>Navigation of Landing page</p><p>In the Opcenter Modular Manufacturing Home page, when you click any tile and then click the back button of the browser, an error page appears.</p>|
|**52833**|<p>Label should be aligned with switch control "All Operations"</p><p>In the **Operations** tab of the **Work Order Details** page, the label alignment of the **Operation History** section should be vertical with switch control.</p>|
|**53731**|<p>Integer values in the Build Details tab for PO are not populated in read mode</p><p>If you modify and save the numeric properties of a print group , the values are not displayed.</p><p>When you select another print group and then switch  back to the first one, the numeric properties are correctly displayed.</p>|
|**53732**|<p>If I fill all the fields in all the Print Group Definition tabs, an error is returned</p><p>In the **Production Orders** page, when you create  or modify a production order and fill all fields in all tabs, an error message appears.</p>|
<!-- ## **Attachments:**
![](known-technical-issues\_132566104.002.png) [image2022-3-4_17-33-8.png](C:\Users\anil.birajdar\Desktop\confl\ModMOM\attachments\132566104\139063320.png) (image/png)  -->


