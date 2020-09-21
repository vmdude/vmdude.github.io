---
title: You are now using version 0_99f "Traptown"!
date: 2019-05-23
---


### Today we are proud to announce the release of the sixth **PoliGraf** update: **0.99f** codename “Traptown”

**Edit 29 may 2019: For the few of you that would encounter this issue after upgrading, [please refer to this post for a fix](http://www.poligraf.io/cannot-read-property-graphiteversion-of-null/):**

![](/img/graphite_version_null.png)

In this new version, we’ve added the support of the new [vSAN 6.7U1](https://code.vmware.com/apis/398/vsan) API ([included in the 0.99e1 emergency patch](http://www.poligraf.io/vsan-dashboards-empty-after-vsphere-6-7u1-update/)).

*   **New features**
    *   [**SuperStats**](http://www.poligraf.io/vsphere-sexipanels/#cluster-superstats)
    *   [**vCenter Bad Events**](http://www.poligraf.io/vsphere-sexipanels/#vcenter-bad-events)
    *   [Early Storage Pod (aka Datastore Cluster) support](http://www.poligraf.io/vsphere-sexipanels/#multi-storage-pod-usage)
    *   [Grafana 4.6.5](https://community.grafana.com/t/release-notes-v4-6-x/3179)

*   **Enhancements and fixes**
    *   vSAN 6.7 Update 1 API fix
    *   Host CPU latency metric
    *   Offline Inventory and vSAN puller speed enhancement
    *   virtualExtent file type to identify vSAN and VVOL usage in the [Datastore Distribution dashboards](http://www.poligraf.io/vsphere-sexipanels/#datastore-usage-distribution).
    *   Added overcommit metric in [VMware All Clusters VM Stats dashboard](http://www.poligraf.io/vsphere-sexipanels/#vsphere-top-n-vm-stats)
    *   Added average vm left metrics for [Multi Cluster Capacity Planning dashboard](http://www.poligraf.io/vsphere-sexipanels/#multi-cluster-capacity-planning)
    *   [Various bug fix](https://github.com/sexibytes/poligraf/issues?q=is%3Aissue+milestone%3A%220.99e+-+White+Forest%22+is%3Aclosed)

To upgrade your existing appliance [get the 0.99f **S**exiGraf **U**pdate **P**ackage](http://files.poligraf.io/poligraf-0.99f.sup) and use it in the [Package Updater](http://www.poligraf.io/web-admin/#package-updater) (you won’t lost any data of course). The update process is the same since 0.99a so you can watch the [0.99a upgrade **recorded demo**](http://www.poligraf.io/you-are-now-using-version-0-99a-city-17/) if you need help.

{{< hint danger >}}
This update will \*ONLY\* apply if you’re running 0.99e “White Forest” version.  
Please reload your browser AFTER the update has finished.
{{< /hint >}}

If you are new to PoliGraf, **the latest appliance is already available** on [the Quickstart page](http://www.poligraf.io/quickstart/).

{{< hint warning >}}
**This the last PoliGraf update package**. Starting from now, we’ll only publish new ova packages and you’ll have to use [the data export/import feature](http://www.poligraf.io/web-admin/#export-import) to migrate your data and settings. We understand that this may be inconvenient but it’ll allow us to deliver a more up to date product more often.
{{< /hint >}}

![](/img/traptown.jpg)
