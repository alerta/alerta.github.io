---
layout: docs
title: Troubleshooting
permalink: /troubleshooting/
categories: server
tags: [rabbitmq, httpd, mongodb, snmptrapd, elasticsearch]
---

### Restart Daemon Services

{% highlight bash %}
$ sudo /opt/bin/alertctl --stop
Shutting down alert-ircbot:                                [  OK  ]
Shutting down alert-pinger:                                [  OK  ]
Shutting down alert-urlmon:                                [  OK  ]
Shutting down alert-solarwinds:                            [  OK  ]
Shutting down alert-logger:                                [  OK  ]
Shutting down alert-aws:                                   [FAILED]
Shutting down alert-mailer:                                [  OK  ]
Shutting down alert-dynect:                                [  OK  ]
Shutting down alert-pagerduty:                             [  OK  ]
Shutting down alert-syslog:                                [  OK  ]
Shutting down alerta:                                      [  OK  ]
$ sudo service httpd stop
Stopping httpd:                                            [  OK  ]
$ sudo service mongod stop
Stopping mongod:                                           [  OK  ]
$ sudo service rabbitmq stop
rabbitmq: unrecognized service
$ sudo service rabbitmq-server stop
Stopping rabbitmq-server: rabbitmq-server.
$ sudo service elasticsearch stop
Stopping elasticsearch:                                    [  OK  ]
$ sudo service snmptrapd stop
Stopping snmptrapd:                                        [  OK  ]
{% endhighlight %}

1. start rabbitmq-server
2. start mongod
3. service elasticsearch start
4. service httpd start
5. /opt/bin/alertctl --start
6. service snmptrapd start
7. /opt/bin/alertctl --report

Log files

{% highlight bash %}
$ tail -f alerta/*.log mongo/mongod.log rabbitmq/rabbit\@infmonalr51.log rabbitmq/rabbit\@infmonalr51-sasl.log
{% endhighlight %}

References

