---
title: "Assignment of Roles to Users and User Groups"
url: 
weight: 1
---

**Created by Alvarez Villanueva, Beatriz, last modified on Dec 02, 2021**  


All MES data and related functionalities must be exposed in conditions that do not present problems regarding security. Systems or people that need to access the functionalities must be authenticated and authorized.

*Authentication* means that the system knows the identity of the external system or user that is going to access some functionalities. In the case of users, the typical user credentials are user name and password. The user accesses the system providing these credentials: if authentication is successful, the user is granted access.

*Authorization* defines the actions that authenticated users/systems can perform in the system. A typical way to implement authorization is by defining groups and roles that summarize the rights a user can have for system resources.

Authentication

In enterprise environments, there is a growing need to guarantee a high level of interoperability among the various systems making up the enterprise itself, without neglecting important qualitative attributes, such as security.

The excerpt from *A Guide to Claims-Based Identity and Access Control (2nd Edition)* at <http://msdn.microsoft.com/en-us/library/hh446528.aspx> illustrates that MES/MOM service applications (based on REST - REpresentational State Transfer) are typically consumed in a "session-less" flow and each request is an independent operation.

No session cookies are handled within this type of communication because there is no concept of a sequence of operations.

Typically, Web Services expect each request to provide the necessary authentication details and treat them in two possible ways:

- **Unauthorized requests** are rejected and trigger a response with HTTP code 401 containing one or more WWW-Authenticate headers, each specifying the details of the required authorization scheme and realm. Clients must analyze these headers to understand how to obtain a token to be included in a valid request.
- **Authorized requests** carry the authorization header containing the authentication token issued by the Identity Provider STS.

Opcenter Modular Manufacturing leverages external Identity provider for authentication needs and implements model-driven role-based authorization through Access Management app. OCMOD SaaS offering leverages Siemens Xcelerator Cloud Service ‘SAM Auth’ for User Identity Management and Authentication needs.

Authorization

Opcenter Modular Manufacturing provides only the administrative roles by default. You must define the roles according to you needs. It is recommended to create the roles following the concept of least privilege.

If you are correctly authenticated in the system, but do not possess the necessary privileges to perform a particular action, the system rejects your attempt to perform the operation, triggering a response with HTTP code 403 Forbidden.


