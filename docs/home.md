---
layout: docs
title: Documentation
permalink: /home/
categories: introduction
tags: [docs]
featured: true
---

Alerta is distributed, scalable, extensible monitoring system that accepts alerts from any source and can forward alerts to any destination.

Alerta is written in python and has been open-sourced under the Apache Software Foundation License v2.0.

* [Design Principles](/docs/principles) - overview of why alerta is the way it is
* [Alert Sources](/docs/integrations/) - SNMP, Syslog, Nagios checks, Ganglia metrics, scripts and more
* [Message Bus](/docs/mq/) - all alerts are published to a shared message bus, that way anything can listen for alerts
* [Alerta](wiki/Alerta-Server) - server daemon that pulls alerts off the message bus and pushes them out onto the notification topic and logger queue
* [Alert Console](/docs/console-v2/) - the 'at-a-glance' web-based GUI for alert visualisation
* [External Notifications](/docs/notifications/) - IRC, email, elasticsearch and others
* [Simple Event Correlation](/docs/correlation/) - how to get one alert to clear another alert
* [Alert Format](/docs/specification/) - all components must understand the same JSON-encoded alert format
* [Alerta REST API](/docs/rest-api/) - the RESTful API can be used for submitting, updating and querying for alerts
* [FAQ](/docs/faq/) - ask a question or find an answer
* [Roadmap](/docs/roadmap/) - what's missing and what's coming soon
