---
title: "Main Functionalities"
url: /customer-doc/opc-mod-mfg-release-notes/main-functionalities_132566501/
weight: 2
---

**Created by Alvarez Villanueva, Beatriz, last modified on Apr 26, 2022** 



Opcenter Modular Manufacturing is the next generation of the Opcenter products, aiming to provide a rich collection of modules. The Opcenter Modular Manufacturing modules can be distributed between on-premises and cloud infrastructures to create a hybrid manufacturing operation management (MOM) application.

Overview of Version 2204

Opcenter Modular Manufacturing version 2204 is provided as a set of functionalities for assembly lines and workshops to trace and track work in progress. It is delivered as microservice components.

Main Features

Supported Architecture: 

- Chimera environment with Rancher OS 2.6.2, running on AWS EKS.
- Kubernetes version 1.21.5 with SQL 2019-CU15-ubuntu-20.04

Functionalities:

- All Opcenter Modular Manufacturing components and apps:
  - configurable logging of application behavior
- Access Management
  - manage authentication 
  - Support Authentication via SAM Auth
- Material Modeling
  - Import Material Definitions from B2MML
  - Populate Material Definition during Import Production Order
  - View Material Definitions
- Factory Modeling
  - Populate data through allocate site during Import Production Order
  - Manually create/delete factory data
- Order Management
  - Import Production Order from B2MML - API and UI support
  - View Production Order and Production Order Details
  - Filter Production Order
  - Change PO priority
  - Change PO Quantity
  - Manual/Auto launch of imported Production Order to Work Orders
- Track and Trace
  - View launched work order with operations, material details and history
  - View Operations list
  - Filter Operations in Operations view by Work Unit/Work Order/Product/Product Revision
  - Open Operations in Operator Terminal
  - View Materials for the Operation and Operation history on Operator Terminal
  - View Document URLs for selected Operation
  - View associated document in new tab by clicking document link
  - Collect throughput for selected operation
    - Support to set Standard Collect Quantity for collection for each operation through B2MML
    - Support for Container Validation if Operation is marked as Collect Container option in B2MML 

