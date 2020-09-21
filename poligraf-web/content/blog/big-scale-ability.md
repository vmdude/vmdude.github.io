---
title: Big Scale Ability
date: 2016-04-14
---


You may wonder how big you can go with PoliGraf? It turns out you already got the answer in your question: **BIG**

Check out how many ESXi and VM you can monitor with a **single** PoliGraf appliance:

![](/img/bigscaleflambx.jpg)

Yes, this is **968 ESX**, **12405 VMs**, **155 TB of RAM** and **1.7 PB of storage** over **18 vCenters**. We only pushed up the appliance to 8 vCPU and 16GB of vRAM to support the load.

We even support high latency networks since one of the vCenters pulling, in this case, takes around 10 minutes to complete where the polling is every 5 minutes:

![](/img/bigscalepull.jpg)
