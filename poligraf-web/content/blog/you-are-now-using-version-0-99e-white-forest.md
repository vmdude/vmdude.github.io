---
title: You are now using version 0_99e "White Forest"!
date: 2018-08-08
---


### Today we are proud to announce the release of the fifth **SexiGraf** update: **0.99e** codename “White Forest”

In this new version, we’ve added the support of the new [vSphere 6.7](https://code.vmware.com/apis/358/vsphere) & [vSAN 6.7](https://code.vmware.com/apis/398/vsan) APIs.

*   **New features**
    *   [**SexiGraf data Export & Import**](http://www.sexigraf.fr/web-admin/#export-import)
    *   [vmhba traffic in cluster dashboards](http://www.sexigraf.fr/vsphere-sexipanels/#cluster-fullstats)
    *   [VM network usage (bandwidth)](http://www.sexigraf.fr/vsphere-sexipanels/#vsphere-top-n-vm-stats)
    *   [VM disk usage (bandwidth)](http://www.sexigraf.fr/vsphere-sexipanels/#vsphere-top-n-vm-stats)
    *   **[vCenter Active Sessions (per user)](http://www.sexigraf.fr/vsphere-sexipanels/#vcenter-active-sessions)**

*   **Enhancements and fixes**
    *   **[VSAN Resync dashboard boost (per reason)](http://www.sexigraf.fr/vsan-sexipanels/#vsan-space-usage-report)**
    *   [Network errors and dropped counters](http://www.sexigraf.fr/vsphere-sexipanels/#cluster-network-usage)
    *   [Early HTTPS support](https://github.com/sexibytes/sexigraf/issues/146)
    *   [Wrong mem.allocated (aka vRAM) value fix](https://github.com/sexibytes/sexigraf/issues/152)
    *   [Various bug fix](https://github.com/sexibytes/sexigraf/issues?q=is%3Aissue+milestone%3A%220.99e+-+White+Forest%22+is%3Aclosed)

To upgrade your existing appliance [go get the **S**exiGraf **U**pdate **P**ackage on GitHub](https://github.com/sexibytes/sexigraf/releases/tag/0.99e) and use it in the [Package Updater](http://www.sexigraf.fr/web-admin/#package-updater) (you won’t lost any data of course). The update process is the same since 0.99a so you can watch the [0.99a upgrade **recorded demo**](http://www.sexigraf.fr/you-are-now-using-version-0-99a-city-17/) if you need help.

{{< hint danger >}}
This update will \*ONLY\* apply if you’re running 0.99d “Nova Prospekt” version.
{{< /hint >}}

If you are new to SexiGraf, **the latest appliance is already available** on [the Quickstart page](http://www.sexigraf.fr/quickstart/).

![](/img/White_forest_sign.png)
