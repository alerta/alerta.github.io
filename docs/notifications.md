---
layout: docs
title: Notifications
permalink: /notifications/
categories: server
tags: [pagerduty]
---

# External Notifications

Alerta publishes non-repeat alerts to a "notification" topic and a "logger" queue. There are several components that listen for alerts on the topic and one specific component that pulls messages off the queue.

### Topic Listeners
1. mailer - distribution list emails only
2. IRCbot - IRC channel #alerts
3. notify - targeted email and SMS notification

### Queue Listener
1. logger to elasticsearch

Alerts can be easily be forwarded from other element managers or monitoring tools. Proof of concept integrations with tools such as Nagios and HP Operations Manager have been successful.

