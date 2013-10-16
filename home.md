---
layout: docs
title: Overview
permalink: /home/
categories: general
tags: [intro]
---

Alerta is distributed, scalable, extensible monitoring system that accepts alerts from any source and can forward alerts to any destination.

Alerta is written in python and has been open-sourced under the Apache Software Foundation License v2.0.

* [Design Principles](wiki/Design-Principles) - overview of why alerta is the way it is
* [Alert Sources](wiki/Alert-Sources) - SNMP, Syslog, Nagios checks, Ganglia metrics, scripts and more
* [Message Bus](wiki/Alert-Message-Bus) - all alerts are published to a shared message bus, that way anything can listen for alerts
* [Alerta](wiki/Alerta-Server) - server daemon that pulls alerts off the message bus and pushes them out onto the notification topic and logger queue
* [Alert Console](wiki/Alert-Console) - the 'at-a-glance' web-based GUI for alert visualisation
* [External Notifications](wiki/External-Notifications) - IRC, email, elasticsearch and others
* [Simple Event Correlation](wiki/Simple-Event-Correlation) - how to get one alert to clear another alert
* [Alert Format](wiki/Alert-Format) - all components must understand the same JSON-encoded alert format
* [Alerta REST API](wiki/Alerta-REST-API) - the RESTful API can be used for submitting, updating and querying for alerts
* [FAQ](wiki/Alerta-FAQ) - ask a question or find an answer
* [Roadmap](wiki/Alerta-Roadmap) - what's missing and what's coming soon


