---
title: "msg.*"
date: 2015-04-02T15:27:17+06:00
draft: false
# page title background image
bg_image: "images/dashboard-msgdictionary.png"
# Research image
image: "images/sexiboards/dashboard-msgdictionary-360x200.png"
# type
type: "sexiboards"
---


The **msg** dashboard is a simple Kibana `topN` query on the `msg` field. This field is created everytime logstash see something like "_msg.something.happens_".

This dashboard allow you to catch errors like `msg.uuid.altered`,  `msg.checkpoint.migration.nodata`,  `msg.svgaUI.badLimits`,  `msg.checkpoint.migration.maxSwitchoverTimeExceeded`, `msg.vmk.status.VMK_TIMEOUT` or `msg.vmotion.connect.failure`.


![dashboard-msgdictionary][1]


This dashboard is embedded in SexiLog. If you want up-to-date version for your own platform, the Gist code for this dashboard is:  `https://gist.github.com/sexibytes/304d615528fe7bb780ce`

_More information about dashboard import in Kibana is available **[here][2]**_

[1]: /images/dashboard-msgdictionary.png
[2]: /rtfm/#dashboardimport "Documentation"

  