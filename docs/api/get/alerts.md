---
layout: default
title: GET /alerts
permalink: /docs/api/get/alerts/
categories: api
tags: rest
comments: true
---

### Resource URL

http://api.alerta.io/v3/alerts?:query

### Parameters

| Paramter | Description |
| -------- | -------- |
| :id<br>_mandatory_| Alert id<br>**Example Values:** bc31f0f7-dec4-4a86-bce0-6e1662a63474|

### Example Request

**GET** `http://api.alerta.io/v3/alerts?environment=production&service=web`

{% highlight json linenos %}
{
}
{% endhighlight %}