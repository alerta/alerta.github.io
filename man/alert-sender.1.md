---
layout: manpage
title: alert-sender(1)
permalink: /alert-sender1/
categories: manpage
tags: [man1]
---

## NAME
`alert-sender` -- sends alerts to alerta server

## SYNOPSIS
`alert-sender` [`-h`] [`-c` _FILE_] [`-r` _RESOURCE_] [`-e` _EVENT_] [`-C` _CORRELATE_]  
               [`-g` _GROUP_] [`-v` _VALUE_] [`--status` _STATUS_] [`-s` _SEVERITY_]  
               [`-E` _ENV_] [`-S` _SERVICE_] [`-T` _TAGS_] [`-t` _TEXT_] [`--summary` _TEXT_]  
               [`--more` _TEXT_] [`--graphs` _URLS_] [`-o` _TIMEOUT_]  
               [`--type` _EVENT_`_`_TYPE_] [`-H`] [`-O` _ORIGIN_] [`-q`] [`-d`] [`--version`]  
               [`--debug`] [`--verbose`] [`--log-dir` _DIR_] [`--log-file` _FILE_]  
               [`--pid-dir` _DIR_] [`--use-syslog`] [`--use-stderr`]  
               [`--yaml-config` _FILE_] [`--show-settings`]

## DESCRIPTION


## OPTIONS
The following options are available:

* `-r` _RESOURCE_, `--resource` _RESOURCE_  
    Resource under alarm eg. hostname, network device, application, web address.

* `-e` _EVENT_, `--event` _EVENT_  
    Event name eg. *NodeDown*, *QUEUE:LENGTH:EXCEEDED*, *coldStart*, *LOG_ERROR*

* `-C` _CORRELATE_, `--correlate` _CORRELATE_  
    List of events to correlate together eg. *node_up* and *node_down*

* `-g` _GROUP_, `--group` _GROUP_  
    Event group eg. Application, Backup, Database, HA, Hardware, Job, Network, OS, Performance, Security

* `-v` _VALUE_, `--value` _VALUE_  
    Event value eg. *100%*, *122ms*, *PingFail*, *55tps*, *ORA-1664*

* `--status` _STATUS_  
    Status eg. Open, Ack, Closed, Unknown (default: Unknown)

* `-s` _SEVERITY_, `--severity` _SEVERITY_  
    Severity eg. Critical, Major, Minor, Warning, Normal, Informational, Debug (default: Normal)

* `-E` _ENV_, `--environment` _ENV_  
    List of effected environments eg. PROD, REL, QA, TEST, CODE, STAGE, DEV, INFRA

* `-S` _SERVICE_, `--svc` _SERVICE_, `--service` _SERVICE_  
    List of effected services eg. R1, R2, Frontend, Discussion, ContentAPI, MicroApp, FlexibleContent, Identity, Mobile, Soulmates, Network, SharedSvcs

* `-T` _TAGS_, `--tag` _TAGS_  
    Tag the event with anything and everything.

* `-t` _TEXT_, `--text` _TEXT_  
    Freeform alert text eg. Host not responding to ping.

* `--summary` _TEXT_  
    Summary text suitable for SMS, pager or email subject.

* `--more` _TEXT_  
    More information eg. a link to a Wiki, ticket number or call reference.

* `--graphs` _URLS_  
    List of graph URLs.

* `-o` _TIMEOUT_, `--timeout` _TIMEOUT_  
    Timeout in seconds that OPEN alert will persist in webapp.

* `--type` _EVENT_`_`_TYPE_  
    Event type eg. exceptionAlert, serviceAlert

* `-H`, `--heartbeat`  
    Send heartbeat to server.

* `-O` _ORIGIN_, `--origin` _ORIGIN_  
    Origin of heartbeat. Usually an application instance.

* `-q`, `--quiet`  
    Do not display assigned alert id.

* `-d`, `--dry-run`  
    Do not send alert. Output as Curl.

## EXIT STATUS

The `grep` utility exits with one of the following values:

```
0        One or more lines were selected.  
1        No lines were selected.  
>1       An error occurred.
```

## EXAMPLES


## ENVIRONMENT

ALERTA_CONF

## FILES

`/etc/alerta/alerta.conf`

## STANDARDS
## NOTES

## BUGS

Report bugs to github issues.

## SEE ALSO

[`alerta.conf(5)`](/man/alerta-conf5/)