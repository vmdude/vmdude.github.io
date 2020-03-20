---
title: "QuickStart"
# page title background image
bg_image: "images/header_veeam2.png"
# meta description
description : "Here is how you can get and quickly setup this awesome appliance named SexiLog."
type: "single-post"
---


### Step 1: Get SexiLog

[Download OVA applicance – v0.99g “Ailuropoda”](http://files.sexilog.fr/SexiLog.ova)

:warning: SHA1 sum is: `7cb35001b04080370ba7e34bb3113d784b880025  SexiLog.ova`

You can find all release notes on our GitHub Milestones page: [https://github.com/sexibytes/sexilog/milestones?state=closed](https://github.com/sexibytes/sexilog/milestones?state=closed)

:blue_book: **This appliance is sized for 1500 msg/s (~20 ESXi hosts)**. If you need someting bigger, you can increase vCPU, vRAM and [vmdk size](http://www.sexilog.fr/rtfm/#vmdk) but you may also need to tune [ES_HEAP_SIZE](http://www.elastic.co/guide/en/elasticsearch/guide/current/heap-sizing.html), LS_HEAP_SIZE and [logstash filterworkers flag](http://logstash.net/docs/1.4.2/flags).

If you prefer to build it yourself, you can follow the [Cookbook](http://www.sexilog.fr/cookbook/)

&nbsp;

### Step 2: Deploy

SexiLog appliance aimed to be deployed on a [VMware vSphere™](http://www.vmware.com) environment which can be achieve via several ways:

*   **vSphere client** ([http://pubs.vmware.com/vsphere-50/topic/com.vmware.vsphere.vm_admin.doc_50/GUID-6C847F77-8CB2-4187-BD7F-E7D3D5BD897B.html](http://pubs.vmware.com/vsphere-50/topic/com.vmware.vsphere.vm_admin.doc_50/GUID-6C847F77-8CB2-4187-BD7F-E7D3D5BD897B.html))
*   **vSphere Web Client** ([http://pubs.vmware.com/vsphere-55/topic/com.vmware.vsphere.vm_admin.doc/GUID-AFEDC48B-C96F-4088-9C1F-4F0A30E965DE.html](http://pubs.vmware.com/vsphere-55/topic/com.vmware.vsphere.vm_admin.doc/GUID-AFEDC48B-C96F-4088-9C1F-4F0A30E965DE.html))
*   **VMware OVF Tool command-line utility** ([https://www.vmware.com/support/developer/ovf/](https://www.vmware.com/support/developer/ovf/))

&nbsp;

### Step 3: Configure

SexiLog is pre-configured in DHCP mode but it’s possible to switch to static mode thanks to **SexiMenu** (this tool is launched automatically when you connect via SSH/console or can be launched with`/root/seximenu/seximenu.sh`).

![SexiMenu](/images/seximenu.png)

Beside menu `0)` to `4)` that matches common operations which are self explanatory (logout, access to shell, reboot or halt system, restart SexiLog services), menu `5)` to `7)` let you configure appliance network, keymap (useful for console troubleshooting on azerty keyboard) and configure Riemann settings (for e-mail alerting).

:blue_book: **SexiMenu** will drive you around the configuration options

&nbsp;

### Step 4: Redirect ESXi syslog

To make [VMware ESXi™](http://www.vmware.com) send logs to your SexiLog appliance, you need to add `udp://your_appliance_fqdn_or_ipv4:514` in the advanced option `Syslog.global.logHost`:

![dashboard-esxi-syslog](/images/dashboard-esxi-syslog.png)

You can use this PowerCLI script to automate the task: [http://blogs.vmware.com/vsphere/2013/07/log-insight-bulk-esxi-host-configuration-with-powercli.html](http://blogs.vmware.com/vsphere/2013/07/log-insight-bulk-esxi-host-configuration-with-powercli.html)

As instructed by the VMware [**KB2003322**](http://kb.vmware.com/kb/2003322) you may need to open the [VMware ESXi™](http://www.vmware.com) firewall to let the syslog traffic pass through.

:blue_book: And here you are, relax and start searching!

&nbsp;

### Annex: Credentials & URL

The default `root` password is `Sex!Log`. The default keyboard layout is **Qwerty US**.

The **SexiLog** web interface (ie **Kibana**) is listening on TCP port 80 so you can reach it at [http://your_appliance_fqdn_or_ipv4/](http://demo.sexilog.fr)


![dashboard-home](/images/dashboard-home.png)
