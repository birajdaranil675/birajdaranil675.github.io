---
title: "Metadata Artifacts"
weight: 7
---

**Model:** Model definition artifacts are stored as C# code files. The object model definition and
the business logic could be separated out into different code files for convenience and
naming convention like ‘object_name’ and ‘object_name_logic’ could be employed.

**Configuration:** Model configuration is stored as json based side-car files along with the model
definition artifacts.

**WORKSPACE OVERRIDES**

The concept of Workspace provides an isolation context for the metadata definition. When a
model definition is overridden in the context of a workspace, new artifacts are created with
the overrides and are placed alongside the original artifacts of the model being overridden.
This technique protects the original artifacts from being modified by other workspaces and
avoids conflicting changes.