---
title: "vmodl.*"
date: 2015-04-02T15:27:17+06:00
draft: false
# page title background image
bg_image: "images/dashboard-vmodl.png"
# Research image
image: "images/sexiboards/dashboard-vmodl-360x200.png"
# type
type: "sexiboards"
---


VMODL stands for VMware Managed Object Design Language. The **vmodl** dashboard is a simple Kibana `topN` query on the `vmodl` field. This field is created everytime logstash see something like `vmodl.fault.object`.

 

![dashboard-vmodl][1]

 

This dashboard is embedded in SexiLog. If you want up-to-date version for your own platform, the Gist code for this dashboard is:  `https://gist.github.com/sexibytes/a012ac5a94477cbbc8e9`

_More information about dashboard import in Kibana is available **[here][2]**_

[1]: /images/dashboard-vmodl.png
[2]: /rtfm/#dashboardimport "Documentation"

  