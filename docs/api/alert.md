---
layout: default
title: Alert Specification
permalink: /docs/api/alert/
categories: docs
tags: spec
---

### Alert on the Wire

Name | Description | Type
----- | ----------- | ----
id<br>_assigned_ | random UUID | String
environment<br>_mandatory_ | namespace for resource<br>**Example Values:** production, development | String
resource<br>_mandatory_ | the actual resource under alarm. can be anything at all | String
event<br>_mandatory_ | name of event | String
severity<br>_optional_ | event severity<br>**Example Values:**  critical, warning, ok (default ok) | String
correlatedEvents<br>_optional_ | list of events this event should be correlated with | List
services<br>_optional_ | list of affected services | List
group<br>_optional_ | logical grouping of events<br>**Example Values:** Web, Network, Hardware, Security, Application, OS, Database, Performance | String
value<br>_optional_ | event value <br>**Example Values:** 100%, ORA-0600, 55tps | String
text<br>_optional_ | descriptive free-form text | String
tags<br>_optional_ | list of tags <br>**Example Values:** london, paris, newyork | List
attributes<br>_optional_ | list of user-defined key-value pairs <br>**Example Values:** runbook=http://my.wiki.com/%eventname% | Map
origin<br>_assigned_ | auto-generated from User-Agent and Remote Address of client, can be used to allow or deny alert sources via pre-receive hook at server | String
type<br>_optional_ | type of alert, used to categorise alert sources <br>**Example Values:** exceptionAlert, snmptrapAlert, syslogAlert | String
createTime<br>_optional_ | time event was generated in ISO 8601 format | DateTime
timeout<br>_optional_ | time alert is valid for, usually deleted after this period | String
rawData<br>_optional_ | raw data of alert <br>**Example Values:** SNMP trap data or Syslog data | String

{% highlight scala linenos %}
    id: String,
    environment: String,
    resource: String,
    event: String,
    severity: String,
    correlatedEvents: List[String],

    services: List[String],
    group: String,

    value: String,
    text: String,

    tags: List[String],
    attributes: Map[String, String],

    origin: String,
    eventType: String,
    createTime: DateTime,
    timeout: Int,
    rawData: String
{% endhighlight %}