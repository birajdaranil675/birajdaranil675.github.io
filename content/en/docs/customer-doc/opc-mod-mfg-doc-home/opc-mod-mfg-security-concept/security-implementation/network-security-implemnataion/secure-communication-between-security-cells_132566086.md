---
title: "Secure Communication between Security Cells"
url: 
weight: 3
--- 

**Created by Alvarez Villanueva, Beatriz, last modified on Nov 26, 2021** 



In order to grant network security, the access points to security cells and the communication, among the various access points, must be rendered secure. In this section, we are going to see how this goal can be reached. In many cases, data exchange among components, that are located in different areas, is required for the correct operation of a plant.

The following sections illustrate how to secure communication channels between the cells.

Secure communication between Enterprise and MES Security Cells

The communication between ERP (enterprise) level and MES level must be filtered by using a specific security cell, known as perimeter cell, in order to decouple the plant network from the external network.

Opcenter Modular Manufacturing communications are mainly based on HTTP protocol: therefore, in order to grant a good level of security, it is necessary to configure the HTTPS between the ERP cell and the perimeter cell, as well as the same protocol between the perimeter cell and the MES security cell.

It is mandatory to configure the channels between:

- the Enterprise Security Cell and the Perimeter Security Cell using SSL/TLS with a server certificate
- the Perimeter Security Cell to the MES security Cell using SSL/TLS with a server and client certificate.

To enable secure communication, it is necessary to create an HTTPS protocol binding on the site hosting Opcenter Modular Manufacturing and the Virtual directories, following the relative IIS procedure specified at the following webpage:

<http://www.iis.net/learn/manage/configuring-security/how-to-set-up-ssl-on-iis>

Secure Communication between MES and Process and Control Security Cell

Communication between applications deployed in the MES Security Cell and the Process and Control Security Cell must be established following the guidelines provided by back-end applications. All information required on the Siemens Process and Control system can be found at the following webpage:

<https://new.siemens.com/global/en/products/automation/process-control.html>

Additional notes on MES Security Cell communication

It is highly recommended that you deploy the components related to manufacturing on the same security cell. Furthermore, it is advisable to apply additional countermeasures to increase communication security.

Secure communication with Opcenter Modular Manufacturing database server

The connection between Opcenter Modular Manufacturing applications and the database must be secured following the guidelines provided in the Microsoft SQL Server documentation:

<https://msdn.microsoft.com/en-us/library/bb283235.aspx>

Opcenter Modular Manufacturing must be configured to use SQL Authentication only.

Secure communication between Opcenter Modular Manufacturing application server and an external system

All communication that makes it possible to join Opcenter Modular Manufacturing applications deployed in the Manufacturing network with other external systems must be based on either application secure protocols that guarantee the goals of confidentiality/integrity or alternative secure solutions provided by your IT department (not contemplated in this document).

If Opcenter Modular Manufacturing Clients are located in different geographic areas, you must set up and configure a firewall between your network and the network where the clients are located. In this scenario, Siemens recommends using virtual private networks (VPNs) to protect communications between the different plants from external attacks.

