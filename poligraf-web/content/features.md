---
title: features
weight: 50
---


![](/img/poligraf_archi_v21.jpg)

**PoliGraf is a vSphere centric Graphite appliance with a Grafana frontend**. Here is what’s under the hood:

*   **Carbon** is listening on TCP:2003 so you can [send any metrics you like in plaintext](http://graphite.readthedocs.org/en/latest/feeding-carbon.html) (like [Windows counters](https://ssc-serv.com/graphite.shtml)…)
*   **[vSphere SDK for Perl](https://developercenter.vmware.com/web/sdk/60/vsphere-perl)** is used to pull VI and VSAN metrics from VMware vCenter APIs and pushed to carbon.
*   **[Collectd](https://collectd.org/)** is here to monitor your PoliGraf appliance (see the [Home page](http://www.poligraf.io/web-admin/)) but it will also be used to collect SNMP metrics in the future.
*   **Grafana** uses **Graphite-Web** APIs to query **Whisper** files and produce the gorgeous dashboards we love so much!

The heart of **PoliGraf** is the famous highly scalable real-time graphing system : **Graphite**. [As described by his creator](http://graphite.readthedocs.org/en/latest/overview.html), it consists of three major components:

1.  **Graphite-Web**, a Django-based web application that renders graphs and dashboards
2.  The **Carbon** metric processing daemons
3.  The **Whisper** time-series database library

![graphite_overview](/img/graphite_overview.png)
