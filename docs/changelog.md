---
layout: docs
title: Changelog
permalink: /docs/changelog/
categories: home
tags: []
featured: true
---

### Version 3.0.3 (not tagged yet)

<ul>
  <li>sundry bug fixes to alert console and other components</li>
</ul>

### Version 3.0.2

<ul>
  <li>add support for detailed alert history queries</li>
  <li>retire alert-query, alert-sender and alert-checker (use unified command-line tool instead)</li>
</ul>

### Version 3.0.1

<ul>
  <li>package in virtualenv, build as RPM using teamcity and deploy via RiffRaff</li>
</ul>

### Version 3.0.0

<ul>
  <li>message queue is no longer a direct dependency because the
  alert publishers send alerts to HTTP API, not message queue. This makes
  the Message queue optional. ie. it's only needed by alert subscribers</li>
  <li>message queue transport is now AMQP, not STOMP, which means that any backend that supports AMQP can be used. RabbitMQ is the obvious candidate however MongoDB and Redis have both been tested and work
  <li>alerta server daemon has been merged into the alerta API to create a new alerta "app" which runs either stand-alone or as a WSGI application</li>
  <li>if the message queue is configured then the alerta "app" publishes alerts to a "fan out" topic. if message persistence is required then create a queue that listens to the topic and read from the queue</li>
  <li>the alert API has changed significantly - both the alert format and the URL endpoints - to be less perscriptive and more extensible. eg. "thresholdInfo" and other less-used attributes have been removed but a new attribute for arbitrary key-value pairs has been added called "attributes"</li>
  <li>similarly, the heartbeat API has changed to make it less prescriptive and more extensible. eg. the "version" attribute has been replaced with a "tags" attribute that takes an arbitrary list of values, one of which can be a version number, if desired</li>
  <li>the command-line tools included in the main repository have been deprecated and will be replaced with unified CLI tools available on GitHub <a href="https://github.com/alerta/python-alerta-client">python-alerta-client</a> repo or can be installed via Pypi using <code>pip install alerta-client</code>
</ul>
