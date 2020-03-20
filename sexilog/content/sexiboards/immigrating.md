---
title: "Immigrating"
date: 2015-04-13T15:27:17+06:00
draft: false
# page title background image
bg_image: "images/sexiboards/dashboard-immigrating.png"
# Research image
image: "images/sexiboards/dashboard-immigrating-360x200.png"
# type
type: "sexiboards"
---


The **Immigrating** dashboard let you visualize the top 20 most frequently migrated VM the last 7 days (manual, initiated by DRS or "self" vmotion – [aka Storage vMotion Fast Suspend/Resume][1]). If a cluster is heavily loaded or if the DRS migration threshold is too aggressive, some VM might be moved very often. Moreover, due to "self" vmotion, fully automated SDRS may also be source of immigrating messages in logs.


    2015-04-10T13:39:31.805Z esx.vmware.com Vpxa: [FFB4DB90 verbose 'Default' opID=WFU-781d38a8] [MIGRATE] (1428673170195986) immigrating VM at path /vmfs/volumes/4cd42fc3-cb64ed4a-d1bc-78e7d163b271/vm_name/vmx_name.vmx has vmid 677

![perf_vmotion][2]

According to [DRS Performance and Best Practices][3] :

> If the loads vary, DRS with a moderate threshold may achieve better throughput in the long run because it would recommend fewer migrations and hence incur a lower VMotion cost compared to DRS with an aggressive threshold.

![][4]

This dashboard is embedded in SexiLog. If you want up-to-date version for your own platform, the Gist code for this dashboard is:  `https://gist.github.com/sexibytes/13851fe3cfb15feaaf05`

_More information about dashboard import in Kibana is available **[here][5]**_

[1]: http://www.hypervisor.fr/?p=2865
[2]: /images/perf_vmotion.png
[3]: http://www.vmware.com/files/pdf/drs_performance_best_practices_wp.pdf
[4]: /images/dashboard-immigrating.png
[5]: /rtfm/#dashboardimport "Documentation"
