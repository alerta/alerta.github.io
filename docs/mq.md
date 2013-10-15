---
layout: docs
title: Message Queue
permalink: /mq/
categories: server
tags: [messaging, rabbitmq, activemq, stomp, amqp, kombu]
---

## Alert Message Bus

An integration pattern called a "message bus" utilising publish-subscribe channels is used by alerta because it is asynchronous, loosely-coupled and highly scalable.

The message bus serves as a universal connector between the various monitoring components and as a universal interface for third-party applications that want to connect to alerta.

In order to allow components to integrate easily any system that wants to interface with alerta must conform to the defined [Alert Format](Alert-Format).
