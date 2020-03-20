---
title: "vMotion pre-copy stun time"
date: 2015-04-02T15:27:17+06:00
draft: false
# page title background image
bg_image: "images/dashboard-precopystuntime.png"
# Research image
image: "images/sexiboards/dashboard-precopystuntime-360x200.png"
# type
type: "sexiboards"
---


The **precopyStunTime** dashboard let you visualize the reported vmotion pre-copy stun time as explained in the [VMware vSphere vMotion][1] [Architecture, Performance and Best Practices in VMware vSphere 5 Performance Study][1]:

> During this final phase, the virtual machine is momentarily quiesced on the source vSphere host, the last set of memory changes are copied to the target vSphere host, and the virtual machine is resumed on the target vSphere host. The guest briefly pauses processing during this step. Although the duration of this phase is generally less than a second, **it is the most likely phase where the largest impact on guest performance** (an abrupt, temporary increase of latency) is observed. The impact depends on a variety of factors not limited to but including network infrastructure, shared storage configuration, host hardware, vSphere version, and dynamic guest workload.

If most of your vmotion precopyStunTime are under 500ms, you are safe, otherwise you may have to troubleshoot.
    
    
    2015-02-20T13:40:24.663Z esx.vmware.com Hostd: [52F4CB90 verbose 'VMotionSrc (1424439619388924)'] Set source task result precopyStunTime to 80477

 

![dashboard-precopystuntime][2]

 

This dashboard is embedded in SexiLog. If you want up-to-date version for your own platform, the Gist code for this dashboard is:  `https://gist.github.com/sexibytes/10dedaf94cc55bfdc938`

_More information about dashboard import in Kibana is available **[here][3]**_

[1]: http://www.vmware.com/files/pdf/vmotion-perf-vsphere5.pdf
[2]: /images/dashboard-precopystuntime.png
[3]: /rtfm/#dashboardimport "Documentation"

  