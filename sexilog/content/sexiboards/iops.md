---
title: "IOps"
date: 2015-04-02T15:27:17+06:00
draft: false
# page title background image
bg_image: "images/dashboard-iops_0.png"
# Research image
image: "images/sexiboards/dashboard-iops_2-360x200.png"
# type
type: "sexiboards"
---


The **IOPS** dashboard is designed to let you have a quick look on the SIOC (aka [Storage I/O Control][1]) IOPS metric of your datastores. This dashboard is of course higly related to the [**IORM**][2] SexiBoard that provide latency metrics.

Like the datastore latency metric, having high IOPS activity could impact your storage performances.

![][3]

This dashboard is actually a template and needs a bit of configuration. You first need to [enable SIOC logging on your ESXi servers][4] and then replace the storage vendors names by your datastore ones in the queries. Since this dashboard is meant to display datastore IOPS per storage controller/array, you can use paterns like `san.vmax.*` or `nas.netapp.*` or any leading caracters you're using to manage your datastores.
    
    
    2014-12-10T18:33:04.910Z esx.vmware.com storageRM:   2707630 avglatency= 0.83 iops= 84 threshold= 30 Win = 30.00 ws= 30 devqdepth= 30 iocount= 4 noio= 0.00 coio= 0.05

This dashboard is embedded in SexiLog. If you want up-to-date version for your own platform, the Gist code for this dashboard is:  `https://gist.github.com/sexibytes/2625fe2a74234b3bda5c`

_More information about dashboard import in Kibana is available **[here][5]**_

[1]: http://kb.vmware.com/kb/1022091
[2]: /sexiboards/iorm/
[3]: /images/dashboard-iops_0.png
[4]: http://www.hypervisor.fr/?p=5252
[5]: /rtfm/#dashboardimport "Documentation"

  