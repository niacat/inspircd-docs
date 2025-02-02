---
title: Module Details (httpd_config)
---

## The "httpd_config" Module

### Description

This module allows the server configuration to be viewed over HTTP via the /config path.

### Configuration

To load this module use the following `<module>` tag:

```xml
<module name="httpd_config">
```

This module requires no other configuration.

### Special Notes

Leaking your server configuration over the internet is a privacy and security risk. You should avoid doing this by either configuring [the httpd module](/3/modules/httpd) to only listen for local connections or by using [the httpd_acl module](/3/modules/httpd_acl) to restrict who can view your server configuration.
