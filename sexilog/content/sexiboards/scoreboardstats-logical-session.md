---
title: "ScoreboardStats Logical Session"
date: 2015-03-06T15:27:17+06:00
draft: false
# page title background image
bg_image: "images/dashboard-logicalsession.png"
# Research image
image: "images/sexiboards/dashboard-logicalsession-360x200.png"
# type
type: "sexiboards"
---


The **LogicalSession** dashboard leverage one of the vpxd-profiler statistic counters logged in vpxd-profiler.log file.

The `Vpxd::Session::LogicalSession` counter helps you **track the vCenter server active & idle connexions** [limited by the maxSessionCount vpxd.cfg parameter][1].

![dashboard-logicalsession1][2]

In the following screenshot you can observe vCenter connections during **backup window**. This dashboard actually helped troubleshooting a real backup jobs scheduling issue as the default maximum session count was reached sometimes.

![dashboard-logicalsession][3]
![dashboard-logicalsession0][4]

 This dashboard is actually a template and needs a bit of configuration. You need to replace the vCenter names by yours.

This dashboard is embedded in SexiLog. If you want up-to-date version for your own platform, the Gist code for this dashboard is:  `https://gist.github.com/sexibytes/f19810766d1780e7d435` 

_More information about dashboard import in Kibana is available **[here][5]**_

[1]: http://kb.vmware.com/kb/2004663
[2]: /images/dashboard-logicalsession1.png
[3]: /images/dashboard-logicalsession.png
[4]: /images/dashboard-logicalsession0.png
[5]: /rtfm/#dashboardimport "Documentation"
