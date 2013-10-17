---
layout: docs
title: Design Principles
permalink: /principles/
categories: server
tags: [spec, api, standards]
comments: true
---

### PUSH not pull
The alerter *WILL NOT* use a central polling mechanism for alert collection (aka nagios, zabbix) because naive polling (ie. polling for each and every metric value) does not scale.

### Decouple alert generation from collection and presentation 

Alerts CAN be gathered by individual components for each alert type however these components do not send alerts directly to the monitoring server but instead publish the results onto a message queue that the monitoring server(s) subscribes to. This allows us to scale alert generation and presentation independently.

### Zero conf

Low admin overhead can be achieved by designing the presentation layer so that it requires little, if any, configuration. The console should easily accept alerts from different sources. As long as the alerts being sent conform to the alert standard and use well-known filter categories the alerts should appear automatically.

### Alert status, timeouts & repeats

All alerts should have a corresponding `Clear` or `Normal` state so that non-normal alerts can be automatically cleared down by the system. An alert is uniquely identified by the combination of the environment, resource and event name. A resource can be anything.
  
Where an alert cannot send a corresponding clear an alert timeout can be defined or a default timeout will be applied.  

Alerts are resent if they are still active which means if all data is lost after a certain amount of time (eg. 2 hours?) you are back to where you were. This will be generally true, however, for some alert sources this isn't possible eg. SNMP traps, log errors (if we decide to monitor logs)

