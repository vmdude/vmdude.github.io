---
title: How Simple Became Complicated
date: 2019-05-11
---


Few months ago, we had the amazing opportunity to deploy SexiGraf in a \***BIG**\* company. Think petabytes scale.

In the past, [we have already been challenged to make our tool scalable](http://www.sexigraf.fr/big-scale-ability/), but not that much:

*   50+ vCenter
*   6000+ ESX
*   115000+ VM
*   18000+ datastores
*   1000+ clusters
*   200ms+ network latency for half vCenter

After many hours of hard work, almost total rewrite of our code and a massive use of hash tables, we are proud to show you a sneak peek of the next SexiGraf version (0.99f) connected to 53 vCenters:

[![](http://www.sexigraf.fr/wp-content/uploads/2019/05/sexigraf099f_superstats-1024x646.png)](http://www.sexigraf.fr/how-simple-became-complicated/sexigraf099f_superstats/)

And since the customer hasn’t figured out how to handle syslog for it’s 6000+ ESX yet, we added a “bad” events dashboard (warnings and errors) grouped by clusters:

[![](http://www.sexigraf.fr/wp-content/uploads/2019/05/sexigraf099f_badevents-1024x646.png)](http://www.sexigraf.fr/how-simple-became-complicated/sexigraf099f_badevents/)

[![](http://www.sexigraf.fr/wp-content/uploads/2019/05/sexigraf099f_exevents-1-1024x638.png)](http://www.sexigraf.fr/sexigraf099f_exevents-2/)

With a **single VM** (16 vCPU and 24GB vRAM), the polling is only taking **3 minutes** (maximum) to complete:

[![](http://www.sexigraf.fr/wp-content/uploads/2019/05/sexigraf099f_pullexectime-1024x389.png)](http://www.sexigraf.fr/how-simple-became-complicated/sexigraf099f_pullexectime/)

Stay tuned 😉