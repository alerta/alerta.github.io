---
layout: docs
title: Integrations
permalink: /integrations/
categories: server
tags: [snmp, syslog, nagios, riemann, zabbix, amazon, ganglia, graphite]
---

# Alert Sources

Alerta accepts events from many sources. Some of these are industry standard formats and protocols, others are bespoke sources developed specifically to interface with Alerta. All use the standard alert format and message bus for sending alerts to the cental alert processer.

Alert sources include:

1. SNMP traps (v1 and v2)
2. Syslog (BSD-style and IETF formats)
3. Nagios check API
4. Ganglia bespoke integration
5. command-line tool for scripts
6. RESTful API
7. URL monitor
8. Amazon EC2 instance status

