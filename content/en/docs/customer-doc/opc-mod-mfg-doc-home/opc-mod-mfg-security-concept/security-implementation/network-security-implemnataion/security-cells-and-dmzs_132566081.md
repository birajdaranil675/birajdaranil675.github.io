---
title: "Security Cells and DMZs"
url: /customer-doc/opcenter-modular-manufacturing-documentation-home/opcenter-modular-manufacturing-security-concept/security-implementation/network-security-implemnataion/security-cells-and-dmzs_132566081/
weight: 1
---

**Created by Alvarez Villanueva, Beatriz, last modified on Apr 21, 2022**  

Dividing networks and connected plants into security cells consists in dividing up a large corporate network into separate networks, each used for a specific business function. This strategy increases the availability of the overall system and is an effective way to mitigate security risks. In the implementation of this approach parts of a network, e.g. an IP subnet, are protected by a security appliance and the network is secured by segmentation. Thus, devices within this 'cell' can be protected from unauthorized access from outside without affecting real-time capabilities, performance or other functions.

Security threats that result in failure can thereby be restricted to the immediate vicinity. The different ISA95 levels can be used to identify security cells, for example by keeping ERP (Enterprise Resource Planning) functions separate from MES (Manufacturing Execution System) functions.

{{< figure src="/images/opcenter-security/security-sell-DMZ-1.png" >}}

According to the ISA-95 levels, the following levels can be identified:

- [Enterprise Resource Planning Level](#SecurityCellsandDMZs-ERP_level)
- [Manufacturing Execution Systems Level](#SecurityCellsandDMZs-MES_level)
- [Manufacturing Control Systems Level](#SecurityCellsandDMZs-MCS_level)

Each level includes one or more networks. In addition, we identify also [perimeter networks](#SecurityCellsandDMZs-perimeter_network).

When creating security cells, you should follow some [design rules](#SecurityCellsandDMZs-design_rules).

In this topic we present also the [example configuration organized in different security cells](#SecurityCellsandDMZs-example_configuration).

Refer to this Siemens website for information on industrial security:

<https://new.siemens.com/global/en/products/automation/topic-areas/industrial-security.html>

Enterprise Resource Planning Level

The Enterprise Resource Planning Level is where the ERP Systems are managed. The network connecting the ERP Systems may need to communicate with both MES and Process Control Systems located in other networks. This network is generally the outermost network used in a plant: as a result, it is the most exposed to potential security risks. For this reason, it is recommended to make this network to connect to other networks via Perimeter Network, instead of direct connection.

Manufacturing Execution System Level

The Manufacturing Execution System Level is where the data exchange among Manufacturing Execution System devices is managed. The network includes MES/MOM servers and can be directly connected to a Process Control Network.

Manufacturing Control System Level

The Manufacturing Control System Level hosts the control-layer software systems, such as generic DNC systems, SIMATIC WinCC or SIMATIC PCS7, and is where the data exchange among Manufacturing Control System devices is managed. Since this network is very close to the field, it is important to keep it as separate as possible from the external networks, to mitigate security risks and to protect the plant production.

Perimeter Network

In addition to the networks listed above, we have also Perimeter Networks in our scenarios, sometimes called DMZs (Demilitarized Zones). These are networks used to isolate certain applications from outside networks, thereby mitigating security risks.

Typically, Web Servers are placed in this network, so that they can collect data from low level networks and, at the same time, they can provide web pages to outer networks (for example an Enterprise Control Network).

If you are planning to connect using the Remote Desktop Service, the Remote Desktop Service Server should be placed in this network.

Design Rules

When designing and implementing a complex network scenario, the following rules should be followed to enhance security:

- all devices and hardware that are used to run production should be physical and located in the Manufacturing Control Systems Network.
- all devices with access to external non-secure networks or that can be accessed from external non-secure networks should be placed in a Perimeter Network.
- all devices that collect data from or provide input to Manufacturing Control Systems Networks, but that could also be disconnected for a certain time, should be placed in a Manufacturing Operations Network.

When creating security cells, you should follow some common guidelines and implementation best practices, such as:

- a security cell is an independent part of the plant.
- all participants inside the cell trust each other.
- access to the security cell is permitted only through clearly-defined access points.
- access points are monitored and access is logged (data traffic, user, hardware).
- all participants of a security cell are directly connected (no bypass to the outside).
- participants with a high network load will be integrated into a security cell to avoid bottlenecks.

Example Configuration with Security Cells

{{< figure src="/images/opcenter-security/security-cell-DMZ-2.jpg" >}}


