---
layout: docs
title: Alerta FAQ
permalink: /faq/
categories: general
tags: [help, faq]
---

# Alerta FAQ

### Q. Why is it called "alerta"?

When it was first proposed it was decided we needing something to do the alerting now that we had the metric collection side of things under control. It was generically known as the "alerter" and so when it came to name it properly the name had stuck. In the end it was decided to just slightly modify the spelling to produce a homophone -- and it also just happens to mean "alert" in spanish.

### Q. How is environment used?

The environment can be used to partition up your infrastructure into meaningful groups. For example, you could simply define `PRODUCTION` and `DEVELOPMENT` environments or if more granularity is required also define `RELEASE`, `QA`, `INFRASTRUCTURE` etc. Whatever you define is entirely up to you. Be aware that environment is used to namespace the resource so that `web01` in `PRODUCTION` would be treated as a different alert source to `web01` in `DEVELOPMENT`.
