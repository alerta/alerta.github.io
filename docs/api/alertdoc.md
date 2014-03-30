---
layout: default
title: Alert Document
permalink: /docs/api/alertdoc/
categories: docs
tags: spec
---

### Alert Document

(as above with additional calculated attributes)

Name | Description | Type
----- | ----------- | ----
status<br>_assigned_ | | String
duplicateCount<br>_assigned_ | | Int
repeat<br>_assigned_ | true or false | Boolean
previousSeverity<br>_assigned_ | | String
trendIndication<br>_assigned_ | trend of alert <br>**Example Values:** moreSevere, lessSevere, noChange | String
receiveTime<br>_assgined_ | ISO 8601 date to milliseconds UTC | DateTime
lastReceiveId<br>_assigned_ | last UUID | String
lastReceiveTime<br>_assigned_ | based on last event if duplicate | DateTime
history<br>_assigned_ | updated | List


{% highlight scala linenos %}

    status: String,
    duplicateCount: Int,
    repeat: Boolean,
    previousSeverity: Option[String],
    trendIndication: Option[String],
    receiveTime: DateTime,
    lastReceiveId: String,
    lastReceiveTime: DateTime,
    history: List[Map[String,String]]
{% endhighlight %}
