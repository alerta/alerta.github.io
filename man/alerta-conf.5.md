---
layout: manpage
title: alerta.conf(5)
permalink: /alerta-conf5/
categories: manpage
tags: [man5]
---

## NAME
`alerta.conf` -- alert monitoring system daemon configuration

## SYNOPSIS
`/etc/alerta/alerta/conf`  
`$ALERTA_CONF`  
`$HOME/.alerta.conf`

## DESCRIPTION

## NAME
## SYNOPSIS
## CONFIGURATION      [Normally only in Section 4]
## DESCRIPTION
## OPTIONS            [Normally only in Sections 1, 8]
## EXIT STATUS        [Normally only in Sections 1, 8]
## RETURN VALUE       [Normally only in Sections 2, 3]
## ERRORS             [Typically only in Sections 2, 3]
## ENVIRONMENT
## FILES
## ATTRIBUTES         [Normally only in Sections 2, 3]
## VERSIONS           [Normally only in Sections 2, 3]
## CONFORMING TO
## NOTES
## BUGS
## EXAMPLE
## SEE ALSO


---
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

---
SYSTEM SETTINGS

timezone
          Set timezone (default: Europe/London)

api_host
          Set API hostname (default: localhost)

api_port
          Set API port (default: 80)

api_endpoint
          Set API endpoint URL (default: /alerta/api/v2)

---
```
[DEFAULT]
api_host = localhost
api_port = 8081
api_version = v2
carbon_host = localhost
carbon_port = 2003
carbon_protocol = udp
conf_file = /etc/alerta/alerta.conf,/Users/nsatterl/.alerta.conf
console_limit = 1000
dashboard_dir = /Users/nsatterl/Projects/alerta/alerta/dashboard/v2/assets/
debug = True
disable_flag = /var/run/alerta/alerta.disable
dynect_customer =
dynect_password =
dynect_username =
ec2_regions = ['eu-west-1', 'us-east-1']
es_host = localhost
es_index = alerta-%Y.%m.%d
es_port = 9200
fog_file = /etc/fog/alerta.conf
foreground = False
forward_duplicate = False
global_timeout = 86400
gmetric_host = localhost
gmetric_port = 8649
gmetric_protocol = udp
gmetric_spoof = 10.1.1.1:alerta
graphite_prefix = alerta.macbookpro.home
history_limit = -10
http_proxy = None
https_proxy = None
inbound_queue = /exchange/alerts
irc_channel = #alerts
irc_host = irc
irc_port = 6667
irc_user = alerta
log_dir = /var/log/alerta
log_file = /dev/null
loop_every = 30
mail_list = websys@guardian.co.uk
mail_user = alerta@guardian.co.uk
mongo_collection = alerts
mongo_database = monitoring
mongo_host = localhost
mongo_password =
mongo_port = 27017
mongo_username = admin
nagios_plugins = /usr/lib64/nagios/plugins
outbound_queue = /queue/logger
outbound_topic = /topic/notify
pagerduty_api_key =
pagerduty_endpoint = https://events.pagerduty.com/generic/2010-04-15/create_event.json
parser_dir = /etc/alerta/parsers
pid_dir = /var/run/alerta
ping_file = /etc/alerta/alert-pinger.targets
ping_max_retries = 2
ping_max_timeout = 15
ping_slow_critical = 10
ping_slow_warning = 5
rabbit_host = localhost
rabbit_password = guest
rabbit_port = 5672
rabbit_use_ssl = False
rabbit_userid = guest
rabbit_virtual_host = /
server_threads = 4
show_settings = True
smtp_host = smtp
smtp_port = 25
solarwinds_group = websys
solarwinds_host = solarwinds
solarwinds_password =
solarwinds_username = admin
statsd_host = localhost
statsd_port = 8125
stomp_host = localhost
stomp_port = 61613
syslog_facility = local7
syslog_tcp_port = 514
syslog_udp_port = 514
timezone = Europe/London
token_limit = 20
token_rate = 2
urlmon_file = /etc/alerta/alert-urlmon.targets
urlmon_max_timeout = 15
urlmon_slow_critical = 5000
urlmon_slow_warning = 2000
use_stderr = False
use_syslog = yes
user_id = alerta
verbose = False
yaml_config = /etc/alerta/alerta.yaml
```

## SEE ALSO
[`alerta(1)`](/man/alerta1/), [`alert-query(1)`](/man/alert-query1/), [`alert-sender(1)`](/man/alert-sender1/)
