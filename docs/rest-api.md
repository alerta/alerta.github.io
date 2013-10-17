---
layout: docs
title: REST API
permalink: /rest-api/
categories: server
tags: [rest, api, json, jsonp, callback, http, curl]
---

# Alerta REST API

The Alerta REST API is how the alert console interfaces with the alert database. It can also be used by any system that can make an HTTP request to get a list of alerts, create, modify or delete alerts. The API supports the HTTP methods `GET`, `PUT`, `POST`, and `DELETE` (or `POST` with posted data of `{ _method: delete }`).

**NOTE: Currently there is no authentication. Web server basic authentication can be used if required.**

## JSONP Callbacks

All requests support a `callback` parameter so that responses can be output in JSONP format.

## Get an alert
`GET /alerta/api/v2/alerts/alert/{id}`

### Request
```json
Nothing
```

### Response
```json
{
    "response": {
        "alert": {
            "createTime": "2012-10-03T21:49:17.000Z", 
            "duplicateCount": 4, 
            "environment": [
                "REL", 
                "QA"
            ], 
            "event": "HostAvail", 
            "expireTime": "2012-10-04T21:54:40.051Z", 
            "group": "Network", 
            "history": [
                {
                    "createTime": "2012-10-03T21:49:17.000Z", 
                    "event": "HostAvail1", 
                    "id": "2a85caa4-1a24-4f1b-acc8-d7de48c8006f", 
                    "receiveTime": "2012-10-03T21:54:07.300Z", 
                    "severity": "MAJOR", 
                    "severityCode": 2, 
                    "text": "Host is not responding to ping", 
                    "value": "Down"
                }, 
                {
                    "status": "OPEN", 
                    "updateTime": "2012-10-03T21:54:07.309Z"
                }
            ], 
            "id": "2a85caa4-1a24-4f1b-acc8-d7de48c8006f", 
            "lastReceiveId": "f092f927-b264-4105-96ab-993aae58c547", 
            "lastReceiveTime": "2012-10-03T21:54:40.067Z", 
            "origin": "alert-api/devmonsvr01", 
            "previousSeverity": "UNKNOWN", 
            "receiveTime": "2012-10-03T21:54:07.300Z", 
            "repeat": true, 
            "resource": "host5", 
            "service": [
                "SharedSvcs"
            ], 
            "severity": "MAJOR", 
            "severityCode": 2, 
            "status": "OPEN", 
            "summary": "REL,QA - MAJOR HostAvail1 is Down on SharedSvcs host5", 
            "tags": [
                "location=London", 
                "region=EU"
            ], 
            "text": "Host is not responding to ping", 
            "timeout": 86400, 
            "type": "exceptionAlert", 
            "value": "Down"
        }, 
        "localTime": "2012-10-03T23:05:04", 
        "status": "ok", 
        "time": "0.010", 
        "total": 1, 
        "warning": "This is the development server. For testing purposes only."
    }
}
```

### Example

`curl 'http://monitoring.guprod.gnl/alerta/api/v2/alerts/alert/9350eee8-7649-43b0-ae02-d69ffeadec31' | python -mjson.tool`

## Get a list of alerts
`GET /alerta/api/v2/alerts?{query}{hide-alert-details=true}{hide-alert-repeats=true}{hide-alert-history=true}{limit=#}{from-date=isoformat}{sort-by=field}`

### Request
```json
Nothing
```

### Response
```json
{
    "response": {
        "alerts": {
                "alertDetails": [
                    {
                       "id": "ffeab578-37c9-4023-970d-491dbb7c469b", 
                        ...
                    }, 
                    {
                        "id": "4f914ae5-a591-4c77-b32a-33058775f565", 
                        ...
                    }
                ], 
            "severityCounts": {
                "critical": 1, 
                "debug": 0, 
                "inform": 0, 
                "major": 1, 
                "minor": 5, 
                "normal": 6403, 
                "warning": 9
            }, 
            "statusCounts": {
                "ack": 34, 
                "closed": 5064, 
                "open": 16
            }
        }, 
        "localTime": "2012-10-01T17:17:16", 
        "status": "ok", 
        "time": "0.457", 
        "total": 6520
    }
}
```

### Example

`curl 'http://monitoring.guprod.gnl/alerta/api/v2/alerts?environment=PROD&group=OS&group=Puppet'`

## Create an alert
`POST /alerta/api/v2/alerts/alert.json`

### Request
```json
{
    "correlatedEvents": [
        "event1", 
        "event2"
    ], 
    "createTime": "2012-06-27T14:55:07.196Z", 
    "event": "event1", 
    "environment": "REL", 
    "group": "group", 
    "origin": "curl/myhost", 
    "resource": "res1", 
    "service": "R1", 
    "severity": "MAJOR", 
    "severityCode": 2, 
    "summary": "REL - MAJOR event1 is val100 on R1 res1", 
    "tags": [
        "tag1", 
        "tag=2"
    ], 
    "text": "text message goes here", 
    "thresholdInfo": "n/a", 
    "type": "apiAlert", 
    "value": "val100", 
}
```

### Response
```json
{
    "response": {
        "id": "82171a5a-cb72-47d9-92fc-3d7048a92e2c", 
        "localTime": "2012-06-27T15:50:54", 
        "status": "ok", 
        "time": "0.006"
    }
}
```

### Example
`curl -XPOST http://api.alerta.io/alerta/api/v2/alerts/alert.json -d`  

```json
{  
    "resource": "host5",  
    "event": "HostAvail",  
    "group": "Network",  
    "value": "Down",  
    "severity": "Critical",  
    "environment": "REL",  
    "service": "SharedSvcs",  
    "tags": [  
        "location=London",  
        "region=EU"  
    ],  
    "text": "Host is not responding to ping"  
}
```

## Modify an alert
`PUT /alerta/api/v2/alerts/alert/{id}`

### Request
```json
{ attribute: 'value' }
```

### Response
```json
{
    "response": {
        "localTime": "2012-10-01T17:21:52", 
        "status": "ok", 
        "time": "0.007"
    }
}
```

### Example
`curl -XPUT http://monitoring.guprod.gnl/alerta/api/v2/alerts/alert/f0130da3-f2d8-4525-9533-5850cfa19a12 -d '{ "status": "ACK" }'`

## Delete an alert
`DELETE /alerta/api/v2/alerts/alert/{id}`

`POST /alerta/api/v2/alerts/alert/{id}`

### Request
Only required if `POST` method is used.

```json
{ "_method": "delete" }
```

### Response
```json
{
    "response": {
        "status": "failed"
    }
}
```

### Example
`curl  -XDELETE http://api.alerta.io/alerta/api/v2/alerts/alert/8ea232ef-3b2d-4e8e-9ec7-e3ae67b4d695`


