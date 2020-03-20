---
title: "NFSLock"
date: 2015-04-02T15:27:17+06:00
draft: false
# page title background image
bg_image: "images/dashboard-nfslock_1.png"
# Research image
image: "images/sexiboards/dashboard-nfslock-360x200.png"
# type
type: "sexiboards"
---


The **NFSLock** dashboard is a compilation of the major NFSLock issues like `Busy`, `Not found`, `exclusive lock` or `Invalid handle`:

![dashboard-nfslock_1][1]

If you need to troubleshoot, for instance `start|stop accessing` issues, just deactivate other filters to focus on your needs:

![dashboard-nfslock_accessing][2]

Associated VMware KB articles:

* http://kb.vmware.com/kb/2016122
* http://kb.vmware.com/kb/2046165
* http://kb.vmware.com/kb/2037507
* http://kb.vmware.com/kb/2013834
* http://kb.vmware.com/kb/2009718

This dashboard is embedded in SexiLog. If you want up-to-date version for your own platform, the Gist code for this dashboard is:  `https://gist.github.com/sexibytes/8db34e5c316ce4d3f258`

_More information about dashboard import in Kibana is available **[here][3]**_

[1]: /images/dashboard-nfslock_1.png
[2]: /images/dashboard-nfslock_accessing.png
[3]: /rtfm/#dashboardimport "Documentation"

  