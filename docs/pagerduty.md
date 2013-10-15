---
layout: docs
title: PagerDuty
permalink: /pagerduty/
categories: server
tags: [paging, sms]
---

# Alert PagerDuty

Integration with PagerDuty is currently only uni-directional. That is, alerts and actions in the alert console will trigger events, acknowledges and resolves in PagerDuty and update notification and escalations procedures accordingly.

However, a direct acknowledge or resolve in PagerDuty will NOT be reflected back in Alerta. This requires additional work because PagerDuty does not provide any callback mechanism. The solution is to continually query the REST API for updates to any incidents and then update the corresponding alert in Alerta.

## Configuration Options

<table>
  <thead><th>Option</th><th>Description</th><th>Default</th></thead>
  <tbody>
    <tr><td><code>pagerduty_endpoint</code></td><td>Incident API Endpoint</td><td><code>https://events.pagerduty.com/generic/2010-04-15/create_event.json</code></td></tr>
    <tr><td><code>pagerduty_api_key</code></td><td>Incident API Key</td><td><code>None</code> eg. <code>7e4e7ce7176a4050bb9419a948ddd28d</code></td></tr>
  </tbody>
</table>

