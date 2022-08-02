---
title: " Introduction of OCMOD Documentation"
weight: 3
---
<!-- 1. [Modular MOM](c:\users\anil.birajdar\desktop\temp\index.html)
1. [Before You Start](c:\users\anil.birajdar\desktop\temp\Before-You-Start_127740192.html)
# **Modular MOM : Introduction of OCMOD Documentation**  -->
Created by Alvarez Villanueva, Beatriz, last modified on Jun 27, 2022 
## **Opcenter Modular Manufacturing documentation spaces**
There are 2 documentation spaces of Modular MOM:

- [momwiki02 ](https://momwiki02.industrysoftware.automation.siemens.com/display/RevMOM/Modular+MOM+2)- Internal Documentation: This space is populated by all Feature team members. Internal documentation is meant to be used as knowledge exchange among teams and cannot be published. 
  (Structure and organization are in progress).
- [momwiki01 ](https://momwiki01.industrysoftware.automation.siemens.com/display/ModMOM/Opcenter+Modular+Manufacturing+Documentation+Home)- User Documentation: This space is updated by the Documentation referent with the collaboration of feature team members, and contains the following official Opcenter Modeler Manufacturing manuals currently released for the version 2204: 
  - [**Release Notes**](https://momwiki01.industrysoftware.automation.siemens.com/display/ModMOM/Opcenter+Modular+Manufacturing+Release+Notes): It is the first manual a user should read because it briefly describe what we provide, the limitations, the available documentation
  - [**Security Concept**](https://momwiki01.industrysoftware.automation.siemens.com/display/ModMOM/Opcenter+Modular+Manufacturing+Security+Concept): Provides a set of concepts, best practices, and practical configuration settings to address security risks and threats.
  - [**User Manual**](https://momwiki01.industrysoftware.automation.siemens.com/display/ModMOM/Opcenter+Modular+Manufacturing+User+Manual): It describes how to use the UI and to guide the user to completely use the product following the production process.
  - [**Integration Guide**](https://momwiki01.industrysoftware.automation.siemens.com/display/ModMOM/Opcenter+Modular+Manufacturing+Integration+Guide): Describes how to integrate external systems with Opcenter Modular Manufacturing and how to perform specific manufacturing operations by using the systems. 

You need to have access in both doc spaces, just check if the **Edit** button is visible.

![](Introduction-of-OCMOD-Documentation\_158371113.002.png)

If not, contact;

- for momwiki01 space: **Bea** Álvarez (beatriz.alvarez@[siemens.com](http://siemens.com)) 
- for momwiki02 space:
  - Platfom: [Khairnar, Prashant](https://momwiki02.industrysoftware.automation.siemens.com/display/~prashant.khairnar) 
  - MES: [Napelyani , Amir](https://momwiki02.industrysoftware.automation.siemens.com/display/~amir.napelyani) 
## **Documentation process**
For quality reasons, any internal or user documentation page must meet the requirements explained in [User Story - Definition of Done (DoD)](https://momwiki02.industrysoftware.automation.siemens.com/pages/viewpage.action?pageId=127742703):

- Internal Documentation ([wiki02](https://momwiki02.industrysoftware.automation.siemens.com/display/RevMOM/Welcome+Modular+MOM+wiki)) is created/updated with the correct details (by Development Teams). In particular, the following points should be taken into account
  - For B2MML schema changes: the default values and the mapping should be also provided (also with an example)
  - For data model changes: the datatype along with the size, the default values, and optional/mandatory options should be provided
  - For the API: the behavior, the input and the output parameters, and the error codes should be provided (also with and example)
  - Messages
- User Documentation ([wiki01](https://momwiki01.industrysoftware.automation.siemens.com/display/ModMOM/Opcenter+Modular+Manufacturing+Documentation+Home)):
  - Create/Update documentation with correct details (by Development Teams)
  - Review documentation (by Documentation Referent)
  - Validate documentation :
    - by  Product Managers, Product Owners, and/or Architects Community in case of new documents or existing documents that have been consistently updated.
    - by Development Team members in case of specific document updates.
## **How to manage TFS Documentation items** 

### **User Documentation**
During the sprint phase 2, the User Stories which require user documentation must have the tag  **Documentation**. 

Tip

Any US that contains the label **UX** must also contain the label **Documentation**: interface updates correspond to documentation updates.

Each US contains :

- 1 task **Draft user  documentation** assigned to one development team member. 
- 1 task **Review documentation** assigned to the technical writer (*bea[triz.alvarez@siemens.com*](mailto:triz.alvarez@siemens.com)*) .

![](Introduction-of-OCMOD-Documentation\_158371113.003.png)

In order to close the task, the page must be reviewed:

- by  the Product Owner in case of new pages or existing ones that have been consistently updated.
- by the development team member in case of specific updates.

To better track the documentation tasks and filter the **Review documentation** tasks regardless of the teams ,the following TFS items are assigned to the OCMOD technical writer:

- 1 tag **Doc-activities** ,
- If necessary, the User Story  **Improve usability of user documentation** to collect doc activities not linked to a certain TFS item that implies documentation updates such as proofreading,  align terminology , update code, update images or diagrams, and fix broken links.

For more information regarding Confluence procedures and how-to pages, see [Working with Documentation](https://momwiki02.industrysoftware.automation.siemens.com/display/RevMOM/Working+with+Documentation).

### **Internal Documentation**
During the sprint phase 2, the User Stories which require internal documentation must have a task with title **Internal Documentation** assigned to one team member.

Be aware that technical writers cannot review internal documentation.


Document generated by Confluence on Jul 28, 2022 11:21

[Atlassian](https://www.atlassian.com/)
**Created with an evaluation copy of Aspose.Words. To discover the full versions of our APIs please visit: https://products.aspose.com/words/**
