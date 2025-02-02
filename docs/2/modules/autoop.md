---
title: Module Details (autoop)
---

## The "autoop" Module

### Description

This module adds channel mode `w` (autoop) which allows channel operators to define an access list which gives status ranks to users on join.

### Configuration

To load this module use the following `<module>` tag:

```xml
<module name="m_autoop.so">
```

This module requires no other configuration.

### Channel Modes

Name   | Character | Type | Parameter Syntax  | Description
------ | --------- | ---- | ----------------- | -----------
autoop | w         | List | `<status>:<mask>` | Grants the &lt;status&gt; rank to users matching &lt;mask&gt; on join.

#### Example Usage

Grants channel operator status on join to users with a mask matching `*!*@example.com`:

```plaintext
/MODE #channel +w o:*!*@example.com
```

Grants channel voice status on join to users logged into the services account named Sadie (requires [the services_account module](/2/modules/services_account)):

```plaintext
/MODE #channel +w v:R:Sadie
```
