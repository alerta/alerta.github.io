---
layout: docs
title: Specification
permalink: /spec/
categories: server
tags: [ rfc5674 ]
---

# ALERT FORMAT

Alerts received and sent by Alerta conform to a common alert format. All components of alerta use this message format and any external systems must produce or consume messages in this format also.

## Alert attributes populated at source

``` html
<table>
  <thead><th>Attribute</th><th>Description</th><th>Optional?</th></thead>
  <tbody>
    <tr><td><code>id</code></td><td>a random UUID that is globally unique</td><td>No</td></tr>
    <tr><td><code>correlatedEvents</code></td><td>list of related event names</td><td>Yes</td></tr>
    <tr><td><code>createTime</code></td><td>UTC date and time the alert was generated in <a href='http://en.wikipedia.org/wiki/ISO_8601'>ISO 8601</a> format</td><td>No</td></tr>
    <tr><td><code>environment</td><td>list of effected environments, used to namespace the defined resource</td><td>No</td></tr>
    <tr><td><code>event</td><td>event name eg. NodeDown, QUEUE:LENGTH:EXCEEDED, AppStatus</td><td>No</td></tr>
    <tr><td><code>graphUrls</td><td>list of URLs to relevant graphs</td><td>Yes</td></tr>
    <tr><td><code>group</td><td>event group</td><td>No</td></tr>
    <tr><td><code>moreInfo</td><td>a URL to a run book, wiki or ticketing system</td><td>Yes</td></tr>
    <tr><td><code>origin</td><td>name of monitoring component that generated the alert</td><td>No</td></tr>
    <tr><td><code>rawData</code></td><td>unprocessed data eg. full syslog message or SNMP trap</td><td>Yes</td></tr>
    <tr><td><code>resource</code></td><td>the resource under alarm, deliberately not host-centric</td><td>No</td></tr>
    <tr><td><code>service</code></td><td>list of effected services</td><td>No</td></tr>
    <tr><td><code>severity</code></td><td>one of Critical, Major, Minor, Warning, Normal, Inform, Debug     See RFC 5674 (Ref [1])<br><table>
  <thead><th>Severity</th><th>Severity Code</th></thead>
  <tbody>
    <tr><td><code>CRITICAL</code></td><td>1</td></tr>
    <tr><td><code>MAJOR</code></td><td>2</td></tr>
    <tr><td><code>MINOR</code></td><td>3</td></tr>
    <tr><td><code>WARNING</code></td><td>4</td></tr>
    <tr><td><code>INDETERMINATE</code></td><td>5</td></tr>
    <tr><td><code>CLEARED</code></td><td>5</td></tr>
    <tr><td><code>NORMAL</code></td><td>5</td></tr>
    <tr><td><code>INFORM</code></td><td>6</td></tr>
    <tr><td><code>DEBUG</code></td><td>7</td></tr>
    <tr><td><code>AUTH</code></td><td>8</td></tr>
    <tr><td><code>UNKNOWN</code></td><td>9</td></tr>
  </tbody>
</table></td><td>No</td></tr>
    <tr><td><code>summary</code></td><td>shortened text suitable for a pager, email subject or SMS message</td><td>No</td></tr>
    <tr><td><code>tags</code></td><td>list of tags in any format eg. "aTag", "aDouble:Tag", "a:Triple=Tag"</td><td>Yes</td></tr>
    <tr><td><code>text</code></td><td>free text</td><td>No</td></tr>
    <tr><td><code>thresholdInfo</code></td><td>threshold rule that triggered the alert</td><td>Yes</td></tr>
    <tr><td><code>timeout</code></td><td>number of seconds before alert is deleted from database</td><td>Yes</td></tr>
    <tr><td><code>type</code></td><td>alert type eg. snmptrapAlert, syslogAlert, gangliaAlert</td><td>No</td></tr>
    <tr><td><code>value</code></td><td>event value eg. 100%, Down, PingFail, 55ms, ORA-1664</td><td>No</td></tr>
  </tbody>
</table>

## Alert attributes added by Alerta server daemon

<table>
  <thead><th>Attribute</th><th>Description</th></thead>
  <tbody>
    <tr><td><code>duplicateCount</code></td><td>a count of the number of times this event has been received for a resource</td></tr>
    <tr><td><code>expireTime</code></td><td>calculated by adding the timeout to the receiveTime</td></tr>
    <tr><td><code>history</code></td><td>whenever an alert changes severity then a list of key alert attributes are kept in the history log<br><table><tr><td><code>createTime</code></td></tr><tr><td><code>event</code></td></tr><tr><td><code>id</code></td></tr><tr><td><code>receiveTime</code></td></tr><tr><td><code>severity</code></td></tr><tr><td><code>severityCode</code></td></tr><tr><td><code>text</code></td></tr><tr><td><code>value</code></td></tr></table></td></tr>
    <tr><td><code>lastReceiveId</code></td><td>the last alert id received for this event</td></tr>
    <tr><td><code>lastReceiveTime</code></td><td>the last time this alert was received. only different to receiveTime if the alert is a duplicate</td></tr>
    <tr><td><code>previousSeverity</code></td><td>the previous severity of the same event for this resource.<br> if no event or correlatedEvent exists in the database for this resource then it will be <code>UNKNOWN</code></td></tr>
    <tr><td><code>receiveTime</code></td><td>UTC date and time the alert was received by the Alerta server daemon</td></tr>
    <tr><td><code>repeat</code></td><td>if duplicateCount is 0 or the alert status has changed then repeat is False, otherwise it is True</td></tr>
    <tr><td><code>status</code></td><td>one of <code>open</code>, <code>ack</code>, <code>closed</code>, or <code>expired</code></td></tr>
    <tr><td><code>trendIndication</code></td><td>based on <code>severity</code> and <code>previousSeverity</code> will be one of <code>moreSevere</code>, <code>lessSevere</code> or <code>noChange</code></td></tr>
  </tbody>
</table>
```

## Example Alert

```json
{
    "origin": "alert-urlmon/devmonsvr01", 
    "group": "Web", 
    "severity": "NORMAL", 
    "service": [
        "R2"
    ], 
    "tags": [
        "location:eu-west-1a", 
        "cluster:guweb"
    ], 
    "text": "HTTP server responded with status code 200 in 566ms", 
    "createTime": "2012-10-01T15:01:54.016Z", 
    "value": "OK (200)", 
    "event": "HttpResponseOK", 
    "environment": [
        "PROD", 
        "INFRA"
    ], 
    "severityCode": 5, 
    "timeout": 86400, 
    "resource": "http://www.guardian.co.uk", 
    "correlatedEvents": [
        "HttpConnectionError", 
        "HttpServerError", 
        "HttpClientError", 
        "HttpRedirectionError", 
        "HttpContentError", 
        "HttpResponseSlow", 
        "HttpResponseOK"
    ], 
    "summary": "PROD,INFRA - NORMAL HttpResponseOK is OK (200) on R2 http://www.guardian.co.uk",
    "thresholdInfo" : "http://www.guardian.co.uk/ : RT > 2000 RT > 5000 x 2",
    "type": "serviceAlert", 
    "id": "081bf132-481d-4b37-8459-5fe87dd8dee0"
}
```

### References

1. [RFC5674](http://tools.ietf.org/html/rfc5674#section-2)
