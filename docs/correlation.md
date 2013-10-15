---
layout: docs
title: Event Correlation
permalink: /correlation/
categories: server
tags: [ecs, esper, riemann]
---

### Simple Event Correlation

An important characteristic of any alert status console is to only display the most recent alert for a particular event on a resource. For example, if a node has gone down then the same alert should be cleared when the node comes back up. Generating a new alert in the console means the operator needs to work out if they are correlated manually which should not be necessary.

In Alerta, there are two supported methods for simple event correlation of events from the same resource. Correlation of events from different resources is a future enhancement (it will probably require something like ESPER or Drools).

Both of the methods described below are equally valid. Which to use in a particular situation is a matter of user preference. 

#### Method 1. Status Events
Use the same `event` name and the `value` is used to indicate the latest status. eg. "NodeStatus" event with values of "Up" or "Down"

#### Method 2. Correlated Events
Use different `event` names and include the list of related events in the `correlatedEvents` attribute eg. "NodeUp" and "NodeDown" events with `correlatedEvents` set to "NodeUp,NodeDown"

#### Example
The table below shows how the two methods might compare when generating Node Up/Down events.

<table>
  <thead><th>Method</th><th><code>event</code></th><th><code>value</code></th><th><code>correlatedEvents</code></th></thead>
  <tbody>
    <tr><td>Status</td><td>NodeStatus</td><td>Up or Down</td><td>do not use</td></tr>
    <tr><td>Correlated</td><td>NodeUp or NodeDown</td><td>time up or down</td><td>NodeUp,NodeDown</td></tr>
  </tbody>
</table>

Note: For alerts using the "status" method the event name does not actually need to include the word "Status". Another example might be to use the event name "SwapUtil" for swap alerts no matter what the severity was.

### Complex Event Correlation

See Riemann.

