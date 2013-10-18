---
layout: manpage
title: alert-query(1)
permalink: /alert-query1/
categories: manpage
tags: [man1]
---

## NAME
`alert-query` -- queries alert server for alerts

## SYNOPSIS
`alert-query` [`-h`] [`-c` _FILE_] [`--minutes` _MINUTES_] [`--hours` _HOURS_]  
                   [`--days` _DAYS_] [`-i` _ALERTID_] [`-E` _ENV_] [`--not-environment` _ENV_]  
                   [`-S` _SERVICE_] [`--not-service` _SERVICE_] [`-r` _RESOURCE_]  
                   [`--not-resource` _RESOURCE_] [`-s` _SEVERITY_]  
                   [`--not-severity` _SEVERITY_] [`--status` _STATUS_]  
                   [`--not-status` _STATUS_] [`-e` _EVENT_] [`--not-event` _EVENT_]  
                   [`-g` _GROUP_] [`--not-group` _GROUP_] [`--origin` _ORIGIN_]  
                   [`--not-origin` _ORIGIN_] [`-v` _VALUE_] [`--not-value` _VALUE_]  
                   [`-T` TAGS] [`--not-tags` _TAGS_] [`-t` _TEXT_] [`--not-text` _TEXT_]  
                   [`--type` _EVENT_`_`_TYPE_] [`--not-type` TYPE]  
                   [`--repeat` {true,false}] [`--show` _SHOW_] [`--oneline`]  
                   [`--date` _DATE_] [`--format` _FORMAT_] [`-o` _SORTBY_] [`-w`]  
                   [`-n` _INTERVAL_] [`--count` _LIMIT_] [`-q` _QUERY_] [`--no-header`]  
                   [`--no-footer`] [`-G`] [`--output` _OUTPUT_] [`-j`] [`-X`] [`-d`]  
                   [`--version`] [`--debug`] [`--verbose`] [`--log-dir` _DIR_]  
                   [`--log-file` _FILE_] [`--pid-dir` _DIR_] [`--use-syslog`]  
                   [`--use-stderr`] [`--yaml-config` _FILE_] [`--show-settings`]


## DESCRIPTION
Displays the latest alerts received by the `alerta` server. One alert is shown per line unless `--show` is specified to display more details or `--output` is specified to display alerts in raw JSON format.


## OPTIONS
List all alerts received optionally filtered by attributes. Sorts alerts in reverse chronological order unless `--sort-by` is specified.

* `--minutes` _MINUTES_, `--mins` _MINUTES_  
     Show alerts for last _MINUTES_ minutes

* `--hours` _HOURS_, `--hrs` _HOURS_  
     Show alerts for last _HOURS_ hours

* `--days` _DAYS_  
     Show alerts for last _DAYS_ days

* `-i` _ALERTID_, `--id` _ALERTID_  
     Alert ID (can use 8-char abbreviated id)

* `-E` _ENV_, `--environment` _ENV_  
     Environment eg. PROD, REL, QA, TEST, CODE, STAGE, DEV, INFRA

* `--not-environment` _ENV_  

* `-S` _SERVICE_, `--svc` _SERVICE_, `--service` _SERVICE_  
     Service eg. R1, R2, Discussion, ContentAPI, Frontend,
     FlexibleContent, Identity, Mobile, Soulmates,
     MicroApp, Mutualisation, SharedSvcs, Network,
     Infrastructure

* `--not-service` _SERVICE_

* `-r` _RESOURCE_, `--resource` _RESOURCE_  
     Resource under alarm eg. hostname, network device, application

* `--not-resource` _RESOURCE_

* `-s` _SEVERITY_, `--severity` _SEVERITY_  
     Severity eg. critical, major, minor, warning, indeterminate, cleared, normal, informational, debug, security, unknown

* `--not-severity` _SEVERITY_

* `--status` _STATUS_  
     Status eg. open, ack, closed, expired, unknown

* `--not-status` _STATUS_

* `-e` _EVENT_, `--event` _EVENT_  
     Event name eg. HostAvail, PingResponse, AppStatus

* `--not-event` _EVENT_

* `-g` _GROUP_, `--group` _GROUP_  
     Event group eg. Application, Backup, Database, HA, Hardware, System, OS, Performance, Storage, Security, Web

* `--not-group` _GROUP_

* `--origin` _ORIGIN_
     Origin of the alert eg. alert-sender, alert-ganglia

* `--not-origin` _ORIGIN_

* `-v` VALUE, --value _VALUE_
     Event value eg. 100%, Down, PingFail, 55tps, ORA-1664

* `--not-value` _VALUE_

* `-T` TAGS, `--tags` _TAGS_  
     Tags can be single, double or triple tags eg. london, location=london, datacentre:location=london

* `--not-tags` _TAGS_

* `-t` TEXT, `--text` _TEXT_  
     Alert text

* `--not-text` _TEXT_

* `--type` _EVENT_`_`_TYPE_  
     Event type eg. snmptrapAlert, syslogAlert

* `--not-type` _TYPE_

* `--repeat` {true,false}

* `--show` _SHOW_  
     Show 'text', 'summary', 'times', 'attributes', 'details', 'tags', 'raw', 'history', 'counts' and 'color'

* `--oneline`  
     Shorthand for `--format '{i} {rd} {sa} {E} {S} {r} {g} {e} {v} {t}'`

* `--date` _DATE_  
     Date format of 'relative', 'local', 'iso', 'rfc', 'short' or 'raw'

* `--format` _FORMAT_  
     Format allows you to specify which information you want to show.

* `-o` _SORTBY_, `--orderby` _SORTBY_, `--sortby` _SORTBY_, `--sort-by` _SORTBY_  
     Sort by attribute (default: lastReceiveTime)

* `-w`, `--watch`  
     Periodically poll for new alerts every 2 seconds.

* `-n` _INTERVAL_, `--interval` _INTERVAL_  
     Change the default watch interval.

* `--count` _LIMIT_, `--limit` _LIMIT_

* `-q` QUERY, `--query` _QUERY_  
     Mongo-compliant query. Must be valid JSON.

* `--no-header`  
     Use with `--no-footer` to produce output that is suitable for processing by another program like `sed` or `awk`.

* `--no-footer`  
     Use with `--no-header` to produce output that is suitable for processing by another program like `sed` or `awk`.

* `-G`, `--color`, `--colour`  
     Synonym for `--show=color`

* `--output` _OUTPUT_  
     Output format of 'text', 'table' or 'json'

* `-j`, `--json`  
     JSON formatted output. Synonym for `--output json`.

* `-X`, `--delete`  
     Delete alerts that match the query. Use with caution.

* `-d`, `--dry-run`  
     Do not run. Output query and filter.

## EXIT STATUS

The `grep` utility exits with one of the following values:

```
0        One or more lines were selected.  
1        No lines were selected.  
>1       An error occurred.
```



## EXAMPLES

To list all alerts, use:

alert-query

To list all Web alerts received in the last 15 minutes, use:

alert-query --group Web --mins 15

To watch for new non-normal alerts from SolarWinds, use:

alert-query --watch --not-severity normal --origin solarwinds


## ENVIRONMENT

ALERTA_CONF
CLICOLOR

## FILES

`/etc/alerta/alerta.conf`

## STANDARDS
## NOTES

## BUGS

Report bugs to github issues.

## SEE ALSO

[`alerta.conf(5)`](/man/alerta-conf5/)