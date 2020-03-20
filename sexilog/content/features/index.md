---
title: "Features"
# page title background image
bg_image: "images/header_snapshot.png"
# meta description
description : "Here is what's under the hood."
type: "single-post"
---


### Features

![features](/images/features.png)

&nbsp;

### Inputs

SexiLog listens on several ports for log sourcing:

*   `UDP/514` for **syslog** protocol: A Lot of [grok](http://logstash.net/docs/1.4.2/filters/grok) magic designed for [VMware ESXi™](http://www.vmware.com) here but you can also send anything that [looks like syslog](https://tools.ietf.org/html/rfc5424). We designed a very tolerant filter 🙂
*   `UDP/162` for **SNMP traps** internaly forwarded as syslog: A bit of grok magic here too, designed for [VMware ESXi™](http://www.vmware.com) and [Veeam B&R™](http://www.veeam.com) but you can send any SNMP traps as well
*   `UDP/1514` for **vCenter logs** in json [forwared by nxlog agent](http://www.sexilog.fr/rtfm/#vpxdlogs): The grok filters here are dedicated to vpxd and vpxd-profiler exclusively
*   `UDP/1515` for **Windows eventlog** forwarded by nxlog agent from your Windows vCenter: You can forward from any Windows as well

&nbsp;

### Filters

SexiLog is loaded with a lot of logstash grok filters to enhance [VMware ESXi™](http://www.vmware.com) logs (mostly).

Here are some examples of few messages where colorized parts are parsed and “fielded” in elasticsearch as you can see in screenshots below:

> <**14**\>**2014-12-10T18:01:03.496Z esx.vmware.com vobd**: \[**scsiCorrelator**\] 14807183227307us: \[**esx.problem.scsi.device.io.latency.high**\] Device **naa.60a9800041764b6c463f437868556b7a** performance has deteriorated. I/O latency increased from average value of 1343 microseconds to **28022** microseconds.
> 
> * * *
> 
> <**181**\>**2015-01-28T11:30:29.653Z** **esx.vmware.com** **vmkernel**: cpu4:19834926)NMP: **nmp\_PathDetermineFailure**:2084: SCSI cmd RESERVE failed on path **vmhba0:C0:T1:L15**, reservation state on device **naa.6006016084b02800b4a07969cd74e011** is unknown.
> 
> * * *
> 
> <**166**\>**2015-01-25T20:16:44.502Z** **esx.vmware.com Hostd**: \[34F99B90 verbose ‘vm:/vmfs/volumes/**548076ca-1a5e9feb-b886-fc15b415a120**/**vm\_name**/**vmx\_name**.vmx’\] Handling message \_vmx3: There is no more **space** for virtual disk PARG1TZCTXWEB02.vmdk. You might be able to continue this session by freeing disk **space** on the relevant volume, and clicking Retry. Click Cancel to terminate this session.

| | |
|:---:|:---:|
| ![](/images/micro_facility.png) | ![](/images/micro_program.png) |
| ![](/images/dashboard-quiescing_micro.png) | ![](/images/micro_correlator.png) |
| ![](/images/micro_hostname.png) | ![](/images/micro_naa.png) |


&nbsp;

### Outputs

Sexilog comes with pre-configured kibana dashboards (aka [SexiBoards](http://www.sexilog.fr/sexiboards/)) where you’ll find critical information about your [VMware vSphere™](http://www.vmware.com) infrastructure.

The one you want to look at first and as often as possible (think wallscreen) is [SexiBoard:Kommandantur](http://www.sexilog.fr/sexiboards/kommandantur)

&nbsp;

![](/images/SexiBoard-Kommandantur.png)

&nbsp;

During on-call duty, lunch, beer or if you are AFK, you need a sharp and clear alerting system, that’s where Riemann comes in. **Logstash forwards filtered warnings and alerts to Riemann where they’re rolled up by type and send by e-mail.**

Medium alerts are aggregate and sent every hour. Critical ones are sent every minutes and have an `*` (asterisk) sign in the subject.

We configure Riemann e-mails with a strict format that will let you know with a single look what’s happening and where. Here are format details:

&nbsp;

![rieman_alert_format](/images/rieman_alert_format.png)

![](/images/rieman_alert_01.png)

![](/images/rieman_alert_03.png)

![](/images/rieman_alert_02.png)

![](/images/rieman_alert_00.png)

![](/images/rieman_alert_04.png)
