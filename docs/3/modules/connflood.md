---
title: Module Details (connflood)
---

## The "connflood" Module

### Description

This module throttles IP addresses which make excessive connections to the server.

### Configuration

To load this module use the following `<module>` tag:

```xml
<module name="connflood">
```

#### `<connflood>`

The `<connflood>` tag defines settings about how the connflood module should behave. This tag can only be defined once.

Name     | Type     | Default Value | Description
-------- | -------- | ------------- | -----------
bootwait | Duration | *None*        | The duration to wait after starting up before connections should be throttled.
maxconns | Number   | *None*        | The maximum number of connections to allow before throttling.
period   | Duration | *None*        | The duration after which the connection counter is reset.
timeout  | Duration | *None*        | The duration to disallow connections for after passing the throttling threshold.
quitmsg  | Text     | *None*        | The message to quit throttled users with.

##### Example Usage

```xml
<connflood bootwait="10s"
           maxconns="3"
           period="30s"
           timeout="30s"
           quitmsg="Throttled">
```
