---
title: "Contribute to the Documentation"
url: /how-to-contribute/
weight: 20
---

## 1 Introduction

All MOD MOM documentation is open to the Modular MOM, which means you can make changes and add to it in ways that you see necessary. Do you see that is inaccurate? You can easily help to improve the documentation for the whole Modular MOM!

All the MOD MOM documentation is stored in a [tfs repository](https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/ModMOM_Documentation). With a tfs05mom access, you can edit all existing documentation. You can also write a new how-to on an awesome topic of your choice and submit it.

To work on the documentation in GitHub, use Markdown. For details on this easy-to-use syntax, see the [GitHub Guide to Mastering Markdown](https://guides.github.com/features/mastering-markdown/).

{{% alert color="info" %}}
All documentation contributions may be edited to conform to our internal style guide.
{{% /alert %}}

{{% alert color="info" %}}
**Quick guide to making a documentation change**

1. Fork the **development** branch of the [mod mom / docs](https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/ModMOM_Documentation) repository.
2. Make your changes.
3. Create a pull request with our **development** branch as the base.
{{% /alert %}}

This how-to will teach you how to do the following:

* Add to and edit existing documentation
* Create new documentation

## 2 Prerequisites

Before starting with this how-to, make sure you have completed the following prerequisites(please follow the steps in same order as mentioned):

1. Have [Visual Studio Code](https://code.visualstudio.com)

2. install [node js](https://nodejs.org/en/download/)

3. hugo setup([hugo-setup](/how-to-contribute/hugosetup/))



## 3 Writing New Documentation {#new-documentation}

The sections below present the key steps in writing new documentation for MOD MOM.

### 3.1 Using a Template

To submit a new page to the MOD MOM documentation, start with a documentation template:

* To get the template, click this link : [Template](https://tfs05mom.industrysoftware.automation.siemens.com/MOM/ModularMOM/_git/ModMOM_Documentation?path=%2FTemplate&version=GBmain)
* You can also find this template file in cloned repo in local machine 
### 3.2 Guidelines & Conventions {#naming}

Follow these guidelines and conventions when writing:

* Make sure the document files comply with these naming conventions:
	* Markdown file names should have the same name as the title of the page (for example, if the page is titled "Create Your App," the filename should be `create-your-app.md`)
	* Document file names should always be lower-case with a hyphen (`-`) between each word
	* Do not use spaces or any other symbols in the file name (for example, `&`), as these will not be accepted
* Make sure the image files comply with these naming conventions:
	* Image file names should always be lower-case with a hyphen (`-`) between each word
	* Do not use spaces or any other symbols in the file name (for example, `&`), as these will not be accepted
	* Make sure the image files have names that make sense so it is easy to find them
	* Save the image files in a sub-folder in the **attachments** folder for the category in which the document is located (this sub-folder should have the same name as the document file name you are working on)
	* The following image extensions are allowed: *.png* (preferred), *.jpg*, *.gif*

### 3.3 Submitting Your Work




