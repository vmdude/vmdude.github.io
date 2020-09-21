---
title: Welcome to Nova Prospekt
date: 2017-07-12
---


### Today we are very proud to announce the release of the fourth **PoliGraf** update: **0.99d** codename “Nova Prospekt”

In this new version, we’ve added the support of the new [vSphere 6.5](https://pubs.vmware.com/vsphere-65/index.jsp?topic=/com.vmware.wssdk.apiref.doc/index.html&single=true) & [vSAN 6.6](http://www.virtuallyghetto.com/2017/04/new-vsan-management-6-6-api-sdks-clis.html) APIs. We also embed the very up to date [Grafana 4.3](https://grafana.com/blog/2017/05/23/grafana-4.3-release/) and all the Debian 8.8 packages upgrades for security concerns.

*   **New features**
    *   [Multi Cluster Top N VM Snapshot](http://www.poligraf.io/vsphere-sexipanels/#multi-cluster-top-n-vm-snapshot) (many thanks to Jo for this great idea)
    *   **[All|Multi Datastore Usage Distribution](http://www.poligraf.io/vsphere-sexipanels/#datastore-usage-distribution)**
    *   [Multi Cluster vCPU pCPU](http://www.poligraf.io/vsphere-sexipanels/#multi-cluster-vcpu-pcpu)
    *   **[All|Multi Cluster Top N VM Latency](http://www.poligraf.io/vsphere-sexipanels/#top-n-vm-latency)**
    *   [Multi Cluster Top N VMFS Latency](http://www.poligraf.io/vsphere-sexipanels/#top-n-vmfs-latency)
    *   **[SAN Monitor 2nd FTT](http://www.poligraf.io/vsan-sexipanels/#vsan-monitor-2nd-ftt)**
    *   [VSAN Monitor “66”](http://www.poligraf.io/vsan-sexipanels/#vsan-monitor) (resyncRead & client.cachestats)
    *   [VSAN Disk Utilization](http://www.poligraf.io/vsan-sexipanels/#vsan-disk-utilization)
    *   **[New All Cluster Top N VM Stats](http://www.poligraf.io/vsphere-sexipanels/#vsphere-top-n-vm-stats) (featuring CPU Ready & snapshots)**

*   **Enhancements and fixes**
    *   [vCPU/pCPU ratio in (Multi) Cluster FullStats](http://www.poligraf.io/vsphere-sexipanels/#cluster-fullstats)
    *   [Power usage in (Multi) Cluster FullStats](http://www.poligraf.io/vsphere-sexipanels/#cluster-fullstats)
    *   [ESX hostname in VSAN NAA Latency dashboard](http://www.poligraf.io/vsan-sexipanels/#vsan-naa-latency)
    *   **[Allocated vRAM in (Multi) Cluster FullStats](http://www.poligraf.io/vsphere-sexipanels/#cluster-fullstats)**
    *   [VM & Cluster dashboard links in Offline Inventory](http://www.poligraf.io/web-admin/#offline-inventory) \*
    *   [VM “blue” folder path in Offline Inventory](http://www.poligraf.io/web-admin/#offline-inventory) \*
    *   [**120d Auto Purge**](http://www.poligraf.io/web-admin/#house-cleaner)
    *   Various bug fix

Because of its size and unlike the previous ones, **the 0.99d update is distributed as an iso file** that you’ll need to mount into your existing PoliGraf VM to **launch the embedded update script**. But don’t worry, we made it easy as always:

First, download the update iso file:

[Download ISO Update – v0.99d “Nova Prospekt”](http://files.poligraf.io/SexiUpdate099d.iso)

{{< hint info >}}
SHA1 sum is: `0cd824b52be3a41b368a80adf74a69a66612002d SexiUpdate099d.iso`
{{< /hint >}}

{{< hint danger >}}
Before any modification, **it is strongly advised to make a snapshot of your VM** in case of an outage during the update process. You’ll be asked for it at the beginning of the update process.
{{< /hint >}}

Now, just mount the **SexiUpdate099d.iso** update file the way you like the most, from a your local disk or a datastore:

![](/img/poligraf_099d_iso.jpg)

Then mount the “cdrom” inside the guest and launch the update script:

```
mount /media/cdrom
bash /media/cdrom/sexiupdate.sh
```

![](/img/poligraf_099d_sexiupdate.jpg)

The update process usually takes between **5 and 10min** depending on the VM “hardware” resources. Once finished, press **ENTER** to reboot and enjoy your new PoliGraf!

![](/img/poligraf_099d_reboot.jpg)

If you are new to PoliGraf, **the latest appliance is already available** on [the Quickstart page](http://www.poligraf.io/quickstart/).

![](/img/poligraf_crab_v4.jpg)

_\* For those who can’t wait the next Offline Inventory refresh (every 6h) to experience the new features, please use [the manual override to force the refresh](http://www.poligraf.io/web-admin/#refresh-inventory)._