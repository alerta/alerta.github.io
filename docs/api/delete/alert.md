---
layout: default
title: DELETE /alert/:id
permalink: /docs/api/delete/alert/
categories: delete
tags: rest
comments: true
---

### Resource URL

http://api.alerta.io/v3/alert

### Parameters

| Paramter | Description |
| -------- | -------- |
| :id<br>_mandatory_| Alert id<br>**Example Values:** bc31f0f7-dec4-4a86-bce0-6e1662a63474|

### Example Request

**GET** `http://api.alerta.io/v3/alert/bc31f0f7-dec4-4a86-bce0-6e1662a63474`

{% highlight json linenos %}
{
  "response": {
    "alert": {
      "history": [
        {}
      ],
      "lastReceiveTime": "2014-03-01T18:05:38.931Z",
      "lastReceiveId": "bc31f0f7-dec4-4a86-bce0-6e1662a63474",
      "receiveTime": "2014-03-01T18:05:38.931Z",
      "trendIndication": null,
      "previousSeverity": null,
      "repeat": false,
      "duplicateCount": 0,
      "status": "open",
      "rawData": "raw data goes here",
      "group": "Web",
      "services": [
        "foo",
        "bar",
        "baz"
      ],
      "correlatedEvents": [
        "NodeDown",
        "NodeUp"
      ],
      "severity": "major",
      "event": "NodeDown",
      "resource": "host77",
      "environment": "release",
      "id": "bc31f0f7-dec4-4a86-bce0-6e1662a63474",
      "value": "110%",
      "text": "Starý kôň na hŕbe kníh žuje tíško povädnuté ruže, na stĺpe sa ďateľ učí kvákať novú ódu o živote.",
      "tags": [
        "cat",
        "dog",
        "bird"
      ],
      "attributes": {
        "graphUrl": "http://example.com",
        "moreInfo": "run book",
        "thresholdInfo": "too high"
      },
      "origin": "curl/7.30.0@0:0:0:0:0:0:0:1",
      "type": "httpAlert",
      "createTime": "2014-11-11T12:00:00.456Z",
      "timeout": 123456
    },
    "total": 1,
    "status": "ok"
  }
{% endhighlight %}