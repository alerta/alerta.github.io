---
layout: manpage
title: alert-sender(1)
permalink: /alert-sender/
categories: manpage
---

alert-sender(1) -- send alerts to alerta server
===============================================

## SYNOPSIS

`alert-sender` [-h] [-c FILE] [-r RESOURCE] [-e EVENT] [-C CORRELATE]
                    [-g GROUP] [-v VALUE] [--status STATUS] [-s SEVERITY]
                    [-E ENV] [-S SERVICE] [-T TAGS] [-t TEXT] [--summary TEXT]
                    [--more TEXT] [--graphs URLS] [-o TIMEOUT]
                    [--type EVENT_TYPE] [-H] [-O ORIGIN] [-q] [-d] [--version]
                    [--debug] [--verbose] [--log-dir DIR] [--log-file FILE]
                    [--pid-dir DIR] [--use-syslog] [--use-stderr]
                    [--yaml-config FILE] [--show-settings]


## DESCRIPTION



## OPTIONS

  -h, --help            show this help message and exit
  -c FILE, --conf-file FILE
                        Specify config file (default: /etc/alerta/alerta.conf)
  -r RESOURCE, --resource RESOURCE
                        Resource under alarm eg. hostname, network device,
                        application, web address.
  -e EVENT, --event EVENT
                        Event name eg. NodeDown, QUEUE:LENGTH:EXCEEDED,
                        coldStart, LOG_ERROR
  -C CORRELATE, --correlate CORRELATE
                        List of events to correlate together eg. node_up and
                        node_down
  -g GROUP, --group GROUP
                        Event group eg. Application, Backup, Database, HA,
                        Hardware, Job, Network, OS, Performance, Security
  -v VALUE, --value VALUE
                        Event value eg. 100%, Down, PingFail, 55tps, ORA-1664
  --status STATUS       Status eg. Open, Ack, Closed, Unknown (default:
                        Unknown)
  -s SEVERITY, --severity SEVERITY
                        Severity eg. Critical, Major, Minor, Warning, Normal,
                        Informational, Debug (default: Normal)
  -E ENV, --environment ENV
                        List of effected environments eg. PROD, REL, QA, TEST,
                        CODE, STAGE, DEV, LWP, INFRA
  -S SERVICE, --svc SERVICE, --service SERVICE
                        List of effected services eg. R1, R2, Frontend,
                        Discussion, ContentAPI, MicroApp, FlexibleContent,
                        Identity, Mobile, Soulmates, Network, SharedSvcs
  -T TAGS, --tag TAGS   Tag the event with anything and everything.
  -t TEXT, --text TEXT  Freeform alert text eg. Host not responding to ping.
  --summary TEXT        Summary text suitable for SMS, pager or email subject.
  --more TEXT           More information eg. a link to a Wiki, ticket number
                        or call reference.
  --graphs URLS         List of graph URLs.
  -o TIMEOUT, --timeout TIMEOUT
                        Timeout in seconds that OPEN alert will persist in
                        webapp.
  --type EVENT_TYPE     Event type eg. exceptionAlert, serviceAlert
  -H, --heartbeat       Send heartbeat to server.
  -O ORIGIN, --origin ORIGIN
                        Origin of heartbeat. Usually an application instance.
  -q, --quiet           Do not display assigned alert id.
  -d, --dry-run         Do not send alert. Output as Curl.
  --version             show program's version number and exit
  --debug               Log level DEBUG and higher (default: WARNING)
  --verbose             Log level INFO and higher (default: WARNING)
  --log-dir DIR         Log directory, prepended to --log-file
  --log-file FILE       Log file name
  --pid-dir DIR         PID directory
  --use-syslog          Send errors to syslog
  --use-stderr          Send to console stderr
  --yaml-config FILE    Path to the YAML configuration
  --show-settings       Output evaluated configuration optionse

  ## EXAMPLES


  ## BUGS


  ## COPYRIGHT


  ## SEE ALSO

