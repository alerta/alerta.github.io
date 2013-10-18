---
layout: manpage
title: alert-urlmon(1)
permalink: /alert-urlmon1/
categories: manpage
tags: [man1]
---

## NAME
`alert-urlmon` -- alert URL monitor

## SYNOPSIS
`alert-urlmon` [`-h`] [`-c` _FILE_] [`--version`] [`--debug`] [`--verbose`] [`--log-dir` _DIR_]  
              [`--log-file` _FILE_] [`--pid-dir` _DIR_] [`--use-syslog`] [`--use-stderr`]  
              [`--yaml-config` _FILE_] [`--show-settings`] [`-f`]

## DESCRIPTION


## OPTIONS

* `-h`, `--help`  
      show this help message and exit  

* `-c` _FILE_, `--conf-file` _FILE_  
      Specify config file (default: /etc/alerta/alerta.conf).

* `--version`  
             show program's version number and exit
* `--debug`  
               Log level DEBUG and higher (default: WARNING)
* `--verbose`  
             Log level INFO and higher (default: WARNING)
* `--log-dir` _DIR_  
         Log directory, prepended to --log-file
* `--log-file` _FILE_  
       Log file name
* `--pid-dir` _DIR_  
         PID directory
* `--use-syslog`  
         Send errors to syslog
* `--use-stderr`  
          Send to console stderr
* `--yaml-config` _FILE_  
    Path to the YAML configuration
* `--show-settings`  
       Output evaluated configuration options
* `-f`, `--foreground`  
      Do not fork, run in the foreground

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
`/etc/init.d/alerta`
`/var/log/alerta/alerta.log`

## STANDARDS
## NOTES

## BUGS

Report bugs to github issues.

## SEE ALSO

[`alerta.conf(5)`](/man/alerta-conf5/), [`alert-urlmon.targets(5)`](/man/urlmon-targets5/)
