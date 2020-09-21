---
title: How Simple Became Complicated
date: 2019-05-11
---


Few months ago, we had the amazing opportunity to deploy PoliGraf in a \***BIG**\* company. Think petabytes scale.

In the past, [we have already been challenged to make our tool scalable](http://www.poligraf.io/big-scale-ability/), but not that much:

*   50+ vCenter
*   6000+ ESX
*   115000+ VM
*   18000+ datastores
*   1000+ clusters
*   200ms+ network latency for half vCenter

After many hours of hard work, almost total rewrite of our code and a massive use of hash tables, we are proud to show you a sneak peek of the next PoliGraf version (0.99f) connected to 53 vCenters:

[![](/img/poligraf099f_superstats.jpg)](http://www.poligraf.io/how-simple-became-complicated/poligraf099f_superstats/)

And since the customer hasn’t figured out how to handle syslog for it’s 6000+ ESX yet, we added a “bad” events dashboard (warnings and errors) grouped by clusters:

[![](/img/poligraf099f_badevents.jpg)](http://www.poligraf.io/how-simple-became-complicated/poligraf099f_badevents/)

[![](/img/poligraf099f_exevents-1.jpg)](http://www.poligraf.io/poligraf099f_exevents-2/)

With a **single VM** (16 vCPU and 24GB vRAM), the polling is only taking **3 minutes** (maximum) to complete:

[![](/img/poligraf099f_pullexectime.jpg)](http://www.poligraf.io/how-simple-became-complicated/poligraf099f_pullexectime/)

Stay tuned 😉
