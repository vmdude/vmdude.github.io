---
title: vSAN dashboards empty after vSphere 6_7U1 update
date: 2018-10-25
---


Due to some [unexpected](https://twitter.com/gostev/status/1052679713154576388) changes in the vSAN 6.7U1 APIs, your SexiGraf appliance won’t be able to fetch vSAN metrics after updating your vCenter in 6.7.0 build 10244857 (aka U1). You’ll also get this error in the log:

> DIE Can’t call method “apiType” on an undefined value at /root/VsanPullStatistics.pl line 136.

Today we’re releasing a **quick fix** (0.99e1) on top of the 0.99e version, meaning you CAN’T apply this fix on previous version. This fix will be integrated in the future patches and releases.

[Download v0.99e1 “White Forest” patch](http://files.sexigraf.fr/sexigraf-0.99e1.sup)

{{< hint info >}}
SHA1 sum is: `9b422763d967d64402ae3971a9e00c31a0dec04b sexigraf-0.99e1.sup`
{{< /hint >}}
