---
layout: manpage
title: alert-query(1)
permalink: /alert-query/
categories: manpage
tags: [cli, tool, api]
---

ALERT-QUERY(1)

NAME

alert-query - alert query tool

SYNOPIS

alert-query [OPTION]...

DESCRIPTION

Displays the latest alerts received by Alerta. One alert is shown per line unless --show is specified to display more details.

OPTIONS

List all alerts received optionally filtered by attributes. Sorts alerts in reverse chronological order unless --sort-by is specified.

-c FILE, --config-file 
        Configuration file for general settings. For example, setting the Alerta server name, API endpoint or local timezone.

--minutes=MINUTES, --hours=HOURS, --days=DAYS
          Show alerts for last X minutes, hours, days

-i ALERTID, --id=ALERTID
          Alert ID (can use 8-character abbreviated id)

-E ENVIRONMENT, --environment=ENVIRONMENT
          Environment eg. PROD, REL, QA, TEST, CODE, STAGE, DEV, LWP, INFRA

-S SERVICE, --svc=SERVICE, --service=SERVICE
          Service eg. R1, R2, Discussion, Soulmates, ContentAPI, MicroApp, FlexibleContent, Mutualisation, SharedSvcs, Network

-r RESOURCE, --resource=RESOURCE
         Resource under alarm eg. hostname, instance id, network device, application, URL, anything at all

-s SEVERITY, --severity=SEVERITY
          Severity eg. CRITICAL, MAJOR, MINOR, WARNING, NORMAL, INFORM, DEBUG

--status=STATUS
          Status eg. OPEN, ACK, CLOSED, EXPIRED

-e EVENT, --event=EVENT
          Event name eg. HostUp, HostDown, AppStatus, LoadHigh

-g GROUP, --group=GROUP
          Event group eg. Application, Backup, Database, HA, Hardware, Job, Network, OS, Performance, Security

-origin=ORIGIN
          Origin of the alert eg. alert-sender, alert-ganglia

-v VALUE, --value=VALUE
          Event value eg. 100%, Down, PingFail, 55tps, ORA-1664

-T TAGS, --tags=TAGS
          Tags can be single, double or triple tags eg. london, location=london, datacentre:location=london

-t TEXT, --text=TEXT
          Alert text.

--not-option
          Prefix any of the following options with –not to make the logical negation. --not-environment,
          --not-service, --not--resource, --not-severity, --not-status, --not-event,
          --not-group, --not-origin, --not-value, --not-tags, --not-text.

--show=SHOW
          Show text, summary, times, attributes, details, tags, raw,  history, counts and color/ colour

-o SORTBY, --sort-by=SORTBY, --order-by=SORTBY
          Sort by createTime, receiveTime or lastReceiveTime (default: lastReceiveTime)

-w, --watch
          Periodically poll for new alerts every 2 seconds.

-n INTERVAL, --interval=INTERVAL
          Change the default watch interval.

-c LIMIT, --count=LIMIT, --limit=LIMIT
          Limit the number of alerts returned. If more alerts are available a plus sign (+) will appear next to the total in the footer.

-q, --query
          Mongo-compliant query string. Must be valid JSON.

--no-header
          Use with --no-footer to produce output that is suitable for processing by another program like sed or awk.

--no-footer
          Use with --no-header to produce output that is suitable for processing by another program like sed or awk.

--color, --colour
          Synonym for --show=color

-j, --json
          JSON formatted output.

-d, --dry-run
          Do not run. Output query and filter.

SYSTEM SETTINGS

timezone
          Set timezone (default: Europe/London)

api_host
          Set API hostname (default: localhost)

api_port
          Set API port (default: 80)

api_endpoint
          Set API endpoint URL (default: /alerta/api/v2)

EXAMPLES

To list all alerts, use:

alert-query

To list all Web alerts received in the last 15 minutes, use:

alert-query --group Web --mins 15

To watch for new non-normal alerts from SolarWinds, use:

alert-query --watch --not-severity normal --origin solarwinds

FILES

/etc/alerta.conf, ALERTA_CONF, $HOME/.alerta.conf

The global configuration file location is /etc/alerta.conf by default. However, this can be over-ridden on a per user or per environment basis.

If an environment variable called ALERTA_CONF refers to a valid configuration file its options will over-ride any global options set in the /etc/alerta.conf file. Likewise, if a file called $HOME/.alerta.conf exists it will be in preference to either the global or environment options. 

An example user-defined options file follows:

[DEFAULT]
timezone = Australia/Sydney
show = text,details
color = yes
limit = 100
BUGS

There is a limitation with the version of MongoDB that is used as the alert databse that does not allow more than four regular expressions in a query.

AUTHOR

Written by Nick Satterly <nick.satterly@guardian.co.uk>

COPYRIGHT

Copyright 2012 Guardian News and Media. Licensed under the Apache License, Version 2.0 

SEE ALSO

More information is available on the GitHub wiki: https://github.com/guardian/alerta/wiki