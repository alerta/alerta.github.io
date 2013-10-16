---
layout: docs
title: Integrations
permalink: /integrations/
categories: server
tags: [snmp, syslog, nagios, riemann, zabbix, amazon, ganglia, graphite]
---

Alerta accepts events from many sources. Some of these are industry standard formats and protocols, others are bespoke sources developed specifically to interface with Alerta. All use the standard alert format and message bus for sending alerts to the cental alert processer.


### Standard Alerta add-ons

* SNMPv1 and SNMPv2 traps
* Syslog (BSD-style, IETF and Cisco)
* URL monitor
* ICMP Ping check

---

### Third-party add-ons:

 * [Riemann](https://github.com/alerta/riemann-alerta)
 * [Nagios](https://github.com/alerta/nagios3-alerta)
 * [Zabbix](https://github.com/alerta/zabbix-alerta)
 * Amazon Cloudwatch

 ---

### User-defined add-ons can be easily developed using:

* alert-sender CLI
* Nagios check wrapper
* RESTful API

Note: Ganglia and Graphite integrates via Riemann.
