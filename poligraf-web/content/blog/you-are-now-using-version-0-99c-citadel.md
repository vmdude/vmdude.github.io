---
title: You are now using version 0_99c "Citadel"!
date: 2016-05-17
---


### Today we are proud to announce the release of the third **PoliGraf** update: **0.99c** codename “Citadel”

In this new version, we’ve added the support of the new [VSAN 6.2 API](https://vdc-download.vmware.com/vmwb-repository/dcr-public/22fd8549-6452-4017-9853-bc78f1b47bcf/b04dce40-37a8-4cac-a50d-92ebf3d98345//doc/index.html) but also FreeNAS and Windows!

*   **New features**
    *   **[VSAN Space Usage Report](http://www.poligraf.io/vsan-sexipanels/#vsan-space-usage-report)**
    *   [**FreeNAS** SexiPanel](http://www.poligraf.io/freenas-sexipanel/)
    *   [**Windows** SexiPanel](http://www.poligraf.io/windows-sexipanel/)
    *   VMware VSAN AF Monitor
    *   Multi VSAN Monitor

*   **Enhancements and fixes**
    *   VSAN witness support removed (no useful stats)
    *   [T10 support in VSAN NAA Latency dashboard](https://github.com/sexibytes/poligraf/issues/65)
    *   [Handle PerformanceManager spikes](https://github.com/sexibytes/poligraf/issues/63)
    *   Various bug fix
    *   OVF properties support

To upgrade your existing appliance [go get the **S**exiGraf **U**pdate **P**ackage on GitHub](https://github.com/sexibytes/poligraf/releases/tag/0.99c) and use it in the [Package Updater](http://www.poligraf.io/web-admin/#package-updater) (you won’t lost any data of course). The update process is the same since 0.99a so you can watch the [0.99a upgrade **recorded demo**](http://www.poligraf.io/you-are-now-using-version-0-99a-city-17/) if you need help.

If you are new to PoliGraf, **the latest appliance is already available** on [the Quickstart page](http://www.poligraf.io/quickstart/).

![](/img/Citadel_s.jpg)
